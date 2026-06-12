---
title: "Gnome shell doesn't get along with Nvidia 173"
date: 2011-12-16
forum: Any Other OS
---

### Post by Randymanme on 2011-12-16
I've read [http://ubuntuforums.org/showthread.php?t=1880458&highlight=gnome+shell+themes+unity%3F](http://ubuntuforums.org/showthread.php?t=1880458&highlight=gnome+shell+themes+unity%3F)  and that doesn't fix my problem.
 

 To sum it up, gnome shell won't open if I have the proprietary nvidia 173 driver installed. It would open to the desktop background with desktop icons, but nothing else. ALT-F2 wouldn't work either. Since I had a terminal icon on my desktop, I could open the terminal. The Gnome 3 desktop on Mint 12 does open, however, when I'm using the Nouveau firmware instead, but the panels and fonts are all garbled. On Oneiric, gnome shell doesn't work at all. On Mint, the nvidia 173-updates driver works with Ubuntu desktop, Enlightenment, Mate, and Gnome-classic, but not as well as the nvidia 173 driver. I tried having both the nvidia 173 and Nouveau firmware installed at the same time and there was no change from just having the nvidia 173 installed.  
 
Nvidia-current broke a previous install of Mint 12 when I was trying to find a solution to this problem, so I reinstalled. While I was googling for some solution, I ran across a posting somewhere where the person was having some problem similar to this one, and it was suggested that they upgrade to the 3.1 linux kernel. I did that and was left with the "Fatal server error: no screens found." I googled around for a solution for that, but soon realized that even if I found out how to fix that, I'd still have the original problems. So I just reinstalled.

I guess I could try the nvidia 185 driver.

With the nvidia 173 driver installed, I googled up the Mint tutorial, [http://community.linuxmint.com/tutorial/view/641](http://community.linuxmint.com/tutorial/view/641). When I used CTRL+ALT+F1, the terminal fonts were so garbled that I had to reboot --(what's the terminal command for "logout?)-- and use the terminal in Mate:

randymanme@randymanme-Dimension-8300 ~ $ w
05:34:21 up 49 min, 1 user, load average: 0.08, 0.10, 0.18
USER TTY FROM LOGIN@ IDLE JCPU PCPU WHAT
randyman pts/0 :0 05:34 1.00s 0.56s 0.01s w
randymanme@randymanme-Dimension-8300 ~ $ 

Then I had to logout and go back to the non-functioning Gnome to execute 
export DISPLAY=:0
gnome-shell --replace

Then the terminal messages were: "(gnome-shell:3720) St-WARNING **: percentage lengths not currently supported Window manager warning: Log level 16: NOTE: not using GLX TFP!

Window manager warning: Log level 16: NOTE: not using GLX TFP!

(gnome-shell:3720): Cog1-WARNING **: ./cog1-framebuffer.c:924: Failed to create an OpenGL framebuffer

(gnome-shell:3720): Cog1-WARNING **: ./cog1-framebuffer.c:924: Failed to create an OpenGL framebuffer

(gnome-shell:3720): Cog1-WARNING **: ./cog1-framebuffer.c:924: Failed to create an OpenGL framebuffer

gnome-shell-calender-server [3734]: HUP on stdin-exiting
Segmentation fault" 

Then CTRL+ALT+F7 to switched back to the display, there'd be no panels or desktop icons, just the background. I'd have to CTRL+ALT+F7 for the terminal, and then sudo init 6 to restart.

I don't know if this bit of extra information will help (I know I need to start another thread), but Gnome 3's top and bottom panels are garbled, as are the fonts inside the shell and mint menu.

There are no such problems with the Ubuntu or Ubuntu 2d login options on Mint; I just like Mint 12's version of gnome shell better than Unity. When I was hosting Mint 12RC on virtualbox with Mint 11, Mint 12 ran more or less perfectly. I just assumed that a physical install would be better because it would be running on a full one GB of ram instead of the guest and host splitting one GB of ram.

I've also gotten a gnome/openbox login option that works just fine on both Mint and Oneiric – except that it's not gnome shell, it's ubuntu 2d!

And, finally, let me add (for the sake of more information), that in frustration, I burned a live cd of fedora 16 to check out it's gnome shell and I had the same problems with the garbled panels; the fonts were okay but were missing letters out of words. I know by it happening with both Mint 12 and Fedora 16, that evidence points to my hardware as being the problem, but it only happens with gnome 3 shell.

Anyway, as always, any and all help and advice will be much appreciated. Thanks.
 

 P.S., the machine I'm posting about is the one on my signature.

---

### Post by flyingfisch on 2011-12-16
i dont know whats the problem, but when i try to use gnome shell the same thing happens. Its also extremely slow.

---

### Post by Crempel on 2011-12-16
I am currently using Mint 12 with a virgin gnome-shell (no MGSE), using the 290.10 driver (64-bit) downloaded from NVIDIA. It works absolutely perfectly. I got a GS 7200 card. Just try and see whether this solves your problem.:)

