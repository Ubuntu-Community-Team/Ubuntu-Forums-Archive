---
title: "Mac Pro Bootloader Issues"
date: 2009-07-09
forum: Apple Hardware Users
---

### Post by PDXP on 2009-07-09
Hi All,

First time poster here.

I've spent the last few days trying to install Ubuntu 9.04 64-bit on my (2006?) Mac Pro, dual Quad-core Xeon. As an advanced Linux user I usually figure this stuff out on my own, but I just can't get this to work and I need some help.

It's got 4 disks in it - OS X 10.5 on disk 0, nothing on disk 1, Ubuntu on disk 2 (ext4), and Windows Vista on disk 3. Installing Ubuntu on the primary disk isn't an option only because OS X doesn't want to resize the partition no matter how hard I try. The disks are 750GB so I'd rather make use of all the space anyway.

**The problem:** After installing Ubuntu and attempting to load it via rEFIt, it goes straight into the Windows loader every time (after freezing at the penguin on the first try - I noticed others experienced this too). If something is happening in Grub that is punting it to the windows bootloader/OS, I'm not seeing it. The screen goes white after the rEFIt penguin icon goes away, followed by a flash of black (possibly grub doing something), then a flash again before windows starts loading.

Some things I've tried:


[LIST]
[*]grub2-pc: Same problem.
[*]grub2-efi: Compiled from SVN and discovered/loaded from rEFIt- "unknown command 'linux'". "insmod linux" succeeds but the command still doesn't work or show up. I had to set --program-prefix to an empty string to get the modules to install in the proper directory, but it doesn't work regardless.
[LIST]
[*]Side note: the default grub.cfg has "terminal console" in it and kicks me directly to the terminal. The linux comman shows up there but doesn't seem to work.
[/LIST]
 
