---
title: "upgrading to feisty when available"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-23
I'm moving my windoze to a seperate hd and will want to upgrade 6.10 to feisty when it becomes available. i will be basically reformatting a whole hd with windoze and 6.10 on it already with the new distro. do i download/burn the iso and go thru the install from the beginning or what is the best way to do this.

---

### Post by bodhi.zazen on 2007-03-23
Not sure what you are asking exactly ...

Partition your HD ...

Install windows, if needed ...

Download Edgy, burn to cd, install Edgy ...

When Feisty becomes available it appears you will be able to upgrade Edgy to Feisty, although IMO, easier to make a /home or /data partition and do a fresh install of Feisty ;p

---

### Post by newbie59 on 2007-03-23
thats what i wanted to know. if i do a fresh install on a hd with 6.10 on it, wil it retain any of the packages i've installed on there or will i have to re-install packages and basically start from scratch

---

### Post by zvacet on 2007-03-23
I belive Feisty will be upgradable like other previous versions.You can upgrade via network or download alternate CD and upgrade from it.I think second option is better because that way you allways have CD(reinstall,give it to your friends,change desktop...).But it is just my opinion.

---

### Post by macogw on 2007-03-23
A fresh install will not save your installed files or your data.  If you want to keep your data, make a /home partition for it.  If you want to keep your installed stuff, just wait til your updates appear on April 19 with a "perform distribution upgrade" button, and it should go as smooth as butter, and probably take about 2 hours as it downloads everything.

---

### Post by bodhi.zazen on 2007-03-23
> **newbie59 said:**
> thats what i wanted to know. if i do a fresh install on a hd with 6.10 on it, wil it retain any of the packages i've installed on there or will i have to re-install packages and basically start from scratch

Well, if you do a fresh install you will be starting from scratch and would need to re-install any packages you had installed beyond the base system. 

Upgrading would retain your installed packages.

It appears actually that the preferred method of upgrading will be to use "Update Manager" which should notify you once Feisty is available and ask if you wish to upgrade. There are other methods, as suggested by zvacet, but currently update manager is the preferred method of updating and is advertised as being the most reliable method.

Both Feisty and Edgy will be supported for 18 months form the time of release.

---

### Post by newbie59 on 2007-03-23
"A fresh install will not save your installed files or your data. If you want to keep your data, make a /home partition for it. If you want to keep your installed stuff, just wait til your updates appear on April 19 with a "perform distribution upgrade" button, and it should go as smooth as butter, and probably take about 2 hours as it downloads everything."

now i want to basically overwrite windows with feisty for the whole hd. will this do that??

---

### Post by bodhi.zazen on 2007-03-23
When you install Edgy or Feisty, if you want, you can overwrite windows.

If you install Edgy along side windows (dual boot) upgrading to Feisty will not over write windows.

If you currently dual boot and you want to remove windows, use gparted (it is on the desktop or live cd) to delete your windows partition and then re-size your Ubuntu(edgy or feisty) partition to occupy the entire HD.

---

### Post by newbie59 on 2007-03-23
thats what i needed to know :guitar:

thank you for your help everyone

---

### Post by newbie59 on 2007-03-23
i can tell i need to give much more info in the beginning about what i'm wanting to do
thank you for being patient with the newbie

---

### Post by bodhi.zazen on 2007-03-23
No Problem.

I forgot to mention, if you remove your windows partition as I discussed in my last post you will need to update /etc/fstab and /boot/grub/menu.lst with the new partition information.

You should either ask or learn how to do this before you manage your partitions.

---

