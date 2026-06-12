---
title: "Booting to Grub2 Command Line"
date: 2015-12-13
forum: Apple Hardware Users
---

### Post by tom217 on 2015-12-13
I'm super new to Ubuntu, hence my choice of forum (hopefully the right one), so far, what I've done is I've installed Ubuntu 14.04 on an external hard drive, as there wasn't space on my internal hard drive. My computer runs OSX, the most recent version of Mavericks.

So the deal is, when I start up without the external hard drive (containing Ubuntu) connected, it boots straight to the Grub2 command line. From there I can just use 'exit' and it will boot into osx, or alternately, while starting up I can hold option and then select to boot from the internal hard drive, bypassing Grub2.
When I start up with the external hard drive connected, I get a Grub2 menu similar to all the others I've seen, with a choice of operation systems to load.
Its probably also worth mentioning that my internal drive only has OSX installed on it. Bearing that in mind, I was wondering about this.

Does Grub2 boot directly to command line as there is only one OS to choose from?

That seems intuitively wrong to me, but perhaps I am mistaken, and it is the conclusion that I arrived at.

I was also wondering what it would take for me to boot my Ubuntu drive on another machine. I'm assuming that machine would have to run Grub2, but is it possible to have Grub2 run from the same hard drive, so that its easily portable?
If not, is it possible to run a live usb grub, and boot from that?

Thanks a bunch in advance, please let me know if I need to clarify anything, add more information to something, or perhaps split these two questions into different posts.

P.S. I have a live Ubuntu (14.04) Usb, I wasn't sure if it was necessary to add that information, or where to do it, hence it ending up here.

---

### Post by yancek on 2015-12-13
> Does Grub2 boot directly to command line as there is only one OS to choose from?


No.  If there is only one OS it will not show a boot menu.  You have two operating systems so you should see a menu.

> 
I was also wondering what it would take for me to boot my Ubuntu drive on another machine.

Install Grub2 bootloader to the master boot record of the drive, attach it  to another computer, enter the BIOS of the other computer and select that drive as the first boot priority in the BIOS.  This usually works if you have not installed any proprietary drivers to the system.  And no, the second machine does not need Grub.  

I've never used Apple products so I don't know what you would expect.  The method you are using may be the only way or the best way.  I'd suggest you wait for someone who has some familiarity with a Mac to respond.  You might try running boot repair and posting a link to the output after selecting the Create BootInfo Summary option.  Do not try to do any repair.  See the link below.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2015-12-13
> when I start up without the external hard drive (containing Ubuntu) connected, it boots straight to the Grub2 command line.
> When I start up with the external hard drive connected, I get a Grub2  menu similar to all the others I've seen, with a choice of operation  systems to load.

That indicates that Grub has been installed on to the OSX drive. The Ubuntu installer will default to installing Grub on to the first hard disk (called sda). And then when we switch on the machine and the motherboard looks to the first hard drive for a boot loader it will find Grub which will then look to the Ubuntu partition to find its configuration file. Which in your case is on the external drive. 

This is why you are getting a Grub rescue prompt when the external drive is disconnected. Grub cannot find its configuration file. And why you can select either Ubuntu or OSX when the external drive is connected. Grub is able to find its configuration file and then draw its boot menu.

a) You need install Grub onto the external drive (sdb). Boot Repair will take care of that for you.
b) You need to install an OSX boot loader to the internal hard drive. I do not know if Boot Repair can do that.

Then you can use the BIOS/UEFI to select which of the 2 drives to load from. The internal drive will load into OSX. The external drive will give you a choice of OSX & Ubuntu.

To avoid this situation some of us advise disconnecting the internal drive when installing Ubuntu.

Regards.

---

### Post by tom217 on 2015-12-14
Is there any reason why I shouldn't just install Grub2 on both drives? Also, I have used boot repair to (I think) install Grub2 on the external drive, but it didn't repair the internal drive, and I didn't have the nerve or expertise to do anything further with it, so I left it.

Also, since I (think) Grub2 is installed on the external drive, I guess the step I was missing was going into the Bios and doing it from there, I'll have to read up on that, any recommendations on where I might start reading?

Also, thanks again, community support, particularly as speedy as this, is imo the most valuable thing you can get. So thanks, I really appreciate it

---

### Post by yancek on 2015-12-14
The boot repair I suggested in my last post will give a lot of information and if you post a link here, someone will be able to tell you where Grub is installed.  You can save the file on your computer to review.  The boot repair would also tell whether you have UEFI or not.

---

### Post by oldfred on 2015-12-14
Is this a Mac, I can move you to the Apple sub-forum where those who know Mac may be able to help.

If not a Mac we cannot help. 
 Ubuntu Forums Code of Conduct
[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

Did you install in UEFI boot mode? On gpt partitioned drive?
External drives only boot from /EFI/Boot/bootx64.efi, so that has to be created.

---

### Post by tom217 on 2015-12-14
I took a picture of the respoonse that boot repair gave me, in case it became useful later, and I have attached it as such, I apologise for not getting the entire message, I assumed the url would be the only part that was really important, as the rest of it would be generic. 
Heres the url so you don't have to type it out: [http://paste.ubuntu.com/13996961/](http://paste.ubuntu.com/13996961/)

I had a brief look over it and I'm confused by the first part of it, I don't understand why "[COLOR=#000000]Windows 2000/XP/2003 is installed in the MBR of /dev/sda.[/COLOR]" But I guess it is.

As for this being a mac:
Yes, my computer is a mac, my apologise for failing to post this in the correct part of the forum.

As for the other stuff you asked, I can't tell you, you'd have to tell me how to find out, as frankly I have no idea, a lot of this stuff is new to me.

Thanks again guys.

---

### Post by tom217 on 2015-12-14
Oops I didn't see that, I'll check out that link and then add whatever details I find out.
As for closing this forum, will do.

---

### Post by tom217 on 2015-12-14
I'm still not exactly sure, that link seemed to focus mostly on windows, so I read through some the UEFI definition link that was there, and skim read through some other parts of the page.

I used a live usb to install Ubuntu onto my external hard drive, I just used the default install, so maybe thats useful for you to know. Also, the Arch Linux page suggested a method for finding out the EFI firmware in your mac, and gave two possible outcomes for using that command in terminal. I tried it but terminal gave me a response suggesting that the command was improperly set out, and I'm not confident enough to try and re-organize it, so I just left it.

I checked the external drive using disk utility, and it is GPT partitioned. 
Hope that helps

---

### Post by oldfred on 2015-12-14
Moved to Apple sub-forum.

Do not now Mac, but grub wants to install to the ESP - efi system partition on sda.
And from UEFI it normally boots from sda, but will boot from other drives, but sometimes only /EFI/Boot/bootx64.efi. With external drives, you need to copy grubx64.efi into /EFI/Boot/ and rename to bootx64.efi  in the ESP. You also must copy all of /EFI/ubuntu to external drive's ESP as /EFI/ubuntu. The renamed grub expects to find files in default location of /EFI/ubuntu.

It looks like your sdd is a hybrid drive. That should be avoided if possible. But to dual boot Windows in BIOS mode you have to have the hybrid as UEFI uses gpt, but Windows in BIOS boot only boots from MBR(msdos) partitioned drive. If you have hybrid you must keep them in sync. 

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

