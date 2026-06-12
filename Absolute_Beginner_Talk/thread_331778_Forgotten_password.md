---
title: "Forgotten password"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Ubun2 on 2007-01-05
I haveotten my password to log on to Edubuntu, and was wondering is there a way to retrieve it. I was going to reinstall edubuntu,, but as I have it set up, with windows on the same hard drive, i am afraid that i will lose everything. I tried this before and grub was deleted and then I had (i am a new and slow learner) reinstall both winedows and Edubuntu..
Thank you

---

### Post by daller on 2007-01-05
I never ran into this problem myself, but I guess you can start in "recovery mode" (press Escape when Grub loads - a little while after you power on)

This will get you loaded with superuser rights (without asking for a password)

Now run the command: "passwd USERNAME"

Enter you new password twice, and you are back in business...

**EDIT: Well, I could have posted you a link instead, here it is: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)**

---

### Post by moma on 2007-01-05
Start your PC and when you see the GRUB boot menu, 
1) Move cursor to the EduBuntu line.
2) Press letter 'e' to edit that menu selection.
3) Select kernel... line  and press 'e' to to edit that.
4) Add the word [COLOR="Red"]single[/COLOR] at the end of the kernel line. Save that line.  (this is not written permanently into /boot/grub/menu.lst).
5) Press 'b' to boot into EduBuntu.

The system will drop you to the shell promt (#). It's called single-user, maintenance mode (runlevel 1).  You will have root admin rights.
6) Change the password for your user name. Eg.
# [COLOR="SeaGreen"]passwd olga-mary[/COLOR]

Boot into runlevel 2 which is the normal operational level with network connection and graphical GUI. It's the normal runlevel of Debian/Ubuntu. (other distros have 3 or 5 as normal runlevel).
# [COLOR="SeaGreen"]init 2[/COLOR]


Of course, Daller's method above is the easiest and best way.

---

### Post by Ubun2 on 2007-01-05
> **daller said:**
> I never ran into this problem myself, but I guess you can start in "recovery mode" (press Escape when Grub loads - a little while after you power on)

This will get you loaded with superuser rights (without asking for a password)

Now run the command: "passwd USERNAME"

Enter you new password twice, and you are back in business...

**EDIT: Well, I could have posted you a link instead, here it is: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)**

Thanks daller it worked I have been wondering about this for a couple of weeks and you fix it in 60 seconds.. Thank you

---

### Post by CroEragon on 2007-01-05
I have one question about this. Doesn't it make Ubuntu very unsecure if your attacker have physical access to computer. If I'm not wrong absolute beginner can crack Ubuntu sudo pasword and do whatever he wants if he just read this thread.

---

### Post by mcduck on 2007-01-05
If somebody gets physical access to your computer it's not secure, no matter what OS or security software you are running.

All OS passwords can be overriden by booting a live-CD, and also it's possible to just move your hard disks to another computer to read all your files. BIOS passwords can usually be cleared simply by removing CMOS battery from motherboard (or using CMOS clear jumpers).

Only way to secure your machine is to make sure that nobody gets a physical access to it, and encrypt all your files.

Anyway, if you feel like it it's possible to set a Grub password to protect some entries in Grub menu.

---

### Post by jvc26 on 2007-01-05
If someone has physical access to your computer I very much doubt you'd worry about whether they had sudo rights or not ;)
Il

---

### Post by Sasa_Ivanovic on 2007-01-05
Yeah, if someone is physicly there. That someone can physicly kick it's *** so hard it would kiss the moon.

---

