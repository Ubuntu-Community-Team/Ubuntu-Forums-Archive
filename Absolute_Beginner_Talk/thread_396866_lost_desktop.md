---
title: "lost desktop"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-03-29
I was trying to install my Nvidia card.  I followed the direction of an old post telling you how to install it.  I followed the directions but when I logged out to finalize it my screen now is all messed up with messages of do I want to see what is causing problem. 

The card I have is a BFG 5500 card.  Could someone please tell me how to get my desktop back?  Also could someone tell me how to install it?

---

### Post by shaft350x on 2007-03-29
Sound to me that maybe your xorg.conf file may be causing your problems.  (I'm currently working through similar things myself, trying to get Beryl working with an NVIDIA card)

You may need to restore your xorg.conf file from a back up.

Once you get through the error screens you'll get to a prompt.  Enter your username, then your password.   Then type

```

sudo cp <backup> /etc/X11/xorg.conf

```

Where <backup> is the name of your backup file.  Probably /etc/X11/xorg.conf.backup or _backup or bkup

Assuming that you've backed it up.  If you haven't someone else may be able to help you find and restore it.

---

### Post by cowlip on 2007-03-29
If all else fails, do 

sudo apt-get dpkg-reconfigure xserver-xorg

choose 'vesa' when it asks for what driver.

BTW, the current easiest way to install Nvidia and ATI binary, proprietary drivers is with Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

With Feisty Fawn, there's also the restricted drivers thing.

---

### Post by tonyr1988 on 2007-03-30
If you don't have a backup, do this when you get to a prompt (black screen) and log in with your username / password:

> sudo nano /etc/X11/xorg.conf

Then type Ctrl+W. It will say "Search: "

Type in "nvidia" (**with** the quotation marks) and hit Enter. It should take you to a line such as:

>         Driver            "nvidia"

*If it doesn't have that line* - Ctrl+X to exit (don't save changes) and post about it. We'll have to do a little more things.

*If it does have that line* - Edit it to say:

>       Driver         "nv"

instead (just change nvidia to nv). Hit Ctrl+X and Y when it asks you to Save Modified Buffer. Restart and see if that works.

Sorry you're having problems. Don't worry - we'll get it fixed soon. :)

---

### Post by tonyr1988 on 2007-03-30
> **cowlip said:**
> If all else fails, do 

sudo apt-get dpkg-reconfigure xserver-xorg

choose 'vesa' when it asks for what driver.

BTW, the current easiest way to install Nvidia and ATI binary, proprietary drivers is with Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I thought vesa was the default driver for ATI cards and nv was the default for nVidia cards, but I could be wrong. 

And I second envy - it's probably way easier than what you were trying before.

---

### Post by cowlip on 2007-03-30
vesa's the X Windows failsafe driver.  'ati' and 'radeon' is the 3d ATI open source driver.  'nv' is the Nvidia open source 2d driver.  'fglrx' is the ATI closed driver, 'nvidia' is the Nvidia closed driver.

(hopefully, 'Nouveau' will someday be the Nvidia open souce 3d driver :))

---

### Post by tonyr1988 on 2007-03-30
Aww..gotcha now. Sorry about the confusion on my part.

---

### Post by jbumgar on 2007-03-30
Ok, I did everything you guys told me and no results. I did check my typing on everything so I know I had no typos.

Tonyr1988 when I typed in the "nv" that didn't help.  Just to satisfy my curiosity I went back into the file and there is nothing there now....kinda funny.  That's my luck. lol.

Cowlip the sudo apt-get didn't work.  Dumb me forgot to write down the error message.  This is the one I tried 3x.

Hopefully there is something else we can try?

---

### Post by cowlip on 2007-03-30
I'm so sorry, I messed up with that command.  There's no apt-get in it.

It should be: 

sudo dpkg-reconfigure xserver-xorg

You can also try 

sudo dpkg-reconfigure -phigh xserver-xorg

for no prompting

---

### Post by tonyr1988 on 2007-03-30
I'm not sure what happened to cause the file to completely disappear.

Either way, cowlip's right on this one: do the reconfigure command.

---

### Post by jbumgar on 2007-03-30
Well guys the sudo dpkg-reconfigure xserver-xorg did it! Thank you both so much!  Now to go to that website and try that to install this blasted card.

Once again many thanks.

---

### Post by tonyr1988 on 2007-03-31
Glad you got your desktop back, and I hope that the driver installation works better for you next time around. :) If you have any questions / problems with it, post about it, but please make a different thread (unless you have the exact same problem as this one).

Since your problem seems to be solved, could you please mark this thread resolved? Simply edit the first post in the thread, click the Go Advanced button, and right below the Title box you'll see a checkbox about your problem being resolved. Please check that one and save. It helps keep the forum clean.

Again, glad it's working for you. Hope it didn't cause too much frustration (especially with all my bad advice :D)

---

