---
title: "hfsplus installed, yes hfs+ drive still not mounting"
date: 2009-03-04
forum: Apple Hardware Users
---

### Post by subtex on 2009-03-04
I'm sorry if this is posted in the wrong section, but it does involve a mac formatted drive so I hope it's ok.

I have an external LaCie usb/fw drive that I'm hooking up to my laptop running Netbook Remix.

I've installed **hfsplus** and **hfsutils** yet when I plug in this drive is still tells me that it's filesystem is "hfsplus" and it's not supported.

Is there something I need to do to get ubuntu to use the hfsplus module?

This drive works on my desktop running 8.04 (nbot netbook remix).

---

### Post by mkvnmtr on 2009-03-04
If it is journeledd it is not supported. If it is hfsplus extended it will work.

---

### Post by subtex on 2009-03-04
It is hfsplus extended.

It does work on my desktop which was running 8.04.  I figured UR which was also based on 8.04 would be the same but apparently it's not.

Is there some test I can do to make sure hfsplus is loaded and running?

---

### Post by mkvnmtr on 2009-03-04
I have an external formated hfsplus. I make a mount point and then mount the drive with commands in the terminal. Then I have to unmount in the terminal. It is not the way I would like to do it but it is the only way I can get it to work. I also then have permission problems. It seems to start out ok but then changes so I have to change permissions in the terminal. It is a pain and I really don't feel good about giving the commands I use to someone else. I am not that sure I am doing it right. Some one that knows should see yuor thread and give you some thing. Be very careful. I have messed up bad enouugh with this problem that I had to reinstall.

---

### Post by cyberdork33 on 2009-03-04
> **subtex said:**
> It does work on my desktop which was running 8.04.  I figured UR which was also based on 8.04 would be the same but apparently it's not.
Is backing up the data and reformatting it to something more compatible out of the question?

---

### Post by subtex on 2009-03-04
> **cyberdork33 said:**
> Is backing up the data and reformatting it to something more compatible out of the question?

Yeah, it's not my drive. It's a friend's that I'm borrowing to grab data off of.

---

### Post by pxwpxw on 2009-03-04
> **subtex said:**
> Yeah, it's not my drive. It's a friend's that I'm borrowing to grab data off of.

If you can run 

```

 dpkg -L hfsplus

```
Gets a list of what is installed.
Look at the 'man' info, I think you have to manually mount using hfsplus commands.
However I dont have UR.

---

### Post by subtex on 2009-03-04
> **pxwpxw said:**
> If you can run 

```

 dpkg -L hfsplus

```
Gets a list of what is installed.


ok, output of that is here:
```

/.
/usr
/usr/bin
/usr/bin/hpmount
/usr/bin/hpumount
/usr/bin/hpls
/usr/bin/hpcd
/usr/bin/hpcopy
/usr/bin/hppwd
/usr/bin/hpfsck
/usr/bin/hprm
/usr/bin/hpmkdir
/usr/share
/usr/share/linda
/usr/share/linda/overrides
/usr/share/doc
/usr/share/doc/hfsplus
/usr/share/doc/hfsplus/copyright
/usr/share/doc/hfsplus/changelog.gz
/usr/share/doc/hfsplus/changelog.Debian.gz
/usr/share/man
/usr/share/man/man7
/usr/share/man/man7/hfsplus.7.gz
/usr/share/man/man1
/usr/share/man/man1/hpfsck.1.gz
/usr/share/man/man1/hpls.1.gz
/usr/share/man/man1/hpmkdir.1.gz
/usr/share/man/man1/hpmount.1.gz
/usr/share/man/man1/hppwd.1.gz
/usr/share/man/man1/hprm.1.gz
/usr/share/man/man1/hpcd.1.gz
/usr/share/man/man1/hpcopy.1.gz
/usr/share/man/man1/hpumount.1.gz

```

Nothing in the man pages about manually mounting via the terminal.

