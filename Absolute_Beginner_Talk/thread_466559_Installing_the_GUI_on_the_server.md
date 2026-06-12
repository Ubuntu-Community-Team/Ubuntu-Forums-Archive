---
title: "Installing the GUI on the server"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by abasel on 2007-06-06
I appear not to be allowin in this issue:

sudo apt-get install ubuntu-desktop

Reading package lists... done
Building dependency tree
Reading state information ... done
E: Couldn't find package ubuntu-desktop

I've done an update and all appears to go well but I just can not get the ubuntu-desktop installed.

---

### Post by Ek0nomik on 2007-06-06
I think apt is just searching the CD.  Go to Preferences/Software Sources.

Check all the options under Ubuntu Software (Downloadable from the Internet)

---

### Post by louieb on 2007-06-06
try [HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

### Post by bukwirm on 2007-06-06
Ek0nomik's advice won't work if you don't have GNOME installed already.

Instead, if that's actually your problem, you need to look at your sources.list file (/etc/apt/sources.list).
Comment out the lines that refer to the cdrom.

---

### Post by Ek0nomik on 2007-06-06
> **bukwirm said:**
> Ek0nomik's advice won't work if you don't have GNOME installed already.

Instead, if that's actually your problem, you need to look at your sources.list file (/etc/apt/sources.list).
Comment out the lines that refer to the cdrom.

LOL.  Good point.  :)

I was going to tell him to edit his sources.list too, but I decided most new people prefer the GUI.

---

### Post by abasel on 2007-06-07
Hi, thanks for that, I editted the source lists but that didn't seem to work i.e. I took the comments out.

I'll look at 
HOWTO: Leightweight Gnome - Ubuntu Forums

When I get a chance.

---

### Post by Ek0nomik on 2007-06-07
> **abasel said:**
> Hi, thanks for that, I editted the source lists but that didn't seem to work i.e. I took the comments out.

I'll look at 
HOWTO: Leightweight Gnome - Ubuntu Forums

When I get a chance.

By "comment out" the line, he meant *add* a "#" to the CD/DVD line of the sources file.  This way, when apt scans the list, it will disregard the CD as a source.

After you add the #, update your sources by typing

```
sudo aptitude update
```

then try to install.

---

### Post by abasel on 2007-06-07
I went to [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and used it to crease the following sources.list

deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

I then run sudo apt-get update but get errors i.e. a lot of Hits down the side of the page together with Ign and Err lines

I don't know how to get the logfile from that computer to this windows box so I can't include it in this posting.

---

### Post by Ahab the Eskimo on 2007-06-27
/etc/apt/sources.list
[COLOR="Red"]
Permission Denied[/COLOR]

I got the "couldn't find package" thing too.

Perhaps it'll be a recovery/reinstall fo me.
That or a NAS that can't find the internet.

---

### Post by Seisen on 2007-06-27
> **Ahab the Eskimo said:**
> /etc/apt/sources.list
[COLOR="Red"]
Permission Denied[/COLOR]

I got the "couldn't find package" thing too.

Perhaps it'll be a recovery/reinstall fo me.
That or a NAS that can't find the internet.

Did you add sudo in front of it?

---

