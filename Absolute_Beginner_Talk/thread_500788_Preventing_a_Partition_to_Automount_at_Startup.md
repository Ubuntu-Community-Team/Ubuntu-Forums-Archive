---
title: "Preventing a Partition to Automount at Startup"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by luvr on 2007-07-14
I'm trying to define an NTFS partition in the **/etc/fstab** in such a way that it will **not** get mounted whenever I boot the computer.

I know that I could simply remove the partition definition from my *fstab,* but I do not want to do that, since I want to be able to mount it via the *File Browser* (an icon for the partition appears under the *Places* heading, and the context menu from that icon includes a *"Mount* option). Once I get things properly set up, I can then change my *fstab*, so that the NTFS partition will get mounted via *ntfs-3g* instead (i.e., with read/write access).

My *fstab* line for the partition currently looks like this:
```
UUID=xxxxxxxxxxxxxxxx   /media/xxxxxxxx  ntfs   defaults,umask=222,user,noauto   0   0
```
The **noauto** option should, in my opinion, prevent the partition to be mounted at startup, but it doesn't work: The partition *still* gets automounted.

Is there any way to **prevent** the automount from taking place?

---

### Post by kidders on 2007-07-15
Hi there,

This is just a stab in the dark, but the "defaults" mount option is expanded to "rw, suid, dev, exec,  auto,  nouser, async" (see mount's man page). It *could* be that specifying both "auto" and "noauto" for the same filesystem is confusing your Ubuntu.

---

### Post by luvr on 2007-07-16
> **kidders said:**
> Hi there,

This is just a stab in the dark, but the "defaults" mount option is expanded to "rw, suid, dev, exec,  auto,  nouser, async" (see mount's man page). It *could* be that specifying both "auto" and "noauto" for the same filesystem is confusing your Ubuntu.

Well, those were my thoughts, too, so I removed the **defaults** option. That didn't help, though; in fact (and according to the documentation), the **noauto** option should override the *auto* setting that gets set by the *defaults* option earlier on in the list of options.

Thanks for the tip, anyway.

By the way, searching a little further, I found a bug report about Ubuntu ignoring the **noauto** option: [***Bug #120829** in util-linux (Ubuntu): /dev/sda3 is mounted despite the 'noauto' option in fstab.*]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/120829") Guess I will simply remove my NTFS partitions from my fstab; I can live with that for the time being. Hopefully someday, the bug will get resolved.

Oh, and here's another bug that I'm running into: [***Bug #71609** in util-linux (Ubuntu): Can't unmount UUID= volume as a user.*]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/71609") I'm not sure if it's limited to volumes that are mounted by UUID, though; I will have to do some more testing to verify.

---

### Post by kidders on 2007-07-16
These bugs are serious! I wonder if they can be avoided by downgrading the system tools involved in mounting things. :confused:

---

### Post by Harcourt on 2007-10-06
Ok, nevermind.  I spoke too soon.
Someone please fix this.  Apparently the bug doesn't exist in gutsy beta.  Can we get a backport plz?

---