---

### Post by Perfect Storm on 2011-12-16
Moved to Other OS/Distro Talk.

---

### Post by Randymanme on 2011-12-17
Sorry, I meant for this info to go to [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11544023](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11544023)  but this was the page I was on when I tried below, so I had to use the reply box here to save the copy and paste. 


randyman@randyman-Dimension-8300:~$ gnome-shell
Window manager warning: Failed to load theme "Aurora": Failed to find a valid file for theme Aurora

Window manager warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
randyman@randyman-Dimension-8300:~$ sudo lightDM --replace
[sudo] password for randyman: 
sudo: lightDM: command not found
randyman@randyman-Dimension-8300:~$ sudo --replace
sudo: invalid option -- '-'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
randyman@randyman-Dimension-8300:~$ sudo export DISPLAY=:0
sudo: export: command not found
randyman@randyman-Dimension-8300:~$ export DISPLAY=:0
randyman@randyman-Dimension-8300:~$ gnome-shell --replace
Window manager warning: Failed to load theme "Aurora": Failed to find a valid file for theme Aurora

Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Dec 17 2011 06:49:31 GMT-0500 (EST)
Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

gnome-shell-calendar-server[2108]: Got HUP on stdin - exiting
Segmentation fault
randyman@randyman-Dimension-8300:~$

---

### Post by wolfen69 on 2011-12-17
Methinks your computer may be a bit too dated to run gnome shell. It can be demanding, resource-wise. Match the OS to the hardware, and you'll be fine. Try Lubuntu or some other lightweight distro.

---

### Post by Randymanme on 2011-12-29
Ubuntu Gnome Shell Remix:  [https://launchpad.net/ubuntugnome](https://launchpad.net/ubuntugnome)
 

 Download Ubuntu 11:10 Gnome Shell Remix iso:  [http://linux.softpedia.com/progDownload/Ubuntu-GNOME-Shell-Remix-Download-74925.html](http://linux.softpedia.com/progDownload/Ubuntu-GNOME-Shell-Remix-Download-74925.html)
 

 Or for an installable Gnome Shell 3 live dvd iso (built on openSUSE by the Gnome Project),  [http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)
 

 These run fine on my current computer (the Dell Dimension 8300 Pent4, 3 Ghz, 1 GB, nVidia 5200 that I was using when I first posted here has died).
 

 Cheers


P.S. Installing the nVidia driver will effectively kill the Gnome 3 os build on openSUSE -- at least on the two antique computers I've tried it out on.

---

### Post by Orlusha on 2012-03-29
> **wolfen69 said:**
> Methinks your computer may be a bit too dated to run gnome shell. It can be demanding, resource-wise. Match the OS to the hardware, and you'll be fine. Try Lubuntu or some other lightweight distro.I've just checked it by replaclng my FX5200 by a set of  ATIs from bottom to top ones. All of them work perfectly both on Gallium and fglrx.

The issue is by all means nVidia-related.

---

### Post by Randymanme on 2012-04-08
As can be seen at my signature, I've gotten a new computer after I first posted this thread. As Crempel posted on December 16th, 2011 12:29 PM and wolfen on December 17th, 2011 07:51 AM ,  the nvidia card I was using at the time was just to old to support the resource demands.

It is worth noting, though, that Ubuntu 11.10 works just fine on an antiquated eMachines 4000+, 1.8 GHz, 1Gb of ram and a nvidia 5500 video card (but it wouldn't do Unity on 11.04).

I've long thought that whatever the SuperOS devs do to give it muscle, should creep into Ubuntu at some point.  I expect Ubuntu 12.04 to be fully operable in low resource, older, machines just like 11.10 got less resource hungry than 11.04 was.

Cheers

---

