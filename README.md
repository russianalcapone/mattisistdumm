import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.event.*;

/**
  *
  * Beschreibung
  *
  * @version 1.0 vom 03.09.2018
  * @author 
  */

public class Zahlenraten extends JFrame {
  // Anfang Attribute
  private JLabel jLabel1 = new JLabel();
  private JLabel jLabel2 = new JLabel();
  private JTextField versuchszahlTextField = new JTextField();
  private JLabel ergebnisLabel = new JLabel();
  private JButton neuButton = new JButton();
  private JButton ratenButton = new JButton();
  private JButton abbruchButton = new JButton();
  int zufallszahl, versuche;
  private JLabel versucheLabel = new JLabel();
  // Ende Attribute
  
  public Zahlenraten(String title) { 
    // Frame-Initialisierung
    super(title);
    setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);
    int frameWidth = 306; 
    int frameHeight = 300;
    setSize(frameWidth, frameHeight);
    Dimension d = Toolkit.getDefaultToolkit().getScreenSize();
    int x = (d.width - getSize().width) / 2;
    int y = (d.height - getSize().height) / 2;
    setLocation(x, y);
    setResizable(false);
    Container cp = getContentPane();
    cp.setLayout(null);
    
    // Anfang Komponenten
    
    cp.setBackground(new Color(0xC0C0C0));
    jLabel1.setBounds(4, 8, 278, 48);
    jLabel1.setText("Zahlenraten");
    jLabel1.setBackground(Color.GRAY);
    jLabel1.setOpaque(true);
    jLabel1.setHorizontalAlignment(SwingConstants.CENTER);
    jLabel1.setHorizontalTextPosition(SwingConstants.CENTER);
    jLabel1.setForeground(Color.BLUE);
    jLabel1.setFont(new Font("Arial", Font.PLAIN, 20));
    cp.add(jLabel1);
    jLabel2.setBounds(8, 80, 229, 25);
    jLabel2.setText("Bitte wählen Sie eine Zahl von 1 bis 100:");
    jLabel2.setHorizontalTextPosition(SwingConstants.CENTER);
    cp.add(jLabel2);
    versuchszahlTextField.setBounds(240, 80, 49, 25);
    cp.add(versuchszahlTextField);
    ergebnisLabel.setBounds(56, 128, 179, 41);
    ergebnisLabel.setText("Viel Erfolg!");
    ergebnisLabel.setHorizontalAlignment(SwingConstants.CENTER);
    ergebnisLabel.setHorizontalTextPosition(SwingConstants.CENTER);
    cp.add(ergebnisLabel);
    neuButton.setBounds(72, 200, 65, 25);
    neuButton.setText("Neu");
    neuButton.setMargin(new Insets(2, 2, 2, 2));
    neuButton.addActionListener(new ActionListener() { 
      public void actionPerformed(ActionEvent evt) { 
        neuButton_ActionPerformed(evt);
      }
    });
    cp.add(neuButton);
    ratenButton.setBounds(144, 200, 65, 25);
    ratenButton.setText("Raten");
    ratenButton.setMargin(new Insets(2, 2, 2, 2));
    ratenButton.addActionListener(new ActionListener() { 
      public void actionPerformed(ActionEvent evt) { 
        ratenButton_ActionPerformed(evt);
      }
    });
    cp.add(ratenButton);
    abbruchButton.setBounds(216, 200, 65, 25);
    abbruchButton.setText("Abbruch");
    abbruchButton.setMargin(new Insets(2, 2, 2, 2));
    abbruchButton.addActionListener(new ActionListener() { 
      public void actionPerformed(ActionEvent evt) { 
        abbruchButton_ActionPerformed(evt);
      }
    });
    cp.add(abbruchButton);
    addWindowListener(new WindowAdapter() { 
      public void windowOpened(WindowEvent evt) { 
        zufallszahl = (int) (Math.random()*100)+1;
        versuche = 0;
      }
    });
    versucheLabel.setBounds(8, 232, 91, 25);
    versucheLabel.setText("Versuche: 0");
    versucheLabel.setFont(new Font("Dialog", Font.BOLD, 12));
    versucheLabel.setForeground(Color.BLUE);
    cp.add(versucheLabel);
    setTitle("Zahlenraten");
    // Ende Komponenten
    
    setVisible(true);
  } // end of public Zahlenraten
  
  // Anfang Methoden
  public void neuButton_ActionPerformed(ActionEvent evt) {
    zufallszahl = (int) (Math.random()*100)+1;
    ergebnisLabel.setForeground(Color.black);
    ergebnisLabel.setText("Viel Erfolg!");
    versuchszahlTextField.setText("");
    versuche = 0;
    versucheLabel.setText("Versuche: "+versuche);
  } // end of neuButton_ActionPerformed
  
  public void ratenButton_ActionPerformed(ActionEvent evt) {
    int versuchszahl;
    versuchszahl = Integer.parseInt(versuchszahlTextField.getText());
    if (versuchszahl < zufallszahl) {
      ergebnisLabel.setForeground(Color.blue);
      ergebnisLabel.setText("Zu klein!");
      versuchszahlTextField.requestFocus();
    }
    else {
      if (versuchszahl == zufallszahl) {
        ergebnisLabel.setForeground(Color.red);
        ergebnisLabel.setText("Richtig!");
      } // end of if
      else {
        ergebnisLabel.setForeground(Color.blue);
        ergebnisLabel.setText("Zu Groß!");
        versuchszahlTextField.requestFocus();
      } // end of if-else
    } // end of if-else
    versuche = versuche + 1;
    versucheLabel.setText("Versuche: "+versuche);
    
  } // end of ratenButton_ActionPerformed
  
  public void abbruchButton_ActionPerformed(ActionEvent evt) {
    System.exit(0);  
  } // end of abbruchButton_ActionPerformed
  
  public void Zahlenraten_WindowOpened(WindowEvent evt) {
    // TODO hier Quelltext einfügen
  } // end of Zahlenraten_WindowOpened
  
  // Ende Methoden
  
  public static void main(String[] args) {
    new Zahlenraten("Zahlenraten");
  } // end of main
  
} // end of class Zahlenraten
