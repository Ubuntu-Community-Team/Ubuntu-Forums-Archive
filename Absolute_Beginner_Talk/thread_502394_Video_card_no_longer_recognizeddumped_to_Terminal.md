---
title: "Video card no longer recognized/dumped to Terminal"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Pingan on 2007-07-16
Ok, Im an absolute newbie when it comes to linux and its commands.  (Diehard WinXP user on 3 systems). I've been trying to get Ubuntu installed for the last few months and when MaximumPC did a quick and dirty "how to" for installation of it I jumped on it.  MaxPC was great for the setup of the drives (partitioned one drive) and initial start.  When it got to the video card section, it blew chunks.....I will explain below.

I setup my oldest machine to dual boot.
Ubuntu 7.04 & WinXPSR2+
Amd Barton 2600+
1.5 Gbyte Ram
80 Gig HD (40 to XP, 38 to Ubuntu, 2 to Swap/Ubuntu)
Plextor DVD R/W (704 series I think)
Lite on CD RW (about 40x)
Nvidia 4200 128mbyte card

I installed Ubuntu with no real problems (except didnt see my USB/Dlink G132 wireless therefore a ran cable from upstairs router to basement machine equals fixed).

I turned on 3rd party 'repositories'.
I updated for security and other updates that it said I need to do.

My problems began when the magazine said to look for 'nvidia-glx' in the update (synaptic manager?) section.  I found 3 items.
a) nvidia-glx legacy
b) nvidia-glx
c)nvidia-glx new
<please keep in mind that I am NOT typing this word for word/exact as I am not near the machine in question>

After reading the descriptions of each of the above I felt my Geforce 4 was a better fit for the nvidia-glx as mentioned by the magazine.  The legacy seemed to be for geforce 2 and the new was for 7/8 series cards.

The magazine said that once I selected the driver all dependices (?) would be automatically selected and installed too.  Didnt see any notification of that when I selected the driver, but hey....what do I know, maybe it does it without you knowing.  After the driver change it said something like 'if you want to restore previous driver enter cp /misc/etc/X11/xorg.config.2007-14-7.11:42:56 /etc/X11/xorg.config'  
<again not exact but very close as I had written it down).

Reboot and bang. Can no longer boot graphical interface (or X server/whatever you call it).

Reboot back to windows XP and looked at the forums to figure out how to restore previous settings. hmmm, Terminal looks a lot like DOS or the old commodore/IBM PET machine stuff.
Reboot back to Terminal (as graphical no longer functions).  Type in info I had written down (discussed above). No work.  

Realized maybe I need to add sudo (Super User Do?? or something).  Nothing.
Realized case sensitive and the X in x11 might need to be capitalized. Nothing. Recheck all case for line against forums (reboots to XP and back several times).  Retype...nothing.

Found a thread in this beginner forum that user just put up recently about Kubuntu and same problem.  Used the suggestions in that thread (titled ummm '....Kubuntu no longer booting...' or similar).
Suggestions were basically
a) to copy the xxxx.config file back to the proper location.  (I guess this assumes you already backed up the original. *cough*)
b) edit the config using gedit.  If I enter this it says it cant find the program.
c) edit the config using nano.  This worked and was able to edit the 'nvidia' under devices to 'nv' as stated in the post.  Didn't do anything for me tho.
d) Try to get the X Server to recreate a new default config (at least that was my understanding of it).  System cant find the Server program.

As it stands I'm going insane over what is probably a simple problem.  Can't wait till I get more experience with this OS.

Any help is appeciated. Btw, I'm at work so all responses will be from memory until I get back on the system.

---

### Post by NewJack on 2007-07-16
Try doing the following:

1-  Clean install of Ubuntu.  (Hopefully you have a separate /home partition, if not at least backups of music/pics).

2-  Before doing anything else after the install, get ENVY installed (I think it is in the Feisty repositories, if not go here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)     -and follow the instructions on the site).

3-  Run ENVY and let it install the drivers for your Nvidia card.

4-  Restart your computer and go about installing/surfing/tinkering/etc.

This is what I had to do when I first installed Ubuntu Feisty.  It worked for me, hopefully it will help you.

---

### Post by CautionaryX on 2007-07-16
Is the 4200 a Ti or a MX? The MX version of the GeForce 4s lacked pixel shaders and are essentially souped up GeForce 2's. In that case I'd uninstall the nvidia-glx drivers and try the nvidia-glx-legacy drivers.

---

