---
title: "iMac G3 333mhz Intrepid Display Problems"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by dmanskiman on 2008-11-11
I recently decided to try and put ubuntu on my old iMac G3 (333mhz) that was sitting around.  I knew going this wouldn't be easy.  So I downloaded the alternate cd.  And I was able to install without much problem.  Then after the install I had to turn it on, I typed in "Linux nosplash" in the yaboot screen and it booted like it should.  Then when the gui login screen tried to work.  It gave me a monitor error and told me I could go into low res mode or try to fix the xorg.conf file.  So just for fun I tried going in to low res mode.  None of the programs including nautilus would work.  So I did a hard shutdown, rebooted, and I tried to edit the xorg.conf file.  I searched and searched the web and tried to fix xorg.conf still nothing works. X windows can detect my display, mouse and keyboard fine, but it gives me an error before the gui login window.  Could this be a missing driver problem?  What do I do?

Help would be greatly appreciated!  Thanks

---

### Post by stream303 on 2008-11-11
Hopefully your iMac has enough ram to make it worthwhile.

A manual edit of /etc/X11/xorg.conf is probably mandatory with Intrepid by using a virtual terminal (ctrl-alt-f2), and once done logout and login or just reboot.  You may have to be fast to get your username and password in on the virtual terminal.

You can use this example xorg.conf as a guide - change the specs for your machine:

[http://ubuntuforums.org/showthread.php?t=978303](http://ubuntuforums.org/showthread.php?t=978303)

You will probably want to specify "ati" for the video driver.  Check these faqs for video frequencies, and other goodies that the ati card can use.  Don't forget to initially disable dri and glx, and then go back and experiment if you want:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

and

[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

although don't expect blazing fast 3D performance, if any at all for stability.

Let us know how it goes....

Also, is your hard drive original, or a replacement that might be larger than oem?

---

### Post by dmanskiman on 2008-11-15
Ok so now I can't even get to the terminal after booting.  After it attempts to start gnome it shows a blank black screen with an underscore in the top left.  Intrepid is getting weird.  What more or less recent versions of ubuntu have had the highest success rate with iMac G3s?  Should I try 8.04 or older?  All it really needs is good wifi support and firefox.  And yes this machine has plenty of RAM, we upgraded that 5 years ago when we upgraded to os x.

---

### Post by stream303 on 2008-11-15
One thought is to try installing Dapper 6.06.x, and doing an immediate upgrade to 8.04 Hardy.

One of my other favorites is Feisty 7.04, but it has EOL'ed, but could be good to establish a reference, or perhaps do incremental upgrades from.

You were editing /etc/X11/xorg.conf as root, right, ie

```
sudo nano /etc/X11/xorg.conf
```

or if you can get some funky graphics working at least

```
gksudo gedit /etc/X11/xorg.conf
```

In the custom xorg.conf file I listed above as a reference for Intrepid, it seems that one might need all the sections listed, even if you don't need to make any changes or is basically empty - otherwise Intrepid seems to go immediately in low-graphics mode if it senses a missing section - I think - I still need to do more testing and verification on that to avoid low-graphics.  At least it is working on my machine (which didn't really need a custom xorg.conf anyway until I wanted to put in that dithering option - then it seems I had to put in all those other sections to keep it from hiccuping.)

---

### Post by dmanskiman on 2008-11-16
Yeah, I was absolutely editing xorg.conf.  And now it won't even let me edit that and any more as I said in the previous post.  

So which installer should I download and use, PPC Dapper or Feisty, gui or alt?  

Thanks

---

### Post by stream303 on 2008-11-16
My recommendation is to always use the "alternate" text-based installer.

You'll have to take your pic of releases, since in nearly all cases for the G3 iMac, you'll be editing xorg.conf from either a virtual terminal, or in rescue-mode or linux single mode.

With the recent changes to the X server, perhaps Gutsy 7.10 is your best bet, whereas I used to swear by Feisty 7.04, but that has EOL'ed recently.  Give Debian 4.0r5 a shot - but you'll still have to edit your xorg.conf.

---

