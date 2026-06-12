---
title: "question about recovery mode &amp; security"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-01-06
this may be a silly question, but i'm very curious:

when grub loads, and you're asked to boot a kernel, you are given the option of normal ubuntu, or recovery mode. upon booting recovery mode of ubuntu it loads a root shell (without asking for a password). when you're done playing in root, it will continue on to boot normal ubuntu.

>> why does it prompt a ROOT shell WITHOUT asking for a password?? this seems like a huge hole in security.

---

### Post by ajmorris on 2007-01-06
I don't know why your's doesn't but mine comes up and says please type root password for maintenance or press ctrl+d to continue.

---

### Post by eXisor on 2007-01-06
Mine doesn'y ask for password either. Straight in as root. ????

How do I fix this?

---

### Post by steve.horsley on 2007-01-06
You can comment out the stanza for recovery mode in /boot/grub/menu.lst if you like, but frankly, letting someone you don't trust have physical access is a huge hole. There are many ways to get in if you have physical access. One neat one I have used is to Escape GRUB before it boots, edit the normal boot like and add the word **single**, which boots into root without a password prompt even if GRUB doesn't offer a recovery mode.

---

### Post by tenn on 2007-01-06
What about if it was used in a business and you simply dont want employees getting root acces, when the people only have limited knowledge of computers a password would be enough to stop them from gaining root access.
I have talked about this before it should not be there and open to any one, to say but if some has physical access to the machine they could do anything is really stretching things a bit, and ignoring the fact that really it is a security issue it is to simple to gain root access.

---

### Post by mcduck on 2007-01-06
If somebody gets physical access to your computer the security is already gone. Any live-CD gives root access and access to your files, and nothing stops somebody from moving your hard disks to another computer and reading files that way. 

But if you feel like it, it's possible to set Grub password so that grub asks for it if you want to access safe mode or edit grub boot lines..

---

### Post by eXisor on 2007-01-06
So to get a login prompt in recovery mode I need to remove the single from the recovery entry in menu.lst?

---

### Post by petermck on 2007-01-06
Yes. There is also a password option in the grub Menu.1st file, which I gather puts a password requirement on editing access at the grub boot, but I haven't tried it myself. 
At the end of the day if someone has physical access to the machine all of this can be beaten with a boot CD like SysRescCD. 
Encryption is really your ultimate defense. There is loopback encrytion support in the kernel using AES, blowfish etc

---

### Post by eXisor on 2007-01-06
petermck:

Thanx, and fair enough. 

Corporates tend to limit physical access pretty effectively, but in a home, access tends to be a given. No knowing what the well-intentioned clueless may do.  :)

Especially when it's me.

---

### Post by az on 2007-01-06
If you set a root password, you get prompted for the password when you enter recovery mode.


> **tenn said:**
>  to say but if some has physical access to the machine they could do anything is really stretching things a bit, and ignoring the fact that really it is a security issue it is to simple to gain root access.

Actually, setting a root password is simply giving you a false sense of security.  If you really want to keep your computer secure, you really need to look into a comprehensive plan.

---

### Post by tenn on 2007-01-06
Its not false it is just an extra step in the process.

---

