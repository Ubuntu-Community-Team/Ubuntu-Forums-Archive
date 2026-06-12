---
title: "[SOLVED] rEFIt vs. GRUB...cont'd"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2008-10-27
So, here's the beginning.

[http://ubuntuforums.org/showthread.php?t=958925]("http://ubuntuforums.org/showthread.php?t=958925")

In case you don't want to read that, long story short is that I have an extra entry in rEFIt marked with the Linux penguin and text stating I can load Linux from HD (instead of partition X).

So I got bored with trying different things and decided to just clear the hard drive and restore my three OSs later. Interesting development: I cleared my hard drive, reinstalled Mac OS X as well as rEFIt...and the vacant Linux penguin is still there!

As an add-on, if you select the Linux penguin, the screen turns black and the word "GRUB" is in the upper left hand corner with a flashing cursor next to it.

I've been told by one of the helpers in the above link that hd0 is the beginning of my hard drive and to remove GRUB from there. If that is the case, I have NO idea how to do that. I've been able to mount/look through the hidden EFI partition at the beginning of the Mac hard drive, but there's nothing in there really (aside from a folder entry of /EFI/APPLE/EXTENSION/firmware.scap ...which sounds essential).

Help? Please?

Oh yeah, and when running Partition Inspector, it says this:


```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    312057519  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    312581807  ee  EFI Protective

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
```

(this is freshly run, with only one partition for Mac OS X...however, I got pretty much the same output when I had all three partitions).

---

### Post by cyberdork33 on 2008-10-27
All you need to do is clear the Bootcode from the MBR...
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-28
> **cyberdork33 said:**
> All you need to do is clear the Bootcode from the MBR...
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

...and that was all I needed. Thanks!

Unfortunately, rEFIt was unable to rebuild my MBR and as a result, I wasn't able to access the saved MBR to restore it. No biggie, though, because as I said before, I backed everything up. So I just re-formatted and reinstalled. Thanks again!

---

### Post by cyberdork33 on 2008-10-29
> **teamjh14 said:**
> ...and that was all I needed. Thanks!

Unfortunately, rEFIt was unable to rebuild my MBR and as a result, I wasn't able to access the saved MBR to restore it. No biggie, though, because as I said before, I backed everything up. So I just re-formatted and reinstalled. Thanks again!
I don't really know what you mean, but glad you got it working.

---

### Post by Tu1J4kXk8NUhMz on 2008-10-29
> **cyberdork33 said:**
> I don't really know what you mean, but glad you got it working.

Yeah, that wasn't too clear, now that I read it again :-P

I cleared out the entire MBR instead of just the bootsector as you outlined in the link. That was a dumb idea, because rEFIt wasn't able to rebuild the MBR (it was missing some file?). So I used my Ubuntu Live CD to try and restore the saved mbr_backup. Only thing is that it was saved to the internal hard drive, and without an MBR the live CD couldn't find said hard drive.

Speaking of which, you may consider changing the tutorial you provided to have the user save the backup MBR externally. Then again, maybe it was user (me) error...I'm not too clear on MBRs so I may have misread or mistyped something somewhere.

---

### Post by cyberdork33 on 2008-10-29
> **teamjh14 said:**
> Yeah, that wasn't too clear, now that I read it again :-P

I cleared out the entire MBR instead of just the bootsector as you outlined in the link. That was a dumb idea, because rEFIt wasn't able to rebuild the MBR (it was missing some file?). So I used my Ubuntu Live CD to try and restore the saved mbr_backup. Only thing is that it was saved to the internal hard drive, and without an MBR the live CD couldn't find said hard drive.

Speaking of which, you may consider changing the tutorial you provided to have the user save the backup MBR externally. Then again, maybe it was user (me) error...I'm not too clear on MBRs so I may have misread or mistyped something somewhere.
Yea I think you had another issue as not having an MBR should not prevent you from booting (as the Mac works off EFI, which really uses the GPT, not the MBR). It sounds like you have a problem with your rEFIt install that was not allowing the partition sync tool to work. I would try reinstalling it. (Also, on that note, there is 'gptsync' in the ubuntu repo that does the same thing as well.)

---

