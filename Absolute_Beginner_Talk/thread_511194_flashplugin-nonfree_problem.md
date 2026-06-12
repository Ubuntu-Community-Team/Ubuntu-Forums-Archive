---
title: "flashplugin-nonfree problem"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by common.route on 2007-07-27
I just recently set up a dual-boot on my old Pentium II PC with XP Pro and Ubuntu, and it runs surprisingly well. I even went ahead and installed Xfce as the default session.

Well, my problem is when I followed the "Enabling Multimedia in Feisty" post to install codecs and such. When I tried to install flashplugin-nonfree, it just freezes up at this text:

Resolving fpdownload.macromedia.com... 72.246.114.70
Connecting to fpdownload.macromedia.com|72.246.114.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   82.08 B/s

And now, when I try to remove flashplugin, or even try to install anything at all, I get the wonderful "dpkg error." So, when I do what the error tells me and enter "sudo dpkg --configure -a" in the terminal, it just starts up the flashplugin-nonfree installation and freezes up again.

Please help, thanks.

---

### Post by reckless2k2 on 2007-07-27
yeah you'll have to go to adobe site...download it,extract, and follow the read me on what to do. it didn't work from the apt-get for me not too long ago. it's an easy install the other way but requires cli.

---

### Post by common.route on 2007-07-27
I'll try that out, but will that enable me to install other programs again?

---

### Post by Majorix on 2007-07-27
You did a mistake. If you are a single user on your computer, your best bet was to go and open up a flash-enabled webpage in your browser. That guide was probably written for people with more than a few users. You shouldn't follow a guide with your eyes closed [-(

---

### Post by common.route on 2007-07-27
Okay, so in other words, I'm screwed unless I reinstall ubuntu?
If so, how can I reinstall it onto the partition already made?

edit;
Also, this is post I followed for the installation: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

It says nothing about being for multiple users only, thank you.

---

### Post by Majorix on 2007-07-27
> It says nothing about being for multiple users only, thank you.

It probably won't say that.. But using just your browser is how you usually install flashplayer on a single or two or probably three user machine.

---

### Post by ugm6hr on 2007-07-27
> **Majorix said:**
> It probably won't say that.. But using just your browser is how you usually install flashplayer on a single or two or probably three user machine.

Though, it works just fine to install from Synaptic (flashplugin-nonfree).  The guide uses Add/Remove, which does a similar thing, although perhaps it is less reliable?

Did you lose internet connection, or turn off, or run out of HD space during the install?  I had a simlar problem when updating an old computer, where it filled the HD, then couldn't finish the install.  I reinstalled, because I couldn't work out how to fix it, but it must be possible?  

If you want to reinstall - just make a backup (to a different partition or external drive) of /home and /var/cache/apt, and paste back following the re-install (use manual install).  Then reinstall all packages from Synaptic (rather than Add/Remove) or Terminal.

---

