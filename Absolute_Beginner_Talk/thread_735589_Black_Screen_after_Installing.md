---
title: "Black Screen after Installing"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by bondboy8 on 2008-03-25
I have a black screen after the ubuntu bar loads.  I installed with the alternate CD so this isnt a livecd problem.  Ive read about people reconfiguring their Xserver in Command Line mode and I want to try that because they all had a Nvidia graphics card like I do.  I just need step by step instructions on how.

---

### Post by jan quark on 2008-03-25
boot into recovery mode and reconfigure the xserver with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bondboy8 on 2008-03-25
Ok 1.) So I just type that in the little part after my name and 2.) What are the steps after that I want a step by step I can print off to walk me through the others mentioned sumthing about vesa

---

### Post by jan quark on 2008-03-25
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this should start an automated reconfiguration process

---

### Post by bondboy8 on 2008-03-25
But i don't understand what to do here it mentions selecting resolutions but when i push enter to pick one it just goes on to the command line again

What is the vesa driver i have a Nvidia card is there anything wrong with that i have heard of problems with that

---

### Post by Therion on 2008-03-25
Try this and see if it gets you over the hump...  You're going to remove the splash screen and do a non-quiet boot to get you to the desktop so you can do your critical system and software updates (make sure you do them ALL) using the default vesa driver.  Then you're going to go back and install the Restricted Driver using Envy.  Then you can put the splash and quiet options back into menu.lst once everything is up and running.

To get the the desktop using the default driver:

Reboot your machine and when you see the GRUB menu, ESCape out.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this particular line.
Delete the words **splash** and **quiet**.
Hit &#8220;Enter&#8221;, then "B" to continue booting.
Once you're in Ubuntu, open up the Terminal and enter:
```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words quiet and splash from the line that starts with Kernel one more time.
Save the file (overwrite), Exit and restart your PC.

If this works and you get to your desktop DO NOT install the Restricted Driver when you are prompted.  We'll get to that later... 

For now, just do your system updates.

---

### Post by bondboy8 on 2008-03-26
It didn't work a bunch of stuff went by as it booted then black screen again.  Does this narrow down the problem?  Should I just reinstall Ubuntu?

---

### Post by mattlew62 on 2008-03-26
I'm having the same problem

---

