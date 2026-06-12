---
title: "USB booting Macbook"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by skiwithpete on 2008-10-30
Hi,

I've put Ubuntu on a USB Flash Drive and use it to bring around with me so I can boot a friendly OS at my friends' places.  

One thing I'm wondering is if I can boot it on a Macbook (I think I have the 4,1 - white 13").

Is there a key to press to boot from USB?

If not, is there a Linux LiveCD that I could pop in the drive of the Mac, that will load the USB drivers to then boot my Flash drive from there?  

Cheers,

P

---

### Post by garyedwardjohnston on 2008-10-30
You need to change the BIOS settings to boot from USB first.

---

### Post by skiwithpete on 2008-10-30
How?

Does the MacBook even have a Bios?

---

### Post by cyberdork33 on 2008-10-30
> **skiwithpete said:**
> How?

Does the MacBook even have a Bios?
no it doesn't

You can try holding Alt/Option key on bootup and it will give you bootable items to choose from.

Booting from USB seems not to work on Intel Macs though so unfortunately it probably doesn't matter. If you check the FAQ here at the top of the forum, it has an extensive thread about this including information about make a bootable cd that can load the linux kernel and run Ubuntu from a usb device after that.

---

### Post by skiwithpete on 2008-10-30
Found it here,

[http://ubuntuforums.org/showthread.php?t=510030&page=11](http://ubuntuforums.org/showthread.php?t=510030&page=11)

But this link [http://www.mediafire.com/?diid1acmdd2](http://www.mediafire.com/?diid1acmdd2) to the bootCD is dead.

Does anyone have an updated link to the bootCD?

Cheers,

P

---

### Post by cyberdork33 on 2008-10-30
I doubt anyone has updated it. You will have to read the information on how it was made and attempt to do that yourself. You basically have to get a kernel and bootloader on the cd to load from the mac, and it in turn, loads Ubuntu from the external storage device.

---

### Post by skiwithpete on 2008-10-30
Way too much of a newb to accomplish that...

P

---

### Post by _Poincare on 2008-11-09
I am having the same problem. I installed 8.10 Intrepid onto an external USB, now when I boot I hold down OPTION and select the HDD for Ubuntu but then it does not boot. Why is this so crappy? PCs can boot off USBs no problem. How do us Mac users boot from USB??

---

### Post by cyberdork33 on 2008-11-09
> **_Poincare said:**
> I am having the same problem. I installed 8.10 Intrepid onto an external USB, now when I boot I hold down OPTION and select the HDD for Ubuntu but then it does not boot. Why is this so crappy? PCs can boot off USBs no problem. How do us Mac users boot from USB??
you don't... not yet anyway.

---

### Post by kriztean on 2009-12-25
I CAN boot Ubuntu Remix 9.10 from USB on my Macbook.
 Basically you need a CD to boot the USB becasue the Macbook can't boot from the USB from itself.
 
 To start you'll need:
 
 3 CD's
 1 USB key
 a Macbook
 Ubuntu 9.10 ISO.
 Ubuntu 8.10 ISO. Yes you need this one as well. 
 
 Steps

 1. From OSX -Get Ubuntu 9.10 ISO and Burned into one of the CDs. [//Link>>]("https://help.ubuntu.com/community/BurningIsoHowto")
 2. From OSX -Get Ubuntu 8.10 ISO and Burned into one of the CDs. [//Link>>]("https://help.ubuntu.com/community/BurningIsoHowto")
 3. Restart the MAcbook with the Ubuntu 8.10 CD and boot Ubuntu from it.
 4. From UBUNTU 8.10 - Copy the file **stage2_eltorito** to your email or website for later access. The file is in** /usr/lib/grub/i386-pc/stage2_eltorito**
 5. Restart and insert the CD Ubuntu 9.10
 6. From UBUNTU 9.10 - Plug the USB-key and Create the bootable USB. [//Link>>]("https://help.ubuntu.com/community/Installation/FromUSBStick")
 4. From UBUNTU 9.10 - Create the CD to Boot the USB. Procedure is in[ //Link>>]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/"), however there is a couple of things that didn't work for me from this procedure. Below, **[COLOR=Red]in red[/COLOR]**, you can see the changes I made.
 
 /......
iii. Copy **stage2_eltorito **from whereever you stored it before to **ubcd/boot/grub**[COLOR=Red]
[/COLOR]iv. Type **gedit ubcd/boot/grub/menu.lst**
 v. Add the following information to your menu.lst file and save it to ubcd/boot/grub
  [INDENT]title Run Ubuntu **[COLOR=Red]9.10[/COLOR]** from USB DISK
root (cd)
kernel /boot/vmlinuz file=/cdrom/preseed/**[COLOR=Red]netbook-remix[/COLOR]**.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/initrd.gz
boot
   [LEFT]
  [/LEFT]
 [/INDENT]  ........../
5. From UBUNTU 9.10  -Copy the ISO file to Internet or another usb key so you can burned later.
 6. From OSX - Burn the **usbcd.iso** to a CD.
 
 7. Restart with both the bootable CD and the USB with ubuntu 9.10.

The changes I made from the procedures in other websites are becuase UBUNTU 9.10 doesn't not include the file stage2_eltorito. So I used a Ubuntu 8.10, which does include it, and copied from there. However you can copy that file from anyother Machine Runnin Linux but I dont hav another.

BTW, I got a little dissapointed, I was expecting the remix version to be agile but its a pain to switch between windows :(

---

