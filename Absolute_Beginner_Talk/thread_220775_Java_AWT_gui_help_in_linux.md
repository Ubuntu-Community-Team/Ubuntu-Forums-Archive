---
title: "Java AWT gui help in linux"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-22
aye so heres my source:

```

// -----------------------------------------------------------------------------

// THIS SCRIPT IS BY GOAT SPIRIT!!

// -----------------------------------------------------------------------------
 

import java.awt.*;

import java.awt.event.*;



public class AWTExample extends Frame {

private Button copyButton;

private Button cutButton;

private Button pasteButton;

private Button  exitButton;


public AWTExample() {

	super("Endar V4 GUI Beta");

	setSize(417, 90);

        addWindowListener(

                new WindowAdapter() {

                    public void windowClosing(WindowEvent e) {

                        System.exit(0);

                    }

}

);


ActionListener buttonListener = new ActionListener() {

        

public void actionPerformed(ActionEvent ae) {

	String action = ae.getActionCommand();

        if (action.equals("Exit Endar V4")) {

        dispose();

        System.exit(0);

        } else {

        }

}      

};


Panel toolbarPanel = new Panel();

toolbarPanel.setLayout(new FlowLayout(FlowLayout.LEFT));



copyButton = new Button("Start Endar");

copyButton.addActionListener(buttonListener);

toolbarPanel.add(copyButton);



cutButton = new Button("Start The Endar Updater");

cutButton.addActionListener(buttonListener);

toolbarPanel.add(cutButton);



pasteButton = new Button("Start The Website Stealer");

pasteButton.addActionListener(buttonListener);

toolbarPanel.add(pasteButton);



add(toolbarPanel, BorderLayout.NORTH);



Panel bottomPanel = new Panel();



exitButton = new Button("Exit Endar V4");

exitButton.addActionListener(buttonListener);

bottomPanel.add(exitButton);

        

add(bottomPanel, BorderLayout.SOUTH);

}



public static void main(String[] args) {

	AWTExample mainFrame = new AWTExample();

        mainFrame.setVisible(true);

}

}


```

where it says

```

copyButton = new Button("Start Endar");

copyButton.addActionListener(buttonListener);

toolbarPanel.add(copyButton);



cutButton = new Button("Start The Endar Updater");

cutButton.addActionListener(buttonListener);

toolbarPanel.add(cutButton);



pasteButton = new Button("Start The Website Stealer");

pasteButton.addActionListener(buttonListener);

toolbarPanel.add(pasteButton);

```

for each button i need it to run another class, is there a function to do this?

other classes are on same directory

---

### Post by Ben Sprinkle on 2006-07-22
ne1?

---

### Post by steve.horsley on 2006-07-22
You can create a different anonymous ActionListener class for each button, if that's what you mean. Like this:

```

        copyButton = new Button("Start Endar");
        copyButton.addActionListener(
            new ActionListener() {
                public void actionPerformed(ActionEvent ae) {
                    System.out.println("Copy button was pressed!");
                }
            }
        );
        toolbarPanel.add(copyButton);


```

I don't see that as any easier than having one ActionListener (ButtonListener) with a bunch of if statements looking at the ActionCommand though.

Maybe I don't understand what you're asking for?

---

