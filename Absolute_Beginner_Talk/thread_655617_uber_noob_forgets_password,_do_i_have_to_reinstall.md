---
title: "uber noob forgets password, do i have to reinstall?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by chaparrazo on 2008-01-01
just installed fluxbuntu, looks great. only prob is that i guess i don't remember which password i used. i've tried all the variants of what i thought i put in. 

do i have to reinstall? i read the following on the fluxbuntu page, this doesn't work either.

The Fluxbuntu Live CD ships with a default user name and password. The username is fluxbuntu and password is livecd.

is it case sensitive? 

thanks

---

### Post by luisromangz on 2008-01-01
In grub, there should be various boot options, at least 2 regarding to the same version of the kernel. The second one should be a recovery terminal. From there, you should be able to get a root terminal, from where you can change you user's password through the command line.

---

### Post by bigken on 2008-01-01
sudo passwd

---

### Post by Fixman on 2008-01-01
First, try doing
```

su
(dont write anything, just press enter)
passwd <<username>>
(type your new password here

```

If this doesn't work, try

Ctrl+Alt+F1
```

User: root
Password: (nothing)

passwd <<username>>
(Put your new password here)

```

If this does neither work, try this long option:

Do
```
gksu gedit /boot/grub/menu.lst
```

There, seek for a line that says

```
 timeout ((number)) 
```

Make sure ((number)) its a big number, like 10 or 20. Later, seek for a line that says

```
hiddenmenu
```
Put a the '#' at the begginning os keeps being
```
#hiddenmenu
```

For, the last, seek for some lines that say (not exacly, could be something that "looks like it". Note that the lines you choose MUST NOT have any # a

```

title Ubuntu
root (hdx,x)
kernel stuffstuffstuffstuff ro splash
intrd stuff stuff stuff stuff
stuff
stuff

```

Copy it, and add single at the end. It should become

```

title Ubuntu
root (hdx,x)
kernel stuffstuffstuffstuff ro splash
intrd stuff stuff stuff stuff
stuff
stuff

title Ubuntu 2
root (hdx,x)
kernel stuffstuffstuffstuff ro splash **single**
intrd stuff stuff stuff stuff
stuff
stuff

```

Then reboot the computer, and you will be prompted for some options. Select "Ubuntu 2", and there you will go to a terminal. There write

```

passwd <<username>>
reboot

```

And everything will be wixed.

EDIT: If it works, please thank me pressing the medal below my post.

---

### Post by jken146 on 2008-01-01
> **bigken said:**
> sudo passwd

Don't do that in Recovery Mode!!  It will unlock the root account and give it the password you supply.  If you're not changing the password of the user you're logged in as, you need to specify which user you mean.  Do this:
```
passwd johndoe
```
where johndoe is the username of the user concerned.

---

### Post by Fixman on 2008-01-01
> **bigken said:**
> sudo passwd

How can he use sudo if he doesn't know his password??

---

### Post by bigken on 2008-01-01
> **Fixman said:**
> How can he use sudo if he doesn't know his password??


sudo passwd (yourname)

try it

---

### Post by Fixman on 2008-01-01
> **bigken said:**
> sudo passwd (yourname)

try it

This happens:
[[IMG]http://img169.imageshack.us/img169/5865/screenshotmartinubuntutya2.png[/IMG]](http://imageshack.us)

It asks me for my password.

---

### Post by gn2 on 2008-01-01
This will tell you how to change your username password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by bigken on 2008-01-01
ken@stratocaster:~$ sudo passwd ken
Enter new UNIX password:

---

### Post by Fixman on 2008-01-01
> **bigken said:**
> ken@stratocaster:~$ sudo passwd ken
Enter new UNIX password:

Do you have a password? I mean, if you sudo something else, does it prompt for a password?
Are you logged as root anyway?

---

### Post by bigken on 2008-01-01
> **Fixman said:**
> This happens:
[[IMG]http://img169.imageshack.us/img169/5865/screenshotmartinubuntutya2.png[/IMG]]("http://imageshack.us")

It asks me for my password.

its passwd not password

---

### Post by Fixman on 2008-01-01
> **bigken said:**
> its passwd not password

Please read more closely what I have written.

---

### Post by bigken on 2008-01-01
> **Fixman said:**
> Please read more closely what I have written.

I do apologise

---

### Post by Fixman on 2008-01-01
> **bigken said:**
> I do apologise

If you really regret then thank all my posts in this thread.

*[COLOR="Silver"]hehehe[/COLOR]*

---

