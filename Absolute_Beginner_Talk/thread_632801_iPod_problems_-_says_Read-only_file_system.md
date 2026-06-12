---
title: "iPod problems - says Read-only file system"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Seamyst on 2007-12-05
My iPod is having weird problems.  I used to be able to play music just fine through Rhythmbox, as in yesterday.  Today, however, it's a different story.  There are three problems.

1.  When I plug it in while in Gutsy, it won't mount.  If I reboot, logging into Gutsy again, it mounts.

2.  Mounted, I open Amarok and try to connect to the iPod, but I get this message:

```
Media Device: failed to create lockfile on iPod mounted at /media/Jessica's Tunes to Go: Read-only file system
```

3.  After letting the iPod just sit for a while, I notice it automatically disappears from the desktop.  Funny thing is, it's still in Nautilus - I can go to Computer and it's there, I can access its properties and everything - but that's it.

This may or may not help, but the mount options is set as follows:

```
ro nosuid nodev umask=22 uid=0 gid=0 nls=utf8
```

Does anyone have any suggestions or advice?  I'm running a dual-boot MacBook CD, if it helps.

---

### Post by vikram on 2007-12-06
> **Seamyst said:**
> My iPod is having weird problems.  I used to be able to play music just fine through Rhythmbox, as in yesterday.  Today, however, it's a different story.  There are three problems.

1.  When I plug it in while in Gutsy, it won't mount.  If I reboot, logging into Gutsy again, it mounts.

2.  Mounted, I open Amarok and try to connect to the iPod, but I get this message:

```
Media Device: failed to create lockfile on iPod mounted at /media/Jessica's Tunes to Go: Read-only file system
```3.  After letting the iPod just sit for a while, I notice it automatically disappears from the desktop.  Funny thing is, it's still in Nautilus - I can go to Computer and it's there, I can access its properties and everything - but that's it.

This may or may not help, but the mount options is set as follows:

```
ro nosuid nodev umask=22 uid=0 gid=0 nls=utf8
```Does anyone have any suggestions or advice?  I'm running a dual-boot MacBook CD, if it helps.

I mount my ipod nano with no problems with 

```

rw,user,noauto

```I'm not a mount expert but ro = read only and rw = read write. not 100 % sure but why dont you try with the new options ?

---

### Post by antisocialist on 2007-12-06
go to 
places>computer>ipod>ipod_control>  then delete the file called itunes lock

---

### Post by Seamyst on 2007-12-06
> **vikram said:**
> I mount my ipod nano with no problems with 

```

rw,user,noauto

```I'm not a mount expert but ro = read only and rw = read write. not 100 % sure but why dont you try with the new options ?

Okay... how do I do this?  I tried changing it in Settings, but that made it (temporarily) unreadable.  Took it out and it's back to what it was before.  Do I do that in Terminal?  If so, how?

[QUOTE=antisocialist]go to
places>computer>ipod>ipod_control> then delete the file called itunes lock[/QUOTE]

That file wasn't there.  I checked in all the subfolders, just to be sure, but I couldn't find it.

---

