---
title: "[SOLVED] differences between ubuntu and kubuntu (under the hood)"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by gregcoit on 2008-04-14
Hi all,

Other than the WM/Desktop and base applications, are there any differences between Ubuntu and Kubuntu?  Threads I've read so far seem to say they are the same, but wasn't there some differences in the 7.10 releases (like parallelized boot and one used /dev/hd* and the other /dev/sd*)?

Or, am I crazy?

Thanks!

Greg

---

### Post by jw5801 on 2008-04-14
I think you might be crazy! They are identical, same kernel, same version of X, same version of glibc, same basic bootscripts. The only difference is in the graphical interface and some of the default apps there.

---

### Post by aysiu on 2008-04-14
You're crazy. They're the same under the hood - just different default packages and artwork installed.

---

### Post by mgranet on 2008-04-14
> **jw5801 said:**
> I think you might be crazy! They are identical, same kernel, same version of X, same version of glibc, same basic bootscripts. The only difference is in the graphical interface and some of the default apps there.

That's not entirely accurate. There are some things which are different. No bulletproof X in Kubuntu 7.10 for example. That is why the 8.04 release of Kubuntu aims for feature parity with Ubuntu.

---

### Post by cm.squared on 2008-04-14
Also, /dev/sd* and /dev/hd* are the designations of sata and ide drives, respectively, not differences between kubuntu and ubuntu.

---

### Post by jw5801 on 2008-04-14
> **mgranet said:**
> That's not entirely accurate. There are some things which are different. No bulletproof X in Kubuntu 7.10 for example. That is why the 8.04 release of Kubuntu aims for feature parity with Ubuntu.

It's not a different version of X however, simply a difference between kdm and gdm. One could install Kubuntu, then install gdm and use it in place of kdm and have a Kubuntu install with bulletproof X. Thus, they are exactly the same "under the hood."

EDIT: [linky](http://www.bryceharrington.org/drupal/node/38)

---

### Post by gregcoit on 2008-04-14
> **cm.squared said:**
> Also, /dev/sd* and /dev/hd* are the designations of sata and ide drives, respectively, not differences between kubuntu and ubuntu.

Yes, but I think kubuntu sees all ide and sata drives as /dev/sd* now (at least it sees my laptop harddrive as /dev/sda).  And I think this behaviour was different between the 2 at one point (or so a friend of mine swears).

The reason I started this thread is this.  There's a fairly popular idea on brainstorm that suggests that Conical should spend as much time on kubuntu as ubuntu.  And while I'm a kubuntu user, I have no issue with more time being spent on ubuntu than kubuntu as long as kubuntu benefits from the "non-WM/Desktop specific" stuff" (it's all a matter of developer interest and I'm not going to tell some developer to spend more time on kde if he/she is a gnome person).

Thanks for the replies!

---

### Post by Tatty on 2008-04-14
> **gregcoit said:**
> Yes, but I think kubuntu sees all ide and sata drives as /dev/sd* now (at least it sees my laptop harddrive as /dev/sda).  And I think this behaviour was different between the 2 at one point (or so a friend of mine swears).!

Im not an expert on this, but im pretty sure that the naming of devices happens much before even X gets loaded, let alone Gnome or KDE.

Im fairly sure that this is managed by the kernel.

---

### Post by jw5801 on 2008-04-14
> **gregcoit said:**
> Yes, but I think kubuntu sees all ide and sata drives as /dev/sd* now (at least it sees my laptop harddrive as /dev/sda).  And I think this behaviour was different between the 2 at one point (or so a friend of mine swears).

The reason I started this thread is this.  There's a fairly popular idea on brainstorm that suggests that Conical should spend as much time on kubuntu as ubuntu.  And while I'm a kubuntu user, I have no issue with more time being spent on ubuntu than kubuntu as long as kubuntu benefits from the "non-WM/Desktop specific" stuff" (it's all a matter of developer interest and I'm not going to tell some developer to spend more time on kde if he/she is a gnome person).

Thanks for the replies!

I'm not sure what part of the kernel/bootscripts populates /dev/, but I can promise you it's not DE specific! And your friend is crazy :P

---

### Post by gregcoit on 2008-04-14
> **jw5801 said:**
> I'm not sure what part of the kernel/bootscripts populates /dev/, but I can promise you it's not DE specific! And your friend is crazy :P

> Im not an expert on this, but im pretty sure that the naming of devices happens much before even X gets loaded, let alone Gnome or KDE.

Im fairly sure that this is managed by the kernel.

Well, yeah, this has nothing to do with the WM/Desktop, but is it a difference in Ubuntu and Kubuntu?  Is this an indication of a "under the hood" difference between the 2 that would indicate a duplication of effort between the 2 groups of developers?

Greg

---

### Post by jw5801 on 2008-04-14
> **gregcoit said:**
> Well, yeah, this has nothing to do with the WM/Desktop, but is it a difference in Ubuntu and Kubuntu?  Is this an indication of a "under the hood" difference between the 2 that would indicate a duplication of effort between the 2 groups of developers?

Greg

The kernel developers are separate from the GNOME/KDE developers. So what I'm saying is that there would be no reason for this to happen and I don't believe it ever did. It might be a difference between say, Ubuntu Gutsy and Kubuntu Feisty. Or between a fresh Ubuntu and a Kubuntu with a kernel upgrade/alteration. But everything in both come from the same repositories. There aren't "kubuntu repositories" there are just KDE apps in the Ubuntu repositories. So everything under the hood must be identical!

---

### Post by gregcoit on 2008-04-14
> **jw5801 said:**
> But everything in both come from the same repositories. There aren't "kubuntu repositories" there are just KDE apps in the Ubuntu repositories. So everything under the hood must be identical!

That makes perfect sense.  I think you've satisfied my curiosity (and concern) - Thanks!!!

Greg

---

### Post by cm.squared on 2008-04-14
Like joshrobinson said, other than using KDE and gnome and their respective default applications, kubuntu and ubuntu are the same.  KDE and gnome are developed indepedently of ubuntu, and not by Canonical, so its not really a question of them spending more time developing one or the other.  The reason they can offer both is that everything under the hood is the same and just the desktop manager packages are different.

Also, sd* and hd* really do signify sata and ide hard drives.  If you still aren't convinced the following is from the man page of fdisk, the partition table utility.

```
The device is usually one of the following:

    /dev/hda /dev/hdb /dev/sda /dev/sdb 


(/dev/hd[a-h] for IDE disks, /dev/sd[a-p] for SCSI disks, /dev/ed[a-d] for ESDI disks, 
/dev/xd[ab] for XT disks). A device name refers to the entire disk. 
```

---

