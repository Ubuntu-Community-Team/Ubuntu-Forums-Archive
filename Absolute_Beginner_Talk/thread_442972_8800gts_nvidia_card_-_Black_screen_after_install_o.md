---
title: "8800gts nvidia card - Black screen after install of Ubuntu 7.xxx"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Hunter4u on 2007-05-14
Ok, you have probably seen this more than once, as I have been searching for 2-3 weeks on howto make this work.

I am dual booting with XP, I install Ubuntu, the 64-bit edition, all goes well, rebbot the machine after install, grub loads, I tell it to goto Ubuntu, loads up to a black screen. I cant get it to load the command line interface from here,  so I reboot, load the command line recovery option, update it and all.  I keep reading on how peeps use envy to laod the correct drivers for the 8800gts, but they are in the gui already, I cant get there.

So I read more and more how peeps say to do it, but I guess I am to dense to figure it out.

Can someone explain a detailed howto for this?

I even downloaded the drivers from nvidia, burnt to a cd, as another guide said to try it that way, well I am pretty green at this Linux, so I would imagine me pooking around with different commands trying to get it to mount the cdrom would be considered a failure. lol

Thanks in advance if someone would help me out, as I believe once I get into the gui, all will be most better

---

### Post by Bachstelze on 2007-05-14
Do you have a net connection on that Ubuntu box ?

---

### Post by Hunter4u on 2007-05-14
yes sir, it has net, just reinstalled it for a 3rd time using the manufactures install option this time, still no joy, did all the updates and such using this:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade


went thru all that no problem, just still can't boot into the gui version, just text mode on recovery

---

### Post by mrazster on 2007-05-14
If I'm not mistaken you have to have the *nvidia-glx-new* drivers installed. I would try something like:

```
sudo apt-get remove nvidia-glx nvidia-glx-legacy
```
Just to make sure you don't have any old nvidia drivers jerking it.

And the do:
```
sudo apt-get install nvdiai-glx-new
```
To get the new ones installed.

And last, do:
```
sudo nvidia-glx-config enable
```
To enable the new drivers.

Not sure, but you might have to reboot between the first two commands.

---

### Post by Bachstelze on 2007-05-14
Before installing nvidia-glx-new, just to be sure, install the restricted modules matching your current running kernel :

```
sudo apt-get install linus-restricted-modules-$(uname -r)
```

---

### Post by Hunter4u on 2007-05-14
that didn't work,  it did make it load a blue screen though, with tons of question marks around it, and some text stating that is didnt load right or something to that nature, and that it would be disabled until I get it fixed.

lol, thought it basically was disabled prior to this.

thanks anyhow,  
anymore thoughts?   going to crash right now, will check this later on today maybe this evening.

---

### Post by meborc on 2007-05-14
you should try to reconfigure your x
```
sudo dpkg-reconfigure xserver-xorg
```
just chose the default answers when you don't know what to put in...

if that doesn't work i would try to install the 32-bit version of ubuntu as 64 edition is less supported (just my view as i have core 2 duo 6600 and i have had many problems with programs/drivers not wanting to run... java will be a b**** for sure on 64)

---

### Post by mrazster on 2007-05-14
OK then...have you tried this..?

When in CLI enviroment(command line) type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
to backup your existing xorg.

Then:
```
sudo nano /etc/X11/xorg.conf
```

Scroll down to *Section "Device"*. It should look something like this:
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GT/GTO"
EndSection
```

Now, as your *nvidia-glx-new* didn't work. you are going to try to load the "natvie" nvidia drivers. To do this change *Driver* from ***nvidia*** to ***nv***.
It should look something like this:
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GT/GTO"
EndSection
```

Press ***ctrl+x*** to exit and press***Y*** when asked to save to xorg.conf
Then reboot:
```
sudo reboot
```
This way you atleast should be able to login to your X...and from there figure out whats wrong.




But before doing this you could try as suggested before, do:
```
sudo dpkg-reconfigure xserver-xorg
```
and see if reconfigure the xorg settings would help.

And if none of this work...well then I'm out of ideas...other than mabey reinstall.

---

### Post by Hunter4u on 2007-05-15
well guys, none of this seemed to work so I go in a and  use my trusty 98se boot dic and do the fdisk /mbr to remove the bootloader for linux, so I could delete/remove the Ububtu install.... MAn that alost turned into a nightmare, took an hour to find one of my programs to fix the mbr, finally got it running again...

Anyway, I downloaded the live cd version of ubuntu 64, still no joy on video, couldnt even see it install liike   before.
\IS there anyway to modify the ISO of the disc to use the newest drivers of nvidia for the 8800gts card?


