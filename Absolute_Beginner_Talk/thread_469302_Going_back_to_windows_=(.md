---
title: "Going back to windows =("
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by terrera on 2007-06-09
I tried installing Ubuntu in my mom`s laptop and unfortunately she did not get used to it. So, in order to recover my disk space, I want to permanently remove Ubuntu.

I was going to user partition maginc to delete the Ext3 partitions and put them back as NTFS until i remembered the boot loader. If i delete ubuntu, grub will also be deleted and the PC wont boot straight to windows. Is there a way i can delete Ubuntu and make the computer load directlhy to windows without having to reinstall windows?

thanx!

---

### Post by Jimmyfj on 2007-06-09
As far as my knowledge goes there is no way around this you'd have to reinstall Windows in order to boot straight into Windows again.

---

### Post by Rocket2DMn on 2007-06-09
I also don't know of a way to do that, but if you want to make the reinstall easy, you should just be able to pop in the Windows disk, delete all partitions from the Setup, and start fresh

---

### Post by LostArt on 2007-06-09
Couldn't you try booting from the windows disk and install the neccessary files, I think you can do that, but I'm not sure

---

### Post by Bohlio on 2007-06-09
I think you just remove ubuntu, Then somehow get into a MSDOS command line and type in "fixmbr". I think thats how you do it. Look it up in the forums, Im sure its been done before.

---

### Post by sethdotcom on 2007-06-09
Get hirens boot cd

and load up just plain dos

and type fdisk/mbr


it will reload the bootloader on the active partition

---

### Post by stalkingwolf on 2007-06-09
If you are using Xp I believe you can boot to your XP disk and under the Other tasks(i think that is what it is) heading there is an option to " repair registry", this will return your registry back to OEM then you should be able to boot the live cd and use gparted to remove or reformat  the ext3 partition to ntfs.

---

### Post by jamespi on 2007-06-09
couldnt he use the windows install cd to boot into a recovery console and use a command to reinstall the windows MBR?

i think it's "fixmbr" or something

you'd have to google the MS knowledgebase article for it, but just my two cents.....

---

### Post by bone43 on 2007-06-09
[http://ubuntuforums.org/showthread.php?t=6817&page=2](http://ubuntuforums.org/showthread.php?t=6817&page=2)

Try that :D

---

### Post by terrera on 2007-06-09
Thanks for your answers.

I decided to do a bizzare thing. I created a 100mb FAT32 partition and installed BootMagic (it wont install in NTFS). Then tested if it worked and it did. Then, back in windows, now using PartitonMagic, i deleted the Ext3 partitions, moved the FAT32 partition to the end of the hard drive and reformated what was left back to NTFS.

Quite a hassle to do, but at least it worked.

---

### Post by jackiecanev2 on 2007-06-09
i'm not positive about this, but if you use the recovery feature, won't windows automatically reinstall its own bootloader?

then just use gparted live to delete and extend your partitions?

---

### Post by acutu on 2007-06-10
Don't just go back to Windows. If you try Xandros I think you will experience what you are looking for. Ubuntu will get there too in time. Windows Vista is going in the wrong directions in my opinion and XP will not support ay a lot of new hardware, and if you reinstall XP at any time you seriously risk wiping all other operating systems including Vista. I strongly recommend you do not waste a lot of valuable time with Windows where you have to manually install so many programs and jump through so many <s>hoops</s> chains. :KS

---

### Post by jamespi on 2007-06-13
why do you think windows xp wont support new hardware?

windows 2000 still supports modern hardware and it's been end-of-lifed for a year or two now, and was superceded by XP 6 years ago.

just curious...

---

### Post by Xen777 on 2007-06-13
I know I'm late, but why complicate things, just boot Windows and run fdisd /mbr, and then delete the ext3 and swap partitions.

About Vista I agree it sux, and in my opinion it's just an oversized media player. ;)

Jaksemaz!

---

### Post by Atomic Dog on 2007-06-13
I think his point is that some manufacturers will not offer XP drivers for their hardware and just support Vista.  That day is a long way off, but will be there eventually.

Unlike many people here I have no issues with Windows itself, XP is a rock on our workstations, and Vista...well it's too soon to tell.  The security model sux to say the least, but it works and I can respect that.

One of the most uber-geeks I ever met is a linux wiz, yet has XP on his laptop.  When I asked him why (as I have Ubuntu on mine) he said that he just needed a laptop that worked, and windows gave him less BS to deal with.  Hey that's cool.  

...and I believe the fixmbr command mentioned here, and linked to, will do the trick for you painlessly and easily.

---

