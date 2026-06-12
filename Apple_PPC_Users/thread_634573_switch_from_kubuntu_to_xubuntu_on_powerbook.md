---
title: "switch from kubuntu to xubuntu on powerbook?"
date: 2007-12-07
forum: Apple PPC Users
---

### Post by driven1 on 2007-12-07
I would like ot try out xubuntu on my powerbook. I am currently running kubuntu in a dual boot. Do I need to wipe out kubuntu and start over or is there an easier to run xubuntu? Thanks

---

### Post by atlfalcons866 on 2007-12-07
you dont need to wipe kubuntu. do this in terminal
> sudo apt-get install xubuntu-desktop

---

### Post by driven1 on 2007-12-11
Well, I was able to install the xubuntu-desktop but couldn't get the session to start in anything other than KDE. Then I started having problems with the KDE desktop crashing. Fortunately I had most of my data backed up (nothing critical here yet anyway). I ended up doing a fresh install of xubuntu. Other than the documented busybox issue on the first boot, everything going as expected. It is a pain to go back and find all of the multimedia codec:( C'est la vie

---

### Post by driven1 on 2007-12-19
OK so now I'm running Xubuntu and I installed the ubuntu-desktop too, but I can't figure out how to get my powerbook to boot with ubuntu instead of xubuntu. I heard that this isn't too difficult, but I can't figure out where to switch it. Thanks.

---

### Post by luisito on 2007-12-20
If you have installed xubuntu-desktop and ubuntu-desktop together, there is still only one operating system. So whenever you boot, the only kernel you have will boot (until you install newer kernels, but that's a different story). The same thing happens if you install kubuntu-desktop, edubuntu-desktop, mythbuntu, and every "buntu" you can find around. Essentially, you have only one linux, and every desktop you install adds a collection of software to it. Now, if you want to switch between xfce, gnome or kde, you have to select your session in the login screen (in xdm, gdm or kdm).

---

### Post by ubuntubrian on 2007-12-20
Ditto, you choose the window manager, xfce, kde, gnome, etc., in the log in window. You do log in don't you?

---

### Post by driven1 on 2007-12-21
yes, I do log in. I was unfamiliar with the whole session concept. I found the selection. Thanks for all the help.

---

