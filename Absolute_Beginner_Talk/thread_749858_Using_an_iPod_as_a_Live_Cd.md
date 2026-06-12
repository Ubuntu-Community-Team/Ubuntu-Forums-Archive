---
title: "Using an iPod as a Live Cd?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by MissingSix on 2008-04-08
I check a few other threads concerning this, most were quiet old or didn't come to a confirmed answer. I have one of the new iPod Videos and an iPod Nano, 60gb and 8gb respectively, is it possible to boot the LiveCD or installation CD off of it? Unfortunately my DVD burner is broken. The main reason for running the Live CD off it is to see how my step-mom feels about it since she uses this computer the most, but has complained of windows for some time. Or should I just buy a 4GB flash drive and boot it that way?

---

### Post by neurostu on 2008-04-08
I'm not exactly sure how you would go about setting up an ipod as a live cd. I installed ubuntu on a internal HDD, then I moved that HDD to a USB enclosure, now when I boot with the usb HDD plugged in it boots to that installation. So you could probably install ubuntu onto the HDD in the ipod and then just enable USB booting.

---

### Post by nhandler on 2008-04-08
You can't use it as a live cd. However, you could install Ubuntu to the iPod and then boot off of it. This would allow your step-mom to try it out without removing Windows. Another option is to install either VMWare or QEmu or another virtualization app. These will allow you to create a virtual machine. You can then install Ubuntu in the virtual machine and try it out there.

---

### Post by MissingSix on 2008-04-08
So if I installed Ubuntu on the iPod and booted off of it, it would have the similar effect of a live cd leaving no trace on the HDD? And with the installation onto the iPod + removal are there any serious risks I may encounter?

---

### Post by Soundman2 on 2008-04-08
One other option is to put the new 8.04 beta CD into her machine with Windows running.  The autorun will pop up a dialog with option to install Ubunto onto that computer within her Windows box (all on in a directory inside NTFS).

Afterwards, she can dual-boot into Linux any time and try it out.  All without reformatting or making any other permanent changes.  If she doesn't like it, boot back into Windows and remove Linux via Control Panel Add/Remove Programs.  For more information, search for "Wubi" or "ubuntu wubi".

Soundman2

---

### Post by neurostu on 2008-04-08
Yes it would be like booting off of a live cd but better as you can download and install stuff and the preferences will stick. It will be faster then a live CD as well, almost exactly like a real ubuntu install.

---

### Post by carolus on 2008-04-09
> **Soundman2 said:**
> One other option is to put the new 8.04 beta CD into her machine with Windows running.  The autorun will pop up a dialog with option to install Ubunto onto that computer within her Windows box (all on in a directory inside NTFS).

Afterwards, she can dual-boot into Linux any time and try it out.  All without reformatting or making any other permanent changes.  If she doesn't like it, boot back into Windows and remove Linux via Control Panel Add/Remove Programs.  For more information, search for "Wubi" or "ubuntu wubi".

Soundman2

Isn't one "permanent change" still required -  changing the master boot record?  Is there any way to boot from the CD instead?  In some way that does not pose any risk of making the system unbootable through ignorance, carelesness, tiredness, or haste?

---

### Post by neurostu on 2008-04-09
NO you won't need to change the MBR.

When you pc turns on the bios will check your: CDrom, HDD, USB, Floppy to see if they are bootable.  The MBR is on the HDD and tells your computer how to boot the HDD.  If you install ubuntu onto your external HDD (ipod) it will have its own MBR.

You need to open your bios when your computer starts and make sure that you have boot to USB enabled and that it checks the USB before it checks the HDD.

---

### Post by neurostu on 2008-04-09
the MBR only comes into play AFTER the bios has selected to boot to the HDD.

If you boot to USB or floppy or CDrom the mbr on your HDD never even gets examined.

---

### Post by carolus on 2008-04-09
> **neurostu said:**
> the MBR only comes into play AFTER the bios has selected to boot to the HDD.

If you boot to USB or floppy or CDrom the mbr on your HDD never even gets examined.

Neither of my computers has a BIOS that will boot to USB.  So if I want to leave my  Windows installation untouched - and I am risk averse - I will have to boot linux from a CD. ( Preferably a special CD that just boots to a USB drive and is  incapable of making any risky changes.)  Currently that leaves me with Puppy and Knoppix. 

