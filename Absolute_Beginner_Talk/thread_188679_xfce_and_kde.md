---
title: "xfce and kde"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-04
i am just a little more than a newbie.
i have dapper ubuntu installed.
i would like to add kde and xfce too.
unfortunately due to problems that i have not been able to identify for a long time i have never been able to get apt going in my pc.
this is true across other debian based distroes too.
how can i add xfce or kde?
can i add them from kubuntu or xubuntu cd? i can get them.

tv

---

### Post by aysiu on 2006-06-04
You can add them from the Xubuntu and Kubuntu CDs or the internet... but you're going to have to use apt-get, Synaptic, aptitude, or Adept.

When you say you can't get apt *going*, what exactly do you mean? What happens when you type ```
sudo aptitude update
``` for example?

---

### Post by drtvasudevan on 2006-06-04
usually connection time out.
reading packagge list done
building dependacy tree.. done
building tag data base...done
err http:// blah blah......could not connect to ...... connection timed out

so on for other servers.

i have a adsl 256 kbps connection.
usually good enough. i get minimum >200

tv

---

### Post by drtvasudevan on 2006-06-04
[QUOTE=aysiu]You can add them from the Xubuntu and Kubuntu CDs or the internet... but you're going to have to use apt-get, Synaptic, aptitude, or Adept.
...
[/QUOTE]

how?
tv

---

### Post by aysiu on 2006-06-04
Connection timed out. Sounds as if you have some kind of weird internet proxy issue. I don't know how to resolve those, but if you search around, there are threads about it (other users whose update timed out with the online repositories).

To install from CD, you need the alternate CDs (not the desktop ones). Go to System > Administration > Synaptic Package Manager > Edit > Add CD-ROM. Put in the CD.

Go to Settings > Repositories and uncheck all the boxes except the CD source you just added.

Close Synaptic.

In the terminal, type ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Do the same procedure for Kubuntu (using *kubuntu-desktop*).

---

### Post by Rackerz on 2006-06-04
If I removed the xubuntu-desktop, would it get rid of all of XFCE's applications from my Gnome menus?

---

### Post by aysiu on 2006-06-04
[QUOTE=Rackerz]If I removed the xubuntu-desktop, would it get rid of all of XFCE's applications from my Gnome menus?[/QUOTE] It should... but you can also just get rid of them by editing the Gnome menus themselves--removing an entire desktop environment seems a bit extreme.

By the way, you can remove Xubuntu easily (*sudo aptitude remove xubuntu-desktop*) if you installed it the way I asked you to.

If you installed it with *apt-get* or Synaptic, it'll be a bit more difficult to remove.

---

### Post by drtvasudevan on 2006-06-05
by some quirky stuff my firefox wont connect till i search for ipv6 setting in about:config and diable it.
can that affect apt?

tv

---

### Post by drtvasudevan on 2006-06-05
thanks.
installed kde desktop in the manner indicated.
no hitches.
xubuntu cd was not the alternate cd. so could not install that too.

tv

---

### Post by carlosqueso on 2006-06-05
[QUOTE=Rackerz]If I removed the xubuntu-desktop, would it get rid of all of XFCE's applications from my Gnome menus?[/QUOTE]
nope...it's just a meta-package just like ubuntu-desktop...it'll do nothing.

---

### Post by aysiu on 2006-06-05
[QUOTE=carlosqueso]nope...it's just a meta-package just like ubuntu-desktop...it'll do nothing.[/QUOTE] unless you installed it with this command: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` and then removed it with this command: ```
sudo aptitude remove xubuntu-desktop
```

---

### Post by carlosqueso on 2006-06-05
need delete post button....

---

### Post by drtvasudevan on 2006-06-09
initially i had installed ubuntu from desktop live cd and did a kde installation.
today i planned to install all three in another partition.
got hold od alternative cd of all three.
did ubntu first.
while installing kubuntu-desktop there was a dependancy missing (libcriv...something ) and had to install that from ubuntu again.
then the process exited to prompt after unpacking kubuntu desktop saying segmentation fault.
i gave the sudo install kubuntu-desltop command again and now it exited to prompt without saying the job is done.
after giving a third command of the same line it finished.

same happened o xubuntu also except the dependancy.

but the desktops have been installed and functiong... at least kubuntu does, i have not checked xubuntu yet.
i am still in kubuntu desktop.

any lights?

tv

[QUOTE=aysiu].....
To install from CD, you need the alternate CDs (not the desktop ones). Go to System > Administration > Synaptic Package Manager > Edit > Add CD-ROM. Put in the CD.

Go to Settings > Repositories and uncheck all the boxes except the CD source you just added.

Close Synaptic.

In the terminal, type ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Do the same procedure for Kubuntu (using *kubuntu-desktop*).[/QUOTE]

---

