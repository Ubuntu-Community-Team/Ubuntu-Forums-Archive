---
title: "Multiboot over existing Windows XP"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by brn on 2006-06-30
**Here's my problem:**  I have a second-hand laptop with XP installed.  I don't want to lose XP but wish to install both Ubuntu and DOS.  I cannot reinstall XP, I don't have any original installation disks.
    Searching the web I find examples of multiboot installations where the user has all systems available for reinstallation.  This is not an option for me.  Thus far, everything I have been able to learn about multiboot programs like GRUB is that they must control the bottom 512 byte segment of the hard drive.  I have heard and seen some evidence that when installed "at the factory", *Windows* jealously guards this sector and any effort to alter it will render XP unavailable.  Is this true?
    I have 'Breezy Badger' 5.10 available.  'Dapper Drake' 6.x is on order and should be here in a few weeks.  

QUESTIONS:  
                   ...Should I  wait for Dapper Drake or try to install Breezy now?
                   ...Is it true that any boot program needs that bottom sector?
                   ...If so, can this be wrested away from XP without losing it?
                   ...How?

Thanks in advance for any help/guidance/advice/sympathy/etc...

---

### Post by Herman on 2006-06-30
Greeting, brn
> I don't want to lose XP but wish to install both Ubuntu and DOS. I cannot reinstall XP, I don't have any original installation disks.If anyone doesn't have their Windows XP install disk they will be taking a risk when they do any partitioning work and install any new operating system.
However, you should know that you will eventually lose your Windows XP after a while anyway, because it will get loaded with spyware and malware and need to be re-installed to get it working properly.> Should I  wait for Dapper Drake or try to install Breezy now?I think install Breezy now because the sooner you do, the sooner you can start using Ubuntu for all your e-mail and internet work and keep Windows off the internet altogether. If you do that you will find that all spyware and adware scans in Windows will soon begin to come up clean, except for adware and spyware that's already there but it takes time for the anti-spy and anti-malware people to recognise and learn how program thier apps to remove. (They never tell you "sorry, but we goofed, there's some stuff here we've never seen before, we won't be able to learn how to remove it for six months." Windows is just not safe on the internet.

However, I repeat, you will be taking a risk to install Ubuntu without a Windows install disk. You shouls also back up your important files fisrt too.
> Is it true that any boot program needs that bottom sector?The first sector of your hard disk is just another sector that can be copied, written to and over-written just like any other sector on our hard disks. 
If you are worried about it, here's how to make a backup copy of it and restore it again using the new Dapper 'Desktop' Live/install CD, [*click here*]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").
If you use the new Dapper 'Alternate install CD, there are options to allow you to choose between Linux bootloaders and specify where you want the bootloader installed other than to MBR. You can for example install GRUB to a floppy disk, or install LILO or GRUB to the first sector of your Ubuntu partition. If you do that you will need to have a GAG Boot Manager CD or floppy disk ready before you begin your install to re-boot with during the install. For a how-to on GAG Boot Manager,[* click here.*]("http://users.bigpond.net.au/hermanzone/p12.htm")
For how-tos for using the new Dapper Drake 'Alternate' install CD, (which, by the way, will be very similar, (but not exactly the same) as your 'Breezy' installer, click on each of the three signature links right at the bottom of my post here, and choose the one that suits you.
> If so, can this be wrested away from XP without losing it? > How? Most people just install GRUB to MBR, GRUB will almost always boot Windows and any other system for you just fine. There are a small but vocal minority who have a little trouble at first, but mostly it's just because they either have special hardware, or/or just haven't had time to learn how to operate GRUB properly. GRUB can do almost anything when we know how. The easiest way to install Ubuntu is to use the 'Desktop' install/live CD if you just want GRUB on your MBR (that's the best) and aysui's website is the one I recommend for that [click here]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")
.
For the 'Alternate' install CD, here's my homepage, [*click here*]("http://users.bigpond.net.au/hermanzone/") , for the illustrated dual boot site that explains about every Ubuntu dual boot option imaginable, and more is still being added. Feel free to peruse that at your leisure and see if there is anything more there that interests you. Anything you want to ask about, please let me know and with a little of your help/guidance/advice/sympathy/etc... I'll explain and/or edit the website to make it clearer or fix any mistakes. All the best with it, Regards, Herman :)

---

### Post by Apple 101 on 2006-07-01
[QUOTE=Herman]However, you should know that you will eventually lose your Windows XP after a while anyway, because it will get loaded with spyware and malware and need to be re-installed to get it working properly.[/QUOTE]That's a negative view... if you keep it maintained everything is fine...

Anyway, if you don't have a Windows install disc, you should backup important files.  Another method, get a partitioning program like Partition Magic and resize your Windows drive that way.  That way the data will not be lost at all.  Then you can install Ubuntu into that free space.

---

### Post by brn on 2006-07-01
Herman and Apple 101:  Thank you.  I will wait for Dapper before attempting the surgery.  I still haven't found the exact recipe I want.  I share Herman's enthusiasm for Ubuntu/Linux but reality compels me to retain Win-XP if I can.  

My progress to date:  Using the Ubuntu 5.10 *install *disk I successfully shrank Window's NTFS partition to 6 GB, More than enough.  It survived but the 5.10 partitioner did not offer the options I think I need.  FDISK (baffling though it is) would allow this but is not an available option.  I will keep trying.

Apple 101:  Interesting that you mention "Partition Magic".  I happen to have it.  I spent $60 (US) in 1999, reading the package that said "Needs DOS".  I didn't know at the time that it needed Windows too.  Shame on me.  I wonder if this now ancient relic will perform today.  Stay tuned, and thanks again.

---

