---
title: "Sudo password refused."
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by Marinmo on 2005-06-07
I am a quite (by now if not before ...) an experienced linux-user. I set my system up from a not-so-easy configuration (using expert-mode, manually setting grub to sda, then deleting root (hd4,0) in order to be able to boot). Anyway, to the question:
Using sudo prompts me for my password. I enter my password (for root, which was set at installation), and all I get is;
```
marinmo@greenmoore:~$ sudo gedit /boot/grub/menu.lst
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
marinmo@greenmoore:~$ su
Password:
root@greenmoore:/home/marinmo #
```
However, using "su" works just fine with my root-password as you can see. This is starting to get really annoying. If it's any help, I use shadowed passwords.

Moreover, trying to launch any admin-application in GNOME (Bootup manager, GDM etc) prompts me for my password aswell (I assume for my "regular" user); I enter it .... And nothing. I try to launch it again; enter my password, and get some error that the child process was killed, returning status 1.

None ... Well, FC4 Test3, but I don't count it really since it is a test, of the distros I've tried so far has given me so many headaches as Ubuntu. Any help here would be wonderful, because I am pretty confident I'm not at fault here, since this is an installation about ... 1 hour (?) old.

Thanks in advance


EDIT: I had no idea where to post this, and if nothing else I feel like a complete newbie. Feel free to move as appropriate.

---

### Post by tonym on 2005-06-07
The password sudo wants is the password of the user you are in when you call it,  not root's password.

---

### Post by Marinmo on 2005-06-07
[QUOTE=tonym]The password sudo wants is the password of the user you are in when you call it,  not root's password.[/QUOTE]
Had to edit /etc/sudoers for this, but thanks a lot, this did the trick. :) This also fixed the problem I had with the GDM etc not launching. I guess I should blame myself for not doing a proper man sudo. Again; sorry.

---

