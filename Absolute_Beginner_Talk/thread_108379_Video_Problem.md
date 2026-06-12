---
title: "Video Problem"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by Moseycd on 2005-12-25
I installed Kubuntu, and it seemed to install fine, however whenever it tries to boot up (right after all that stuff scrolls down the screen when it starts up), the screen gets messed up (like when you try to run at a resolution that is too high for your monitor or when you first start a mame rom and it flashes wierd patterns for a little while before it starts the game). I even tried ubuntu, and the same thing happens. However, when I tried knoppix it worked. I recently upgaded my video card from a Geforce 4 MX 440 to a Geforce 6600. The MX440 worked fine when I tried it, but I would rather use my 6600. I really want to try out Kubuntu, but I am having a hard time getting it to work. I was wondering if anyone had any suggestions on how I might fix this.

---

### Post by bscbrit on 2005-12-26
Reboot the computer and select recovery mode from the Grub menu.

Edit /etc/X11/xorg.conf to start your display in a basic mode e.g. 1024x768

Save your changes

Reboot into normal mode

Log on

Set up your screen again

---

### Post by tentimes on 2005-12-31
I've the same problem. Your solution though, I cannot try :( I can find no way of editing a text file once I run recovery mode.I've tried logging in also, but it seems the text editors all require the display, which isn't working....

So back to square one :(

Any help appreciated :)

---

### Post by bscbrit on 2005-12-31
There are several editors that do not require X to be running.  'vi' and 'emacs' are the most popular but they do require a little work before you can simply jump in a use them.  
Many people criticise the command line - but this is when it is invaluable.  You cannot start X - the graphics server - but without it you cannot use any of your favourite editors to fix it!  Only the command line, or remote access from a working network machine, can help you now.
I cannot say for sure, but 'pico', 'nano' and 'ed' might also be installed and might be easier to use for a newbie.

---

