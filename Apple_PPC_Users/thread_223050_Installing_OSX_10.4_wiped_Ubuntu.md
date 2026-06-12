---
title: "Installing OSX 10.4 wiped Ubuntu"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by llamakc on 2006-07-25
My buddy installed OSX 10.4 and now doesn't get the yaboot prompt. He claims that osx only installed on the existing osx partition, and not over the entire disk.

What steps should I suggest he take to get yaboot back up and running?

---

### Post by AlphaMack on 2006-07-25
sudo ybin from Ubuntu.

---

### Post by llamakc on 2006-07-25
> **alphasubzero949 said:**
> sudo ybin from Ubuntu.

I'm familiar with livecd's and with running ybin (the laptop was mine before his). You're saying to run the livecd and issue ybin with the correct flags to the root partition as defined in /etc/yaboot.conf, right?

---

### Post by llamakc on 2006-07-25
I'm interested in a solution for this.

---

### Post by robino on 2006-07-26
Hi, please refer to this post for howto solve your boot-up issue:

 [intall osx after install ubuntu.yaboot not run:(]("http://ubuntuforums.org/showthread.php?t=210639")

---

### Post by llamakc on 2006-07-26
Thanks much.

---

### Post by aimislame15 on 2006-07-26
>  He claims that osx only installed on the existing osx partition, and not over the entire disk.

I'm afraid that it isn't possible to install OS X over a linux partition. One of the things that many people learned when installing linux is that if you're doing dual boot, you must have OS X installed first on the hard drive. OSX does not allow for installation alongside another OS.

P.S. At least, that's how it used to be... I doubt Apple changed their ways about it.

-Eric

---

### Post by robino on 2006-07-26
> **aimislame15 said:**
>  OSX does not allow for installation alongside another OS.

Of course it does. You can easily 1st install Linux & then OSX on a different partition. Best thing though is to leave these disk-space free or partition it as HFSplus when paritioning your harddrive and installing Linux.

However, after installing OSX, it will set itself as default start up disk. This means yaboot will be overridden, but not to worry. U can very easily change this back again & have dualboot with yaboot.

For directions, please follow the thread I linked to in the above posting. This is how I have restored yaboot multiple times, for example after doing an upgrade of OSX.

The only critical thing is that you should avoid repartitioning your drives through OSX after you installed Linux and or other OS's, since repartitioning through OSX is very likely to **** up all your drives completely & u will end up reinstalling it all.

---

### Post by aimislame15 on 2006-07-26
Sorry then, disregard my post. When I tried installing Ubuntu before OS X on my iBook, OS X wouldn't allow an installation because an operating system already existed (even though there was a clean second partition...)

---

