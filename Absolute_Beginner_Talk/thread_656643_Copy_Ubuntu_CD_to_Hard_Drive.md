---
title: "Copy Ubuntu CD to Hard Drive?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by robertlankford on 2008-01-02
I installed Ubuntu 7.10 from a live CD onto my computer.  Sometimes, when I add/remove software from the package manager, Ubuntu prompts me for the install disk.  This is fine, I guess, since it presumably saves bandwidth for someone's servers somewhere (I'm all for that).  But what I'd really like to do is cache the entire CD contents to my hard disk so that Ubuntu will pull the files it needs from that local copy instead of asking me for my disk.  Is this possible?

Thanks in advance...

---

### Post by philinux on 2008-01-02
Maybe you installed without internet access.

You need to goto

System>Admin>Software Sources.

Untick the cd and tick the main multiverse repo's etc.

Otherwise you wont get important security updates.

---

### Post by ~LoKe on 2008-01-02
Possible, yes, but necessary?  Absolutely not.

I believe the installer leaves the cdrom repository for users without internet access.  Just do this:
```
gksu gedit /etc/apt/sources.list
```
And look for the line at the top that says something along the lines of deb cdrom and remove it.

---

### Post by Saint Angeles on 2008-01-02
well if you go to synaptic package manager and settings->repositories, you can un-check the CDROM from your sources and you will never have that problem.

as for copying it, ive never tried. basically its your repoistory list that tells ubuntu where to install packages from... so maybe its possible to setup some kind of source line under third party sources pointing towards files on your own drive.

has anybody done this?

---

### Post by robertlankford on 2008-01-02
Thanks everyone for the quick replies!  I hadn't realized that it was this easy to configure.

:)

---

### Post by shad0w_walker on 2008-01-02
You can disable the system asking for the disc by going to  System > Administration > Software sources

There will either be a tab labeled CDROM or a section somewhere on the starting tab that lets you choose to disable the CDROM. After you do this you just need to do a update (In synaptic, aptitude, whatever) and you are good to go.

---

### Post by g2g591 on 2008-01-02
I'd have to go with loke, but instead of removing the line totally, just put a # infront of it

---

