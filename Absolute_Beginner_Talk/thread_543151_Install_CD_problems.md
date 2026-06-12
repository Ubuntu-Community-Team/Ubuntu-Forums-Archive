---
title: "Install CD problems"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by codeking on 2007-09-04
I'm having some problems installing Ubuntu 32-bit.  I started to install it, but had some problems, so I canceled it.  Now, whenever I start Ubuntu from the install disc, it shows the menu.  I click start and install Ubuntu, then it starts to load.  Then it goes to the Linux shell (or whatever that DOS-like thing is called), and gives me an error about jobs being disabled or something like that.  Then when I try to shut it down (using "exit", I'm not sure if this is correct), it gives me the error again.  What should I do?

---

### Post by K.Mandla on 2007-09-04
I suppose it's possible that there's a partial installation in place on your hard drive, and that's confusing the setup program.

Can you blank your hard drive? I usually use [Killdisk]("http://www.killdisk.org") to wipe a disk clean between installations, but if you have something on that drive that you need -- like music files or photos or documents or a Windows installation -- then that's not an option.

---

### Post by codeking on 2007-09-06
ok, here's a better description of what the error is:

the menu appears.  i click start and install ubuntu.  then it goes to the loading screen.  after a shorter time than it should take, it goes to a black screen with white text, and this is what it says:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
Type 'help' for a full list of commands

/bin/sh: can't access tty; job control turned off

(inintramfs) *blinking '_'*

---

### Post by rsambuca on 2007-09-06
This is a common error that occurs from bad iso burns.  If you can, I think you should reburn the CD at a much lower burn rate.

---

### Post by codeking on 2007-09-07
I burned another CD at 8x instead of 52x, but it didn't help.  Any other ideas?

---

### Post by funrider on 2007-09-07
did you do a check sum for the iso file? maybe the file is corrupted itself.

---

### Post by BrendanM on 2007-09-07
Before you actually start the installer, when the CD first starts up, there's an option like "Verify disc integrity" or something like that. Try that before you start the install.

---

### Post by codeking on 2007-09-08
It did work before I canceled the installation, so there is nothing wrong with the CD or the ISO file.  But, I tried out your suggestions anyways and they didn't work.  Would there be some file in the harddrive that's messing it up?  Telling it to boot using the nonexistant files in the harddrive instead of the CD?

---

