---
title: "Folder sharing for a newbie"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by wayne_n on 2008-10-27
I hope I'm not asking an old question.  I just got 8.04 up and running on my Mac Pro in VMware Fusion.  I am trying to get it to see folders on my Mac, but no joy.  I created a Shared folder on my desktop and setup the sharing preferences, as would not let me set up sharing of the public folder because I didn't have permission; even thought I am an admin user.  Any input on what I might not be doing right.  I am brand new to Linux.

---

### Post by _mario_ on 2008-10-28
> **wayne_n said:**
> I hope I'm not asking an old question.
Since this sub-forum primarily deals with questions installing Ubuntu natively on a Mac, you might be better off asking in the networking section.
> **wayne_n said:**
> I just got 8.04 up and running on my Mac Pro in VMware Fusion. I am trying to get it to see folders on my Mac, but no joy. 
That means you're trying to access folders shared by OSX from within your Ubuntu installation inside a virtual machine?
> **wayne_n said:**
> I created a Shared folder on my desktop and setup the sharing preferences, as would not let me set up sharing of the public folder because I didn't have permission; even thought I am an admin user.
... which means OSX is complaining about missing permissions. so i cannot help you, as i don't use OSX.
> **wayne_n said:**
> Any input on what I might not be doing right. I am brand new to Linux.
But some more general considerations:
1. This permission problem is most likely the cause.
2. What protocol (AFP?, CIFS?) does OSX use to share?
3. Is the network set up correctly. Your Ubuntu needs to access the host, so a virtual network must be configured appropriately.
4. If so, does OSX block incoming traffic (firewall?).

If I'm understanding the problem correctly, Linux might not be the main problem ...

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-28
> **_mario_ said:**
> Since this sub-forum primarily deals with questions installing Ubuntu natively on a Mac, you might be better off asking in the networking section.
or even the virtualization forum.

---

### Post by wayne_n on 2008-10-28
Mario,

Mac uses AFP typically.  But I don't think it's a network issue, as when using WinXP on Mac VMware Fusion, I just selected the folders to share using VMware and the folders were visible in the virtual machine.  Trying to determine why it isn't the same in Ubuntu.  I am not trying to physically network two computers.  It's a virtual machine.

---

### Post by wayne_n on 2008-10-28
Didn't see the virtualization forum at first.  I'll post it there.

---

### Post by _mario_ on 2008-10-28
> **wayne_n said:**
> Mac uses AFP typically.  But I don't think it's a network issue, as when using WinXP on Mac VMware Fusion, I just selected the folders to share using VMware and the folders were visible in the virtual machine. Trying to determine why it isn't the same in Ubuntu.  I am not trying to physically network two computers. It's a virtual machine.
you didn't mention VMware's shared folder feature in your first post...
that's the point. for this to work you'll have to install VMware's guest tools. I don't know whether they are also available for linux. otherwise you can set up a virtual (!) network in VMware (e.g., type host-only) and share folders using OSX. (which means other machines connected to your host may also access these shares, unless properly secured.)

ciao,
Mario

---

### Post by wayne_n on 2008-10-28
Sorry I left out the information you stated.  I already have the VMware Tools installed for Linux.  I will probably have to get with VMware support for an answer.  But, I will look into the virtual network.  My network is tied down fairly well, so it shouldn't be an option.

---

### Post by ronocdh on 2008-10-29
> **wayne_n said:**
> Mario,

Mac uses AFP typically.  But I don't think it's a network issue, as when using WinXP on Mac VMware Fusion, I just selected the folders to share using VMware and the folders were visible in the virtual machine.  Trying to determine why it isn't the same in Ubuntu.  I am not trying to physically network two computers.  It's a virtual machine.
Rather trivial to set up Samba in OSX, actually... I use Samba for networking between WinXP, OSX, and Ubuntu.

Also, are we sure OP wasn't referring to accessing the OSX partition on the same machine? If that's the case, then just disable journaling in the OSX partition and, if you want, edit the permissions on your home folder to be viewable by others (be very careful with this!).

---

### Post by cyberdork33 on 2008-10-29
> **ronocdh said:**
> Also, are we sure OP wasn't referring to accessing the OSX partition on the same machine? If that's the case, then just disable journaling in the OSX partition and, if you want, edit the permissions on your home folder to be viewable by others (be very careful with this!).
Can you access physical hard drive partitions from within a VM?

---

