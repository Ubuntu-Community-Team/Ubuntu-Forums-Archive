---
title: "GRUB error"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by IDipSkoalMint on 2006-06-08
I had a dual-boot with Windows and Ubuntu and to make room for Vista, I used Partition Magic to erase my Linux partition, and now I get a GRUB error 22 message popping up. I tried using my WinXP disc and doing the "fixmbr" command, but that didn't work. Can someone help please? Thanks.

Regards,
Matthew

---

### Post by nalmeth on 2006-06-08
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Try that one out

---

### Post by IDipSkoalMint on 2006-06-08
[QUOTE=nalmeth][http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Try that one out[/QUOTE]

Thanks, but I'm trying to get rid of GRUB all-together ... I guess I should have clarified better

Any help there?

---

### Post by nalmeth on 2006-06-08
That guide should fix the GRUB problem, but if you want something else look into lilo boot-loader. 

EDIT: And I misread your thread again :)

I have no knowledge of fixing windows mbr problems. 

Erasing linux for vista.. For shame.. :p

---

### Post by IDipSkoalMint on 2006-06-08
[QUOTE=nalmeth]That guide should fix the GRUB problem, but if you want something else look into lilo boot-loader. 

EDIT: And I misread your thread again :)

I have no knowledge of fixing windows mbr problems. 

Erasing linux for vista.. For shame.. :p[/QUOTE]

It tried to fully reinstall Ubuntu ... I tried the "fixmbr" and "fixboot" solution mentioned and it gave me a "cannot find system drive or drive specified is not valid" error.

I can get into WinXP using Ultimate Boot CD, but I'm trying to just get the Windows bootloader up and running again. Anyone know how I can do it from that? Thanks.

---

### Post by IDipSkoalMint on 2006-06-08
UPDATE: I installed Vista and the Windows bootloader overwrote the GRUB, so I'm fine. Thank you for your help, nalmeth ;)

---