I'll be leaving work soon, so I'll see what's different about my desktop setup that is letting me automount the mac drive no problem.

Any suggestions on what I should be checking on the machine where this works no problem?

---

### Post by subtex on 2009-03-04
ok, so it's definitely an issue with UNR not loading the hfsplus module.

on my desktop i ran 

```
modprobe -l | grep hfs 
```

and I see:

```

/lib/modules/2.6.24-23-generic/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.24-23-generic/kernal/fs/hfs/hfs.ko
/lib/modules/2.6.24-23-generic/kernal/fs/hfsplus/hfsplus.ko
/lib/modules/2.6.24-23-generic/kernal/net/sched/sch_hfsc.ko

```

on my netbook I see:

```

/lib/modules/2.6.24-19-lpia/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.24-19-lpia/kernel/net/sched/sch_hfsc.ko

```

but what's weirder is the desktop doesn't even have the hfsplus package installed!

so perhaps it's more to do with the fact that UNR is using a different kernel entirely.  "lpia" instead of "generic".

?

---

### Post by pxwpxw on 2009-03-05
> **subtex said:**
> ok, so it's definitely an issue with UNR not loading the hfsplus module.

on my desktop i ran 

```
modprobe -l | grep hfs 
```

and I see:

```

/lib/modules/2.6.24-23-generic/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.24-23-generic/kernal/fs/hfs/hfs.ko
/lib/modules/2.6.24-23-generic/kernal/fs/hfsplus/hfsplus.ko
/lib/modules/2.6.24-23-generic/kernal/net/sched/sch_hfsc.ko

```

on my netbook I see:

```

/lib/modules/2.6.24-19-lpia/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.24-19-lpia/kernel/net/sched/sch_hfsc.ko

```

but what's weirder is the desktop doesn't even have the hfsplus package installed!

so perhaps it's more to do with the fact that UNR is using a different kernel entirely.  "lpia" instead of "generic".

?
EDIT: Yes, just read your post properly - the netbook kernel version just does not have the hfsplus.ko module apparently. Maybe a later version does.

The hfsplus package does not provide a module. The hfsplus package is just a collection of utilities such as hpmount for manual use.

