---
title: "problems with amule"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mrsdeath on 2006-10-24
Hi!!

I finally found my way to crate a new thread. Ok, so what happened to me was that I had to uninstall my amule because it wouldn't work properly, and now i want to reinstall it but it looks like it doesn't want to come back. I use ubuntu 5.0.4

can anyone please help me?

thanx a lot!

---

### Post by meng on 2006-10-24
I assume you're installing like this:
sudo apt-get install amule
please post the error message (again)

---

### Post by mrsdeath on 2006-10-24
Depends: libc6 (>= 2.3.2.ds1-21) but it will be installed 2.3.2.ds1-20ubuntu15
Depends: libwxbase2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1
Depends: libwxgtk2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1

I did it with apt-get without sudo

---

### Post by meng on 2006-10-24
Try this:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amule

(3 separate commands, entered one at a time)

---

### Post by mrsdeath on 2006-10-24
[QUOTE=mrsdeath;1658883]Depends: libc6 (>= 2.3.2.ds1-21) but it will be installed 2.3.2.ds1-20ubuntu15
Depends: libwxbase2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1
Depends: libwxgtk2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1

I did it with apt-get without sudo. However, I have just tried to do the same using the sudo command, but the same error appears

---

### Post by mrsdeath on 2006-10-24
I did sudo apt-get update but now I get this message:  GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
 What can I do?

---

### Post by meng on 2006-10-24
That GPG error should not be a problem, it just indicates that the packages are not authenticated by the correct GPG key. You can override this when it asks you later if it is okay to install/upgrade unverified packages (just say yes).

I imagine some of your problems are due to the hoary repositories no longer being updated. If you are able to upgrade to a newer version of Ubuntu, some of these problems may be solved.

---

### Post by mrsdeath on 2006-10-24
The problem is that when I try to upgrade to a new version it downloads the pakages but then it can't install them because of this error. It also happens with synaptic.

---

### Post by meng on 2006-10-24
Have you run the other two commands?
sudo apt-get upgrade
sudo apt-get install amule

otherwise try
sudo apt-get -f install amule

---

### Post by mrsdeath on 2006-10-24
It says broken packages. No way to upgrade, two packages not installed. Ubuntu doesn't love me anymore :(

---

### Post by meng on 2006-10-24
They are all the tricks I know, I thought that including "-f" should fix broken packages.

---

### Post by mrsdeath on 2006-10-24
Ok, don't worry. Do you think that updating from a cd would delete all my information? Does ubuntu have the option of upgrade instead of install?

---

### Post by meng on 2006-10-24
Installing a new version of Ubuntu from CD would overwrite your data, unless you had been keeping it on a separate (/home) partition. There is an upgrade option, but upgrading from one version to another has been associated with problems in the past, if you're lucky it may just break the xserver temporarily (which can be fixed with the command sudo dpkg-reconfigure xserver-xorg) but if you're unlucky, it may be more problematic than that.

I can't really remember back as far as version 5.04, so what I say may not be entirely accurate.

---

### Post by mrsdeath on 2006-10-25
Thanks for everything. I have everything in my patition /home, so I hope there won't be any problems. Anyway, I'll backup everything on dvds so that I lose nothing when I upgrade to a new version, which will be 6.0.6. I've seen this new version work, and I like it! The only thing I really miss there is the Root Terminal.

---

