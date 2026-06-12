---
title: "After trying to load ATI drivers, No screen!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Satummoo on 2007-12-11
I followed the steps in an ATI driver install and now when I boot up, I see the ubuntu sign load bar, then after it's done, the screen is black.  I had this same problem before with 7.04 and the only solution was the complelty reinstall.  Is there any easy way to recover and is there a guide that works :( ? I remember last time trying every guide and nothing helped

---

### Post by Teknyk on 2007-12-11
What steps to install the ATI drivers were you following? I used the ATI drivers under the restricted drivers manager and didn't have any issues.

---

### Post by Saint Angeles on 2007-12-11
try restarting in recovery mode and then: vim /etc/usplash.conf

change your resolution to the correct settings and then try restarting.

---

### Post by Satummoo on 2007-12-11
[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz)

tried doing that and the wiki guide on unoficial drivers from ATI

so If I enter what you said, I won't have to redo the xserver? It will just revert?

---

### Post by kpkeerthi on 2007-12-11
Found some workarounds here...
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)

---

### Post by Satummoo on 2007-12-11
> **Saint Angeles said:**
> try restarting in recovery mode and then: vim /etc/usplash.conf

change your resolution to the correct settings and then try restarting.

that didn't do anything at all :confused:

and the other link didn't seem the be good for me either,  maybe i'll just re-install fresh again?  I know it sounds stupid but i'm really new to all of this.

Should I install envy? Is that the easiest way?

also, is there a way to backup the way ubuntu is so If I do something I didn't want, I can revert back?

---

### Post by mcduck on 2007-12-11
> **Satummoo said:**
> that didn't do anything at all :confused:

and the other link didn't seem the be good for me either,  maybe i'll just re-install fresh again?  I know it sounds stupid but i'm really new to all of this.

Should I install envy? Is that the easiest way?

also, is there a way to backup the way ubuntu is so If I do something I didn't want, I can revert back?

The easiest way is to use the drivers from the Restricted Drivers Manager.

The second easiest way is to run 'sudo apt-get install xorg-driver-fglrx' and then 'sudo aticonfig --initial'

These will both use the drivers from Ubuntu repositories and that is much less likely to cause problems than any other way.

---

### Post by Satummoo on 2007-12-11
> **mcduck said:**
> The easiest way is to use the drivers from the Restricted Drivers Manager.

The second easiest way is to run 'sudo apt-get install xorg-driver-fglrx' and then 'sudo aticonfig --initial'

These will both use the drivers from Ubuntu repositories and that is much less likely to cause problems than any other way.

is the restricted drivers way just unchecking my video card when I go to system>admin>restricted drivers?  I've done that before with 7.04 and when I rebooted all I got was a black screen.

and the 2nd way, do I just simply copy and paste what you put into the terminal w/o unchecking the restricted driver?  Or do I first uncheck the driver, then copy and paste what you put in the terminal, and then everything I need will be downloaded?

and how do I do a "system restore" if something goes wrong, currently, I'm on the live CD typing and reinstalling b/c I know of no other way of fixing the problem (I tried the steps above but got nothing)

thank you guys too for your patience! :)

---

### Post by mcduck on 2007-12-11
> **Satummoo said:**
> is the restricted drivers way just unchecking my video card when I go to system>admin>restricted drivers?  I've done that before with 7.04 and when I rebooted all I got was a black screen.

and the 2nd way, do I just simply copy and paste what you put into the terminal w/o unchecking the restricted driver?  Or do I first uncheck the driver, then copy and paste what you put in the terminal, and then everything I need will be downloaded?

and how do I do a "system restore" if something goes wrong, currently, I'm on the live CD typing and reinstalling b/c I know of no other way of fixing the problem (I tried the steps above but got nothing)

thank you guys too for your patience! :)

If the using the Restricted Driver manager gives you black screen it's most likely just a resolution/refresh rate issue and can be solved by changing the resolution in /etc/X11/xorg.conf to something that your display can handle.

For the second way, if you have already installed the driver from Restricted Driver Manager the first command will simply reply that the driver is already installed. The second command might or might not help if the drivers are already installed.

There is no 'System Restore' in Ubuntu, but if you save a backup of the /etc/X11/xorg.conf before doing anything, if things go wrong all you need to do is to boot into the recovery mode and copy the backup file back.

For example you could create the backup by running this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

And to copy it back in recovery mode you'd run this:
```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
(no sudo this time, it's not needed as you are already root in the recovery mode)

---

### Post by Satummoo on 2007-12-11
yay good news, After I updated all my software, I backed up my xorg and installed envy as all the guides seemed difficult for me to understanding what I am doing.  Well it worked!  Booted up and now I'm at my monitors native resolution.  HOWEVER, I get a lil popup saying that under restricted drivers that my graphics card is not enabled, yet the drivers are installed.  Should I check off my graphics card under restricted drivers or keep it as is?

now comes the hard part of flash and java :(

---

### Post by mcduck on 2007-12-11
> **Satummoo said:**
> yay good news, After I updated all my software, I backed up my xorg and installed envy as all the guides seemed difficult for me to understanding what I am doing.  Well it worked!  Booted up and now I'm at my monitors native resolution.  HOWEVER, I get a lil popup saying that under restricted drivers that my graphics card is not enabled, yet the drivers are installed.  Should I check off my graphics card under restricted drivers or keep it as is?

now comes the hard part of flash and java :(

It says that the restricted drivers are not enabled because envy doesn't use drivers from Ubuntu's repositori3es and because of that Ubuntu's package management doesn't know that you have the driver installed.

You can just go to System/Preferences/sessions and disable the Restricted Drivers Manager on the Startup Programs-tab.

Both Flash and Java are available in the Add/Remove-thing in the applications menu. Just make sure to pick the Sun Java instead of the Blackdown version.

---

