---
title: "Getting Rid of GRUB?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Ðrehmini on 2005-12-16
I don't have my Windows XP disc.
But I was wondering If there was anyway I could get rid of GRUB and reinstall the old MBR without the disc.

I use Windows XP Home.

---

### Post by Stereotypical Rage on 2005-12-16
Can you boot to Windows Recovery Console or no? If so: fixmbr

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Stereotypical Rage]Can you boot to Windows Recovery Console or no? If so: fixmbr

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)[/QUOTE]

Nope... Unfortunatelly I've been searching for 3 hrs on how to rewrite GRUB with the XP MBR

I cannot access the Recovery Console But I was wondering...

My computer was made By DELL and their BIOS has a recovery selection.

I've read about fdisk but I'm unsure on how to actually make a Dos Bootable CD. (my floppy is on the fritz.)

Thanks for the reply.

EDIT: I was reading about this [http://www.nu2.nu/bootcd/#cdromsi](http://www.nu2.nu/bootcd/#cdromsi) -  Any ideas?

---

### Post by Evil Whisper on 2005-12-16
*Deleted*

---

### Post by Stereotypical Rage on 2005-12-16
Borrow a XP CD from a friend or download a copy of it. Since you already own it and it is legal to do so as long as it's for backup purposes. There's no way to make a DOS boot disk to my knowledge in XP, since DOS is virtual. Chances are you're using NTFS as a file system and if I recall, a DOS bootdisk won't read NTFS.

---

### Post by Emerzen on 2005-12-16
I don't know how you can fixmbr without the disk.  However, if it's a relatively new Dell you have, then you do not want to choose the recovery function until you've fixed the MBR.  New Dell's ship w/ a Symantec (Norton Ghost) image of the original hard drive...it will reinstall your windows back to the day you bought it but that will not include reinstalling XPs boot loader.

---

### Post by Ðrehmini on 2005-12-16
Alrite I'll download a ISO of Windows XP.

Is there any chance I can Overwrite GRUB with XPMBR using the ubuntu Live cd?

---

### Post by Stereotypical Rage on 2005-12-16
A simple over looked website: [www.bootdisk.com](www.bootdisk.com)

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Stereotypical Rage]A simple over looked website: [www.bootdisk.com](www.bootdisk.com)[/QUOTE]

Thanks for the site...
EDIT : Still can't find a MBR Recovery.

---

### Post by Herman on 2005-12-16
The one I use from boot disk.com is the Windows 98SE one called boot98c_seoem.exe, but they have a more up-to-date equivalent there now.
I just re-start the computer with that in the floppy drive an type:
> fdisk /mbr  after the A:\ prompt.
That's what works for me anyway. I just do that for testing purposes, so I can practice ways to re-install GRUB. It works, but, I really prefer GRUB. :D (Herman)

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Herman]The one I use from boot disk.com is the Windows 98SE one called boot98c_seoem.exe, but they have a more up-to-date equivalent there now.
I just re-start the computer with that in the floppy drive an type:
 after the A:\ prompt.
That's what works for me anyway. I just do that for testing purposes, so I can practice ways to re-install GRUB. It works, but, I really prefer GRUB. :D (Herman)[/QUOTE]

Problem is my Floppy drive is on the fritz...
Any chance the program can make a bootable cd?

EDIT : Is there any chance If I were to Reformat My other HDD that grub will recongize the Linux install is gone and Will automatically boot to Windows XP?

---

### Post by Stereotypical Rage on 2005-12-16
Should be able to create a bootable disk with Nero. I do believe.

---

### Post by Herman on 2005-12-16
>  Any chance the program can make a bootable cd?
Well, that would be too complicated for me. It would be simpler to either buy a new floppy drive for your computer, or borrow an XP disk from a freind.
What is it you are trying to do anyway. I know you want to restore your boot sector, but why? :smile: 
Maybe there is something completely different that you could consider even, such as installing GAG to it instead, if you don't like GRUB, but I don't understand what it is you are trying to accomplish in the first place. :confused: (Herman)

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Herman]Well, that would be too complicated for me. It would be simpler to either buy a new floppy drive for your computer, or borrow an XP disk from a freind.
What is it you are trying to do anyway. I know you want to restore your boot sector, but why? :smile: 
Maybe there is something completely different that you could consider even, such as installing GAG to it instead, if you don't like GRUB, but I don't understand what it is you are trying to accomplish in the first place. :confused: (Herman)[/QUOTE]


