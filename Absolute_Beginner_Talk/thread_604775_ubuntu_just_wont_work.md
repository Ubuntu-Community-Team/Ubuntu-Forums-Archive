---
title: "ubuntu just wont work"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by ineedsumhelp on 2007-11-06
ubuntu 7.10 live cd wont work for me and i am running windows xp version 2002 on a compaq and i insert the cd and it boots windows not ubuntu can sum1 plz help?

---

### Post by ineedsumhelp on 2007-11-06
and yes i insert it then i restart the computer

---

### Post by misfitpierce on 2007-11-06
push f12 or f10 to force choose startup to cd.

---

### Post by creeco on 2007-11-06
Try burning a new copy of ubuntu, and when your burn it, burn it as a disc image!

---

### Post by twiceasworn on 2007-11-06
Sounds like your BIOS is configured to boot from the hard drive and not the cdrom drive.  When the computer is booting you need to hit a key (it usually tells you what to hit), typically the DEL key or one of the function keys (f10 is popular).  Once you are into the bios you need to change the boot order to where the cdrom is first, so that it will boot the ubuntu cd.  

Also i believe you can start the livecd and install through windows by clicking on the cd rom drive.  But I could be wrong, never tried it that way before.

---

### Post by ineedsumhelp on 2007-11-06
1st boot device: CD-ROM Group
 2nd boot device: Floppy Group
 3rd boot device: HDD Group
 4th boot device:network boot

---

### Post by twiceasworn on 2007-11-06
If it is still not booting to the liveCD i would suggest re-burning the disc at 2x or 4x to make sure you do not lose data during the burn.

---

### Post by Maestro23 on 2007-11-06
> **creeco said:**
> Try burning a new copy of ubuntu, and when your burn it, burn it as a disc image!

Only thing I can think of as well.  HIs boot order looks good in his BIOS.

---

### Post by creeco on 2007-11-06
99% of all bios'es are configured to boot from the cd as default, so i think it is better to tell people how to burn a distro properly instead of telling them to get their hands down into their BIOS!

---

### Post by ineedsumhelp on 2007-11-06
my friend used the EXACT same disk (in fact it is his disk) and he has an hp computer and it worked for him

---

### Post by Maestro23 on 2007-11-06
> **ineedsumhelp said:**
> my friend used the EXACT same disk (in fact it is his disk) and he has an hp computer and it worked for him

Perhaps you drive has difficutly reading that brand of media?  Since it doesn''t even recognize it in the drive when you boot up. How old is the drive?  Is there a firmware upgrade for the drive?

---

### Post by ineedsumhelp on 2007-11-06
> **Maestro23 said:**
> Perhaps you drive has difficutly reading that brand of media?  Since it doesn''t even recognize it in the drive when you boot up. How old is the drive?  Is there a firmware upgrade for the drive?

it does recognize the disc as ubuntu as it is in the drive but for some reason it just wont boot

---

### Post by Maestro23 on 2007-11-06
> **ineedsumhelp said:**
> it does recognize the disc as ubuntu as it is in the drive but for some reason it just wont boot

So it recongizes it as Ubuntu.  Do you get a screen with boot options, you choose Ubuntu and it boots Windows anyway?  

Or the computer boots up, acts like it reads the disc and boots into Windows anyway?

---

### Post by ineedsumhelp on 2007-11-06
> **Maestro23 said:**
> So it recongizes it as Ubuntu.  Do you get a screen with boot options, you choose Ubuntu and it boots Windows anyway?  

Or the computer boots up, acts like it reads the disc and boots into Windows anyway?

i'm not totally sure what u mean but when i try to boot there is absolutely no idication tht ubuntu is even in the drive but when i go to "My Computer" it says ubuntu is in the drive and if i double click on ubuntu it just goes to the "ubuntu browser" which gives u information about ubuntu but there r no boot options there

---

### Post by stchman on 2007-11-06
> **ineedsumhelp said:**
> ubuntu 7.10 live cd wont work for me and i am running windows xp version 2002 on a compaq and i insert the cd and it boots windows not ubuntu can sum1 plz help?

You need to go into the BIOS and tell your computer to boot from CD.

Another question.  Did you burn the .iso image or just burn a great big 698MB .iso file onto a CD?

---

### Post by Steven Redman on 2008-01-14
I seem to be having the same problem:

With the Ubuntu CD in the DVD-Rom drive my computer bypasses the CD boot and starts up Windows XP which is the operating system installed on the Hard Drive. 

I have a Compaq Evo N800v notebook which I have Widows XP installed on. I am keen to intsall Ubuntu 7.10 but so far can't get my system to boot from the CD despite:

1- Checking my BIOS for boot order which is set first to multibay "which contains the DVD-ROM Drive"  and second to HDD Hard Drive. I burnt a second CD and checked it for errors with WinMd5Sum which matched the checksum. As a TestI tried to boot with my Compaq restore CD which boots from the CD and doesn't go to Windows.

I also checked to see if I had sufficient space on the hard drive which is 9GB free.

Stumped and aggravated I can't try out Ubuntu.

As Compaq was bought by HP and the HP notebooks look pretty similar to the previous Compaq's this may be a Compaq/HP issue.

Either way, currently out of ideas.

Help!

---

