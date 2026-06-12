---
title: "black screen instead on splash screen"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by ichimeno on 2007-09-17
hello. ive installed cedega and then ran the test and open gl had failed. so i took a look at the restricted drivers place where i found my graphics driver in there(ati) so i decided to enable it...after it started downloading some stuff and installed in promped me to restart the computer..so i did that and then after the ubuntu logo loadin sign instead of the splash screen there was nothin but black. is there a way i can uninstall this driver via like recovery or something? thnx in advance--ichimeno

---

### Post by alienexplorers on 2007-09-19
Boot your computer in recovery mode and log in.  From the terminal type in :
> sudo dpkg-reconfigure xserver-xorg 
answer all questions and then reboot and see if that helps.

---

### Post by ichimeno on 2007-09-19
thank you. i will try this. -ichimeno

---

