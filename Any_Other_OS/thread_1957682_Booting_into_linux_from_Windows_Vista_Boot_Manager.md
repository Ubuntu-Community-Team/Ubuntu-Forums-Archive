---
title: "Booting into linux from Windows Vista Boot Manager"
date: 2012-04-12
forum: Any Other OS
---

### Post by JASONFUSARO on 2012-04-12
I was wondering if anyone is currently booting linux from their windows boot manager? 
 
I would like to get some idea as to the stability of doing things that way as opposed to writing Grub to the MBR.
 
I was doing it that way but just recently learned how to boot into linux through the windows boot manager. I also go through a dedicated boot partition on sda6 and can also get back to the windows menu from linux.
 
I have been experimenting with EasyBCD, Visual BCD Editor, Vista-bootPro, bcdedit,MBRfix and others to try and get a handle on the best route to recovery when the onknown strikes!
 
Any thoughts on the subject would be appreciated, thanks.

---

### Post by darkomano on 2012-04-15
Windows 7/Vista boot environment is more rigid and with less capabilities than that of GRUB.
 
There is the requirement of placing Windows boot related files on a primary and active partition. GRUB can be placed on extended logical partition.
 
Repairing Windows 7/Vista booting always involves writes of Windows MBR to disk so having a Linux/GRUB MBR there is not a very good idea. Repairing GRUB does not necessarily mean writes to MBR on disk !
 
 
To summarize when having Windows and Linux dual-boot:
1) always use a Windows MBR and Windows boot manager as base to be able to quickly repair Windows booting.
2) boot GRUB2/GRUB based LInux versions over a Windows boot sector loader giving as parameter boot image file "boot.img" or "stage1" from /boot/grub2 or /boot/grub directory.

---

### Post by kc1di on 2012-04-15
Though I agree with the previous poster that grub is a better boot loader option for dual boot. He didn't really answer your question.
here is a page that give step by step instructions on how to do what you asked. 
[http://blogs.technet.com/b/port25/archive/2006/10/13/http-port25-technet-com-archive-2006-10-12-windows-and-linux-integration-3a00-a-conversation-with-the-author-aspx.aspx]("http://blogs.technet.com/b/port25/archive/2006/10/13/http-port25-technet-com-archive-2006-10-12-windows-and-linux-integration-3a00-a-conversation-with-the-author-aspx.aspx")

Also an alternative to either plan is EasyBCD found here [http://neosmart.net/EasyBCD/]("http://neosmart.net/EasyBCD/")
Good Luck , Let us know how you make out.

---

### Post by darkomano on 2012-04-15
I don't agree on post above in the part EasyBCD as it introduces third party boot manager - neogrub or whatever for booting Linux based OS.
 
Having Windows bootmgr and GRUB/GRUB2 is enough for dual-booting Windows and Linux/Ubuntu. There is no need of third party boot managers !
 
From Windows any "foreign" system can be booted over a so called "boot sector loader".
The boot sector loader needs a copy of the partition boot record of the "foreign" system.
 
The partition boot record for GRUB is /boot/grub/stage1.
The partition boot record for GRUB2 is /boot/grub2/boot.img.
No need for extracting boot sector with dd.
 
The link posted above seems to be popular in Google for dual booting Linux from Vista/Windows 7.

---

### Post by kc1di on 2012-04-15
> **darkomano said:**
> I don't agree on post above in the part EasyBCD as it introduces third party boot manager - neogrub or whatever for booting Linux based OS.
 
Having Windows bootmgr and GRUB/GRUB2 is enough for dual-booting Windows and Linux/Ubuntu. There is no need of third party boot managers !
 
From Windows any "foreign" system can be booted over a so called "boot sector loader".
The boot sector loader needs a copy of the partition boot record of the "foreign" system.
 
The partition boot record for GRUB is /boot/grub/stage1.
The partition boot record for GRUB2 is /boot/grub2/boot.img.
No need for extracting boot sector with dd.
 
The link posted above seems to be popular in Google for dual booting Linux from Vista/Windows 7.

I'm not saying that I use or even would use easyBCD but was just showing the options available , my choice has always been grub or lilo they work fine for what I'm doing , Those running bsd O.S. however may dis agree with your assessment of easyBCD. Just a thought :)

---

### Post by darkomano on 2012-06-21
For FreeBSD the file is "/boot/boot1" 
The utility "[ufs2tool - ufs for Windows]("http://ufs2tools.sourceforge.net/")" gives read access to a BSD partition.
Unix descendants need  a primary partition ;)

---