### Post by sad_iq on 2007-07-16
Ok...boot your ubuntu box...no graphical stuff needed..login and type ```
sudo dpkg-reconfigure xserver-xorg
``` it will ask you a lot of questions...but when you get to the video driver to use (or something similar) choose **nv**...and about the monitor choose simple(if you don't know the refresh rates of your monitor)...everything should be simple...just don't go wrong about the monitor...that will get you to a graphical login...then search these forums for **Envy**...to install the driver for your video card!!! 
 Later you can google the refresh rates of your monitor and input them in **/etc/X11/xorg.conf**.

---

### Post by agurk on 2007-07-16
When at the command prompt, open your /etc/X11/xorg.conf file using for instance the 'nano' text editor (you'll need to type 'sudo nano /etc/X11/xorg.conf', since editing this file requires administrator's privilegies). Find the section 'Device' and set the 'Driver' to either "nv" or "nvidia" (try the second if the first one doesn't work). Save and reboot.

If it still doesn't work, run 'sudo dpkg-reconfigure xserver-xorg' to reconfigure your X window system from scratch.

---

### Post by forestpixie on 2007-07-16
It might need this instead

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but not completely sure :)

---

### Post by CautionaryX on 2007-07-16
Forestpixie is right, the "-phigh" is needed otherwise you'll be slammed with a ton of options for xserver that you probably didn't know existed.

---

### Post by Pingan on 2007-07-16
hmm, thanks for the speedy responses everyone.

I will try the latest redist...xserver info, including the extra command to reduce questions.

My concern is that the line mentioned is suspicously like the last one I tried last night where it was supposed to rebuild my default config.  At the time it came back with something like 'cant find program' message.

It was the same when thing when I tried to edit the config using gedit.  Ended up using Nano.  


At this point I don't know how to list directories or 'see' whats in a directory.  
If I was in DOS I could manually search for a exe file by changing directories (cd), then listing the files (dir /p).  At least in DOS I could verify the path to the program.

To be honest, at this point I'm not sure the xserver line will work, but who knows, maybe I was just too tired last night and miskeyed a letter.... ;)

---

### Post by forestpixie on 2007-07-16
not sure about listing directories - ls lists from within a directory

you can use locate to find files though

```
sudo update db

```
then use sudo locate 

```
kevin@kevin-desktop:~$ sudo locate xorg.*
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/doc/kde/HTML/en/kompmgr/xorg.html
/usr/share/X11/xkb/rules/xorg.lst
/usr/share/X11/xkb/rules/xorg.xml
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/lib/X11/config/xorg.tmpl
/usr/lib/X11/config/xorg.cf
/etc/X11/xorg.conf.bak
/etc/X11/xorg.conf
/etc/X11/xorg.conf.bak.1207
/var/lib/dpkg/info/xorg.md5sums
/var/lib/dpkg/info/xserver-xorg.list
/var/lib/dpkg/info/xserver-xorg.prerm
/var/lib/dpkg/info/xserver-xorg.postrm
/var/lib/dpkg/info/xserver-xorg.md5sums
/var/lib/dpkg/info/xserver-xorg.postinst
/var/lib/dpkg/info/xserver-xorg.preinst
/var/lib/dpkg/info/xorg.list
/var/lib/dpkg/info/xserver-xorg.templates
/var/lib/x11/xorg.conf.roster
/var/lib/x11/xorg.conf.md5sum
kevin@kevin-desktop:~$ 

```

man <command> gives manual entry in terminal

eg man ls

---

### Post by Pingan on 2007-07-16
btw, in response to a your posts above (CautionaryX), I have the Ti series card.  I didnt buy into Nvidias rebranding (i.e. Nvidia MX rebrand of Geforce 2 line).

Oh, I like your choice of the ASUS A8N-32SLI Deluxe....my main system (WinXP only at this time) is running similar except I have a X2 4400 (2x1mb) and a 7950GX2 card. :)  Preferred more graphics horsepower over cpu.  Not that I cant OC my CPU as it has a ton of room to go.

---

### Post by CautionaryX on 2007-07-16
I think you might need to disable the 'nv' driver module. 

Type **sudo nano /etc/default/linux-restricted-modules-common** and add the "nv" module to the restricted modules list, save, and exit.

Then type **sudo nano /etc/X11/xorg.conf**  and under the Devices section, make sure the driver says "nvidia" and not "nv".

I'm not sure it'll work but its worth a shot.

I was originally going to get a 4400+, however the price difference on Newegg between the 4800+ and the 4400+ was about $50. So I decided it was worth it to upgrade. My video card is on the cheap side, but I can run FEAR at mostly high settings while maintaining ~40 FPS so I'm not complaining that much. I do plan to buy another 7600GT and SLI as soon as my next paycheck comes in. (I don't see the point in buying a DX10 card when there wont be any DX10 games for quite some time.)

---

### Post by Pingan on 2007-07-16
Woot!

Im back up and running on graphical interface.  Now to figure out how to change refresh/resolutions and then on to getting 3d driver running.

Awesome help everyone. :)

---

### Post by CautionaryX on 2007-07-16
in a terminal type 
```
glxinfo | grep render 
```

and you should see something like 'direct rendering: yes'. that means that 3d is working. I think a package called nvidia-settings will help you change resolution, etc. However you might have to manually put the resolution you want  in the xorg.conf file.

---

