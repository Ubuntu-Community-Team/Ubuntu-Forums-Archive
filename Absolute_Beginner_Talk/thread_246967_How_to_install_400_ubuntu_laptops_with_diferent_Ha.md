---
title: "How to install 400 ubuntu laptops with diferent Hardware?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by egoldtech on 2006-08-30
Hi everyone, thanks in advance for reading and response ....
Heres is the dilema :
we want to install more than 400 ubuntu on laptops, some lots they have same hardaware, others no. 
What i will love to do is, install on one PC, and then install all the extra Appplications we need, extra CODECS or playt dvd, mp3, Firefox and system Tune ups, bla bla bla .  and then, replicate this configuration to all this computers ....
I know with the same hardware, i will make a partition image and the restore it ...... 
but what about all diferents brand and hardware??????
 
regarda
Eze

---

### Post by hakre on 2006-08-30
Well this looks like a very challenging mission to me, with a that high count of installs I would recommend you get in touch with a professional.

Before that I think it is very important you define what really is needed and what not. I would devide this into two parts:

1.) Hardware
2.) Software

When you get a base install working with all the hardware you got (maybe group them, so to have 300 computers all the same Type A, 50 type B, 30 Type C and 10 Type D), then you can go on.

It should be possible to apply all the same softwarepackages repository on them. Checkout Ubuntu's packet manager if he can do this job the way you need it on your 400 machines. This config / script can be copied on each computer and executed there.

Inbetween you need a concept of creating a root user on each computer and maybe you should implement a remote access feature (ssh) sothat you're able to control the 400 pieces setup from a single box - as you already suggested.

But I'm a beginner only as well, so you should look around if someone did a related task already. The more you're informed the better is with such a big project.

---

### Post by amo-ej1 on 2006-08-30
The ubuntu kernel is rather 'generic'. So cloning a basic install will get you rather far. So I suggest you create a simple install, put everything on it that you want (install it on one of the most common laptops). After this take a look at [http://systeminstaller.sourceforge.net/]("http://systeminstaller.sourceforge.net/") systeminstaller bundles systemimager and systemconfigurator. With systemimager you will be able to take an image of you first installed laptop (the 'golden client') after this you can make a network setup where each other laptop gets bootstrapped from a central server. This would require support for network boot on all laptops, but most laptops should support it (i hope for you).
The only thing you'd need to do is test each individual laptop and correct settings like loaded modules, if needed ip config and X config. 
Or you could create an image for each 'type' of laptop mentioned in (one of) the post(s) above.

---

### Post by coffeecat on 2006-08-30
Last year I installed Foresight Linux on an AMD 64 box with a VIA chipset on the motherboard. With the onboard video chipset the installer set up xorg.conf with the generic VESA driver. Then I took the harddrive out and put it in an Intel Celeron box with Intel chipset (and Intel 845G graphics). Completely different sound device, different ethernet controller, USB controllers, etc, etc. As far as I remember it booted up fine and ran OK. Hats off to Linux and Foresight. Imagine what Windows would have done! :)

I should imagine the main problem will be the graphics chipset. I only got away with that experiment because the installer had set up the VESA driver. If you were to install on a machine with ATI graphics (say) and then transfer the image to an Nvidia machine, the xorg.conf file will be wrong and xorg will crash. But I should think all other hardware will be OK so long as the drivers are in the kernel and the hardware is autodetected on bootup. At the moment I cannot think of another example of hardware which needs a static .conf file, and graphics is a special case anyway because of the xserver.

Suggestion - group your machines as hakre has suggested, except by video only. Then take two otherwise wildly dissimilar machines, install on one, transfer partition image to other and see what happens.

One last thing. You'll have to have your partition layout the same for each machine otherwise you'll have to edit fstab for each installation.

---