I am not giving up, but am looking into other ways of going about this, any info would be great on what I need to try.


Thanks

---

### Post by mrazster on 2007-05-15
It has been an issue before with G80 cards...bugas are reported and fixed. If you have downloaded latest .iso and done a 
```
sudo apt-get upgrade
```
after install then you should be all fine....

Just for the heck of it....what other hardware are you using..?

---

### Post by Hunter4u on 2007-05-16
I downloaded the ubuntu x86  32 bit version yesterday to test my setup,  it actually loaded the live cd correctly, so I could see the desktop--I installed it and all went well. I really wanted to run the 64-bit version just  to see how well my new rig would handle it, guess I can us vmware to test it can't I?


My hardware is as follows:
Asus M2N32-SLI Deluxe
+5600 X2  AM2  2x1m cache    2.8 mhx x 2
EVGA 8800GTS  320 meg version
2 gigs Corsair XMS DDR2 6400  4-4-4-15 timings @ 800
Lite-on 167 DVD Reader
Lite-On 160P5S  Burner  - I think that is the model
1 - 160 gig Samsung HD
Antec 650 Trio PS
Antec 900 series Case
1.44 floppy mitsumi
Samsung 225bw    22 inch Wide screen   1680 x 1050  res

---

### Post by mrazster on 2007-05-16
Oh well...atleast it's all fine with 32bit...

I have tried them both as I'm running a Opteron rigg...and I can safely say that you won't "notice" any difference...other than the fact that you'll have less hassle getting stuff to work porperly.

---

### Post by Hunter4u on 2007-05-16
well, I went to install the newest nvidia drivers for it and get the screen with all the questions marks on it telling me that it isn't configed right.
I ran this:

sudo dpkg-reconfigure xserver-xorg

this didnt seem to help the problem, so guess I will try to reload the backup of the xorg.conf file, then if that doesnt work, reckon it will be a reinstall...again....

woohoo!
reminds me of the win 3.1  or 95 days....lol

---

### Post by Hunter4u on 2007-05-17
Got it going guys.
I used ENVY to achieve this, I am now happily moving along at 1680x1050 res at 60hz..
All looks good thus far.


I know that envy probably isnt the best solution for it, but it did make it easier for a greenhorn like me to achieve what was on hand.

---

### Post by Matthaeus on 2007-05-17
Your not alone - there are a couple of bugs in regards to nvidia drivers and 8800's series cards. It depends on which one you are referring too, but if its the wfb or libwfb, then the steps on this [page]("http://ubuntuforums.org/showthread.php?t=433979&highlight=http%3A%2F%2Falbertomilone.com%2Fubuntu%2Fnvidia%2Fnvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb") should fix it. I can't remember where i found it initially - i can't use envy, or couldn't get it working with my proxy server.

Good work getting it going.

---

### Post by midiwriter on 2007-05-17
Hunter4u, I am in the same boat as you...same card, same setup basically.  I too, FINALY got the drivers to work thru Envy, but still can't get Baryl and Emerald working.  It seems to install ok, and I get all the configuration programs installed, but still no baryl effects.  Do you have Beryl working on your system yet, and if so, how did you do it?  

On a similar note, is anyone working on these issues with the GeForce 8800 series driver issues???
Thx

---

### Post by heldal on 2007-05-21
> **midiwriter said:**
> Hunter4u, I am in the same boat as you...same card, same setup basically.  I too, FINALY got the drivers to work thru Envy, but still can't get Baryl and Emerald working.  It seems to install ok, and I get all the configuration programs installed, but still no baryl effects.  Do you have Beryl working on your system yet, and if so, how did you do it?  

On a similar note, is anyone working on these issues with the GeForce 8800 series driver issues???
Thx

The driver-package is being fixed as shown on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103050")

In the meantime copy the missing file manually as described in [this]("http://ubuntuforums.org/showthread.php?p=2687780#post2687780") thread.

There are some options in the X-server (screen-handler) that has to be updated to make beryl or compiz working. I added the following lines manually to the "Device"-section of /etc/X11/xorg.conf:
```
Option "AllowGLXWithComposite" "true"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```
The command "sudo nvidia-glx-config enable" should do the same thing.

---

### Post by Codestorm on 2007-10-20
So what do you do when even using Envy doesn't work for you? (It installs the drivers fine, but once X loads the black screen is still there)

I'm desperate to get 3D acceleration working in Ubuntu 7.10 with my 8800GTS 640mb. I've tried all the things people have suggested here, and in other threads, but to no avail. Can anyone help?

---

