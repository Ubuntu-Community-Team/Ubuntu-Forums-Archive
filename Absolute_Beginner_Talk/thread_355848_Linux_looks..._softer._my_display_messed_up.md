---
title: "Linux looks... softer. my display messed up?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-07
I'm a noob coming from windows and mac use. I notice that windows has a "sharper" appearance to it. I'm wondering if I have some vid settings or something that makes linux look softer. I'm dual booting windows and running both OS's at the same res. Is it just the theme that has that look? am I crazy?

---

### Post by tonyr1988 on 2007-02-07
What graphics card do you have? I found (especially on my laptop with an ATI) that went I get official drivers, it makes things noticeably crisper.

---

### Post by moshuptrail on 2007-02-07
I agree.  I think the fonts are a little bit larger.  But yes, "softer" would be a good way to describe it.

I have an ancient ATI card, not supported by "official" drivers.
Since my eyesight isn't so good any more, I rather like it!

I'll say no more to give away my age except that I started programming the same year AT&T released the first version of Unix.

---

### Post by -Ghost9- on 2007-02-07
> **tonyr1988 said:**
> What graphics card do you have? I found (especially on my laptop with an ATI) that went I get official drivers, it makes things noticeably crisper.

I have an atix850xt.

Where'd you get the official drivers?

---

### Post by -Ghost9- on 2007-02-08
I download the ati drivers off the amd site. I followed their instructions up to the last part but that's where it goes south. It says I need to say and configure it, but I don't seem to know how to do that. So supposedly the drivers are installed, but I dunno how to configure it.

---

### Post by Maestro23 on 2007-02-08
> **-Ghost9- said:**
> I download the ati drivers off the amd site. I followed their instructions up to the last part but that's where it goes south. It says I need to say and configure it, but I don't seem to know how to do that. So supposedly the drivers are installed, but I dunno how to configure it.

Sounds like you need to #sudo aticonfig ....

Check this link here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by -Ghost9- on 2007-02-08
> **Maestro23 said:**
> Sounds like you need to #sudo aticonfig ....

Check this link here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

see i tried doing a sudo config after installing the ati proprietary drivers, but it said "nothing to do, finishing". Plus I'm trying to use the ati proprietary drivers.

So i'm a little lost.

These are the instructions from the ati website that I've been following and except for the file name being wrong they work up until step 8. At step 8 i get a file not found error. When I just run the sudo aticonfig it tells me there's nothing for it to do. I can tell my card isn't functioning properly because when I shut down and the screen blackens all the colors change to a very ugly old vga look. Also google earth won't start and i think that's because i don't have the ability to use 3d yet.

link to ati site: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6-inst.html)

   1. Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver you have downloaded
   2. Enter the command sh ./ati-driver-installer-8.33.6.run to launch the ATI Proprietary Linux driver installer.

      The ATI Proprietary Linux Driver Setup dialog box is displayed

	Note: 	You must be logged in with super user privileges in order to successfully install the ATI Proprietary Linux driver.

   3. Select Install Driver and click Continue. The ATI License Agreement is displayed.
   4. Read the License Agreement and Click I Agree to continue the installation, or Cancel to terminate the installation. The Mode of Installation Dialog Box is displayed.

   5. Select Custom and click Continue. The ATI Proprietary Linux Driver Setup options is displayed.

   6. Select the driver components to be installed and click Continue. The ATI Proprietary Linux Driver is installed, and the Installation Complete Dialog box is displayed.

   7. Click View HTML Release Note for last minute driver information, or Exit to close the driver installer.
   8. Launch the Terminal Application/Window and run /usr/X11R6/bin/aticonfig --initial to configure the driver.
   9. Reboot your system.

---

### Post by tonyr1988 on 2007-02-08
1) Try re-doing step #2, this time running:

> sudo sh ./ati-driver-installer-8.33.6.run

Then continue like normal. I'm not sure if that will affect anything, but maybe it didn't dump the aticonfig file (and others) because of permissions issues? I think the /usr/X11R6/bin is just a symbolic link to /bin (I may be wrong), and /bin won't be writeable by you, only root.

2) If that still doesn't work, you may want to try this thread:

[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

Scroll down and it has install instructions - looks much easier than from ATI's site. But make sure you read / print the top half, in case that happens.

But I'd try sticking with what you're working with as long as possible - it's no fun to have tons of clutter from different failed attempts. Who knows what kind of problems it can cause. :D

---

### Post by -Ghost9- on 2007-02-08
this is what i get after running your quoted line:

Found fglrx primary device section
Nothing to do, terminating.

and this is my fgrlxinfo

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

