---
title: "the user/password isn't recognize"
date: 2004-11-22
forum: Apple PPC Users
---

### Post by fede_dev on 2004-11-22
the installation is ok.
:sad:  But at login screen the user/password isn't recognize and I couldn't login in the system.
Solution?
thanks in advance.

fede

---

### Post by arctic on 2004-11-22
are you sure that you haven't done a typo? check if you have e.g. caps-lock enabled. linux-systems are case-sensitive.

---

### Post by fede_dev on 2004-11-22
yes (isn't a type error), if I type the user and the password the characters in the field are correct.
But the system didn't let me in.

The others things in the installation are ok and I see the splash page and the login without error.

the only problen appears to be the user.

I try to install in another machine and I have the same problem.

bye

p.s. there's a way to enter in rescue mode or something similar?

fede

---

### Post by khc on 2004-11-24
Is there anything special about the username/password? Try to use something that contains only letters to rule out any keyboard config problems.

---

### Post by fromtheflames on 2004-12-08
Same problem here...
I'm an Italian user; during the installation, deb-installer asked me for my "usb keybord"... I set it up to Italian, but the layout is different for the one on my ibook... the "m" char is at the "ò" position and "a" and "q" are swapped... I think the old awerty layout...
Anyway, after the installation process, the layout in gnome appears to be ok; so I changed my dummy password (that selected in the installation) with my own password... rebooted and.... nothing: the password isn't recognised.

I tried previus installation of warty on the same machine.

This one was first installed as warty, and then upgraded to hoary (changed utf8 too); I think is impossible the problem could be in that!

Suggestion?

---

### Post by slux on 2004-12-08
Gnome may change the keymap to the right one itself, have you checked the correct one also used in the login screen? might explain the password problem if some of the keys you need to press for the password are in different places on the incorrect keymap.
<edit>
for rescuing, you can just enter the parameter "init=/bin/bash" to the kernel from the yaboot prompt or use the ubuntu install CD (provided that it did give you a console, I don't remember.
</edit>

---

### Post by fromtheflames on 2004-12-08
[QUOTE=slux]Gnome may change the keymap to the right one itself, have you checked the correct one also used in the login screen? might explain the password problem if some of the keys you need to press for the password are in different places on the incorrect keymap.
<edit>
for rescuing, you can just enter the parameter "init=/bin/bash" to the kernel from the yaboot prompt or use the ubuntu install CD (provided that it did give you a console, I don't remember.
</edit>[/QUOTE]
 Rescued my installation running osx on an external disck, mounting the ext3 partition and erasing the password field in the /etc/shadows file....

Thank you slux...

---

### Post by slojimfizz on 2006-01-25
Having that same prob., TWICE: done another new, clean install with particular attention to typing in user name and password. Seems to accept user name, but not the password. And I know it is correct--same as entered in the install. I use 5 letters & two numbers. Am dying to get to desktop--anyway around this? Hate to do another complete install, which may just end up with same result.  Thx, anyone.

---

### Post by decoomzaLP on 2006-02-25
Greetings All

I seem to have encountered the same problem, and am eargerly awaiting assistance.

I have (I think) forgotten my Ubuntu login. I have tried all the combinations (case sensitive!) and I just cannot login. Its my fault, I'd been away since Dec 2005 (Id set and used Ubuntu a coupla times) and now am back. Didn't know it'll behave like the girlfriend (I seem to have wrong password with her too):-D .

My setup is a dual-boot with Win XP-Pro, however each runs from a seperate HDD.

How do I reset my userID/Password for Ubuntu? . . . . . and the girlfriend?

Please help. I eargerly wanna use my apps, and install new ones too.

Waiting. . . . .

---

