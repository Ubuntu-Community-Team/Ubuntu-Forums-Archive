---
title: "problems installing eagle software"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-05
Hi,
I am trying to install a software called Eagle layout editor.  I downloaded it from their website.  It was a tgz file.  After downloading it, I opened it and went to my terminal and typed:
sudo ./install
I get the message that it installed properly
and then when i type: eagle
in my terminal window
I get a prompt asking me to register the product either as a freeware or using a license disk.  I click on "Run as Freeware".  I then get the message:
Can't open '/opt/eagle/bin/eagle.key'  Permission denied

so I click ok and the program exits.  Can anyone help me with this problem?

---

### Post by htinn on 2006-04-05
You don't need to install the package from their website. Just enable the "multiverse" in the normal repos and install "eagle" in Synaptic.

---

### Post by HisEm on 2008-03-30
Hmmm Same problem here however I DID install using Synaptic. Any Ideas?

---

### Post by krlhc8 on 2008-03-30
Go to the terminal and type: sudo eagle
After that, you should be able to run 
eagle without being root.  The next problem 
you could run into if you're using Compiz is the 
lucid window background, making it 
difficult/impossible to view anything.  

To run Eagle every time you must type In the terminal::
XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/eagle/bin/eagle

I haven't figured out how to get this to work with a 
launcher; that would be ideal.

---

### Post by HisEm on 2008-05-21
This is what I did:
1. right click on 'Applications' menu - 'Edit Menu'
right click on the 'Eagle' menu and in command point it to:
             ~/scripts/./eaglelauncher.sh
2. make a file called eaglelauncher.sh in a folder called scripts in your home folder.
3. copy this in:
          #!/bin/bash
          XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/eagle/bin/eagle
4. Save file
5. run eagle.

:)

---

