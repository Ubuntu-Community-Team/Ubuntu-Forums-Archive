---
title: "Best option for Multiple Linux OS' on one computer"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by U2XS on 2007-11-26
I've been looking around and after trying Ubuntu, I am very curious to try Linux Mint, Mandriva, Red Hat, Polar Bear and a few others that caught my eye.

I originally thought of making 10 partitions, but I'm told that it is a messy process and that I'm better off emulating one OS within Ubuntu.  Is this really the best option?  If so, how do I do this?  Thanks

---

### Post by bluepowder7 on 2007-11-26
ten?!?!?  sweet jesus.  and i thought i was nuts to set up my partitions for six.  and, i'm still using just one of those six.  have yet to install PCLinuxOS, Sabayon, Slackware, and FreeBSD.  that's five.  i left one spot free for god knows what.  maybe a DOS spinoff of some kind.

---

### Post by Inxsible on 2007-11-26
I would much rather use the Live CDs of those distros and see if I like the look and feel of it before installing it on the drive.

Also, once you decide you want to install, installing it separately would be the way to go. At least, that's what I'd do.

IMHO, No matter how many OS'es you have on you machine, you (more often than not) end up using only one of them all. I love Ubuntu, so I do not think, I will use anything else on this machine. But yeah, on some older machine, I might just give some other distro a go !

---

### Post by patchido on 2007-11-26
> **U2XS said:**
> I've been looking around and after trying Ubuntu, I am very curious to try Linux Mint, Mandriva, Red Hat, Polar Bear and a few others that caught my eye.

I originally thought of making 10 partitions, but I'm told that it is a messy process and that I'm better off emulating one OS within Ubuntu.  Is this really the best option?  If so, how do I do this?  Thanks

it might be expensive but get 1 external drive for each OS or 1 external for each 3 OS

---

### Post by timcredible on 2007-11-26
you can do that if you want, but it might be easier to use a virtual machine for each of these.  virtualbox is probably the leading virtual machine software, give it a try.  I'm discounting vmware here because it's not open source.

---

### Post by U2XS on 2007-11-26
Thats great!  Each of you gave very different but practical solutions.  This is why I love Ubuntu :)  So many options

**bluepowder7**
10 was just a thought.  So you partitioned the drive into 6?  Do you have problems with the GRUB?

**Inxsible**
Sometimes the best answers are the most practical.  I'm better off trying the Live version of the distributions before I install, but I would like to get some in-depth knowledge, so I will probably install.

**patchido**
That would be a cool solution, but its a hard expense to justify to myself.

**timcredible**
I'll probably do this if I am on the fence about installing or not.

---

### Post by bluepowder7 on 2007-11-26
well, my laptop currently has....  (checks)....  12 partitions.  well, 13 if you include the extended one that houses a few of the logical ones.  but, so far, i only have one OS installed, and grub has no problems at all.

here's how my partitions look (clickable thumbnail):
sda3 is where i store all my documents, downloads, etc
the rest you can tell by the mountpoint field (blank ones are unused for now, reserved for other OSes)

[[IMG]http://i106.photobucket.com/albums/m244/GregR7/th_bp7_laptop_partitions.jpg[/IMG]](http://i106.photobucket.com/albums/m244/GregR7/bp7_laptop_partitions.jpg)

---

### Post by bodhi.zazen on 2007-11-26
> **U2XS said:**
> I've been looking around and after trying Ubuntu, I am very curious to try Linux Mint, Mandriva, Red Hat, Polar Bear and a few others that caught my eye.

I originally thought of making 10 partitions, but I'm told that it is a messy process and that I'm better off emulating one OS within Ubuntu.  Is this really the best option?  If so, how do I do this?  Thanks

Why stop at 10 ? I have 24 (10 are virtual). And I install an OS in OpenVZ in a matter of minutes, 2 minutes top.

The best way to handle multiple os, IMO, is to install grub into both the MBR AND the root partition of each distro. Then chainload. 

This way you do not need to update /grub/menu.list each time you upgrade to a new kernel on each and every distro.

---

### Post by anaconda on 2007-11-26
You might want to try also DamnSmallLinux.. 

It is amazingly fast when loaded completely to RAM.. and one 60MB partition would be enough..

---

### Post by theharshone on 2007-11-26
You should really chose distros that meet ur needs. I've heard good things about mandriva 2008 and linux mint. I myself really like mandriva and kubuntu. But really, it all depends on ur use.  It would be wise to emulate with virtual box to see if u like the feel of the distro. There are many things to take into account like the DE and load time. Have you heard of gOS? Its ubuntu 7.10 with e17. [gOS website]("http://www.thinkgos.com") All in all, happy testing!

---

### Post by louieb on 2007-11-26
> **U2XS said:**
> ...I originally thought of making 10 partitions..

> **bodhi.zazen said:**
> Why stop at 10 ? ...The best way to handle multiple os, IMO, is to install grub into both the MBR AND the root partition of each distro. Then chainload. ...

Lots of partitions, installing Grub to the root partition, and chain loading. Thats the way I did it before more or less  settling on Ubuntu. 

Gives you a lot of flexibility   and its a great time waste to  see the distros come and go.

---

### Post by master_kernel on 2007-11-26
You would probably be best off installing them into a VM (VirtualBox, qEmu, Java VM...). They don't require much space (maybe 2-3G apiece for an average distro) and are easily accessable.

---