### Post by egoldtech on 2006-08-30
Hi,  thanks for the ideas ...
the true is I dont have all the laptops at the same time, I will have 40 or 50, and then the next lot, etc , so will be a litle random .
I like the idea with  systemimager.   lets see  ...
if not, will work by models, like we did on our last projects win guindows .... a server with images for every model and language, and restore them via USB IDE . .....

---

### Post by insub2 on 2006-08-30
if i understand you, you want to have the same programs on all the laptops, this may be of interest:

[http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/")

it is a custom cd maker.  i haven't used it but it is discussed in this thread:

[http://www.ubuntuforums.org/showthread.php?t=229625]("http://www.ubuntuforums.org/showthread.php?t=229625")

i'm not sure all of what is capible of or if it will work for you.  but it was my fist thought to how i would solve your problem.  good luck with whatever you use.


***
EDIT:
just found this:

[http://uck.sourceforge.net/]("http://uck.sourceforge.net/")

---

### Post by Frank Golden on 2006-08-30
> **coffeecat said:**
> Last year I installed Foresight Linux on an AMD 64 box with a VIA chipset on the motherboard. With the onboard video chipset the installer set up xorg.conf with the generic VESA driver. Then I took the harddrive out and put it in an Intel Celeron box with Intel chipset (and Intel 845G graphics). Completely different sound device, different ethernet controller, USB controllers, etc, etc. As far as I remember it booted up fine and ran OK. Hats off to Linux and Foresight. Imagine what Windows would have done! :)

I should imagine the main problem will be the graphics chipset. I only got away with that experiment because the installer had set up the VESA driver. If you were to install on a machine with ATI graphics (say) and then transfer the image to an Nvidia machine, the xorg.conf file will be wrong and xorg will crash. But I should think all other hardware will be OK so long as the drivers are in the kernel and the hardware is autodetected on bootup. At the moment I cannot think of another example of hardware which needs a static .conf file, and graphics is a special case anyway because of the xserver.

Suggestion - group your machines as hakre has suggested, except by video only. Then take two otherwise wildly dissimilar machines, install on one, transfer partition image to other and see what happens.

One last thing. You'll have to have your partition layout the same for each machine otherwise you'll have to edit fstab for each installation.
I am guessing you are IT for a company that wants to outfit it's
fleet of laptops to Ubuntu and they have tasked you with doing this. If it were me I would seek funds from my employer and
install and optimize Ubuntu on however many machines as it takes to cover all the different hardware layouts.
Then using the representative drives, farm out the work to a Pro
company that has the equipment to take the different drive samples and clone them to their respective drives. You would
have to remove the drives fom the computers remembering to carefully mark them as to their hardware layout type and bring them to the pro doing the clonimg.

I don't know if I am making a lot of sense here.
But your time is money and this approach may save you in the long run.
 It would take a lot of time to copy images to each machine yourself using partimage or similar software. Drive clone machines are available for purchase I don't know what the cost is but for 300 or more machines it may be worth purcasing one.

---

### Post by egoldtech on 2006-08-30
> **insub2 said:**
> if i understand you, you want to have the same programs on all the laptops, this may be of interest:

[http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/")

it is a custom cd maker.  i haven't used it but it is discussed in this thread:

[http://www.ubuntuforums.org/showthread.php?t=229625]("http://www.ubuntuforums.org/showthread.php?t=229625")

i'm not sure all of what is capible of or if it will work for you.  but it was my fist thought to how i would solve your problem.  good luck with whatever you use.

wow, RECONSTRUCTOR looks good, definitily we have to try it .....

Firts steep is almost 50 laptops, then later the others one, so I dont think we are going to think big as Frank Golden says ...

---

### Post by Frank Golden on 2006-08-30
> **egoldtech said:**
> wow, RECONSTRUCTOR looks good, definitily we have to try it .....

Firts steep is almost 50 laptops, then later the others one, so I dont think we are going to think big as Frank Golden says ...
I thought you said 400 laptops?
Anyway 50 is gonna be a chore. Mostly time consuming if you 
are forced to use a CD. If you have access to 1-2GB thumb drive
you can install LiveCD to that after making RECONSTRUCTOR
image. Use this to install on thumb drive. Of course
your bios needs to support booting from thumb drives.
The below link describes how to install the Ubuntu DesktopCD
on a thumb drive. If you use a Ubuntu Desktop Thumb drive
it is much faster booting and installing is real quick (about 10 minutes). You just boot the Reconstructor Live "ThumbDrive"
and install from desktop.
Tell the partitioner to erase the whole HDD and install.
You would need to know user names and passwords for each install
or use a generic user name and password and instruct the individual users to change later.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28)
LiveUsb%29

Another option if you can boot from USB devices is to install SystemRescueCD on a small partition at start of a USB external HDD. Then create you representive install on a machine and
use partimage on the SystemRescueCD to create an image on a second Fat32 partition of the USB HDD.
You can then makesure all machines have same partition structure as the "master" and boot to SystemRescueCD on each machine
and use partimage to intall the image on each one. Depending on the image size it should take no more than 15-20 per machine.
This has the advantage of having the image to restore on the same drive as the installer(partimage). I have never tried this approach but if the partition structure is the same for all machines (ie: the master machine has Ubuntu only installed at
/dev/hda1 then making sure there is a /dev/hda1 on the other machines to overwrite
you should succeed)

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

The above link tells you how to install SystemRescueCD on a thumb drive or a USB HDD.
The below how to tells you how to use partimage from
the Linux SystemRescueCD.

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

---

### Post by Frank Golden on 2006-08-30
> **Frank Golden said:**
> I thought you said 400 laptops?
Anyway 50 is gonna be a chore. Mostly time consuming if you 
are forced to use a CD. If you have access to 1-2GB thumb drive
you can install LiveCD to that after making RECONSTRUCTOR
image. Use this to install on thumb drive. Of course
your bios needs to support booting from thumb drives.
The below link describes how to install the Ubuntu DesktopCD
on a thumb drive. If you use a Ubuntu Desktop Thumb drive
it is much faster booting and installing is real quick (about 10 minutes). You just boot the Reconstructor Live "ThumbDrive"
and install from desktop.
Tell the partitioner to erase the whole HDD and install.
You would need to know user names and passwords for each install
or use a generic user name and password and instruct the individual users to change later.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28)
LiveUsb%29

Another option if you can boot from USB devices is to install SystemRescueCD on a small partition at start of a USB external HDD. Then create you representive install on a machine and
use partimage on the SystemRescueCD to create an image on a second Fat32 partition of the USB HDD.
You can then makesure all machines have same partition structure as the "master" and boot to SystemRescueCD on each machine
and use partimage to intall the image on each one. Depending on the image size it should take no more than 15-20 per machine.
This has the advantage of having the image to restore on the same drive as the installer(partimage). I have never tried this approach but if the partition structure is the same for all machines (ie: the master machine has Ubuntu only installed at
/dev/hda1 then making sure there is a /dev/hda1 on the other machines to overwrite
you should succeed)

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

The above link tells you how to install SystemRescueCD on a thumb drive or a USB HDD.
The below how to tells you how to use partimage from
the Linux SystemRescueCD.

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)
Update: Tried the technique of installing the SystemRescueCD
on an external USB hard drive and copying partimage image to another Fat 32 partition on same drive. It will work but is very slow copying the image. It will be very slow restoring.

---

### Post by egoldtech on 2006-08-30
wow, really apreciate your replies .
thanks
I said 400 because will be like 400, we are going to start with this 50 and then continued with another lots.
There is a lot of imformation, and many thinks to try and test ... 
on every ubuntu we have installed, internet was really slow, until we did the tune up we found on this forum, like removing ipv6, and speeding up firefox, I dont understand why this setting dont come us default?  they will fixed on next releases or is on purposes ??

regards
Eze

---

