---
title: "ATI Radion Video Cards for Newbies"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by jfank on 2007-12-16
There has been a few posts done on here already about the ATI Radeon Video Cards.  However, I found this other website that I don't believe I saw listed on the other topics.  Now ALL TOPICS ARE HELPFUL, this is just a different setup.  Of course I don't konw how well this works, because it found the driver for my ATI, and mine works perfectly so I didn't have to do any steps to get it to work.  I have set this topic up mostly for newbies to the world of Linux, or even experienced users.  At the end of the message I will include the guide that I found this information on.  This guide has many other IMPORTANT information for Linux users, and this is specific for the new 7.10 Gusty version of Ubuntu.  It will work with all versions of Ubuntu including, Kubuntu, Xubuntu, and Edubuntu.  It will also work with the 64 bit editions as well.  If you experience any problems with these steps, please post a reply on here so others can help you seek the solution.


 ATI users and Compiz

Some ATI cards don't need their proprietary drivers to work with Compiz as the open-sourced driver (radeon) also has support for 3D acceleration. However, the open-sourced driver isn't as fast as the closed-sourced (fglrx) one, so if you need the proprietary one you'll have to tinker around in the terminal a little.


1. After you've installed the driver, either through the proprietary manager or directly from [[COLOR="Blue"]**ATI's site**[/COLOR] ]("http://ati.amd.com/support/driver.html ") , you'll have to setup the Xorg configuration file to work with your new driver. Always remember to back up the original file before altering, in case something goes wrong. Open up a terminal and enter: 

```
  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
  sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

This will disable the default radeon driver and replace it with ATI's own.


2. Now, let's tell Compiz not to care about drivers that are blacklisted: 

```
  echo SKIP_CHECKS="yes" >> $HOME/.config/compiz/compiz-manager
```

Alternatively, you could whitelist the driver, which is a much prettier solution. Run this command to edit the Compiz startup-script:

```
gksudo gedit /usr/bin/compiz
```

Search for Driver whitelist and add fglrx to the end of the line, like this: 

```
 # Driver whitelist
 WHITELIST="nvidia intel ati radeon i810 fglrx"
```


3. Reboot your computer, login and enable Compiz as mentioned above et voilà! Behold Compiz and ATI hugging.

I hope this works for everyone that is having problems with their ATI video drivers, and if there is still issues there is plenty of other topics with many different ways to solve the problem, and thousands of fellow Ubuntu users to aid you in the solution to the problem.  Below is a link to the guide where I found this information, and please take a look at it to learn more on doing various things to the Ubuntu OS.

[[COLOR="Blue"]**Ubuntu Guide - Gusty**[/COLOR] ]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy  ")

---

### Post by flamelab on 2007-12-16
[img]http://www.adslgr.com/forum/images/smilies/thumb_dup.gif[/img]
&#924;any people here have problem with legacy Radeons .
I'll bookmark your thread the fastest ( I had lost the original wiki url :()

---

### Post by jfank on 2007-12-16
> **flamelab said:**
> [img]http://www.adslgr.com/forum/images/smilies/thumb_dup.gif[/img]
&#924;any people here have problem with legacy Radeons .
I'll bookmark your thread the fastest ( I had lost the original wiki url :()

I had many problems getting my Radeon to work correctly in earlier versions of Ubuntu, but this new version has access to the drivers for my specific video card, and I hope others that had or still have problems can find some good use for this guide I found.  I do want other topics to be viewed, and get as many different solutions to getting that video card to work.

I wish I could take the video card out of my desktop, but it's a gaming machine and most of my computers I have Linux on are laptops:lolflag: But my gaming maching is a Nivida GForce card that is perfect on Linux.

---

