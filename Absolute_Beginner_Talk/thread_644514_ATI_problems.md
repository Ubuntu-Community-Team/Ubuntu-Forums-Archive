---
title: "ATI problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Judacoth on 2007-12-19
First my specs:
2 Gig Dual channel DDR2 PC5200 RAM
ATI X700 video Card
P4 64bit HT

Hi im an absolute beginner to Unix, never touched it in my whole life.  so bear with me cus im still learning the absolute basics to things like terminal, terminal commands, and how to get everything running.

So my first problem is that im struggling to get my X700 drivers working.  I have used this site "https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html"
to get the instructions on how to install the drivers, but it might as well be in Chinese.  (As previously stated, im still learning command line code with the command line for beginners forum) 
Where it tells me to "1. Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download."
(I go into the super user, and then I tried "cd desktop" and im already there in terminal.
then
"2. Enter the command  ati-driver-installer-7-11-x86.x86_64.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed."
I did this by dragging in the Downloaded file, and this is what my terminal sais.  '


judacoth@judacoth-desktop:~$ sudo bash
root@judacoth-desktop:~# '/home/judacoth/Desktop/ati-driver-installer-7-11-x86.x86_64.run' 
bash: /home/judacoth/Desktop/ati-driver-installer-7-11-x86.x86_64.run: Permission denied
root@judacoth-desktop:~#

Im at a complete loss, and at a dead end here.  Can somone help em out here.

---

### Post by kpkeerthi on 2007-12-19
Follow the instructions from ubuntu wiki. This is much easier. [Here you go]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

---

