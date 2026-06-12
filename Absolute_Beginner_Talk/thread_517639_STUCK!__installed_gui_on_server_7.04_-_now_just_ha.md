---
title: "STUCK!  installed gui on server 7.04 - now just hang after ubuntu gui loading screen"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by lukalock on 2007-08-04
I’m relatively new to Linux, and completely new to server administration... I have installed Ubuntu server edition 7.04 Feisty Fawn (LAMP & DNS) successfully on my PC – but have decided that I would really be more comfortable with a GUI interface….


So after reading this post (and a few others)..

[http://ubuntuforums.org/showthread.php?t=487057](http://ubuntuforums.org/showthread.php?t=487057)



...I seemed to have finally, after many failed attempts, successfully installed a GUI interface (Ubuntu-Desktop) on my Ubuntu server 7.04...


Now, after rebooting, I get the typical GUI Ubuntu "orange-bar" loading screen...  

..and then nothing.  

Instead of it loading up the desktop like I expected, it just hangs at a blank screen - forever.  and rebooting doesn't do anything of course...


Any ideas?  am I completely stuck and will just have to do a complete reinstall of everything???  if so - does anyone have any ideas of what I might have done wrong, or what I should do to prevent this from just happening again?



Below is what I did to install Ubuntu Desktop:


>  You will need to edit the source list.

1) backup your source list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2) edit the file with vi or any editor you like:
```
sudo vi /etc/apt/sources.list
```

3) search for cdrom and when you find it add # to the beginning of the line to make a comment.

4) save and close

5) update the repository:
```
sudo aptitude update
```





Then, after updating everything - 

To install Ubuntu (Gnome):

```
sudo aptitude install ubuntu-desktop
```



Everything seemed to go perfectly.  Towards the end, it went off a bit on how it wouldn't be able to install webmin due to missing dependencies - so I just selected the option to not install webmin.

But then everything finished, and I was brought back to the normal command line prompt.  I did a reboot, it started loading up the Desktop...and then   ...black screen of nothingness...


Help?

---

### Post by bren on 2007-08-04
sounds like a prob with your graphics driver....

what hardware are you running (incl graphics card)?
post results of 
> lspci
executed in terminal if you can get there by booting in safe mode
bren

---

### Post by lukalock on 2007-08-04
ok...  selected Recovery Mode from Startup, and am in the CLI as root now (eep!)...

```
lspci
```

gives me

```
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)

00:09.0 RAM memory:  nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge:  .....
00:0a.1 SMBus:    ....
00.0a.2 RAM memory:  ... memory controller...
...
.... USB Controller...    ....

.....    .........  IDE Controller....  Serial ATA Controller ...

..PCI bridge  ...    ...
Audio device...  ............ ...........
...Bridge....              ....
Host bridge....       ...     DRAM Controller......

.....
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
```


of course, I didn't post the ENTIRE thing  (hence the "..." everywhere)  ...is there something specific I am looking for?

---

### Post by lukalock on 2007-08-04
> **bren said:**
> sounds like a prob with your graphics driver....


ok, so I was able to find this:   [http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313)

"[Owners of Nvidia cards]  Post the way you got the Nvidia driver to work"


After reading some of the posts on there, I tried the following:



> 
...use the legacy driver :
Code:
```
$sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
```

and change Driver from "nv" to "nvidia" in xorg.conf 



Now after rebooting, instead of just going to a black screen and hanging, I get a crappy grey & blue box (similar to what you see during installation of 7.04) that says:

```
 (==)log file: "/var/log/xorg.0.log", time:sun aug 5...
(==) nividia: mo matching device section for instance (busID pci:3:0:0) f
nvidia: could not open the device file /dev/nvidia0 (input/output error)
(EE) nvidia (0): failed to initialize the invidia graphics device!
```



...any ideas?

---

### Post by nostrilface_c on 2007-08-07
I encountered a similar problem when trying to run the KDE desktop. It began the splashscreen with the loading bar and then it would hang to a blinking cursor. I managed to solve it by trawling Google but I can't remember exactly how I solved it because I since realised I hadn't properly selected the LAMP option during installation (you have to actually hit the space bar) and have re-installed Ubuntu.

But. I think it was along the lines of running
```
lspci
```
and looking to see the bus address of the gfx card
```
01:07.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```
then editing xorg.conf
```
sudo nano /etc/X11/xorg.conf
```
and changing the Bus identifier for the graphics device from PCI:0:1:0 to PCI:1:7:0 (or whatever it happens to be in your case), the former being the on board gfx controller the latter the TNT card that the monitor was plugged into.

Might help:
[http://ubuntuforums.org/showthread.php?p=3017113](http://ubuntuforums.org/showthread.php?p=3017113)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

