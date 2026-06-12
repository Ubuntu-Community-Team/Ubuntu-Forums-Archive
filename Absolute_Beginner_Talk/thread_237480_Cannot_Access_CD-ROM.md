---
title: "Cannot Access CD-ROM"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by backinblack on 2006-08-16
That was the above message the program gave after booting into safe mode in order to find out why the program just "sat there", for lack of a better term.
Anyhow, Ubuntu is sharing this HD with WindowsXP64-bit, and was installed with a bootable CD created from an ISO image.
Please correct me if this is wrong, but I am assuming that after the initial install the program still needs to access the CD-ROM in order to install the FireFox browser and various other programs.
At this point it would be a major thrill just to get the program to  browse the web and check -email!!!
Thank you!

---

### Post by Metacarpal on 2006-08-16
Hi!

I hope I'm understanding your problem correctly.  Here are the details I'm basing my reply on:
1. You had WinXP on this computer, then added Ubuntu as a dual-boot
2. The installation process completed successfully and you are able to boot into Ubuntu

When you installed Ubuntu, it should have given a message at the end to remove the CD-ROM so the system could reboot.  Did you take the disc out at that time?  If not, remove the CD and reboot.  You won't need the CD in the drive after the installation.  Ubuntu installs Firefox by default during the initial setup.

Also, when you wish to add more programs, you won't need the installation CD to do so.  You can download additional programs through the Add Software feature in the main Ubuntu menu, through Synaptic in the System > Administration menu, or using the command-line
```
sudo aptitude install <package_name>
```
in a Terminal session (Applications > Accessories > Terminal).  The packages will be downloaded from online repositories for installation.

**If you are not able to boot into Ubuntu without the CD-ROM in the drive, then the installation probably didn't complete properly, and that's a whole new can of worms.

---

### Post by backinblack on 2006-08-17
Metacarpal, thank you for your response.
At this point here is what the progam is doing: I can login with username and password, and yes, FireFox installed, but that's it.
I can't access the internet, or even find a command Console.
The message about not being able to access CD was given while Ubuntu was in recovery mode. A memory check did not reveal any problems. The splash screen that appears while the system is booting up says that everything is in order, but I cannot get the program to perform a single function, other than opening FireFox.
I am very confused!

---

### Post by bodhi.zazen on 2006-08-17
backinblack:

Not sure if I am understaning your problem. It soulds like there are 2 problems:

1. I am not sure if Ubuntu will run on a 64-bit CPU. What hardware are you using?

2. It sounds as if X is not woring. In this case you are at a terminal or CLI. You can log in and interact with the shell, but no GUI ?

If so, again what hardware are you running (video card and monitor). You will need to configure X.

What happers if you type X at the command line? you should get a grey screen with a large black X as a mouse cursor. Ctrl-backspace to exit.

---

### Post by Metacarpal on 2006-08-18
> **backinblack said:**
> Metacarpal, thank you for your response.
At this point here is what the progam is doing: I can login with username and password, and yes, FireFox installed, but that's it.
I can't access the internet, or even find a command Console.
The message about not being able to access CD was given while Ubuntu was in recovery mode. A memory check did not reveal any problems. The splash screen that appears while the system is booting up says that everything is in order, but I cannot get the program to perform a single function, other than opening FireFox.
I am very confused!

The default setup for Ubuntu's desktop is to have Firefox in the launcher panel, but nothing else.  You can add additional programs and applets by left-clicking the top panel and choosing Add.  Alternately, you can launch your other programs through the menu.

The Console (aka Terminal) is located in the main Applications menu (upper left corner, marked with the Ubuntu logo).  In that menu is an Accessories submenu, and you'll find Terminal there.

If the menu isn't working or is empty, then something went wrong with your install.

As for accessing the 'net, it could well be that you just haven't told it how to connect yet.  Are you using a dial-up modem, broadband through an ethernet port, wireless, or a different connection?  If wireless, is it an in-tower (PCI) card, a USB device, or a (laptop) PC-card?

bodhi.zazen also raised a good question - which install CD did you use?  If you're running on an AMD 64-bit chip, you'll need the AMD64 installation CD, not the i386 CD.

---

### Post by bodhi.zazen on 2006-08-18
Metacarpal: Thanks, I did not know Ubuntu had a 64 bit version (nerver looked).

---