[*]Bootloader on the MBR vs. Partition: no change.
[*]Syncing GPT/MBR with rEFIt: same.
[*]Changing the root in menu.lst/grub.cfg in case grub doesn't see it as hd2: same problem.
[*]Reading almost every page of this forum relating to my problem and trying the fixes: no change. (side note: the refit ubuntu package doesn't seem to exist anymore)
[/LIST]

I'm at a dead end here and have spent way too much time scouring threads trying to get this working. I'd really appreciate some advice on how to get this working!

Offtopic: all this rebooting got me sick of the Mac startup sound. I'd be insane right now if I hadn't found a way to turn it off: [http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html.]("http://www5e.biglobe.ne.jp/%7Earcana/StartupSound/index.en.html")

---

### Post by pxwpxw on 2009-07-10
> **PDXP said:**
> Hi All,

First time poster here.

I've spent the last few days trying to install Ubuntu 9.04 64-bit on my (2006?) Mac Pro, dual Quad-core Xeon. As an advanced Linux user I usually figure this stuff out on my own, but I just can't get this to work and I need some help.

It's got 4 disks in it - OS X 10.5 on disk 0, nothing on disk 1, Ubuntu on disk 2 (ext4), and Windows Vista on disk 3. Installing Ubuntu on the primary disk isn't an option only because OS X doesn't want to resize the partition no matter how hard I try. The disks are 750GB so I'd rather make use of all the space anyway.

**The problem:** After installing Ubuntu and attempting to load it via rEFIt, it goes straight into the Windows loader every time (after freezing at the penguin on the first try - I noticed others experienced this too). If something is happening in Grub that is punting it to the windows bootloader/OS, I'm not seeing it. The screen goes white after the rEFIt penguin icon goes away, followed by a flash of black (possibly grub doing something), then a flash again before windows starts loading.

Some things I've tried:


[LIST]
[*]grub2-pc: Same problem.
[*]grub2-efi: Compiled from SVN and discovered/loaded from rEFIt- "unknown command 'linux'". "insmod linux" succeeds but the command still doesn't work or show up. I had to set --program-prefix to an empty string to get the modules to install in the proper directory, but it doesn't work regardless.
[LIST]
[*]Side note: the default grub.cfg has "terminal console" in it and kicks me directly to the terminal. The linux comman shows up there but doesn't seem to work.
[/LIST]
 
[*]Bootloader on the MBR vs. Partition: no change.
[*]Syncing GPT/MBR with rEFIt: same.
[*]Changing the root in menu.lst/grub.cfg in case grub doesn't see it as hd2: same problem.
[*]Reading almost every page of this forum relating to my problem and trying the fixes: no change. (side note: the refit ubuntu package doesn't seem to exist anymore)
[/LIST]

I'm at a dead end here and have spent way too much time scouring threads trying to get this working. I'd really appreciate some advice on how to get this working!

Offtopic: all this rebooting got me sick of the Mac startup sound. I'd be insane right now if I hadn't found a way to turn it off: [http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html.]("http://www5e.biglobe.ne.jp/%7Earcana/StartupSound/index.en.html")


Hi,

That is a complex situation, it will be easier to sort out using grub2 efi or pc to find ubuntu kernel, grub.efi can also boot osx or pass to the windows loader.

On the grub-efi thread page 78 post #772 is a working grub64.efi package to get started.
[http://ubuntuforums.org/showpost.php?p=7502407&postcount=772](http://ubuntuforums.org/showpost.php?p=7502407&postcount=772)

It has a small menu which you can use to get started and expand later, I will have to look at it to see if it suits your system.

Using either grub2.efi or grub2-pc,
you should be able to list all the drives and partitions and find the ubuntu kernel from the grub command line -
```

grub> ls
grub> search /vmlinuz
grub> set pager=1
grub> ls -l

```

That info should suffice to add a menuentry for your system in grub2 pc or efi.
Note that refit 013 does not see ext4 partitons, can be confusing, not a problem with grub2-efi.

See also links on post #1 of grub efi thread, and the grub2 ubuntu wiki.

---

### Post by PDXP on 2009-07-10
Thanks for the link- I had read all the wiki pages you mentioned and tried to read that long thread, but didn't get through all the posts.

This looks like something I can use, but for some reason my rEFIt is 32-bit even though the machine's architecture is 64-bit. Is there a way to force rEFIt to install the 64-bit version?

If not, I'll try using my compiled 32-bit version with the steps you outlined- I had done it a bit differently before. Will update soon.

---

### Post by mossman44 on 2009-07-10
I don't know whether it will work but maybe you should look into using EasyBCD in combination with the windows vista bootloader. It has an easy to use GUI and you can add Linux and MacOSX entries with it.

---

### Post by pxwpxw on 2009-07-10
> **PDXP said:**
> Thanks for the link- I had read all the wiki pages you mentioned and tried to read that long thread, but didn't get through all the posts.

This looks like something I can use, but for some reason my rEFIt is 32-bit even though the machine's architecture is 64-bit. Is there a way to force rEFIt to install the 64-bit version?

If not, I'll try using my compiled 32-bit version with the steps you outlined- I had done it a bit differently before. Will update soon.

Ah, if refit says 32 thats what your Macs EFI is. Use the grub.efi from post #762, it will do 32 or 64, use the grub.cfg from the other one.

[http://ubuntuforums.org/showpost.php?p=7275427&postcount=762](http://ubuntuforums.org/showpost.php?p=7275427&postcount=762)

The problem with your compile may have been in the preloaded modules and maybe the version.

---

### Post by PDXP on 2009-07-10
That 32-bit EFI worked well for me, especially after I figured out that the initrd was seeing my root partition as something other than the installer. UUIDs should fix that, but I believe the /dev map will still be different... such a weird issue.

It wasn't seeing the kernel in my ext4 partition, so I re-installed with an ext2 boot partition and ext4 root partition.[B]

Note to other readers[/B]- when installing Ubuntu, creating a boot partition and setting the mount point as "/boot" will cause the install to either fail or not boot properly. I chrooted into the install and set it up manually.

So, in closing, problem solved! Thanks a bunch!

---