I would very much like access to the Ubunto repositories, but I'll wait until I see a way that does not put my vendor-installed Windows at any risk.  It looks like WUBI will solve the partition problem, but the boot problem remains. I gather from this forum that there are ways to handle this too, but setting them up does not yet appear to be without risk. I assume that within a year or so there will be some simple foolproof way. What I would really like is a live USB hard drive that runs on any PC and yet lets me install anything from the repositories, with a boot CD for machines that do not allow USB bootiing or on which I do not want to monkey with the BIOS.

I can do this right now with Puppy Linux, but it lacks the extensive repositories of Ubuntu.

---

### Post by neurostu on 2008-04-09
Are you sure that your Bios doesn't support usb booting?  You might want to check to see if a new bios is available for your MOBO.  Also you might want to consider upgrading your mobo to something that does support usb booting.

---

### Post by MissingSix on 2008-04-09
How exactly do I go about installing it to my iPod so I can boot it off of it? Do I need to use Nero to 'burn' it to my iPod? Also this isn't going to do any reformatting of my iPod is it? And how easy is is to remove the Ubuntu install from it? Also for my boot option, do I set it as USB FDD or USB ZIP?

---

### Post by neurostu on 2008-04-09
I'm not exactly sure how you would go about setting up the ipod so you could install to it. I have a couple of ideas though...

You could create an image of your current installation then copy that image to your ipod HDD.

You could open up GParted and try to reformat the ipod as EXT3 and install that way...

I'll think about it and get back to you.

---

### Post by carolus on 2008-04-09
> **MissingSix said:**
> How exactly do I go about installing it to my iPod so I can boot it off of it? Do I need to use Nero to 'burn' it to my iPod? Also this isn't going to do any reformatting of my iPod is it? And how easy is is to remove the Ubuntu install from it? Also for my boot option, do I set it as USB FDD or USB ZIP?

If your ipod is new or expensive, I would be cautious about installing Ubuntu.  Nobody seems to be saying "I did this and it worked."

---

### Post by neurostu on 2008-04-09
You might want to consider just buying a new HDD (any size >20gb will work) and a usb enclosure. That will definately work, and you won't run the risk or possibly ruining your ipod.

---

### Post by dazzur on 2008-04-10
I would like to install Ubuntu 7.10 on the iPod hard drive and run the OS as the host OS on any (external) hardware (through a USB 2.0) connection. I also want to install another partition on the iPod - which I would like to encrypt and in which I would like to install VMWare virtual machines. The idea is that I could plug in the iPod, restart the computer - which starts from the USB port, runs Ubuntu and automatically runs VMWare - which itself loads a default VM. I still want the iPod OS to be the start-up OS (so I can use the iPod) when not being used to boot up another hardware device.

I found this link [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) which points out how to create a Live USB but I am very uncertain about how to change the iPod bootloader especially in combination with creating the appropriate partitions AND not destroying the iPod. 

I've also found SoulPad from IBM Research [http://en.wikipedia.org/wiki/SoulPad](http://en.wikipedia.org/wiki/SoulPad) (go to the IBM site and watch the YouTube video) which pretty much does what I want. 

Can anyone suggest to me whom I can talk to or where I can look to to read about this?

Thanks

---

### Post by neurostu on 2008-04-10
Messing with the ipod bootloader. is WAY BEYOND the scope of this forum. This is a beginners forum and as of yet I haven't seen anybody supplant the ipod MBR (let alone provide a turn key tutorial).

Try googling it or talk to the people over at ipodLinux.

---

### Post by Tomatz on 2008-04-10
**_DONT USE YOUR IPOD_**

Unless you want to run the risk of briking it.

Use wubi to install ubuntu under windows (as you would install any other windows program):

[http://wubi-installer.org/index.php](http://wubi-installer.org/index.php)

---

### Post by neurostu on 2008-04-10
Again though,

IT IS PERFECTLY POSSIBLE TO BOOT UBUNTU FROM AN EXTERNAL HDD.

I have it working on a 20gb USB HDD that I have.  

The point being made here is that ipods are special and are not just "external HDDs". You can seriously damage and ruin an ipod if you don't know what you are doing.

---

### Post by Tomatz on 2008-04-10
> **neurostu said:**
> Again though,

IT IS PERFECTLY POSSIBLE TO BOOT UBUNTU FROM AN EXTERNAL HDD.

I have it working on a 20gb USB HDD that I have.  

The point being made here is that ipods are special and are not just "external HDDs". You can seriously damage and ruin an ipod if you don't know what you are doing.

Yeah i have xubuntu running on my 2gb flash drive. It's just not worth attempting to do this on your ipod.

Wubi would be best as he is installing it on his Mothers computer. No (major) changes would need to be made to the system/disk using wubi also you don't need a cd/dvd rom ;)

---

