---
title: "New EduUbuntu- Help with wireless router and sound?"
date: 2007-08-06
forum: Apple PPC Users
---

### Post by shedt on 2007-08-06
I had booted with a older 5.10 I believe Ubuntu cd, it had sound but it could not install. I installed EDUbuntu works great, but there is no sound.

Using a G4. I also cannot get my d-link router to work, D-Link WUA 1340. I really don't know where to start or what to do. Transfered over some drivers with usb key, but I don't know how to install them

:(


Any help or suggestions are welcome.

---

### Post by tcrroadie on 2007-08-06
What model Mac are you using?  Please visit the link below and post back with the specific model that you are using. 

[apple-history.com]("http://www.apple-history.com/")

What version of Edubuntu are you using?

If you like, you can also download the latest version of Ubuntu (Feisty Fawn) for PowerPC from the link below.  

[Ubuntu PPC Downloads]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")

---

### Post by shedt on 2007-08-07
Thanks, I was looking for that but I could not find it.

---

### Post by shedt on 2007-08-09
Ubuntu (Feisty Fawn) does not load with "live"

It stops and says:

failed to start the x server...........

clicking yes for error log-

)EE) end of block range 0xefffffff


(**) RADEON(0): RADEONPreInit


there is more but i dunno what it means.


then it says:

the x server is now disabled. restart GDM when it is configured correctly. Then it just goes to a black promt.

I think this is the Mac:

[http://www.apple-history.com/body.php?page=gallery&model=g4da&performa=off&sort=date&order=ASC](http://www.apple-history.com/body.php?page=gallery&model=g4da&performa=off&sort=date&order=ASC)

---

### Post by stmiller on 2007-08-09
Hm sounds like the Live CD probably won't work on that machine. iMac G5s have similar problems, due to the Radeon card and radeon driver.

If you have your data backed up, you can completely install Feisty with the alternative PowerPC CD.

The alternative CD boots and goes right to an installer (no pretty desktop), to just install Feisty. Press tab at the boot prompt to see all options.

So try that alternative CD.

---

### Post by shedt on 2007-08-10
I can't do anything with  the disc I have? Can I install with the live disc if x server does not work from the prompt?

I wish I could just type install blah blah etc

:D

---

### Post by tcrroadie on 2007-08-10
The link you posted to the Power Mac, list a Nvidia video card.  Does your Power Mac have a Nvidia card or an ATI card?  If it has an ATI card, is it a Radeon card or Rage 128 card?

Don't sweat.  We should be able to get you a working Xserver still.  If you are dropped to a command line after the Xserver fails to start we can make some changes to the configuration file for the xserver to try and get it to come up.  Lets try booting your live Ubuntu Feisty disc again.  

1.  After you are dropped to the command line, type this
```

sudo nano /etc/X11/xorg.conf
``` 

Nano is a text editor and will allow you to edit the Xservers configuration file "xorg.conf".

2.  Page down the file using the arrow keys on your keyboard until you get to a line that says Section "Device".  Now if your Mac has a Nvidia video card, within that section, change the line that says Driver  "ati" to "nv".  The "ati" driver is for ATI Radeon and Rage 128 video cards.  Should look something like this.  

        ```
Section "Device"
        Identifier      "Nvidia GeForce2"
        Driver          "nv"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"  "true"
```

3.  Now press ctrl+x to save the file and exit nano.  

4.  Restart your xserver by typing this at the command prompt. 

```
sudo /etc/init.d/gdm restart
``` 

5.  This will start Gnome's login manager GDM.

The above should work for a Nvidia video card.  Now if your Mac has an ATI video card, you can always try using the video driver "fbdev" to get you going.  

6.  Do the above steps again and edit the "Device" section of your xorg.conf to look something like this.  Change the Driver line to "fbdev".

```
Section "Device"
        Identifier      "ATI display adapter"
        Driver          "fbdev"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"  "true"
```

7.  Save the file again (ctrl+x) on your keyboard, and restart your xserver.

```
sudo /etc/init.d/gdm restart
```

---

### Post by shedt on 2007-08-10
Radeon card, I'm being dropped I think back into open firmware?

Nano does not work.

I've installed the alternative CD but on first boot it's doing the same thing.

edit

i'm in the command line just logged in.

---

### Post by shedt on 2007-08-10
Raedon RV200 QW 7500

---

### Post by shedt on 2007-08-10
I'm in, thanks for the help I really appreciate it!


EDIT

Still no sound? The 5.10 live disc had sound, this one does not. I'll do some forum searches though and check the hardware.

---

### Post by shedt on 2007-08-10
I'm online now and downloading updates.

---

### Post by shedt on 2007-08-10
Solved!


> **ajmctaggart said:**
> Just Try This...

sudo nano /etc/modules

& add this line to end

snd-powermac

save and reboot

Let us know if this solves it...

---

### Post by tcrroadie on 2007-08-10
Great.  :)

So what video driver are you using?  The correct video driver for your card is "radeon".  

The radeon driver is a community created driver for ATI Radeon cards that has 3D support for many Radeon cards.  See the man page for more information on this driver.

```
man radeon
```

If you are currently using the "fbdev" driver, you may want to try changing the driver used to "radeon".  Maybe there was an update that helped fix the xserver failure problem you were having, when the xserver was trying to load the radeon driver.     

If X is still failing on you when using the radeon driver, we can take a peek at the xorg.log and try to figure out what is causing the failure.  

Glad to here you got Feisty installed and working.  If you have not done so already, I would suggest reading the PowerPC FAQ Wiki.  It is a must read.  The wiki has great information on configuring Ubuntu on your Mac.  

[PowerPC FAQ Wiki]("https://wiki.ubuntu.com/PowerPCFAQ")

---

### Post by shedt on 2007-08-14
thank you for the help. I tried to change the file again (I know it was working) since I was stuck at 60hz refresh rate. It's broke again, but i will try to use the raedon driver now.

thanks for the help!

---

### Post by shedt on 2007-08-14
I can't get a command prompt now, it just tries to use a boot script or something. Sudo won't work nor will open firmware commands.

---

### Post by tcrroadie on 2007-08-14
Exactly what is happening?  Do you see the Ubuntu splash screen when booting?  Do you receive an xserver failure massage?  What change have you made that caused the xserver to fail? 

If your machine appears to be booting somewhat normally, and the xserver never comes up, give it about the same time you think it would take to boot to the login manager, and then press **ctrl+alt+F2**.  This should bring up a virtual terminal with a command prompt asking you to login.  Then you can fix you Mac from here.

---

### Post by shedt on 2007-08-14
I got into it via linux video=ofonly


not sure what it does, but I will try to change my xorg.conf file again. I was trying to do something I read here in regards to setting up a proper display. I don't think it likes the radeon driver.

edit

darn control alt f2 made my screen black. cannot display this video mode. I will reboot and try the linux video=ofonly

---

### Post by shedt on 2007-08-14
OK I'm in with the Linux video=ofonly

The resolution and refresh rate seems fine now, it is changed to what I was trying to change it too. No more 60hz. But i'm not sure, do I have to boot video=ofonly each time?

I'm going to try and edit it to the fbdev driver, that is a driver correct? It does not seem to like ati or radeon.

---

### Post by tcrroadie on 2007-08-14
Just as you said, it sounds like your video card does not like the radeon driver.  Yes you can use the fbdev driver for your system.  Should work fine with fbdev.

---

