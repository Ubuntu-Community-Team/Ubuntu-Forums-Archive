---
title: "HeLp!"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-08-13
help.ubuntu.com/community/windowsdualboot

is this for real or does the new one do it easier?

---

### Post by aysiu on 2006-08-13
It's case-sensitive, actually:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

You may find these guides more to your liking:

**Desktop CD**
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

**Alternate CD**
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by kebes on 2006-08-13
I think that link should read:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

What is your question, exactly? Dual-booting with windows is possible and is quite easy with the current version of Ubuntu. The best way is to install windows first (but don't use the entire drive space), and install Ubuntu second.

If windows is already installed, do what the guide suggests: defrag your windows drive, then resize it during the Ubuntu installation.

Does that answer your question?

---

### Post by sean_ on 2006-08-13
> **kebes said:**
> I think that link should read:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

What is your question, exactly? Dual-booting with windows is possible and is quite easy with the current version of Ubuntu. The best way is to install windows first (but don't use the entire drive space), and install Ubuntu second.

If windows is already installed, do what the guide suggests: defrag your windows drive, then resize it during the Ubuntu installation.

Does that answer your question? No, forget about Defragging. Grab Partition Magic 8, by buying it or well, I'm sure you know what other way you can grab it. You can resize your hda1 without defragging.

Please note after you finish resizing HDA1, do not put in your ubuntu disc after finishing resizing, please run Windows and windows will automatically resize it. After you reboot from windows resizing it, put in your Ubuntu disc.

---

### Post by kebes on 2006-08-13
> **sean_ said:**
> No, forget about Defragging. Grab Partition Magic 8

Is there any reason to use Partition Magic when GParted is free and included on the Ubuntu install CD? GParted allows for resizing partitions. (And you don't have to defrag them first--although it doesn't hurt.)

---

### Post by sean_ on 2006-08-13
> **kebes said:**
> Is there any reason to use Partition Magic when GParted is free and included on the Ubuntu install CD? GParted allows for resizing partitions. (And you don't have to defrag them first--although it doesn't hurt.) Uhhh.. you can't resize your hda1 on linux, afaik without installing ubuntu.

---

### Post by kebes on 2006-08-13
> **sean_ said:**
> Uhhh.. you can't resize your hda1 on linux, afaik without installing ubuntu.

When you boot off of the Ubuntu 6.06 CD, you get into a LiveCD environment. As far as I know, GParted is available in that environment. If you start the graphical install process and select "manually partition" you enter GParted and have the option to format, move, and resize partitions. Resizing of NTFS partitions is supported. (I have never personally used GParted to resize an NTFS partition... which is why I asked that question:  I was wondering if there was some reason to avoid GParted.)

---

### Post by RRS on 2006-08-13
Gparted works quite well.

You can also run it from the live cd without going into the installation process. It's under System>Administration and sometimes works better to set up your partitions ahead of time.

---