I want to unistall Ubuntu.. But First remove the GRUB bootloader to insure I don't mess up anything.

I didn't realize until I installed Ubuntu that my other HDD will Not Be recognized by Windows XP Because of its format.

---

### Post by Herman on 2005-12-16
I think if you want the cheapest and easiest solution then, is to first find the page in my 'sig link' about GAG, and download a copy of GAG for yourself, and make a GAG boot CD, (sig link + gag's own instructions both explain how), and configure and write GAG to your MBR instead. It will cost you nothing to try that, and it should solve your problem.:D (Herman).

---

### Post by Mustard on 2005-12-16
[QUOTE=Ðrehmini]I want to unistall Ubuntu.. But First remove the GRUB bootloader to insure I don't mess up anything.

I didn't realize until I installed Ubuntu that my other HDD will Not Be recognized by Windows XP Because of its format.[/QUOTE]

What complications has it caused because XP can't read the linux file format?

If you wanted to swap stuff between linux and XP you could create another vfat partition and use that partition to move files from one system to the next.  Both linux and XP recognise vfat and both can write to vfat.

Anyway, good luck with solving your problem. :)

---

### Post by Mustard on 2005-12-16
> EDIT : Is there any chance If I were to Reformat My other HDD that grub will recongize the Linux install is gone and Will automatically boot to Windows XP?

I would be asking the question of which drive had grub installed on it and whether grub would still be there after you formatted, before I would go down that road.

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Mustard]I would be asking the question of which drive had grub installed on it and whether grub would still be there after you formatted, before I would go down that road.[/QUOTE]

Well I had installed it on my primary HDD (Windows XP is installed on).

[QUOTE=Herman]I think if you want the cheapest and easiest solution then, is to first find the page in my 'sig link' about GAG, and download a copy of GAG for yourself, and make a GAG boot CD, (sig link + gag's own instructions both explain how), and configure and write GAG to your MBR instead. It will cost you nothing to try that, and it should solve your problem.:D (Herman).[/QUOTE]
Prehaps there is a chance GRUB would auto select Windows XP and boot within 4-5 Secs?

Thanks for all your help Guys (And Gals if any) I Appreciate you helping me.

---

### Post by Herman on 2005-12-16
Well, what this is all about is just a wee, small 446 byte 'note' on your MBR (or bootsector), which looks at your partition table, which is also squeezed on the 512 byte MBR, and points to the bootable partition, where the second stage boot loader, which is much too big to fit on 446 bytes, takes over.

Your 'boot sector' used to have a note on it making it point to Windows.
Now, it has a note on your MBR/bootsector (same thing basically), making it point to Ubuntu. 

If you erase Ubuntu, it will still point there, but there will be no second stage boot loader there, so nothing will happen, you'll probably end up with a black screen and maybe an error message. (Because Ubuntu will be gone, along with the second stage of GRUB boot loader.

If you install GAG, it will also install a 446 byte note on your MBR, since you haven't got a Windows CD, and your floppy drive isn't working, and it will install the second stage of its boot loader elsewhere on the first track of the disk, which (hopefully) hasn't got anything else on it. (Read GAG's instructions about this). All GAG will do is then act as a 'relay', and pass on the 'urge' to boot, to your Windows NTloader, the same as GRUB used to do. And you can install and erase operating systems after that all you like and you'll always be able to re-configure GAG to suit whatever new systems you add or old ones you remove. You just need to install any new operating systems you may want with the boot loader on the new partition. (Or re-install GRUB, it won't matter). But GAG will boot Windows in the meantime for you. If you want, you can just try it out and boot off a GAG CD. It's just that the CD won't 'remember' your settings, like GAG can if it's on a floppy disk or on your hard disk. 
I'll be here if you need to know more. :smile: (Herman)

---

### Post by Ðrehmini on 2005-12-17
Thanks for all your Help Guys.

I've come across [THIS](http://drehmini.net/tools/xp_rec_con.zip) ISO.
I've uploaded it to my webserver.

What the ISO is of the actual recovery console from the Windows XP CD.

As I said... I appreciate everyone's help.

Thanks for the great advice...

---

