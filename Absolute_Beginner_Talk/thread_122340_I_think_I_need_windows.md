---
title: "I think I need windows"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by apette on 2006-01-27
A month ago I formatted my computer and installed ubuntu on it. As times go, I realise that I need certain windows application - that don't run under wine. Therefore I want to install windows again to be able to use those applications. My harddrive only has one partition - the one ubuntu is using. My question is therefore, is there an easy way to make another parition which I can install windows on, or do I have to reformat all over again?

---

### Post by xmastree on 2006-01-27
The first thing to ask youself is, "is there a linux equivalent to the applications you need?"

What are they?

---

### Post by chimera on 2006-01-27
Is there any free, unpartitioned space on your disc? If so, windows should be able to install on it without messing up your ubuntu partition.

However if you can tell us the name of the application you need, maybe we could see if there is a similar application for Linux.

---

### Post by xmastree on 2006-01-27
[QUOTE=chimera]windows should be able to install on it without messing up your ubuntu partition.[/QUOTE]I suspect it'll have a problem with the boot sector though...
For dual-boot systems it's always best to install windows first.

---

### Post by Chris Tucker on 2006-01-27
[QUOTE=xmastree]I suspect it'll have a problem with the boot sector though...
For dual-boot systems it's always best to install windows first.[/QUOTE]

just need to get a livecd and install grub again after...

---

### Post by earobinson on 2006-01-27
what apps, it can be a bit of a pain to install windows after but chris is correct all you need is a live cd.

---

### Post by dsierpin on 2006-01-27
Getting Windows on there shouldn't be too tough at all.  You could either run gparted from the Ubuntu live CD, or (my preference), download and burn the gparted live CD ISO [here]("http://gparted.sourceforge.net/livecd.php").  Resize your Ubuntu partition to make room for Windows, and you'll be ready to go.  You might want to also make a swap partition and a FAT32 partition to share files between Ubuntu and Windows while you're at it.

The problem will be booting back into Ubuntu once you've installed Windows, since I imagine that the windows install will overwrite grub in the master boot record and won't give you the option to boot into other operating systems.  That's why it's always better to install Windows first, like xmastree pointed out.    You could solve this I think by installing grub again from the live CD, but I'm not sure of the exact steps involved.  Someone with a bit more know how might chime in here.

---

### Post by HJThis on 2006-01-27
Hello,To all

Hmm other then a Trojan scanner or Spyware scanner
i can't think of any item from Windows that i can't download
& install on my Ubuntu

Best of luck

---

### Post by apette on 2006-01-28
The applications that I need to run in Windows:
LabView (which excists in a linux version, but my job only has site licence for windows and you often encounters problemt when cross-using the two versions)
EES (which I might be able to run with Wine, but might be unstable)
Origin (which I can't run with Wine, hence need full windows)
A billing software (which I need for my small company, and I can't find any helpful linux software)

Therefore, I have to install Windows.

---

### Post by coolclassic on 2006-01-28
On Origin web site thay do have a forum for linux users:

[http://www.originlab.com/forum/forum.asp?FORUM_ID=6](http://www.originlab.com/forum/forum.asp?FORUM_ID=6)

---

### Post by coolclassic on 2006-01-28
And again info on using EES with linux on there web site:

[http://www.fchart.com/ees/eeslinux.shtml](http://www.fchart.com/ees/eeslinux.shtml)

---

### Post by mips on 2006-01-28
apette,

Another option is to run windows from within a virtual machine via ubuntu. You can use VMPlayer for that. That way you dont have to dual boot and can access both win & linux at the same time.

[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)

You'll ahve to adapt the wiki slightly, just changing a few names. You'll also ahve to create a ISO image off the windows install disk but the procedure is identicall to the one for Dapper installation above.

Pretty painless, I did this yesterday for Dapper and no reason why you cant use it for windows or any other os for that matter.

It's pretty fast as well, I was amazed.

---

