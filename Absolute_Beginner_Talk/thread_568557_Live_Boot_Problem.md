---
title: "Live Boot Problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Darthguac on 2007-10-05
I am absolutely new to Ubuntu and Linux so if my question seems obvious to you guys, forgive me.

When I tried to do a live CD boot of Ubuntu, the first menu came up fine (the one with options including start or install Ubuntu, start Ubuntu in safe graphics mode, check CD for errors, etc).  But when I tried to select start or install Ubuntu, start Ubuntu in safe graphics mode, or check the disc for errors, the computer shows nothing for awhile then shows the following text on the screen:

[200.172000] Buffer I/O error on device fd0, logical block 0
[238.276000] Buffer I/O error on device fd0, logical block 0

The computer then won't do anything unless I press control alt delete, at which point it brings me back to the first menu.

I am using Ubuntu Edition: Ubuntu 7.04 desktop for computer platform: i386

I did a checksum after the download and the hashes matched.  After I got this error, I burned another disc, and the same error occurred.  And yes, I burned an image of the iso both times, not a data CD.  I thought that maybe the CD drive wasn't working, so I put in Starcraft and it worked just fine.  Windows says that it is working fine in the device manager, and I even reinstalled its driver.

I am using a Dell Optiplex GX110 x86 Family 6 Model 8 Stepping 10 running Windows 2000 SP 4.

Any help is greatly appreciated.

---

### Post by ryanVickers on 2007-10-06
It looks like something is corrupt - I don't know exactly what fd0 is ;), but it doesn't look good.  This one time, windows had had a completely messed up partition, and hadn't even noticed until Ubuntu cam along and said it's wrong! and fixed it :p

Try these:
[link 1]("http://ubuntuforums.org/showthread.php?t=438923")
[link 2]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306")

---

### Post by Darthguac on 2007-10-07
Before I posted I did a search of the threads for my problem and didn't find these threads...must have skipped right over them.  Sorry about that.

The two main fixes suggested in the threads were to disable the floppy drive in the BIOS and to use a CD drive, not a combination CD-DVD drive.  Well BIOS says that no floppy drive is installed, and I don't have access to a plain CD drive.

So my question is, will this problem be fixed when the next release of Ubuntu comes out later this month?  If not, is there any other way to fix the problem?

Thank you very much.

---

### Post by Darthguac on 2007-10-21
Well, I waited until 7.10 was released to see if the problem was fixed.  Unfortunately, the basic problem persists, with a few changes.  Now when I check the disc for errors, no error results (yay).  But when I select start or intall Ubuntu, the same message flashes up.  If I let the message sit for awhile, then a new message flashes:

[  304.396000] EIP is at unionfs_rename+0x4df/0x9f0 [unionfs]
[  304.396000] eax: 00008000    ebx: 000000002   ecx: 00000000   edX: c04ee6e8
[  304.396000] esi: 00000000   edI: ffffffff  ebp: 00000001   asp: c2a65e24
[  304.396000] ds:  007b   es:  007b  fs: 00d8  gs: 0033  ss: 0068
[  304.396000] Process debconf-set-sel (pid: 5062, ti=c2a64000 task=c24a2a60 task.ti=c2a64000]
[  304.396000] Stack: 00000000 00000000 00763b78 00000000 c5c7e030 c04ee6e8 c5c7e030 ffffffe4
[  304.396000]            00000001 c5d410c0 00000001 00000000 00000002 c58af5d8 00000000 00000000
[  304.396000]            00000000 00000001 00000000 00000000 00000001 00000000 c896e3c0 c04ee6e8
[  304.396000] Call Trace:
[  304.396000]  [<c0188cde>] vfs_rename+0x3de/0x480
[  304.396000]  [<c018abf6>] sys_renameat+0x1e6/0x220
[  304.396000]  [<co183cbe>] sys_stat64+0x1e/0x30
[  304.396000]  [<c018ac57>] sys_rename+rename+0x27/0x30
[  304.396000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[  304.396000]  =========================
[  304.396000] Code: 40 00 00 0f 84 f4 02 00 00 8b 4c 24 44 39 4c 24 50 0f 84 b9 02 00 00 8b 4c 24 54 85 c9 74 0c 81 f9 00 f0 ff ff 0f 86 34 02 00 00 <0f> 0b eb fe 8b 44 24 14 31 d2 e8 22 f3 ff ff 83 f8 d9 89 44 24
[  304.396000] EIP: [<c896439f>] unionfs_rename+0x4df/0x9f0 [unionfs] SS:ESP 0068:c2a65e24

If I try to start ubuntu in safe graphics mode, I don't get the fd0 message; it goes straight to the one I just typed above.

So please, is there a good solution to my problem?  Both of the fixes mentioned in threads linked to by ryanVickers won't work: there doesn't appear to be an option to disable the floppy in my BIOS, and I don't have access to a plain CD drive.  If I simply can't get ubuntu to work, what other distros would you recommend to someone new to unix and that won't have the same problem?

---

### Post by Darthguac on 2007-11-09
So, it's been two weeks.  Anyone got an answer to my problem?

---

