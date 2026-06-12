---
title: "Installing stuff - Mainly Flash"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2005-12-09
I'm having trouble installing Flash player. I'm a complete Linux n00b so I havn't got a clue what the command line is that's mentioned in the Readme with the download I'm sent to.

I've tried following the section in the Ubuntu FAQ Guide for installing flash and it isn't popping up under where it says it should in Synaptic. I've followed the instructions and repeated them several times carefully and it still isn't their. Can anyone tell me were the command line is located so I can follow the instructions in the read me as aposed to going though the whole Synaptic stuff?

---

### Post by PatrickMay16 on 2005-12-09
Yo, man!
Which version of Ubuntu are you running? Warty, Hoary, or Breezy?

You'll need to make the according changes to your sources.list file to enable the Multiverse and Universe repositories. Assuming you're running Breezy, here's the line to add to your sources.list:
```

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

```
If you've already got that done, ignore it and skip onto this next bit:

Then, open a terminal and run these commands:
sudo apt-get update
sudo apt-get install flashplayer-mozilla

Hope this helps.

EDIT: Fixed some mistakes.

---

### Post by Brunellus on 2005-12-09
go to the wikipage RestrictedFormats.  You will find out anythign you need to know.

---

### Post by giloth on 2005-12-09
I really think you're trying too hard. For me, it's as simple as going to a flash enabled page, clicking on Install Missing Plugins, and going through the Firefox wizard.

---

### Post by Rackerz on 2005-12-09
Ok, open up the menu, go into 'System' and there should be something called 'Konsole' or 'Terminal'. This is the command line they are talking about.

---

### Post by Glass_Onion on 2005-12-09
[QUOTE=PatrickMay16]Yo, man!
Which version of Ubuntu are you running? Warty, Hoary, or Breezy?

You'll need to make the according changes to your sources.list file to enable the Multiverse and Universe repositories. Assuming you're running Breezy, here's the line to add to your sources.list:
```

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

```
If you've already got that done, ignore it and skip onto this next bit:

Then, open a terminal and run these commands:
sudo apt-get update
sudo apt-get install flashplayer-mozilla

Hope this helps.

EDIT: Fixed some mistakes.[/QUOTE]

I'm running Breezy. Where's the sources.list file aswell?

[QUOTE=Brunellus]go to the wikipage RestrictedFormats.  You will find out anythign you need to know.[/QUOTE]

To install it on Ubuntu for 64bit processors I have to access the terminal for the first step - I don't know were it is and the page doesn't tell me.

[QUOTE=giloth]I really think you're trying too hard. For me, it's as simple as going to a flash enabled page, clicking on Install Missing Plugins, and going through the Firefox wizard.[/QUOTE]

For me it says unidentified plug in then sends me to the download page for Flash.

[QUOTE=Rackerz]Ok, open up the menu, go into 'System' and there should be something called 'Konsole' or 'Terminal'. This is the command line they are talking about.[/QUOTE]

Neither under the System menu.

---

### Post by Brunellus on 2005-12-09
Applications>System Tools> Terminal.

If you can't find that, just hit CTRL+ALT+F1, which will bring you to a textmode console. log in there.  You can switch back and forth from the console to your GUI by hitting CTRL+ ALT + F7 to get to the gui and CTRL+ALT+F1 for the console.  

1) You didn't tell us if you were running Ubuntu (GNOME) or Kubuntu (KDE).
2) You didn't tell us you were trying to do this on a 64-bit system.  Confirm--you are running Ubuntu for AMD 64?

sources.list is at /etc/apt/sources.list

to edit it, you must 

sudo nano /etc/apt/sources.list

you may replace nano with your favorite text editor (gedit for GNOME; kate for KDE;  vim, or emacs)

---

### Post by Gustav on 2005-12-09
I don't think that flash works on a 64-bit system, sorry.

---

### Post by Glass_Onion on 2005-12-09
Sorry about that Brunnellus, I'm running Ubuntu Breezy for a PC with AMD64.

Well, Gustav seems to have found the reason why it doesn't work. I'll try and look into one of those 3rd party ones tomorrow it's to late for me to bother now.

---

