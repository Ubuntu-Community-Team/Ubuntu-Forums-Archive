---
title: "Lost Linuxes on a PowerBook"
date: 2008-06-23
forum: Apple Hardware Users
---

### Post by mfox on 2008-06-23
Although I already had Ubuntu 8.04 running pretty well on my PowerBook G4/1.33 Al, I decided to get fancy and install a second Linux. I made some free space available and installed Yellow Dog 6.0. It loaded all right except for no AirPort, but access to Ubuntu was lost from the bootloader (yaboot). I experimented, trying to paste in what I thought were the right commands in yaboot.conf, with no success. Finally, I erased the YDL and put the new openSUSE 11 on instead. With this move, I not only lost access to Ubuntu from the yaboot options one gets at startup, but also to MacOSX. I played with it further, trying to add Ubuntu and MacOSX back to the yaboot menu, but the commands I added to yaboot.conf didn't produce the desired result. I still had MacOSX access, but through open firmware or starting up with the option key. Finally, I screwed everything up with some command I entered in the yaboot.conf file, and now I can't even access openSUSE. The command resulted in some error shown at bootup, and I had no way to access any Linux to fix it. To make matters even more difficult, I accessed MacOSX and changed the startup disk.  Now booting into OSX is easier, but yaboot isn't invoked at startup anymore. I assume I can do something about this when I get home and have access to the Ubuntu/openSUSE install disks I'm on the road this week), but is there anything I can do without them to get access to the yaboot menu from MacOSX (Leopard) and remove the faulty command?

---

### Post by mfox on 2008-06-28
I'm still needing help with this.  The Ubuntu 8.04 PPC install disk doesn't have a repair option; it just goes right into installation mode.  I now know that the bootloader partition is still there (actually there are two of them), so it looks like the problem is with the file partition map, which I suspect that MacOSX either rewrote or destroyed.

A friend on another forum suggested that I use a utility called TestDisk.  I read the instructions on TestDisk, and this looks like it might work.  BUT, it suggests for my problem that I use pdisk to initialize the disk, and that doesn't sound right.  In Mac language, initialize means destroy everything on it.  Does it mean something else in Linux?

---

### Post by stream303 on 2008-06-28
You can try going into the rescue or single user mode.  If you have the "alternate" installer, at the second-stage of the yaboot boot: prompt, interrupt the automatic countdown with -tab- key.

You should see some options, and I'd type "rescue-powerpc" or just use "Linux single"

It will look like it is going to install, but at some point, it will ask you what partition you'd like your shell to be dropped into.

If you had a totally dedicated install, you'd pick

/dev/hda3

If you don't know which was your root partition, you can try again and this time use /dev/hda4 and keep doing this working your way up until you can get to a shell.

Once in the shell, you could try running

```
sudo yabootconfig
```

and this might help you out.  It doesn't work right on G5's, but your G4 might be ok.  Otherwise, you can get in and modify your yaboot.conf manually.  When done, don't forget to make the change known to the system with

```
sudo ybin -v -C  /etc/yaboot.conf
```

---

