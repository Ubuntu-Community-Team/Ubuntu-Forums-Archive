---
title: "xubuntu and virtualbox: how-to?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by dan04 on 2008-04-20
Hi,

I'm trying to install xubuntu as a guest os - using virtualbox - in my win xp machine.

the guide says:
[B]Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions.run[/B]

how to do this in xubuntu?

Hope someone can help.

thanks

---

### Post by LaRoza on 2008-04-20
> **dan04 said:**
> Hi,

I'm trying to install xubuntu as a guest os - using virtualbox - in my win xp machine.

the guide says:
[B]Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions.run[/B]

Hope someone can help.

thanks

What? The VirtualBox installer for Windows is a typical installer.

Go to the download site and get VirtualBox for Windows.

---

### Post by dan04 on 2008-04-20
> **LaRoza said:**
> What? The VirtualBox installer for Windows is a typical installer.

Go to the download site and get VirtualBox for Windows.


LaRoza,

i have already INSTALLED VirtualBox and my problem is installing XUBUNTU inside VirtualBox.

need someone to help install the VBoxAdditions (of VirtualBox) in the Xubuntu guest

---

### Post by vyruss on 2008-04-20
> **dan04 said:**
> LaRoza,

i have already INSTALLED VirtualBox and my problem is installing XUBUNTU inside VirtualBox.

need someone to help install the VBoxAdditions (of VirtualBox) in the Xubuntu guest

Try **Devices -> Install Guest Additions**.

Then when the guest additions image has been mounted, open a terminal in the guest os and type:```
**cd /media/cdrom** (or whatever device name it's mounted as in /media)
**sudo ./VBoxLinuxAdditions.run**
```

---

