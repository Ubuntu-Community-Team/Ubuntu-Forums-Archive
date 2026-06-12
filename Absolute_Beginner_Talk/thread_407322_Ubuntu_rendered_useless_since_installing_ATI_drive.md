---
title: "Ubuntu rendered useless since installing ATI driver"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by reedness on 2007-04-12
Hi, I am new to Ubuntu and Linux for that matter.  I got my laptop to work great, thanks to reading these helpful forums.  We just got a new computer and the best part is that we did not have to purchase an OS.  I just love that!  :D 

Anyway, here is my issue.  I hope somebody can help me.  :confused: 

We have an ATI Radeon X1650 XT video card in the computer and I read the topic below and it seemed to match the qualifications for this driver  :o 

[BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9")

Well, I followed all the instructions very carefully, and when I hit ctrl - alt - backspace it just went to a gray screen and stayed that way.  So I pushed the reset button, and the beginning UBUNTU screen comes up and the orange colored loading meter gets almost to the end and stops.  I turned it off and back on.  It keeps doing that.  :( 

Then I tried to boot from the Live CD.  It takes a while, but when it boots, I hear the startup sound and all.  The taskbars on the top and bottom are visible but I can't see any icons at all.  The main portion of the desktop is all twisted and garbled and completely unusable.  I can't even re-install the OS because it's impossible to tell what you are doing because it's so garbled.  I rebooted again from the CD and tried "safe graphics mode" but it does the same thing.  ](*,)

Anyway, I am on my laptop now looking for things that might help me.  I then find this link  :frown:

[Radeon Driver]("https://help.ubuntu.com/community/RadeonDriver#head-b60183e198b030e0c2d76385685c6073aec882af")

This one says that it is unsupported.  I am so frustrated right now.  If there is anyone that can possibly help me out, that would be SO awesome.  I have been so excited about the whole Linux OS and all the free software, and now I am wigging out.  LOL.  Well, I just need some help, uninstalling the driver, or just a way to even format the drive and reinstall Ubuntu.  :?

Actually, any help at all would do.  Thank you so very much!!!  I look forward to being a part of this community.  :guitar:

---

### Post by jem7v on 2007-04-12
Can you reboot into Recovery mode, or whatever it's listed as at the Grub menu?  If not, when it gets to the end of the loading bar, can you press Ctrl+Alt+F1 to switch into a virtual terminal?

If so to either, you could use nano to edit your xorg.conf file and change the driver back to the default one that you were using before... i.e.,

```
sudo nano /etc/X11/xorg.conf
```

and then change the Driver (under Device) back to whatever it was to start with.

---

### Post by reedness on 2007-04-12
Ctrl-Alt-F1 did nothing.  I did get to Grub menu by telling the Live CD to boot from HD first, then hitting escape and pushing C at the menu that I got.  The sudo nano command does not work with Grub menu, but I can get to recovery mode prompt and open that /etc/X11/xorg.conf file but I don't know what the hell I am doing, or how to save it, or what the driver was before.  I tried to run the command to bring it back to default but it did nothing.  The command was sudo dpkg-reconfigure -phigh xserver-org     I have no idea what to do.  I'll get back to it tomorrow.  Thanks for the help!

---

### Post by jem7v on 2007-04-12
Boot into recovery mode.
Open that file with **sudo nano /etc/X11/xorg.conf**
Scroll down to where it says Section "Device" (the Page Down key about 6 times gets me to it in my xorg.conf)
Where it says Driver, change whatever it says to "ati" and save and exit (Ctrl+X, Y enter, enter.)
Reboot and see what happens.  That might get you to a working desktop again.

Meanwhile, the version of fglrx included in the repositories is a bit out of date.  The newer releases of it Do support your card!  Hopefully changing your driver back to "ati" will let you boot up into Ubuntu, and then I'd go to this page and follow the instructions for "Install the 8.35.5 Driver Manually": [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
(Well, read the Entire page, obviously, and not just that subsection... The Edgy repository only has version 8.28.8 of the driver and support for your card wasn't added until 8.32.5!)

---

### Post by reedness on 2007-04-12
I did exactly what you told me to do.  My driver was 6 pg dn as well as yours.  I changed it exactly as you told me to, and it's still doing the same stuff.  I saved it and rebooted.  I hope I didn't ruin my machine :cry:

Well, I will try any suggestions any of you have.  Thanks for the help.  I'll read that whole link you sent me Jem, I appreciate ALL the help.  I am not giving up.  I'm just a little sad right now.  :frown:

---

### Post by Feba on 2007-04-12
Short answer: ATI + Linux = ****


Long answer: I had a very similar problem. I just put in an nVidia and reinstalled from the live CD. Got nVidia drivers, been working fine since then (well, except for the fact that i'm using a GeForce2 MX, but meh)

---

### Post by reedness on 2007-04-13
I have been reading more and more and apparently ATI is not the recommended card for Linux.  I personally am displeased with them for giving us the finger, and I will not support them in the future either.  I am still attempting to troubleshoot the issue.  It's a good learning experience, but a pain in the neck.  I'm just hoping this system will be useful some time soon.  :confused:

---

### Post by kvonb on 2007-04-13
Which version of Ubuntu are you using on your new computer?

I would recommend using 6.10 Edgy, (unless you can wait until the 19th April to download the new 7.04 Feisty).

If using Edgy, boot from the LiveCD (standard i386 install CD, DO NOT USE THE 64 bit VERSION!!!!), and select safe graphics mode.

If you can get to a decent desktop on that, go ahead and re-install.  Do a clean install, format your partitions.

Boot your nice clean Edgy installation.  If you have a garbled desktop, then do this:

Press <CTRL><ALT><F1> and login with your standard username and password.

Type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now, it will ask you which screen sizes you want, and also which "driver" you need, select "vesa" and finish the setup.

Now type:

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

That should now re-load X and hopefully you should see a "normal" desktop.

Now go to this page:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And download then install "envy".  Look on your menu under "System" there should be an "Envy" icon, run it and select "Install ATI driver", follow the instructions and all should be rosy!

Or as a failsafe method, ask the store that you bought the computer from if you can change the ATI card for an Nvidia one, it will save you tons of problems!

Regards, KEv :)

---

### Post by kvonb on 2007-04-13
Oh yes I forgot to mention:

Each time you update your computer (the update notification icon thing), it is likely that when you reboot that you will **not** get to the desktop.

This is because the video driver has to be custom made for the "kernel" version that you are running, so if there is a new kernel or related update, the old video driver will not work.

But it's not too big of a problem, simply exit the error messages about X server not working etc', then type:

```
sudo envy
```

And go through the installation again, it is simple and fast.

---

### Post by jem7v on 2007-04-13
> **kvonb said:**
> Oh yes I forgot to mention:

Each time you update your computer (the update notification icon thing), it is likely that when you reboot that you will **not** get to the desktop.

This is because the video driver has to be custom made for the "kernel" version that you are running, so if there is a new kernel or related update, the old video driver will not work.

Specifically, what he means is any time you have an update to your kernel, restricted modules, or xorg you'll have to reinstall your video driver.  Other updates won't really do anything.


The "vesa" driver is probably a smart one to try.  It has awful performance, but it'll probably at least function.

---

### Post by reedness on 2007-04-13
:D   Thank you guys SO much.  Thanks to you, I now have a visible desktop, and I am now using envy to download my ATI driver.  Thank you all so much for your help!!!  I will probably be helping someone else out with the same problem in the future.


Thanks again!!!!!  You guys are AWESOME!!!!  :D    :guitar:


By the way, that driver works GREAT!!!  I am so happy right now!!!!

:D   :D   :D   :D   :D

---

### Post by kvonb on 2007-04-13
Glad to hear it worked out for you.

Don't forget the advice in posts 10 and 11 though, as you may need it in the near future :).

The new version of Ubuntu (7.04 Feisty Fawn) will be released soon (the 19th if all goes to plan), and envy does not work on that yet.

Although supposedly it is a simple 1 click install for the video driver, and it works perfectly with my Nvidia cards (on 3 computers so far), you might want to wait a little while before upgrading.  Maybe keep an eye on the forums for ATI drivers in Feisty, or even post a thread asking what other peoples experiences are.

Regards, Kev :)

---

### Post by freebird54 on 2007-04-13
Actually - I used Envy to toss the ATI drivers on a test install of Feisty about a week ago.  A separate link exists on the Alberto Milone site now.  Just in case you needed to know :)

