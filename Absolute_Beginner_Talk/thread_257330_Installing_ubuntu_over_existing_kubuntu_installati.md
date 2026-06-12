---
title: "Installing ubuntu over existing kubuntu installation using ubuntu live cd"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-14
hi,

 i have a kubuntu installation in my system i want to test the ubuntu too...is there any method to install the ubuntu-desktop to the existing installation using the UBUNTU LIVE CD???

---

### Post by bulldog on 2006-09-14
Just use synaptic or aptitude or apt-get.

Not the live cd because you will loose your existing install.

If I remeber it correct,but I'm not sure about it,

sudo aptitude install ubuntu-desktop 

should do it.

When you login screen appears you can make the choice between Ubuntu and Kubuntu.

---

### Post by kurian on 2006-09-16
but i have done all sorts of things like that but iam unable to obtaing the ubuntu packages from the Ubuntu live cd is it because we cant retreive the packages from a live cd????

---

### Post by aysiu on 2006-09-16
The only packages on the **Desktop CD** (or live CD) are *build-essential* and *ndiswrapper*.

If you want to install Ubuntu on top of Kubuntu, you need either an internet connection ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` or the **Alternate CD** ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by dmpo5450 on 2006-09-16
I've only been using ubuntu for less than a month and wanted to try the different versions.  All I had to do was use synaptic and install the files.  It gave me the choice at logon as to which desktop to use.

---

### Post by kurian on 2006-09-17
hi , Is there any method by which we can convert a live cd to an alternate cd..........??? I do not have a larger bandwidth internet connection....

---

### Post by quordandis on 2006-09-23
> **bulldog said:**
> Just use synaptic or aptitude or apt-get.

Not the live cd because you will loose your existing install.

If I remeber it correct,but I'm not sure about it,

sudo aptitude install ubuntu-desktop 

should do it.

When you login screen appears you can make the choice between Ubuntu and Kubuntu.

Hi,

I tried doing this because I have a kubuntu installation and I don't like it and I wanted to switch it over to an ubuntu one. However, when I ran the "sudo aptitude install ubuntu-desktop" command in a console terminal, this is what I got:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find package "ubuntu-desktop".  However, the following
packages contain "ubuntu-desktop" in their name:
  kubuntu-desktop
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Any suggestions?

--Q

---

### Post by aysiu on 2006-09-23
What's in your /etc/apt/sources.list? Post the output of this command: ```
cat /etc/apt/sources.list
```

Do you have a high-speed internet connection or a Ubuntu **Alternate CD**?

---

