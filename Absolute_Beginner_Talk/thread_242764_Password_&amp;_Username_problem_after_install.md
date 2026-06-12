---
title: "Password &amp; Username problem after install"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by StGeorge on 2006-08-24
I installed Ubuntu 6.06 Alternate as a Stand Alone OS.
During install I remember entering a password and remember that password.
The problem is that I do not remember entering a UserName.
I gave the Laptop its Network name and I know what username I would have used if prompted for one.
I have tried these but to no avail.
Any Ideas?

---

### Post by scxtt on 2006-08-24
boot into recovery mode, do a **ls -l /home**, any user you created during install should have a folder by that name in /home

---

### Post by StGeorge on 2006-08-24
Don't understand.
I have a window up with username.
Options only give restart, shutdown etc.
Complete novice to Ubuntu.

---

### Post by scxtt on 2006-08-24
your question makes no sense then, it appears that you don't know the username, i gave you a way to figure it out ... your 2nd post makes it sound like you're sitting at a GDM/KDM login screen - maybe you should be more explicit about the problem ...

---

### Post by bvali on 2006-08-24
try the username ubuntu. A friend of mine got the same thing after installing ubuntu and told me the user ubuntu with his supplied password worked.

---

### Post by StGeorge on 2006-08-24
OK.
This is a fresh install.
Don't know how to boot into recovery mode.
I am sitting at the login screen.
I am on my desktop accessing the forum.
The install is on my Laptop.
After intalling Ubuntu 6.06 I come to my first Login screen.
As I have said I cannot remember entering a username during install.
If I had entered a username I know what it would have been.
I do not know how to get to view what has been registerd as a username.

---

### Post by scxtt on 2006-08-24
reboot your laptop, if necessary hit escape at the grub menu [it'll optionally tell you to do so] (this is before ubuntu starts loading) - you should have an option to boot into recovery mode which will drop you into a root login shell, then type **ls -l /home** and see what directories are listed there ...

---

### Post by StGeorge on 2006-08-24
Ok.
Tried ubuntu uppercase and lowercase for username.
Did not work.
Rebooted into recovery mode did ls -l /home.
Got:
total 4
drwxr-xr-x 2 oem 4096 Aug 23 21:11 oem(blue coloured text on final oem entry)

---

### Post by StGeorge on 2006-08-24
Sorry that should have been:
total 4
drwxr-xr-x 2 oem oem 4096 Aug 23 21:11 oem(blue coloured text on final oem entry)

---

### Post by scxtt on 2006-08-24
you installed it in OEM mode, not a problem, you can probably enter **oem** as the username, and the password you provided ... there's also a command (that you were told about) which you can run to delete the oem user and create your own ... i'm sure it's here in the forums somewhere ...

---

### Post by StGeorge on 2006-08-24
Thanks scxtt.
oem, which was in blue text was the username.
Hopefully this will help others out.

---

### Post by Koski on 2006-09-01
> **StGeorge said:**
> Thanks scxtt.
oem, which was in blue text was the username.
Hopefully this will help others out.

It did. Thank you.

---

