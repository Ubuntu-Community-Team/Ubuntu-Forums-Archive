---
title: "Disappearing Drives"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by TimMcE on 2008-01-07
I'm currently dual-booting Ubuntu 7.10 and Windows XP.  XP decided to do what XP does best and crash spectacularly last night, and then decided it would crash every time I tried to get back in before it even got to the login screen.  I didn't mind terribly, since I use it so rarely.

But when I rebooted into Ubuntu, I noticed that my two data drives, which are formatted under NTFS, weren't showing up in my Places menu anymore.  I had a peek in /media, and there were entries for sdb1 and sdc1, but if I opened them, I just got an empty window.

"fdisk -l" told me that Ubuntu was seeing the two drives, so I tried mounting them, and got an error that they had been "flagged as being in use" due to an improper Windows shutdown, and suggested I reboot into Windows and shut down normally, but since this wasn't an option, I went with the other suggestion which was to use the "force" option.

And it worked.  Sort of.  I can now access both drives through /media/sdb1 or sdc1, but neither drive is showing up in my Places menu, making for a lot of clicking to access two drives that I use quite frequently.

So my question is, how do I get those two drives back into my Places menu where they belong?

---

### Post by Moop on 2008-01-07
If XP won't even boot you could be losing that harddrive and should get any important data backed up before you do anything else. 

I think you need to boot from the XP cd and choose repair. From there you can run chkdsk to fix any errors and then maybe Ubuntu won't complain about it not shutting down properly.

---

### Post by nowshining on 2008-01-07
what MOOP said

---

### Post by exile on 2008-01-07
I had the same problem during the week. The drive was bad/corrupt. I wasn't able to recover anything from it because neither windows nor linux was able to mount it. I didn't spend a great deal of time on it though, so I'm not saying give up on it, just that I don't think it is OS related - more of a hardware problem. You might be able to resurrect the partition table or superblocks and nodes etc to get data off the uncorrupted segments, regardless I would suggest looking at a replacement disk.

Good luck with it.

---

### Post by TimMcE on 2008-01-08
> **Moop said:**
> If XP won't even boot you could be losing that harddrive and should get any important data backed up before you do anything else. 

I think you need to boot from the XP cd and choose repair. From there you can run chkdsk to fix any errors and then maybe Ubuntu won't complain about it not shutting down properly.

Thanks, that worked a treat.  There weren't any errors, but I did a repair install and that seems to have made Ubuntu happy again.  Now my only question is whether or not it's possible to rearrange the order of the drives, or am I stuck with alphabetical?

Currently, it shows them in order of Applications, Boot (Windows drive), Data, but I'd like to stick Data at the top and Boot at the bottom, so the ones I access most often are closest to the top.

---

### Post by nowshining on 2008-01-08
linux doesn't use drive letters; they are all located in /media/

as for changing names u can right click - properties - tab volume and under Mount Point choose a name, click close, right-click the drive - unmount and re-mount. :)

---

### Post by TimMcE on 2008-01-08
> **nowshining said:**
> linux doesn't use drive letters; they are all located in /media/

as for changing names u can right click - properties - tab volume and under Mount Point choose a name, click close, right-click the drive - unmount and re-mount. :)

Thanks for that, but I don't actually want to rename the drives.  I've given them names/labels, which I'd like to keep, I just want to change the specific order they appear in the Places menu.  I suppose I could always rename Boot to zBoot, but that seems like a rather cudgy way of doing it.

---

### Post by nowshining on 2008-01-09
as far as I know that's what u'll have to do, :)

mine are

oldbackup
PORTMY


in that order :)

---

