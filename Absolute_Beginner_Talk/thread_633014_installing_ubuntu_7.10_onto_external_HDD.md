---
title: "installing ubuntu 7.10 onto external HDD"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-06
ok, i have finally found out a way to install ubuntu 7.10 onto my external drive, AND be able to move the drive between different computers to use ubuntu on them.
:popcorn:
ok first you have to have the [live ubuntu] CD you made from the ubuntu ISO.
>boot up into ubuntu from the live CD
>open the provided installer that will be on the ubuntu desktop
>go thru and select [guided] use entire drive] and select your external drive
>go thru the steps, inserting your info untill you get to the step where you see the [advanced button] and click advanced, then where it says (hd0,0) change the first zero with your external drives number (mine was 1 so i changed it to (hd1,0)
>finish installation and reboot
>keep your external drive plugged in and make sure your bios has your external drive as booted before anything else (except CD, i like to keep my order boot CD then boot USB HDD)
>save bios changes and reboot
>now when our computer boots you will see the option to choose either ubuntu or windows, if you let it sit you get error 17 (this is normal and needed to be done for you to be able to boot into windows without your external plugged in)
>highlite UBUNTU and press [E] a new window will popup and press [E] again.
>now edit the (hdX,0) to hd0,0 (so i would edit (hd1,0) to (hd0,0)
[CENTER]---note---you will have to do this^ everytime you boot. this is so you can boot your pc without always needing your external plugged in---note---[/CENTER]

>after editing press [Enter] and you should be back to the last menu you were just at. now press [B] and Ubuntu should boot!

--------->you should never have to change your bios after you change it once<--------

I Hope This Helps!!!!!!

~Nate:popcorn:

---

### Post by candtalan on 2007-12-10
Useful information.

May I add that if in future you use the computer without the external drive connected, then I guess that since the mbr points to the linux partition on the external drive, then it will not boot correctly without the external drive connected. I think to avoid this the boot directory could be installed into a small extra directory on the original internal drive?

---

### Post by go_dragons on 2007-12-26
You shouldnt need to edit your grub boot instruction every time you boot ubuntu.

/boot/grub/menu.lst is the file grub looks at to determine where your operating systems are, how to boot them, etc. Scroll down to the bottom of this file and you will see a section that has all of the different boot options for all of the operating systems installed on your compuer.

There may be multiple ubuntu sections depending on how many times you have updated your kernel, if you have 'recovery' options, etc. You can change your root partition information from there and you wont have to manually change the information every time you boot.

short answer:
sudo gedit /boot/grub/menu.lst
change your hd(1,0)'s  to hd(0,0)

---

### Post by TGFF on 2007-12-27
I just tried installing Fiesty 7.04 on a new external HDD with Windows XP on the internal but now for some reason I cant load windows at all. This is all very new to me and I have no idea how to program or anything of the sort.  
   I just want Ubuntu on my external and Windows on my internal so I can learn while still able to use all of my school programs. Any suggestions?

---

### Post by candtalan on 2007-12-28
> **TGFF said:**
> I just tried installing Fiesty 7.04 on a new external HDD with Windows XP on the internal but now for some reason I cant load windows at all. This is all very new to me and I have no idea how to program or anything of the sort.  
   I just want Ubuntu on my external and Windows on my internal so I can learn while still able to use all of my school programs. Any suggestions?
Are you using the machine all the time with the external drive connected? The ubuntu install onto a second drive, at least the default install, uses a boot loader which is located in the ubuntu installed (drive or partition) area. If you want to remove the external drive, then a slightly more sophisticated install method can be used, with the ubuntu 'boot' directory located into a small new partition on the internal drive, so it is always there to properly manage things when windows is needed, and the external drive is not.

hth

---

### Post by Chayak on 2007-12-28
It's fairly easy with the alternate install CD.  You can simply select the drive to install to.  You can even encrypt your hard drive and set it to boot off a usb key.

You can install everything to an external drive and as long as your computer supports usb booting you can go into the bios and set usb as the top boot choice and simply unplug the drive and boot when you want to use windows or boot it with the drive plugged in to boot into linux.  It's not hard.

---

### Post by GeorgiaBoot on 2007-12-28
I would suggest you follow these simple instructions I wrote from info on the web I have found. I have found if you don't disconnect your internal drives sometimes problems happen.



Things you will need:

    * Ubuntu Linux (Free) [http://www.ubuntu.com/](http://www.ubuntu.com/)
    * A External Hard Drive
    * A Windows Machine, should work on Vista as well
    * A Little Time and Patience

Prep work:

    * 1. Download the LiveCD iso and burn to CD. Or have Ubuntu Ship you one for (Free).
    * 2. Prep your USB drive by deleting all partitions, no matter what kind they are.
    * 3. Disconnect your internal hard drive(s). This is Key
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

### Post by gyterpena on 2007-12-28
I remember my doing it this way and had some trouble when booting on different computers due to different hardware. At the end I settled for [this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") solution and it works fine.

---

