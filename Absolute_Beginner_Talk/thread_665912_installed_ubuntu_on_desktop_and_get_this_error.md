---
title: "installed ubuntu on desktop and get this error"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by mike_pasara on 2008-01-12
I am trying to install flash and i get this

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/mike/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/home/mike/Desktop/install_flash_player_9_linux/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/mike/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n): 




i want to be able to view youtube videos so flash is a must. any help?

---

### Post by Cypher on 2008-01-12
Go to Places->Desktop and in the Nautius window that appears, double-click on "install_flash_player_9_linux" and there see if the file "libflashplayer.so" exists.

Report back on what you see in that directory.

---

### Post by dcstar on 2008-01-12
> **mike_pasara said:**
> I am trying to install flash
........

How?

---

### Post by JayTee on 2008-01-12
were you running this with sudo? try sudo su then run the installation. I'm assuming your running an install script so you probably want to cd to the directory you're installing from first.

---

### Post by mike_pasara on 2008-01-12
> **Cypher said:**
> Go to Places->Desktop and in the Nautius window that appears, double-click on "install_flash_player_9_linux" and there see if the file "libflashplayer.so" exists.

Report back on what you see in that directory.

no such file... only flashplayer-installer

i double clicked that one and ran that in terminal and what i posted is what i got so now i am back in the circle

---

### Post by krendar on 2008-01-12
> **mike_pasara said:**
> 
NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Try to do like it says. First locate xpti.dat by running this command

**locate xpti.dat**

Then remove it as administrator:

**sudo rm /folder/xpti.dat**

Where folder is the folder that locate found. Then try to run the installer again.

PS: Make sure you exit firefox when told so by the installer, not sure if that was the problem.

---

### Post by Cypher on 2008-01-12
> **mike_pasara said:**
> no such file... only flashplayer-installer

i double clicked that one and ran that in terminal and what i posted is what i got so now i am back in the circle
Rather than double-clicking the installer, open up a terminal with Applications->Accessories->Terminal and then type
```

cd ~/Desktop
sudo ./flashplayer-installer

```
This will run the installer but with Root privileges needed to copy the files to the "/usr" directory..

---

### Post by mike_pasara on 2008-01-12
> **krendar said:**
> Try to do like it says. First locate xpti.dat by running this command

**locate xpti.dat**

Then remove it as administrator:

**sudo rm /folder/xpti.dat**

Where folder is the folder that locate found. Then try to run the installer again.

PS: Make sure you exit firefox when told so by the installer, not sure if that was the problem.


mike@mike-desktop:~$ locate xpti.dat
mike@mike-desktop:~$ 


it doesn't do anything

---

### Post by mike_pasara on 2008-01-12
i managed to get it going. thanks for all the help

---

