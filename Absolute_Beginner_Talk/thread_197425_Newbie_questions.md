---
title: "Newbie questions"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-06-15
Hiya,

  

   Its been a few years since I tried Linux and I am ready to give it a go. I do have a few questions.
I am installing a 18 gig hard drive to the IDE port for my linux install. My windows install is on a SATA drive.
Do I need to worry about Ubuntu hosing my boot sector or boot.ini?? 

Also as always I happen to have the same hardware that is giving a lot of folks a headache. I have a MSI mobo with an ATI chipset and an ATI PCI express x800xl and an LCD monitor. I am planning on installing the 32 bit version because being a newb I dont need additional hassles. 
I have tried running Ubuntu Live and was not able to get the graphic application started. ( I dont remember the exact error ) 
Any advice on this setup would be appreciated. 

Peace
Rich

---

### Post by catlett on 2006-06-15
I'll answer the install/mbr part. If you want to be safe, install grub to a floppy. That way your mbr isn't touched. The only thing you have to make sure of is to use THE ALTERNATE INSTALL CD. It is available at the same download page. The live cd installer has very few options. It  does what it wants pretty much. It  gives out defaults and your stuck with them.
Anyways, during install,  when it asks to install grub to the mbr say no. The next screen you wil be able to enter where you want to install grub. Just put in the location, in your case the floppy. You would then enter /dev/fd0 or the grub specific fd0 (it gives you the options on the page so you don't have to remember any of this)
When the install is done grub is on the floppy. When you want to boot to ubuntu put the floppy in. If you want windows just leave the floppy out and you will have your regular boot process.

As far as ATI and such, good luck. There have been a ton of posts lately and it doesn't seem like people are having luck.

---

### Post by muep on 2006-06-15
Ubuntu by default installs the boot loader into MBR, but usually it works just fine, you can select the operating system to boot into with a menu.

I think boot.ini is in your 'C' partition, which Ubuntu doesn't touch.

I suggest that you first try the livecd. When booted it is quite similar to a fresh install of Ubuntu. You can first teach yourself to fix any problems within it, after that it is very easy to repair the installed one. If you mess something up in the livecd environment, just reboot :)

With luck, most of your hardware may even work out of the box.

---

### Post by -::Bas::- on 2006-06-23
Your graphical card (x800xl) will probably give you some trouble.
Follow Louis' tips: [http://www.ubuntuforums.org/showthread.php?t=200559](http://www.ubuntuforums.org/showthread.php?t=200559)

Good luck.

---

