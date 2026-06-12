---
title: "getting ubuntu to load on external HD"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by steve70 on 2007-12-09
What's up everybody...

I'm another noob trying to escape to the light of gutsy gibbon. I downloaded the CD, and fortunately, I have the Live CD up and running. The problem is trying to install 7.10 on my external HD. I went through the installation questions, and after I click the install button, the  'installing system' box hangs at 15%  (message at bottom of box -'detecting file systems'). It's been about 40 minutes, and I still don't see any  progression. 

I also tried to load the alternate desktop CD on my external HD, but it wasn't able to boot after the installation was completed.

WHAT THE F@%#K AM I DOING WRONG WITH THE INSTALLATIONS?

---

### Post by GeorgiaBoot on 2007-12-09
Well I just recently installed (Gutsy) on my external HD without a hitch.


Things you will need:

    * Ubuntu Linux (Free) [http://www.ubuntu.com/](http://www.ubuntu.com/)
    * A External Hard Drive
    * A Windows Machine, should work on Vista as well
    * A Little Time and Patience

Prep work:

    * 1. Download the LiveCD iso and burn to CD. Or have Ubuntu Ship you one for (Free).
    * 2. Prep your USB drive by deleting all partitions, no matter what kind they are.
    * 3. Disconnect your internal hard drive(s). *This is Key*
    * 4. Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
    * 1. CD
    * 2. USB
    * 3. Hard drive. 

If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

    * 5. Connect the USB drive
    * 6. Insert the LiveCD and boot your system
    * 7. When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

System > Preferences > Removable drives & media.

    * 8. In the Removable drives & media window deselect:
    * * Mount removable drives when hot-plugged
    * * Mount Removable Media When Inserted
    * * Browse Removable Media When Inserted

    * 9. Close this window.
    * 10. Select the Install Ubuntu Icon and run through the install routine steps. When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk. You can partition out any space you require later.

    * 11. Run the installation. Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot. Choosing sda or anything of that nature is not required by the new install cd.
    * 12. Restart the system when it is done.

Enjoy

---

### Post by steve70 on 2007-12-11
Thank you much GeorgiaBoot :guitar:

I looked at the instructions, gave it a try, and ubuntu is on my external hard drive!

Another question to ask: 
How can I get a dual boot with the PC HD (Windows XP)?

After the successful installation, I shut down my PC, and reinstalled my regular HD. When I fired my PC up, it booted right into XP. 

I checked the BIOS to reconfigure the boot priority. I noticed that there was one for the system AND a seperate priority setting for HDs

I set the priorities as follows:

SYSTEM:                                                
1. CD                                                      
2. HD                                                      
3. FLOPPY

 HDs
1. USB (**_'NOT INSTALLED'_** MESSAGE)
2. SYSTEM BIOS SETTINGS

The weird part is this, USB isn't noticed on the BIOS, but when I installed ubuntu on my external (from the LiveCD), it saw it right away!

---

### Post by GeorgiaBoot on 2007-12-11
In the System Bios you should be able to set to to USB.

Basically you don't want to change the boot bios now since you have the external drive installed. 

This is how you should configure your System Bios

CD
Usb
HD
IDE
USB/Floppy

or

USB
HD
CD
IDE
USB/Floppy

If you don't have USB before HD you won't be able to boot into Ubuntu, As it reads from the external drive first then internal. So if HD was before USB it would always boot into XP.


I don't think in HD bios it is detecting the external because it is not on.

---

### Post by GeorgiaBoot on 2007-12-11
Okay so I looked into dual booting. I personally don't dual boot as I see no point with it being on an external HD.

Basically if you setup dual boot, you would turn on your computer and your external HD (with Ubuntu) and pick on screen what system you want. 

I think it would be more practical to not install or make it dual boot, this is why.

How you have it setup now if you want ubuntu  you turn on the external HD and then the computer and you got Ubuntu. If you want XP just tun the computer on without turning on the external HD.

Basically you have to do the same amount of work either way to choose your OS to boot with. If you had installed Ubuntu on an internal HD you would need dual boot.

Now if you still want dual boot I will need to look it up for you as I have not done it with my external Drive.



I am not sure if you meant dual boot or what you really wanted was running them both virtually. Virtually will be a little more tricky to accomplish. Let me know what you meant or were wanting.


Goodluck :)

---

### Post by steve70 on 2007-12-11
In the System Bios you should be able to set to to USB.


My BIOS  has a boot priority setup for the system that has a generic HD selection (named C: Drive).

However, there's  a separate boot priority setup for hard drives, which gives me a choice on which HD should be booted first in the system's boot priority...

When I select the boot priority for the HDs I would set the USB HD to boot first, but the BIOS doesn't recognize it. When I select it, the follwing is displayed:

US_**B device (not installed)**_

Is there something else I need to pay attention to when it comes to BIOS seeing my external HD.

l

---

### Post by steve70 on 2007-12-11
HOLD ON,  :oops:

I might've found the answer at this link:

[http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives](http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives)

As soon as I get off of work, I'm going to give this a try.

---

### Post by GeorgiaBoot on 2007-12-11
So does your regular System Bios let you go

CD
USB
HD
IED
Floppy?

If yes it does, then can you boot regularly into XP or Ubuntu? 

If you can boot regularly, then all you want is it to dual boot right?

That tutorial might work, the only thing I am seeing that might go wrong is it is basing off both of them being internal drives where yours is an external. Though I think it may work.


As for the not detecting a (external Drive) in HD bios I am a little confused as my system does not have that. Does Ubuntu an XP not load properly? If they do then don't mess with it not detecting it. 

Is the not detecting effecting anything with loading the OS's?

---

### Post by steve70 on 2007-12-11
[B]So does your regular System Bios let you go

CD
USB
HD
IED
Floppy?[/B]

No, it wont let me list it like that. 

The external HD is booting fine. This, along with your reasons why you chose not to dual boot with your ext HD, will keep me at bay until I get a chance to get a little more deeper in ubuntu. 

Until then, I'm slapping the dual-boot link in the faves until I get my command-line game up. :lolflag:

---

### Post by steve70 on 2007-12-11
[B]How you have it setup now if you want ubuntu you turn on the external HD and then the computer and you got Ubuntu. If you want XP just tun the computer on without turning on the external HD.

Basically you have to do the same amount of work either way to choose your OS to boot with. If you had installed Ubuntu on an internal HD you would need dual boot.[/B]

Makes a lot of sense...I have to admit, my overthinking about linux clouded my clarity.

---

### Post by GeorgiaBoot on 2007-12-11
No worries, I thought you could not boot or were having problems with it.

---