But the bad news is I tried hpmount here for fun, and it has crashed my separate hfsplus partition which MacOSX can no longer mount or repair.  ( It's ok, it only had a few files on it.)

Consequently I recommend you trash hfsplus before it does it to you. 

The best suggestion seems to be to get a ubuntu810 live cd and run it to copy the files you want. I can't suggest any other safe way to mount it.

---

### Post by cyberdork33 on 2009-03-05
> **pxwpxw said:**
> The hfsplus package does not provide a module. The hfsplus package is just a collection of utilities such as hpmount for manual use.
hfsplus modules are in the kernel. There are no extra packages needed to mount hfsplus volumes. You kernel appears to have that files system disabled (likely for space / overhead savings).

---

### Post by subtex on 2009-03-05
> **cyberdork33 said:**
> hfsplus modules are in the kernel. Your kernel appears to have that files system disabled (likely for space / overhead savings).

So is there an easy way to re-enable them?

---

### Post by tiresia on 2009-03-05
To see if you have hfsplus module```
lsmod
```
Can you see it in the list that you get from that command?
If not try ```
modprobe hfsplus
```
Check now if you can mount your hd
If you want to mount a hfsplus device, let's say 'sda', on a mount point '/mnt' run
```
sudo mount -t hfsplus /dev/sda /mnt 
```

---

### Post by cyberdork33 on 2009-03-05
> **subtex said:**
> So is there an easy way to re-enable them?
If what tiresa is saying does not work, you can recompile.

---

### Post by subtex on 2009-03-05
neither the hfs nor the hfsplus module is there at all in lsmod.

---

### Post by subtex on 2009-03-05
> **cyberdork33 said:**
> If what tiresa is saying does not work, you can recompile.

Considering I've never had to recompile a kernel ever, I'm a bit wary of doing it just from a newb-perspective.

Here's a question though: if someone else were to recompile the hfs and hfsplus modules for lpia, would I be able to take those .ko files and chuck them in the modules directory, reloading them, etc?

Or does it have to be a full kernel recompile.

---

### Post by tiresia on 2009-03-05
Have you tried to load the module with modprobe?

There is not a big difference in building in hfsplus in the kernel and loading it at boot up. 
As I said try to load it with modprobe, if it works - as it should, you can decide to load it at boot up or only when you need with modprobe.

---

### Post by subtex on 2009-03-05
> **tiresia said:**
> Have you tried to load the module with modprobe?

yup.  I get:

```
FATAL: Module hfsplus not found.
```

---

### Post by tiresia on 2009-03-05
Ok, I don't know UNR and how its Kernel is built.
Please, can you run following commands:
To get which kernel are you running
```
uname -r
```
```
cat /boot/config-'uname -r' | grep HFS
```
Instead of 'uname -r' write the name of your kernel.

---

### Post by subtex on 2009-03-05
[QUOTE=tiresia;6844837]
uname -r:

```
2.6.24-19-lpia
```

cat /boot/config-2.6.24-19-lpia | grep HFS:

```

CONFIG_NET_SCH_HFSC=m
# CONFIG_HFS_FS is not set
# CONFIG_HFSPLUS_FS is not set

```

---

### Post by tiresia on 2009-03-05
> **subtex said:**
> [QUOTE=tiresia;6844837]
uname -r:

```
2.6.24-19-lpia
```

cat /boot/config-2.6.24-19-lpia | grep HFS:

```

CONFIG_NET_SCH_HFSC=m
# CONFIG_HFS_FS is not set
# CONFIG_HFSPLUS_FS is not set

```

Ok, there is the point we are missing.
Both the values with '#' should be '=m' also compiled as module.
Now, either you boot from the LiveCD as suggested from pxwpxw for an easy solution, or you recompile your kernel. If you are planning to use your hfs drive often, your should recompile your kernel.

Recompiling a Kernel is easier as one could think. Here are the easiest links I know:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
(you need only the section: 'Alternate Build Method: The Old-Fashioned Debian Way')
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

The second link is just two pages.

You don't need of course to recompile the all stuff, but you should just use the configuration you already have, and starting from that, build the two missing modules. 
Reading the links and rebuilding your kernel should take not more than one hour if you never did it.

Let us know, how it works.

---

### Post by subtex on 2009-03-05
I'm reading those kernel compiling links and it looks like more work than I want to do.  ;)

I think I'll just deal with only being able to use that portable drive on my desktop for now.

Thanks for all the help though, guys. I've learned a ton.

I appreciate it!

---

### Post by satbunny on 2009-03-11
I have the same problem.

It is rather sad that the lpia kernel shipped with the Dell Mini12 does not have hfsplus support, maybe someone didn't want to annoy Apple?

I also am quite nervous about recompiling my kernel on a diskless netbook using a variant architecture, so I'll probably reformat my iPod to a Windows format like fat32 or ntfs, or whatever iTunes on XP thinks is normal.

BUT. I shall try and do a kernel recompile on my desktop Dell, so one last question.. how do I make the new compile ensure that the HFSplus module is turned on?

Then, maybe, I'll risk doing it on my Mini..

---

### Post by tiresia on 2009-03-11
Recompiling a Kernel is not such a difficult task. If you do it wrong, you can always restart your computer and choose the old Kernel.

It's much easier if you start from your actuall configuration and check the other stuff you need.

As I wrote in the last post, to have HFS+ support, you need just to set
CONFIG_HFS_FS
CONFIG_HFSPLUS_FS

I find the how-to on howtoforge (the second link) clear and easy, even if it is a bit old (read the second page, where he says 'it's a good idea to use the configuration of your current working kernel as a basis for your new kernel').

---

### Post by pxwpxw on 2009-03-12
.

---

