---
title: "Please HELP!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-02
Ok i downloaded ubuntu, but it doesnt work, lots of errors
thing is the screen its shows when you restart, you get the option to use winxp or Ubuntu
Ubuntu is at top and winxp is under it, but i want to use windows, but it wont let me move down at all to pick winxp
can i fix this, or is there any other way to run winxp when you restart

---

### Post by Tootles on 2007-09-02
still need help

---

### Post by Rocket2DMn on 2007-09-02
Are you using a USB keyboard or a PS/2 one?  And geez, give it longer than 3 minutes to get a response, please.

---

### Post by Tootles on 2007-09-02
usb keyboard

---

### Post by Rocket2DMn on 2007-09-02
USB sometimes doesn't load fast enough during the boot sequence to be available when the GRUB menu appears.  You can search your BIOS to see if you can opt to have USB devices load earlier in the boot sequence, or you may want to use a USB to PS/2 converter for your keyboard - these often come with USB keyboards and mice.

---

### Post by Duck2006 on 2007-09-02
Then use a hard wired keyboard.

---

### Post by Tootles on 2007-09-02
ok but is there a way to pick windows xp without going to that menu
and is there a way to uninstall ubuntu in the black screen

---

### Post by Rocket2DMn on 2007-09-02
> **Tootles said:**
> ok but is there a way to pick windows xp without going to that menu
and is there a way to uninstall ubuntu in the black screen

Do you not want to have Ubuntu on your computer anymore?  That black screen is the GRUB boot menu where you select which operating system you want to boot in to - it was installed when you setup your dual boot with Ubuntu and WinXP.

---

### Post by groeswenphil on 2007-09-02
I get the same thing, but I just press the down arrow button until I get to Windows XP, then I press [return]

Phil

---

### Post by Tootles on 2007-09-02
ok i do not want to have ubuntu anymore, because it did not work, didnt even start up, but i cant start winxp because i cant choose that option in the GRUB menu
is there another way to uninstall ubuntu without starting up xp
because i used the wubi-installer

---

### Post by Tootles on 2007-09-02
or is there another way to start xp without gonig to the grub menu

---

### Post by Rocket2DMn on 2007-09-02
There is a thread that explains how to get rid of Ubuntu and revert to using only Windows: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
However, it requires that you are able to boot into windows from GRUB.  So, I suggest checking your BIOS like I mentioned before to see if you can have USB enabled early in the boot sequence.  Otherwise, find and use a USB to PS/2 converter if possible so the keyboard will be initialized by then.  Once you are able to fix the initial problem here, you can go uninstall Ubuntu as described in the HowTo thread.

---

### Post by Tootles on 2007-09-02
how do i check my bios, post instructions because i do not know what you are talking about

---

### Post by Rocket2DMn on 2007-09-02
When you first turn on your computer you will have the option to enter the BIOS or Setup.  You will only have a second or two to hit the right button (hopefully your keyboard will be temporarily initialized that this point before it shuts off to start up with the O/S).  The initial splash screen should tell you which button to press to enter the Setup - common keys are usually F2, F8, F12, DEL, or ESC.
Once in the BIOS search around for features relating to USB during Bootup (like preboot recognition).  If you don't see anything, you will have to find a PS/2 adapter or borrow somebody's PS/2 keyboard so you can enter Windows and follow the guide to remove Ubuntu and get XP working correctly.

---

### Post by steveneddy on 2007-09-02
> **Tootles said:**
> how do i check my bios, post instructions because i do not know what you are talking about

Hoo boy!

---

### Post by Tootles on 2007-09-02
These are the options i have, which 1?
F8 boot menu
F12 network boot
DEl Setup
ESC Skip memory

---

### Post by IusedTObeSOMEONEelse on 2007-09-02
> **Tootles said:**
> how do i check my bios, post instructions because i do not know what you are talking about

Wow!! You went through effort to set up a dual boot, (some thing I would find difficult) May I suggest that maybe instead of being a quitter, that you ask for a little assistance in getting both systems working. I am sure that if you let us know your system and how you set up etc. that the community would be more than happy to assist you. Being "very" new to this, of course your gonna have a little drama, slow down and take deep breath. If you did the dual boot thingy, I am quite sure you can get the "hang" of Ubuntu:):)
Sally

---

