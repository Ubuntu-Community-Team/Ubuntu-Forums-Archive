---
title: "Two issues"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by dodgerwv on 2007-06-19
I work in a small college athletic office with two older computers.  I've had only two small issues in the conversion to Ubuntu.  The first is that I've got an older Dell that works great once it's booted, but it takes forever to boot up.  Any ideas on how to speed that up.

The second issue may not be for this forum.  I love the open source programs, but have two programs that I don't have a workaround for because they're job-specific.  VirtualBox does a fine job in running those, but I can't get my USB thumbdrive to work in VirtualBox.  I need to be able to move data over into those with it.

Thanks to the forum for answering a couple of my other issues in getting started.  We've been able to salvage a couple of older computers and getting great performance out of them.

---

### Post by p_quarles on 2007-06-19
You should be able to get better response times by installing Xubuntu. That's a version of Ubuntu that runs the lightweight Xfce window manager. 

I've never used Virtualbox, though, so I can't help with that.

---

### Post by starcraft.man on 2007-06-19
> **dodgerwv said:**
> I work in a small college athletic office with two older computers.  I've had only two small issues in the conversion to Ubuntu.  The first is that I've got an older Dell that works great once it's booted, but it takes forever to boot up.  Any ideas on how to speed that up.


Agreed with p. Xfce and enlightenment are great for older hardware. I am curious though... slow boot up doesn't seem to be something that should be tied to the DM used. Does it go through a fschk? Are there errors? Anything in particular that stands out during the boot? Or does it just take a long time at the orange bar?

One way to figure out is to install "bootchart" its in the repos. Install it and then restart your machine, the boot chart program will monitor your boot up and show how long services took to start. We can then see if one in particular is giving trouble. I forgot the directory it outputs to, someone else remember?

> The second issue may not be for this forum.  I love the open source programs, but have two programs that I don't have a workaround for because they're job-specific.  VirtualBox does a fine job in running those, but I can't get my USB thumbdrive to work in VirtualBox.  I need to be able to move data over into those with it.

Easy fix, use shared folder. Open up the main manager, click on the VM, then settings. Go to the shared folder tab, then push the browse button and target the folder or drive you want to share on the Host OS.

Now I'm gonna blow your mind... boot into the XP VM and go start > Run > cmd.exe (Gasp, its a command line :p).

```
net use x: \\vboxsvr\sharename
```

Thats the command you want, it will mount the folder to a network attached drive in the explorer of XP. Replace *sharename* with actual name of the folder/partition you put into the shared folder settings. 

That will do it :). And yes, they are the ones doing the slashes backwards...

---

