---
title: "Download and Create Update Disc"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by sporry on 2007-09-13
Is there a way to download the lastest  updates (to a Windows machine) and burn them to a disc to update another computer with Ubuntu installed?

I only have have dial-up access for the newly installed Ubuntu computer and want an easy way to install the large chunk of first updates.

Thanks in advance.

---

### Post by chuckyp on 2007-09-14
I thnk you are looking for apt-cdrom command in ubuntu.  man apt-cdrom and check it out for info.  The repos are availible at packages.ubuntu.com

You may be able to download the latest daily build of the feisty iso and just use apt-cdrom to update that way.  Unless you are using software that was installed without the cd that should update everything you have.

---

### Post by Irihapeti on 2007-09-14
There's an option in Synaptic to create a package download script for the files you want to install. Although the script wouldn't run on a Windows machine (as far as I know), it does give you a list of URLs which you could then feed into a download manager.

---

### Post by hyper_ch on 2007-09-14
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by sporry on 2007-10-02
I just installed APTonCD. I have the amd64 version of Ubuntu installed on this computer so when I run APTonCD and create an ISO they all end up being amd64 packages.

The problems is that the computer I want to install the repositories on has the i386 version of Ubuntu installed. So is there are way to have this amd64 Ubuntu create an i386 repositories iso disc with APTonCD.

If not, where can I manually download the i386 repositories files?

---

