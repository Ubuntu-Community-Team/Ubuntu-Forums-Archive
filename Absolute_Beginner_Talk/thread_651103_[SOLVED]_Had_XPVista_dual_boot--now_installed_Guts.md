---
title: "[SOLVED] Had XP/Vista dual boot--now installed Gutsy on old Vista partition-need GRUB"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-12-27
Hi There

I silly question I guess, one I have tried to resolve.

Problem: When I dual booted XP (primary) and Vista (secondary), Vista installed a funny looking boot menu (I think Vista boot sector is different from XP). I now have gutsy on the previous Vista partition, and Grub has recognized Windows on disk, and written a line for booting into it in GRUB, as [FONT="Courier New"]Windows Vista/Longhorn (loader)[/FONT]. Because I do not have Vista any more, I wish the bootloader to only show Win XP at boot up. So when I select this option from the menu, I get into another bootloader menu (Vista I think did this), from where I now have to select Winodws XP from the menu.

I did this to try and get my bootloader say what I want to say: Windows XP directly from my GRUB menu, and get rid of the Vista Bootloader
1. Using  XP disc to fixmbr from recovery console--this wiped the GRUB (could not see Ubuntu in menu), but the second stage Vista menu is still there
2. Using Gutsy live CD to reinstall Grub--this at least reinstalled GRUB correctly and I was able to boot back into Gutsy

I hope you could help me get rid of the Vista menu.

Thanks

S:confused:

---

### Post by meierfra on 2007-12-27
You probably just have  to edit c:\boot.ini on your windows partition.

Edit: This is problems wrong, since Xp uses boot.ini, but I think Vista doesn't.

---

### Post by shuttleworthwannabe on 2007-12-27
BTW, I used your excellent instructions to help me get back to the GRUB. thanks

---

### Post by meierfra on 2007-12-27
So did editing "boot.ini" work?


> BTW, I used your excellent instructions

Did you click on FixGrub?  All the credit goes to "catlett".  I hope you gave  him a "Thank you".

---

### Post by shuttleworthwannabe on 2007-12-27
Hi there again,
I am not sure what to make of this: the boot.ini file looks like this: > ;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

I guess to edit the Vista boot menu I have to find/use BCDEdit.exe; where is this executable or where do I get it from?

And yes, I did use your fixmbr link, and placed a thank-u for both of you too!
thanks

---

### Post by meierfra on 2007-12-27
I did some googling and found this

[http://www.vistabootpro.org/]("http://www.vistabootpro.org/")

But I'm not sure if it works  without vista installed.

---

### Post by shuttleworthwannabe on 2007-12-27
Cool, vistabootpro made it work.

this is what I did:
1. Downloaded and installed VBP in Win XP
2. During installation, needed .NET framework; downloaded and installed this--no problems
3. Completed the installation VBP
4. In one of the menu items, I removed Vista bootloader and installed XP loader, on the XP partition

done,

So now to chnage the GRUB Windows entry in the menu.lst

Superb!!
Double thanls
S

---

### Post by meierfra on 2007-12-27
> So now to chnage the GRUB Windows entry in the menu.lst

That should be easy.  If you need help, post the output of "sudo fdisk -l".

---

### Post by shuttleworthwannabe on 2007-12-27
done: I did this
> sudo gedit /boot/grub/menu.lst

change the > Windows entry from Windows Vista/Longhorn (loader) to > Windows XP Professional

---

