---
title: "Playing DVDs, How-I-Did-It, Totem-xine"
date: 2005-03-27
forum: Apple PPC Users
---

### Post by tater on 2005-03-27
I got DVDs to play, no choppiness, no sound out of sync with video.  

My system:

Powerbook Pismo
G3 - 500MHz
1G memory
stock-standard Matshita SR-8174 DVD/CD-ROM drive
stock-standard Toshiba 12GB hard drive

fresh install of Hoary 5.04


1. Enabling the built-in ATI RAGE 128 graphics processor for Direct Rendering/3D hardware acceleration, by reducing color depth.  This is described elsewhere in these forums, but it's a bit different when using hoary, so I've updated the steps accordingly

1) Change into one of the Virtual Terminals using Ctrl+Alt+F1 (or Func+Ctrl+Alt+F1) and login with your username and password.

2) Type the following command to edit your XF86Config-4 file -

sudo nano /etc/X11/xorg.conf

3) Move to the Section "Screen", which you can do either by scrolling down or by pressing Ctrl+W and typing "Screen" into the search box.
4) Change the figure after DefaultDepth to 16 from 24. Press Ctrl+X to save the file.
5) You've now made the requisite changes, but to have them enabled, you will need to restart X itself. An easy way to do this is to switch back to X by pressing Ctrl+Alt+F7 (or Func+Ctrl+Alt+F7) and then pressing Ctrl+Alt+Delete. 
6) Log in and check if 3D acceleration is enabled by opening a Terminal (Applications->System Tools->Terminal in Gnome) and typing the following command-

glxinfo | grep "direct rendering" 

7) If the answer is "Yes", it worked.


2.  I abandoned trying to get the hoary-installed Totem to work, and installed Totem-xine instead.

1)  If you haven't done so already, you need to enable getting apts from the universe
 
sudo nano /etc/apt/sources.list

2)  Move to the lines that fetch things from other places in the universe.  Remove the # sign in the front of each of these lines.  (The # sign "comments-out" these lines, so nothing is fetched from those locations.  Removing the # sign makes them active).  (Note: If you want to keep a copy of this file before you modify it, then before you bring it up for editing, do a cp /etc/apt/sources.list sourcesold.list.  This will save the original file as sourceold.list)

3) Save & quit the file.

4)  Get Totem-xine

sudo apt-get install Totem-xine

3.  Totem-xine or any other player for that matter, needs libdvdcss to be able to play commercial DVDs, because they are encrypted.  

1)  I got it from the following:

[http://honk.physik.uni-konstanz.de/~agx/linuxppc/debian/mplayer/libdvdcss2_1.2.8-0.0_powerpc.deb](http://honk.physik.uni-konstanz.de/~agx/linuxppc/debian/mplayer/libdvdcss2_1.2.8-0.0_powerpc.deb)

2)  Install it:

sudo dpkg -i libdvdcss2_1.2.8-0.0_powerpc.deb

4.  This is important -- if you already have a DVD in the drive, eject it.  And even if you didn't have a DVD in the drive, do a reboot of the system. I know others talk about restarting stuff from the command line, but I'm a newbie.  However, I did learn the hard way that if I didn't reboot (or know how to do some sort of restart) that Totem-xine would not recognize that the libdvdcss was installed, resulting in 
the error message something like, "you are trying to play an encrypted DVD without libdvdcss installed" -- just drove me nuts!

5.  After rebooting, turn on DMA for the DVD/CD-ROM

1)  I wanted to ensure that I knew exactly what my DVD/CD-ROM was called.  To do this, from the pull-down menus in Ubuntu, choose System, Administration, Device Manager.  Under KeyLargo Mac I/O, I saw at the bottom, MATSHITADVD-ROM SR-8174.  clicking on it to choose it, displayed info about it on the right hand 
side of the screen.  Choosing the Advanced tab, in the first line I saw the needed info:  block.device string /dev/hdc. So, /dev/hdc is the name of my DVD/CD-ROM drive.

2)  Now knowing the name of my DVD/CD-ROM drive, then going back into the Terminal screen, I typed:

sudo hdparm -d1 /dev/hdc

3)  Other folks have posted about how to make this change permanent, by modifying the /etc/hdparm.conf file, and doing some other tricks, but I haven't gotten that far yet to see if/how that would work for me.  So I do the sudo hdparm -d1 /dev/hdc everytime before playing a DVD, for now.


6.  Go ahead and try playing a DVD.  For me, this works.  However, I noticed that after a few minutes, the audio and video got very-slightly, but annoyingly out of sync.  I found that if I checked Deinterlace, this problem immediately went away:

1)  From the pull-down menu in Totem-xine, choose View, Deinterlace.  As long as Deinterlace is checked, my audio and video do not get out of sync.  Perhaps others here will know why that works.

Hope this helps someone,
tater

---

### Post by callipeo on 2005-03-27
> **tater]1)  I wanted to ensure that I knew exactly what my DVD/CD-ROM was called.
[/QUOTE]

With udev, you should be able to see the /dev/dvd symlink said:**
> 3)  Other folks have posted about how to make this change permanent, by modifying the /etc/hdparm.conf file, and doing some other tricks, but I haven't gotten that far yet to see if/how that would work for me.  So I do the sudo hdparm -d1 /dev/hdc everytime before playing a DVD, for now.


Making the change to hdparm.conf works very well: just add these lines at the bottom of /etc/hdparm.conf:

/dev/dvd {
        dma = on
}

and restart hdparm.

Thanks for the pointers, especially the libdvdcss one.

---

### Post by tater on 2005-03-27
Thanks!  Now I don't have to keep turning DMA on for my DVD each time I reboot!

tater

---

