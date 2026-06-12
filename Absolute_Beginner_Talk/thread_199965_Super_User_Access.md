---
title: "Super User Access"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Absurd on 2006-06-19
When I attempt to install the ati drivers (so that I don't have keep removing my video card each time I want to use a different OS), it says I must be a super user.

However, when I try the "su" command and use my password, it tells me that it is incorrect.:confused: I don't understand; it's the same password I used when I installed and/or added the user ([thread](http://www.ubuntuforums.org/showthread.php?t=198074)).

If my password isn't the correct password, then what is it?

---

### Post by Jagot on 2006-06-19
With Ubuntu you need to type 'sudo' before anything that requires root privileges.

If you don't want to type sudo before each command then you can type:

```
sudo -i
```

You can read more here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by glotz on 2006-06-19
You'll need to **sudo su**. Remember to logout root account before surfing web, etc!

See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Absurd on 2006-06-19
ok, I used that command and then I used su, entered the password and I still get "Authentication failture."

By the way, why won't the password show up in plain text?

Sorry if I sound restless or impatient by the way.

---

### Post by Jagot on 2006-06-19
Using sudo -i you should be able to get to root without having to type a password in.

---

### Post by PingunZ on 2006-06-19
```
sudo -s -H
```

---

### Post by Absurd on 2006-06-19
The ati driver installer still will not proceeed even though I logged in with sudo -i.

If I do

> sudo sh -i ./ati-driver-installer.run

nothing happens

btw, if I go to the terminal and enter

> gksu users-admin

I get the message <username> is not in the sudoers file. Why not?

---

### Post by bruce89 on 2006-06-19
That's not how you install the drivers anyway, follow this - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Absurd on 2006-06-19
Well, I can't install and/or use sudo if I'm not in the sudoers file. How do I view and edit the contents of the file?

---

### Post by b1g4L on 2006-06-19
Go to users, and just retype the password for root. Then it should accept that password.

---

### Post by bruce89 on 2006-06-19
There is no root login by default, you should add yourself to the "admin" group to get sudo privillages.  Edit /etc/group and add your user name to the list in admin.  I realise that you need root permissions to do this, so boot into recovery mode, and type ```
nano /etc/group
```
(Sorry, couldn't explain it better just see below for a much better description in the link below)

---

### Post by aysiu on 2006-06-19
What bruce89 says is correct, except that was always back up config files before editing them: ```
cp /etc/group /etc/group.backup
``` Better to have a broken file than an empty one.

Full instructions here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by bruce89 on 2006-06-19
[QUOTE=bruce89]There is no root login by default, you should add yourself to the "admin" group to get sudo privillages.  Edit /etc/group and add your user name to the list in admin.  I realise that you need root permissions to do this, so boot into recovery mode, and type ```
nano /etc/group
```[/QUOTE]
Yikes, that was all just an educated guess!  I had to do something similar earlier today, my home directory went all wrong on the slow computer, and the Applications menu (XFCE) wouldn't open.  So I deleted my user, and home directory, made a new one and added myself to the admin group.

---

### Post by Absurd on 2006-06-19
[QUOTE=aysiu]What bruce89 says is correct, except that was always back up config files before editing them: ```
cp /etc/group /etc/group.backup
``` Better to have a broken file than an empty one.

Full instructions here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)[/QUOTE]
THANK YOU SO MUCH

seems all I had to do was 

> addgroup <username> admin

---

