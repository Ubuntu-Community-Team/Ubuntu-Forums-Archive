---
title: "[SOLVED] I messed up!!!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by indiana_crook on 2008-03-19
Guys, I bought a new monitor and in the process of trying to change the resolution, i've made it worse!!!  I can't see antyhing in ubuntu the screen is all scrambled.  What do i do!!!??? Can I change the settings back to default throught the grub menu?

---

### Post by overdrank on 2008-03-19
> **indiana_crook said:**
> Guys, I bought a new monitor and in the process of trying to change the resolution, i've made it worse!!!  I can't see antyhing in ubuntu the screen is all scrambled.  What do i do!!!??? Can I change the settings back to default throught the grub menu?

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by indiana_crook on 2008-03-19
Okay, I'd do that but I can't read or see antyhing on the screen.  I need to change the screen settings back to default.

---

### Post by ajmorris on 2008-03-19
when your ubuntu boots, and it is sitting at the login screen, press ctrl+alt+F2

Login as root

then do dpkg-reconfigure -phigh xserver-xorg

then you can either start X with startx to start your default XSession, or type gdm to bring back the login manager

**EDIT: **Overdrank beats me to it :P  

what vga mode is set in your grub boot menu? press 'e' on the kernel line in grub, remove any vga mode, press enter, then 'b' on your edited line, if it goes back to the choice of kernels, the change will be lost, so you need to press b on the line after pressing enter, then you can change the vga mode to a different one, or remove it completely once logged in. See below a page for the list of grub vga modes:

[http://www.mepis.org/node/2992](http://www.mepis.org/node/2992)

hope it helps,
AJ

---

### Post by indiana_crook on 2008-03-19
> **ajmorris said:**
> when your ubuntu boots, and it is sitting at the login screen, press ctrl+alt+F2

Login as root

then do dpkg-reconfigure -phigh xserver-xorg

then you can either start X with startx to start your default XSession, or type gdm to bring back the login manager


My screen is all scrambled at the login screen, will i still be able to do that?  I can't read anything..

---

### Post by ajmorris on 2008-03-19
> **indiana_crook said:**
> My screen is all scrambled at the login screen, will i still be able to do that?  I can't read anything..

most likely, it should be just X that the resolution is scrambled, so pressing those keys will bring you to a command line, that the resolution is set by the grub vga mode.

---

### Post by donnyblaze1 on 2008-03-19
Yes, you will be able to.  This will log you in using text only and allow you to reset everything you need to.

---

### Post by indiana_crook on 2008-03-19
THANK YOU ALL SOOOOO MUCH!!!   Ubuntu forums comes through again!  Now, how do i change my resolution to 1680 x 1050?  It's not on my list of options for resolution.

---

### Post by overdrank on 2008-03-19
> **indiana_crook said:**
> THANK YOU ALL SOOOOO MUCH!!!   Ubuntu forums comes through again!  Now, how do i change my resolution to 1680 x 1050?  It's not on my list of options for resolution.

Hi and what is the model of the graphics card and what version of Ubuntu are your using, Gutsy or Feisty?

---

### Post by indiana_crook on 2008-03-19
how do i find out what model graphics card?

---

### Post by overdrank on 2008-03-19
> **indiana_crook said:**
> how do i find out what model graphics card?

Hi and you can use the command lspci in the terminal located under applications, accessories. and look for VGA

---

### Post by indiana_crook on 2008-03-19
okay, got it:

 ATI Technologies Inc Radeon X1200 Series

---

### Post by overdrank on 2008-03-19
> **indiana_crook said:**
> okay, got it:

 ATI Technologies Inc Radeon X1200 Series

Ok I have not had the pleasure of using that card but I have read that some users have had success with Envy installing the drivers.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

