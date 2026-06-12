---
title: "Opening a .dmg file?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Transmit on 2006-09-30
Can anyone tell me how to open a .dmg file in the latest version of ubuntu? (dapper drake I guess)

thanks in advance!

---

### Post by Transmit on 2006-09-30
anyone:(

---

### Post by llamakc on 2006-09-30
Open a Terminal.

```

file nameof.dmg

```

The above will let us know whether or not you really have a .dmg file

Next,

```

[B]sudo mount -t hfs -o loop myImage.dmg /mnt

```

[/B]If it complains about filesystem type, we'll need to load the appropriate kernel module for that fileystem.

```

sudo modprobe hfs

```

And try the mount command again.

cd to /mnt and browse the contents.

---

### Post by pay on 2006-09-30
Just making sure that you know that dmg files are mac osx installers and won't work in linux, but it's safe to extract them.

---

### Post by llamakc on 2006-09-30
Some wallpaper packs are distributed as dmg (which was my case).

---

### Post by Transmit on 2006-09-30
so if it was an installer in the dmg I probably wouldn't be able to use it? Do I need a mac or can I just install OS X then?

---

### Post by nereid on 2006-09-30
You will need a Mac as you can't install Mac OS X legal on a normal PC.

---

### Post by Transmit on 2006-09-30
is there a way to install it illegaly? I thought it was always possible...

but let's say I would be illegal, I could be able to install MAC OS X on my PC?

---

### Post by pay on 2006-09-30
You can install Mac with Vmware server.

---

### Post by haxer on 2006-09-30
Yeah and for the note on every new mac pc is running under pentium so all new software for make like the os is running steady on a pc to or?

---

### Post by Transmit on 2006-09-30
yes I know but don't I need a new/extra harddrive or does partitioning works?

---

### Post by pay on 2006-09-30
Huh? Vmare server doesn't need a new harddrive, it takes space from your current harddrive though. Sorry if I miss interpretated the question.

---

### Post by Transmit on 2006-09-30
No no, When you use VMware to install MAC OSX on a pc doesn't it(OSX) need a new harddrive to be installed on?

---

### Post by pay on 2006-09-30
I haven't installed OSX on vmware server but win xp didn't need a new harddrive to be installed on in vmware server.

---

### Post by nereid on 2006-10-01
There is still a difference between a Mac and a PC. A Mac doesn't use BIOS and so you can't simply boot Mac OS X from a PC. I don't know about VMware if it works, but you don't need a new harddrive. VMware creates a virtual disk on a existing harddrive.

---

### Post by Sef on 2006-10-01
Transmit and everyone else:

> is there a way to install it illegaly? I thought it was always possible...

but let's say I would be illegal, I could be able to install MAC OS X on my PC?
Reply With Quote

Please don't ask how to do something illegal on Ubuntu forums.

---

### Post by Transmit on 2006-10-01
je m'excuse!

---

### Post by Gen2ly on 2006-12-04
k, I did try this:
> file frosty_icons.dmg
frosty_icons.dmg: VAX COFF executable not stripped - version 1539

Is this then a true .dmg?  It returned this:
> sudo mount -t hfs -o loop frosty_icons.dmg /mnt
Password:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm thinking not.  This problem is close to the author's.  I just want to access a desktop picture.

Also, for true .dmg images a more thorough explanation how is given here:

[http://baghira.sourceforge.net/dmg.htm]("http://baghira.sourceforge.net/dmg.htm")

---

### Post by engla on 2006-12-04
I know from OS X that there are quite a few options for .dmg images, you can make them sparse, compressed, use UDIF etc etc. Perhaps this only works on plain uncompressed HFS images?

For example, one CD .dmg I had was reported by "file" to be an HFS Extended disk. In that case you have to use the type "hfsplus", not "hfs"

---

