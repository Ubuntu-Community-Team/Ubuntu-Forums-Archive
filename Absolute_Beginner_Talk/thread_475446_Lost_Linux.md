---
title: "Lost Linux"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by JoBangles on 2007-06-16
Hi,
Much to my dismay I have had to return to WinXP to ask for help. Nearly formatted WinXp drive to Linux today.
I have latest Ubuntu Linux installed and switched on ATI 3D, now I nearly get to final screen then black screen.
I have SuperGrub boot disk but do not know what to enter on command line to undo ATI 3D change.For ever in your debt for help to get this excellent system working again.

---

### Post by Jimmyfj on 2007-06-16
try this

sudo dpkg-reconfigure xserver-xorg

---

### Post by JoBangles on 2007-06-16
A thousand thanks Jimmfj, for the resurrection! Some of the selections I had to make were a bit of guesswork, but, Linux lives again.
JoBangles

---

### Post by Crafty Kisses on 2007-06-16
> **JoBangles said:**
> A thousand thanks Jimmfj, for the resurrection! Some of the selections I had to make were a bit of guesswork, but, Linux lives again.
JoBangles

You might also want to try backing up your X server after this occasion, you can do this by:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then if something ever goes wrong, you can recover it by trying this:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by drowner on 2007-06-16
You might also want to try backing up your X server after this occasion, you can do this by:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then if something ever goes wrong, you can recover it by trying this:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by Crafty Kisses on 2007-06-16
> **drowner said:**
> You wanna try that one again?

Sure. :)

---

### Post by Crafty Kisses on 2007-06-16
> **JoBangles said:**
> Hi,
Much to my dismay I have had to return to WinXP to ask for help. Nearly formatted WinXp drive to Linux today.
I have latest Ubuntu Linux installed and switched on ATI 3D, now I nearly get to final screen then black screen.
I have SuperGrub boot disk but do not know what to enter on command line to undo ATI 3D change.For ever in your debt for help to get this excellent system working again.

You might want to visit this link:

[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/]("http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/")

---

### Post by drowner on 2007-06-16
> **Codename said:**
> You know, you should actually stop being a dick, and correct my fault.

sorry man, was joking.

Ill remove it.

---

### Post by Crafty Kisses on 2007-06-17
> **drowner said:**
> sorry man, was joking.

Ill remove it.

No problem man, I was just trying to help, I was angry, friends again? :)

---

