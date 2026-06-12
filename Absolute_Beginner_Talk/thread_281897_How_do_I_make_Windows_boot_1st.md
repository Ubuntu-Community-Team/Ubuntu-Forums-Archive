---
title: "How do I make Windows boot 1st?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by rholster on 2006-10-21
[COLOR="Blue"][/COLOR]**** I finally broke down and installed Ubuntu and I'm really impressed. The only thing I want to change is to have Windows XP be at the top of by boot list so that if I'm not sitting here to manually select, it will autimatically go to Windows. When I get the hang of Linux...I have the feeling I'll be saying goodbye to Windows completely. Thanks for any help.

---

### Post by Sef on 2006-10-21
Read [Change Default OS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") to boot Windows first.

---

### Post by ciscosurfer on 2006-10-21
Set the default number in your /boot/grub/menu.lst file to correspond to your Windows entry.  Right now, the default is set to 0 which corresponds to your first entry.  (Remember also that 'memtest' counts as an entry in the file).  So let's say your Windows line comes right after your memtest entry, you'd set your default number to that.  So if your Windows entry is fifth down on the list, you would put the number 4 in as your default entry.  You can also use your arrow keys once your GRUB menu loads and select which drive/partition/OS you want to boot.  Hope this helps.  If you need more info, just check the GRUB link in my signature.  Like Sef said, this link ([https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)) is also helpful.

---