---

### Post by reedness on 2007-04-13
Right on.  So when I need to reinstall the drivers, I just use envy to get the right one and do it again?  That's cool.  :D 

One more question though...  When I first went back to use the "Vesa" driver, I chose the resolution 1280 X 1024.  After I got the ATI driver, my system advised me that 1400 X 1050 was the better resolution option, so I am using that now.  My entire screen is shifted to the right whenever I start now.  Do I need to go back and choose the better resolution from that prompt where I was when I chose "Vesa" or has that been negated by the newer ATI driver?  That's probably a stupid question, but I don't know.  :confused:

---

### Post by jem7v on 2007-04-13
Have you gone to System > Preferences > Screen Resolution to try to change your resolution the easy way?

---

### Post by reedness on 2007-04-13
Yea I did it the easy way, but I was just wondering if what I did when I was changing over to the "Vesa" driver had an impact on the system.  You know, it seemed kinda like BIOS settings that I was editing even though I know that I wasn't.  You know what I mean?  Kinda just had that feel.

---

### Post by jem7v on 2007-04-13
The xorg.conf settings are basically the settings for your GUI environment, so they're pretty important.

As for the picture ending up not centered on screen, though, I find that just Happens with some monitors when you change from one resolution to another.  Mine certainly does!

---

### Post by reedness on 2007-04-14
Ok, as long as I'm not the only one with that experience.

I'll just go take a look at the xorg.conf file and absorb knowledge.  I'm here to learn this stuff, not just get through a problem.  I love it.

---

