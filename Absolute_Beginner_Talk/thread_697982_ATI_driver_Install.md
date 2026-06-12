---
title: "ATI driver Install"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by DennisOS2 on 2008-02-15
I'm running Kubuntu GG on a DellXPS400 with a n ATI Radeon 550.  DL'd the latest drivers from the ATI site and installed.  

When I try to start the ATI Catalyst I get the error message: '.......problem initializing the control center ...................'  

I ran ATICONFIG --INITIAL  and got the error message:

[COLOR="Black"]dennis@Study:/usr/bin$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.[/COLOR]

What could possibly have a bad 'Bad File Descriptor'

I've installed numerous time to get either the improved ATI drivers in the distributiom or now the ATI drivers.  Either the screen ends up blanking on re-boot or the ATI drivers won't work.  any help would be appreciated!

---

### Post by stchman on 2008-02-15
> **DennisOS2 said:**
> I'm running Kubuntu GG on a DellXPS400 with a n ATI Radeon 550.  DL'd the latest drivers from the ATI site and installed.  

When I try to start the ATI Catalyst I get the error message: '.......problem initializing the control center ...................'  

I ran ATICONFIG --INITIAL  and got the error message:

[COLOR="Black"]dennis@Study:/usr/bin$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.[/COLOR]

What could possibly have a bad 'Bad File Descriptor'

I've installed numerous time to get either the improved ATI drivers in the distributiom or now the ATI drivers.  Either the screen ends up blanking on re-boot or the ATI drivers won't work.  any help would be appreciated!

Just use Envy.  It will install the latest drivers for that card.

---

### Post by Rocket2DMn on 2008-02-15
You probably need to run aticonfig with root privileges
```
sudo aticonfig --initial
```

Although I hear Envy is really nice, I don't recommend it.  It requires you to uninstall your Envy + the video driver you installed with it before doing a dist-upgrade or you could end up seriously breaking some things.
You should follow this guide to install ATI proprietary drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by erginemr on 2008-02-15
Maybe "sudo aticonfig --initial" will do.

---

### Post by brunolabs on 2008-02-15
> **DennisOS2 said:**
> I'm running Kubuntu GG on a DellXPS400 with a n ATI Radeon 550.  DL'd the latest drivers from the ATI site and installed.  

When I try to start the ATI Catalyst I get the error message: '.......problem initializing the control center ...................'  

I ran ATICONFIG --INITIAL  and got the error message:

[COLOR="Black"]dennis@Study:/usr/bin$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.[/COLOR]

What could possibly have a bad 'Bad File Descriptor'

I've installed numerous time to get either the improved ATI drivers in the distributiom or now the ATI drivers.  Either the screen ends up blanking on re-boot or the ATI drivers won't work.  any help would be appreciated!


Same problem here!
I don't know what causes this. I follow the installer instructions available in [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat82-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat82-inst.html")  
and the install runs ok.
After the "aticonfig --initial" I also get that terminal output.

Anyone knows how to solve the problem?

Thanks!

---

### Post by brunolabs on 2008-02-15
> **erginemr said:**
> Maybe "sudo aticonfig --initial" will do.

Doesn't work. I don't think it is a "permissions" problem.

---

### Post by Rocket2DMn on 2008-02-15
Why don't you try removing the fglrx stuff and starting fresh with it.
Follow the removal portion on this guide: [https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)
then restart the fglrx setup with the guide I provided above - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you still get an error, reboot from the LiveCD and run fsck on your disk as it may be corrupted.  From the LiveCD
```
sudo fsck /dev/(yourdevice)
```
where (yourdevice) is the hd** or sd** device of your root (/) partition.

---

### Post by erginemr on 2008-02-15
This thread archive:
[http://ubuntuforums.org/archive/index.php/t-239517.html](http://ubuntuforums.org/archive/index.php/t-239517.html)

suggests that something may be wrong with the aticonfig tool:
> [COLOR="Black"]**Posted by moma**[/COLOR]
Try to run it with sudo.
$ sudo aticonfig --initial

If it fails again, then it's probably an internal error in "aticonfig". Do not worry abbot it.
aticonfig --initial does not do much. It just writes "fglrx" and some other basic values to /etc/X11/xorg.conf.

Move on and run
$ sudo dpkg-reconfigure xserver-xorg

---

