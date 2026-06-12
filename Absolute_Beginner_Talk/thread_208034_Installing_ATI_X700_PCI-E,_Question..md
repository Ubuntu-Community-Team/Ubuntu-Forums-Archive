---
title: "Installing ATI X700 PCI-E, Question."
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by vincent85 on 2006-07-02
Hi there,i're trying to install Ubuntu 6.06 or 5.XX using an ATI video card x700 today and it give me the Error: "No screen Found"

I did some search on the forum and found this [http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

I've followed all the intructions in that thread but after change the xorg.conf from ati to vesa , my monitor signal dies ...

I've tried many possible ways(change the resolution to the minimum,check " or a extra point or a blank space that may acidentally inserted....) but nothing work.

I also try this:
In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

The code"sudo apt-get install xorg-driver-fglrx" did not work properly becasue  it can not connect to the internet so i can not use sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv.(Error:aticonfig is invalid command)


Any idear how to fix my problems? 
Thank in advantage.

---

### Post by joshrobinson on 2006-07-02
[QUOTE=vincent85]Hi there,i're trying to install Ubuntu 6.06 or 5.XX using an ATI video card x700 today and it give me the Error: "No screen Found"

I did some search on the forum and found this [http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

I've followed all the intructions in that thread but after change the xorg.conf from ati to vesa , my monitor signal dies ...

I've tried many possible ways(change the resolution to the minimum,check " or a extra point or a blank space that may acidentally inserted....) but nothing work.

I also try this:
In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

The code"sudo apt-get install xorg-driver-fglrx" did not work properly becasue  it can not connect to the internet so i can not use sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv.(Error:aticonfig is invalid command)


Any idear how to fix my problems? 
Thank in advantage.[/QUOTE]

```
sudo dpkg-reconfigure xserver-xorg
```

pick whatever driver you want to use, go through the onscreen stuff and see what happens

---

### Post by vincent85 on 2006-07-02
Hi,thank for reply, yes, i've tried this "sudo dpkg-reconfigure xserver-xorg" after i enter "startx" my monitor signal dies again...
Any idear.?

---

### Post by Rich3077 on 2006-07-03
Well this is a longshot but just in case you have the same problem I had.. I will tell ya. If you are using an LCD monitor with a digital cable switch over to an analog cable or at least use an adapter and plug into the analog port on the video card. That solved the problem for me. I now have the ATI driver installed but have been to lazy to try the digital output so I dont know if it works now.

Peace
Rich

---

### Post by vincent85 on 2006-07-03
that's it,i have enough, i move to Suse, How can Ubuntu be anygood without you can even install it? Fair well Ubuntu....you rest in peace...

---

### Post by Rich3077 on 2006-07-03
[QUOTE=vincent85]that's it,i have enough, i move to Suse, How can Ubuntu be anygood without you can even install it? Fair well Ubuntu....you rest in peace...[/QUOTE]


Good luck with Suse.. that was my first install and it was buggy as hell.
When I posted in the Suse forums for help an Admin told me that there was no fix for my problem. You WILL be back to Ubuntu in time.. and we WILL be here to help you with your problems. Your best bet is to not waste the 5 CD's unless it is already to late. If you cant install Ubuntu then your chances of installing Suse are slim to none. 


Peace 
Rich

---

