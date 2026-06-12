---
title: "Ubuntu on Sata HDD - bual boot?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Peerob on 2007-08-01
This is the first time I have used Linux and although I can follow instructions I am not  a real expert by any means.

I have an MSI motherboard with 2 x 120GB HDD on sata1 & sata2. I have XP on the first HDD which works fine etc. I downloaded ubuntu and created the bootable cd (dvd actually). After reformatting sata2 I went through all the installation and checking procedures along the way to install the OS, everything was fine, ubuntu installed correctly on sata2 (the clean newly reformatted drive)&#8211; too good to be true? &#8211; Yes! I rebooted this time choosing sata2 (ubuntu) expecting it to boot as the boot device. It just hangs on black screen??  I thought it would be a piece of cake.

---

### Post by felicity on 2007-08-01
You say you rebooted and "chose sata 2", does that mean you chose that drive from the BIOS screen? Or did you choose the Ubuntu (sata 2) from the GRUB boot menu that Ubuntu installed?

---

### Post by notwen on 2007-08-01
Are you still using Windows MBR or are you using Ubuntu's GRUB for your boot loader?  During your Ubuntu installation did you install GRUB?

---

### Post by Peerob on 2007-08-01
i did not use grub - i just selected the drive from f11 on boot up to select the boot drive. I was hoping to be able to switch between HDDs as and when I need to. Perhaps it is not as simple as this and i need to read more.

---

### Post by NDPeter on 2007-08-01
I'm planning on doing a similar install this weekend once I get my new powersupply and a fresh, new HD tomorrow.  Before starting a new thread I thought I'd ask here and hopefully not hijack it.

I'll be installing on a second (third physical)  sata drive from XP and think I have that figured out...sda0, sda1 etc.  I've read lots on the Windows MBR and GRUB issues but have had trouble sorting the info out from older versions of Ubuntu (think I've seen some as old as 5.x) vs the latest (FF).

Is it right to imply from a few posts back (sorry I haven't quoted) that you can use the MBR to dual boot?  

A confusion from reading all the different notes from over the years...does the current installer ask you whether or not to install the GRUB loader?  Does it ask you where?  i.e. Does the latest installer somehow workaround the previous problems by recognizing the other OS, and not writing over things?

And lastly, if I install it on the 3rd SATA with the ubuntu install, then I will have to change the BIOS settings to boot that drive before the other, right?

Thanks, hopefully this prevents yet another dual boot thread from being started...there are some good tutorials out there but none deals so well with the dual boot from two physical drives and a good work around the MBR problem if XP is pre-exisiting and not a new install.

Can't wait to get this up and try it out.  Hopefully I can switch nearly completely over except for when I need XP for some chemistry apps.

---

### Post by sigge on 2007-08-01
> **Peerob said:**
> i did not use grub - i just selected the drive from f11 on boot up to select the boot drive. I was hoping to be able to switch between HDDs as and when I need to. Perhaps it is not as simple as this and i need to read more.

You do need to use a bootloader of some kind. Changing bootdrive does not help, as there is no bootloader on your second drive. I'm not shure about windows bootloader, but I hear it can sense other OS, and give you a menu to choose Ubuntu at boot time.

In the bios, change bootdrive back to your windows HDD, and see what happens.
If it doesn't fix it, you need to access a bootloader like grub. report back when you have tried, and we'll help you along after you tried the stuff I mention above. ;)

---

### Post by sigge on 2007-08-01
> **NDPeter said:**
> 
Is it right to imply from a few posts back (sorry I haven't quoted) that you can use the MBR to dual boot?  

A confusion from reading all the different notes from over the years...does the current installer ask you whether or not to install the GRUB loader?  Does it ask you where?  i.e. Does the latest installer somehow workaround the previous problems by recognizing the other OS, and not writing over things?

And lastly, if I install it on the 3rd SATA with the ubuntu install, then I will have to change the BIOS settings to boot that drive before the other, right?
.

The installer ask whether to install grub. Like I said in my previous reply to the post that started this thread, Windows apparently is able to sense other OS. The windows bootloader writes itself to the MBR (MasterBootRecord) which is a physical space on your primary (1st) HDD.
Grub give a choice where to install, and may also be installed in the MBR. It will sense your windows OS, and give you a menu at boottime, so you may choose wich OS to load.

Hope that clears things up... :D

---

### Post by NDPeter on 2007-08-01
> **sigge said:**
> The installer ask whether to install grub. Like I said in my previous reply to the post that started this thread, Windows apparently is able to sense other OS. The windows bootloader writes itself to the MBR (MasterBootRecord) which is a physical space on your primary (1st) HDD.
Grub give a choice where to install, and may also be installed in the MBR. It will sense your windows OS, and give you a menu at boottime, so you may choose wich OS to load.

Hope that clears things up... :D

I think it does.  What remains is for me to just try it finally.  I've been reading around for 2+ weeks now and i need to leave the hesitation behind and make the leap.  I'll deal with any problems getting back into windows if and when they arise.  I'll have a two or three weeks to get things back to normal before classes begin again.

---

### Post by sigge on 2007-08-01
Good luck, friend!

Hope it turns out right. And don't worry. It usually does :)
Just pop the cd in, boot and go ahead. And have some :popcorn: handy.

---

### Post by MQMike on 2007-08-01
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
Dual booting options and methods

In case it’s a video issue,
How to get started with no GUI
[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

---

### Post by Peerob on 2007-08-02
I tried to install again and saw that during the installation grub was installed. After the first reboor ubuntu went through various checks all of which appeared to be OK! Then it rebooted again and after f11 to choose the boot disc ubuntu successfully booted! 

Now I have XP on HDD1 and Ubuntu on HDD2 - not too keen on the screen resolution but once I start getting to grips wit:D it all it might look better, any suggestions welcome!

---

### Post by MQMike on 2007-08-02
I'm not sure where exactly we are now, but here's the theory:

Let's say your PC is Off.
Turn it On.
After the POST, GRUB should present you with a boot menu, showing you Windows and Ubuntu.
You highlight one of those, press Enter, and GRUB should boot you into the OS you chose.
No F11 key.

---

### Post by Peerob on 2007-08-03
This is where I am at:

I started again and sat watching ubuntu load. grub loaded as part of the installation.
On boot up ubuntu went through various checks and then rebooted.
I am not presented with a choice to select XP or Linux, instead I press f11 to select which drive I am booting from and all works well.

I have Linux and XP on different physicall drives as stated in my first post. All is well that ends well!

now to start exploring!:biggrin:

---

### Post by MQMike on 2007-08-03
I see.  Not an uncommon setup, where you can select your boot hard drive using an F-key.
Good!   Glad you have you system working again (and Ubuntu up and running!), and many thanks for your feedback.

---

### Post by NDPeter on 2007-08-03
Mike and Sigge...

Thanks for the notes and reassurances.  I'm up and running and it all went perfectly once I set up the partitions manually.  Still not sure all of them actually formatted as they show RAW in windows...but I can work that out.  

THANKS AGAIN!  :):):)

---

### Post by MQMike on 2007-08-04
NDPeter -- Thanks for your feedback and glad you got it fixed! -- Mike

---

