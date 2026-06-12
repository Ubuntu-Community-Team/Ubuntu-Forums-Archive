---
title: "Why is anything to do with network on linux so hard? gaah!"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2007-11-26
i am begining to get really fed up with this...

on windows, it is all so easy, my main problem on linux is backing up.

on windows, you just install software, select where to backup from, and where to, and it does it! (i want to back up to a networked drive).
but doing such a thing on linux is IMPOSSIBLE! for a start, you cant see the network when you select where to backup to (or even when you are just trying to open a file in open office etc). When you type in smb://, it doesn't let you, or it complains about something or other..... it just doesn't make sense!

even something simple, like changing the location of my music library on banshee to something on the networked drive is not possible - it just wont let me do it! this is so annoyng....

so. help required or i am seriously thinking of just quitting.

p.s. i'm sure there [I]is[I] a way, but it is so much simpler on windows. :confused:

---

### Post by PeterJS on 2007-11-26
> **benji.ijneb said:**
> i am begining to get really fed up with this...

on windows, it is all so easy, my main problem on linux is backing up.

on windows, you just install software, select where to backup from, and where to, and it does it! (i want to back up to a networked drive).
but doing such a thing on linux is IMPOSSIBLE! for a start, you cant see the network when you select where to backup to (or even when you are just trying to open a file in open office etc). When you type in smb://, it doesn't let you, or it complains about something or other..... it just doesn't make sense!


The big problem here is that there are at least three ways of accessing remote file systems, if you're using a smb:// url then you are going through kio, or gnome-vfs, the kde and gnome url handlers repsectively, problem is gnome apps don't work with the kde handlers and vice versa, which is a problem. Which brings us to the third (and what'd say is the most correct way) of handling remote file systems which is mounting them locally, which is pretty much analogous to mapping a file share in windows. I say this is best because once it's working, it's transparent to the software which won't even know it's not local.

try:
```

sudo mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

```
See here for more information and how to set it up to mount automatically
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

> 
even something simple, like changing the location of my music library on banshee to something on the networked drive is not possible - it just wont let me do it! this is so annoyng....

so. help required or i am seriously thinking of just quitting.

p.s. i'm sure there [I]is[I] a way, but it is so much simpler on windows. :confused:

That's because there's one way to do everything on windows, it is a singular frame work, there is only one url handler. Linux is not nearly so unified, freedesktop.org and others are working on creating that unity at a higher lever, but for now if you want things to just work right, then you need to do them at the operating system level, while the desktop environment guys get their acts together.

---

### Post by HermanAB on 2007-11-26
Network configuration is only difficult with Ubuntu.  Most other distributions have decent wizards.  So if you don't like the Ubuntu network wizard, switch to another distro, eg. Mandriva, Suse, Fedora...

---

### Post by benji.ijneb on 2007-11-27
[QUOTE=PeterJS;3842843]
```

sudo mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

```

[QUOTE]

thanks, that's really helpful, but it doesn't seem to work....
it gives me this message:

Anonymous login successful
7572: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


err...

what i put as the 'mount directory' - i think that's my problem.

thanks a bundle

---

### Post by PeterJS on 2007-11-27
> **benji.ijneb said:**
> 
Anonymous login successful
7426: tree connect failed: ERRDOS -** ERRnosuchshare (You specified an invalid share name)**
SMB connection failed


Uhhh, well looking at the error message you posted it looks like the problem is with the share name, not the mount point. Are you sure that's the right name?

##########

> **benji.ijneb said:**
> 
Anonymous login successful
7572: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


That's a different problem, then eh? Are you sure that the user name and password you supplied are correct and should have access to that share?

---

### Post by benji.ijneb on 2007-11-27
i am trying to mount this:

smb://iomega-01b44c/public

to somewhere on my desktop.

the username and password are correct.....

ta

---

### Post by PeterJS on 2007-11-27
> **benji.ijneb said:**
> i am trying to mount this:

smb://iomega-01b44c/public

to somewhere on my desktop.

the username and password are correct.....

ta

If you can connect to it with other programs but not smbfs, I don't know what to tell you, it looks like it should work. The only thing that strikes me is iomega-01b44c, is a rather strange name for a system, but if that's what it is, that's what it is.

---

### Post by benji.ijneb on 2007-11-27
woop! it works! thank-you so much!

---

