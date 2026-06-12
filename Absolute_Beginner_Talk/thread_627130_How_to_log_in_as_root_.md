---
title: "How to log in as root_"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by quintacal on 2007-11-29
Hello -

I am using Fiesty fawn in aa VMplayer.
I am trying to copy over my kontact files from a prvious instalation *Gutsy*.
It starts to copy over the files, but them says I do not have permission to write to that folder as I am not logged in as root.
I gave myself all permissions - still no go.
You are also unable to log in at the login screen as root.
How am I to copy over these files?

Thanks so much,
Chris

---

### Post by jordanmthomas on 2007-11-29
```
gksudo nautilus
```
or ```
kdesu konqueror
``` for kde
Then you can copy /move / delete whatever you want.

To log in as root you need to give root a password.
To log in as root through gdm, you have to enable it in system --> administration --> login window.

I won't say how to do these two things because if you can't figure it out somehow, you shouldn't run as root.  :)

Also, after copying these files (I'm assuming they're settings and saved messages?) you may want to make sure your user has permission to read and write them.

---

### Post by PmDematagoda on 2007-11-29
You can do that in Recovery Mode, or by entering sudo -i in a terminal which will put you in sudo mode only in the terminal or by starting your file manager in root mode. e.g.:-

For Kubuntu

```
sudo konqueror
```

For Xubuntu

```
sudo thunar
```

For Ubuntu

```
sudo nautilus
```

---

### Post by jordanmthomas on 2007-11-29
You shouldn't use sudo for launching graphical programs, but gksudo or kdesu.
Using sudo can mess up your .ICEAuthority's (and other file's) permissions I believe.

---

### Post by Dr Small on 2007-11-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PmDematagoda on 2007-11-29
> **jordanmthomas said:**
> 
I won't say how to do these two things because if you can't figure it out somehow, you shouldn't run as root.  :)


1+ to that, being root is a dangerous thing if you don't know what you are doing since you can delete critical system files in a way that any other normal file would be deleted.

> 
Also, after copying these files (I'm assuming they're settings and saved messages?) you may want to make sure your user has permission to read and write them.

Forgot that part, thanks jordanmthomas:).

---

### Post by limac on 2007-11-29
but remember loging in as root isn't recommended.

---

### Post by PmDematagoda on 2007-11-29
Basically what is being said by jordanmthomas, Dr Small, limac and myself is that you should only use the sudo command if that is necessary **only**, not as a part of your day to day work with the PC.

---

### Post by Dr Small on 2007-11-29
> **limac said:**
> but remember loging in as root isn't recommended.
... But it is essential in alot of situations.

---

### Post by limac on 2007-11-29
well for me sudo always did the work. but in some cases you do.

---

### Post by GnomviD on 2007-11-29
jordanthomas, Dematagoda, you've just made a linuxnewb very, very happy. After a few hours of fruitless trying to copy files, I give up and forum search - straight into you.

In my forgetfulness, I forgot about gksudo. Thanks for reminding me, you've made my night. :)

---

