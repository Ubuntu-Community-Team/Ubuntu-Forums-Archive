---
title: "Should I install Dapper as a USB or HDD install?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by jerseyboy91 on 2006-10-12
I have a 20 GB MP3 player, an Inoi MP180, that I want to use to install Ubuntu. However, I've been using the USB method that DaBruGo made a while back to install Ubuntu. However, nothing's working for me. 

My computer recognizes it as a hard drive, but I connect it through a USB port. I'm not sure how I should go through with installing this. Every time I install Ubuntu on my MP3 player using the USB install method, I always end up getting Error 17 on the GRUB bootloader, and I've already put "groot=(0,0)" and all that.

So basically, I want a portable Ubuntu on my MP3 player. I'm not really sure how to go through with installing Ubuntu, but any help is appreciated.

---

### Post by Kateikyoushi on 2006-10-12
Would you like to boot that installation on different machines ?

---

### Post by gn2 on 2006-10-12
> **jerseyboy91 said:**
> I have a 20 GB MP3 player, an Inoi MP180, that I want to use to install Ubuntu. However, I've been using the USB method that DaBruGo made a while back to install Ubuntu. However, nothing's working for me. 

My computer recognizes it as a hard drive, but I connect it through a USB port. I'm not sure how I should go through with installing this. Every time I install Ubuntu on my MP3 player using the USB install method, I always end up getting Error 17 on the GRUB bootloader, and I've already put "groot=(0,0)" and all that.

So basically, I want a portable Ubuntu on my MP3 player. I'm not really sure how to go through with installing Ubuntu, but any help is appreciated.

Does your BIOS support boot from USB?

Have you enabled boot from USB in your BIOS? 

Is USB before HDD in the BIOS boot order?

If yes to all of the above, does it absolutely have to be Ubuntu?

PCLinuxOS is vastly better suited to USB implementation, it has an automated installer for installing to USB.
.

---

### Post by jerseyboy91 on 2006-10-12
It does not support loading the BIOS from a USB, but it recognizes it as a hard drive, so I can put it as the first priority for loading hard drives, with my internal hard drive on second priority for booting. Of course, CD booting is first.

And also, I'd like it to load Ubuntu from different machines, but it's just that GRUB doesn't work that well right now, since i keep getting Error 17. Does anyone know if LILO will work with this?

---

### Post by gn2 on 2006-10-12
> **jerseyboy91 said:**
> It does not support loading the BIOS from a USB, but it recognizes it as a hard drive, so I can put it as the first priority for loading hard drives, with my internal hard drive on second priority for booting. Of course, CD booting is first.

And also, I'd like it to load Ubuntu from different machines, but it's just that GRUB doesn't work that well right now, since i keep getting Error 17. Does anyone know if LILO will work with this?

Suggest you try PCLinuxOS as a "proof of concept" if it works, it will show that Ubuntu can be set to do the same.

Difference is that it will take a lot of tweaking to get Ubuntu set up to do so.

There are more Distros that are much better suited to the USB option than Ubuntu, which is badly lacking in this respect.
.

---

### Post by jerseyboy91 on 2006-10-12
So, if this works, then I should try installing Ubuntu again? I'm guessing that it automatically makes a menu.lst file for the MP3 player for GRUB, is that right?

EDIT: Also, since the question came up, I might as well ask. If I want to use Ubuntu on ONLY this computer, should I just install GRUB on the MBR?

---

### Post by gn2 on 2006-10-12
> **jerseyboy91 said:**
> So, if this works, then I should try installing Ubuntu again? I'm guessing that it automatically makes a menu.lst file for the MP3 player for GRUB, is that right?

Can't help much with Ubuntu on USB. Only know it can be done, but I gave up trying (after much frustration) when I found out about PCLinuxOS.

If you do try, boot the PCLinuxOS live CD with the Windows hard drive disconnected, then you will not have the problem of the MBR being overwritten by Grub (or LiLo) which will be written to the USB drive.

PCLinuxOS feels more advanced to me (just an opinion)

Sorry can't be more help, there are Ubuntu on USB guides out there, but I wouldn't recommend any.
.

---

### Post by jerseyboy91 on 2006-10-12
Alright, I'm gonna download PCLinuxOS tomorrow, and if that works, I'll see how it works on different computers.

---

