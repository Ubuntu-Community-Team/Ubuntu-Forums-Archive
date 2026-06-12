---
title: "[SOLVED] Problem Booting"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by ohyeah12321 on 2008-07-10
Hi everyone! First off, sorry if this is in the wrong forum, I'm new here, and new to Ubuntu as of this week. I've been doing all sorts of reading on Ubuntu and decided to make the leap. I chose Ubuntu Studio, but I don't think that's relevant to my question. I installed Ubuntu and rEDIt and got it installed (to my knowledge) all fine and dandy. Now my trouble. I turn on my computer (a Macbook Pro running Leopard if that helps), choose Ubuntu with rEDIt, and am confronted by a gray screen showing Tux. It appears to freeze at this screen and not do anything. The one time it did something, I had the Ubuntu Studio disc I had burned in the drive, and I was confronted by command prompt and some mumbo jumbo I didn't understand. It seems that without the disc it stays at the Tux screen. I've done my best to search for my answer to no avail, so I come to you. How do I get around this? If you have any questions, feel more than free to ask. Thanks! -Erik

---

### Post by cyberdork33 on 2008-07-10
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by ohyeah12321 on 2008-07-10
I posted this in the thread you gave me, but also figured I'd post it here. I seem to be running into obstacle after obstacle trying to get Ubuntu to work. First, I got it so that it freezes when selecting Ubuntu through rEFIt (grey screen, tux logo freeze). I followed the steps in the guide for how to get around that, and that is where my trouble lies. Instead of ending up with Ubuntu working, I now have 2 boot logos for Ubuntu (boot from HD and boot from partition 3) and both of them bring me to a command prompt screen and nothing else. Sorry for the broad question, but where do you think I went wrong and how do I fix it? Please forgive me for being a total noob,  but I made my journey into the world of Ubuntu last night.

---

### Post by cyberdork33 on 2008-07-10
> **ohyeah12321 said:**
> Okay, I seem to be running into obstacle after obstacle trying to get Ubuntu to work. First, I got it so that it freezes when selecting Ubuntu through rEFIt (grey screen, tux logo freeze). I followed the steps in the guide for how to get around that, and that is where my trouble lies. Instead of ending up with Ubuntu working, I now have 2 boot logos for Ubuntu (boot from HD and boot from partition 3) and both of them bring me to a command prompt screen and nothing else. Sorry for the broad question, but where do you think I went wrong and how do I fix it? Please forgive me for being a total noob, but I made my journey into the world of Ubuntu last night.
well, you have two tux logos because you have the grub bootloader installed in two different locations. This is not going to hurt anything, so just don't worry about it, yet.

what do you mean by it starts to a commandline? what do you see? are there any error messages? what is on the screen?

---

### Post by ohyeah12321 on 2008-07-10
I would equate it visually to MS-DOS. It shows all the processes being run and such. I would assume it's showing me what goes on behind-the-scenes when Ubuntu is loaded. However, it displays some errors from what I could catch. It moves pretty fast so I wrote down what I could, I hope some of it helps. 

Something like "no controller found" followed by "error recieving vevent - no buffer space". This is followed by "hub_port_status failed (err = -71)" IT shows these among other things, most of it looks like it's working fine, displaying a process on one side and [OK] on the other. It then brings me to: 
" Ubuntu 8.04.1 ubuntu tty1
 
ubuntu login:"

If i type in my username and password, it sits there at the line not doing anything.

It also displays an error when I press my power button, it prepares to shut down and when it says it is ready to power off, an error about it being "unable  to iterate" some device.

I hope any of this helps.

---

### Post by cyberdork33 on 2008-07-10
are you sure that you didn't install the server version of Ubuntu? if not then i would guess that you got a bad install for some reason.

---

### Post by ohyeah12321 on 2008-07-11
Okay, well apparently the answer to my problem lies in the installation of the desktop, something I will be able to fix tomorrow when I get my disc from my mom's house (I'm 16). However, I still have the issue of the two boot icons one to boot from the hard drive and one from partition 3, do you have an idea of how to fix that?

EDIT: Ah, never mind. Through the magic of the search bar I was actually able to find your thread on how to fix the problem. Thank you very much for all your help, you've made my Ubuntu experience a good one so far.

---

