---
title: "loaded OS, no internet, need to load video driver"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by dsonyay on 2007-05-25
OK,
I've got Ubuntu 7.04 loaded on my laptop.
It's got an ATI x1400 card.

I need to get it running so I can get my screen resolution set.  Currently it's loaded in a generic vesa 640x480.

When I go to"restricted drivers manager" ATI accelerated graphics drivers" shows up, but I cannot enable it.  There's a checkbox, and when I click it, a pop up box comes up asking if I want to enable the driver.  I click "enable driver" but nothing happens.

I want to do an apt-get update,
BUT- I have no internet.  I cannot get the internet connection up and runnig.  When I look at my devices installed, the ethernet card shows up  (Broadcom BCM4401-B0 100Base-TX).  The internet connection works on my PC, but when I plug the cable into my Dell (E1505), I cannot get any pages to load.

I try to set up my connection manually, but I'm getting no where.  I double click the network icon on top of the screen and the Network settings window opens.  I hilight "Wired Connection", click prpoerties, nad have no clue what do do now.  Do I take out of roaming mode?  If I do that are there default settings I can try?

I'm now tired and frustrated. 

David

---

### Post by jargoman on 2007-05-25
Assuming your card is supported because you said it was before....

System >> administration >> network

highlight your wired connection, then click properties. Take it off roaming mode (I don't know why you have that option because that's for wireless cards) then change it to "Automatic configuration (DHCP)" leave the rest blank. When you exit make sure the little box infront of "wired connection" is checked. A little window should pop up reading something about configuring interface. 

This should work. 

Make sure the router you are hooking your computer to is set to dhcp. This is probably the case if your other pc "just works" when you plug it in.

---

### Post by lsalminen on 2007-05-25
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

That should help with your ATI X1600 card.

---

### Post by dsonyay on 2007-05-25
I'll try that once my internet is up.  I cannot do the update until I get my internet connection up.

---

### Post by dsonyay on 2007-05-25
router??
My cable internet comes out of the wall into a "webstar" cable modem then into my laptop.  No router.
When I plug the ethernet cable into my PC, voila, instant internet.  When I plug into my laptop- nothing.

Yes, I did take it out of roaming, yep- the automatic config is on.

I've spent all dayt trying to get this OS running.  I can't remember a day this bad since I had Win98.

---

### Post by jfinkels on 2007-05-25
> **dsonyay said:**
> I'll try that once my internet is up.  I cannot do the update until I get my internet connection up.
What is the output when you type this command in the terminal (Applications > Accessories > Terminal)?
```
ifconfig -a
```

If you can't get your internet connection to work, you may need to install the driver found here: [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by southernman on 2007-05-25
> **dsonyay said:**
> I can't remember a day this bad since I had Win98.

Flogs dsonyay with a wet noodle  ):P

---

### Post by dsonyay on 2007-05-25
Oh geez.  I don't think I'll ever complain about XP again.
Ok, I'll try that. 
I'm doing a double scotch and going to bed first.


> **jfinkels said:**
> What is the output when you type this command in the terminal (Applications > Accessories > Terminal)?
```
ifconfig -a
```

If you can't get your internet connection to work, you may need to install the driver found here: [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by dsonyay on 2007-05-26
OK,
I have my plan figured out.
First- get my internet runnig.  When I run pppoie (or something like that) it tells me there are 3 devices:  
eth0, eth1, and something else (can't remember).  It tries to connect up to one of them but can't.  When I do a hardware test (The Ubuntu utility that tests your hardware then asks you to type out comments for each and automaitically e-mail the results), it actually tells me my ethernet card is OK,  it does a ping to somewherein the system and it comes up OK to Ubuntu.

After I get my internet up- getting the ATI card issue fixed will be much easier by doing the simple step by step listed here: 

sudo apt-get update
sudo apt-get dist-upgradeInstall fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrxUpdate loaded modules.
sudo depmod -aConfigure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot

---

### Post by cymen on 2007-05-26
Sorry this is being so stressful for you! Let's see if we can save your eyes though. I think I got my Radeon card working under the correct resolution with the default driver by manually editing my xorg.conf, before installing the fglrx driver. So let's backup your xorg.conf and open it up:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Look for the Display sections. Anywhere you see "640x480" add your preferred resolution in. Here's what the relevant bit of my file looks like, for reference, yours won't be exactly the same:

```

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800" "800x600"
        EndSubSection
EndSection

```

Restart X by hitting Ctrl+Alt+Backspace, login and try to change your resolution again. If it all goes horribly wrong and you're left with nothing more than a text prompt, restore the backup of your xorg.conf.

```
sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

I really hope that helps.

---

### Post by amok69 on 2007-05-26
just went thru something similar and all got updated / solved as soon as the internet connection was installed. have a look [here]("http://ubuntuforums.org/showthread.php?t=451169&page=3") for some info on doing that.

hope it helps.

---

### Post by dsonyay on 2007-05-26
Sorry, but didn't help at all.  I replaced with a screen res of 1440x900.  Rebooted.  System would xorg would not load up.  Back to old settings.

---

### Post by jfinkels on 2007-05-26
What is the output when you type the following command into the terminal (Applications > Accessories > Terminal) after plugging in your ethernet cable?
```
ifconfig -a
```
Copy and paste it here.

You may need to get the drivers for your card as I said above...

---

