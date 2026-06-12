---
title: "MD5SUM on Windows succeeds, Check CD for defects fails"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by bnoll on 2007-01-24
So, I'm trying to make the switch from XP to Ubuntu.  I've got the desktop version downloaded, and do an integrity check as per [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM), specifically MD5SUM on Windows.  After doing this, all is well and I get the "MD5 Check Sums are the same" message.

So, now I burn the cd as per [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto), again, following the Windows instructions to the tee, using Infra Recorder, etc.  This works.

Then, I boot to the CD I just burnt, and "Check CD for defects" as per [https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck), but this fails.... telling me there were something like 27 checksum failures.

Any advice on this?  I've seen where people have said to burn it at a slower speed, but Infra Recorder only offers me "Write Speed: Maximum" as an option, and I've tried it on two different machines.  The only other thing I can think of that may be out of the ordinary is that I'm burning to CD-RWs.  Does this make a difference?  If so, I'll just have to grab a few CD-Rs, because all I currently have are the RWs

TIA....

Bryan

---

### Post by FreakinSyco on 2007-01-24
Sorry I cant comment on your immediate problem. But its been my experience that Nero can also burn the ubuntu .isos as long as its set to "disc-at-once". If you happen to have Nero installed than you might be able to make another quick copy to try. Otherwise I'm sure someone with a tad more knowledge can help ya.

---

### Post by Sef on 2007-01-24
> Any advice on this?

Read [How to burn an iso to a cd]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

Get [Iso Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by bnoll on 2007-01-24
I'll give this a go, but as I said earlier, it seems that I'm able to burn the iso just fine using Infra Recorder.  Is this tool you referred me to doing something different?

---

### Post by bnoll on 2007-01-24
So, that ISO recorder didn't even work for me.  It just froze up.  Is there anyone out there who may have an idea about what's going on here?  Seems like if I can verify its a good download with the MD5SUM instructions, then the problem has to be with the burn.  I'm leaning towards the fact that I'm burning it to a CD-RW that has been burnt to and erased several times.  Is this a valid thought?  I'd really like to get Ubuntu up and going, but this is proving to be a fairly insurmountable hurdle very early in the game.

---

### Post by K.Mandla on 2007-01-24
It's a possibility. I'd go with a straight CD-R, and if that still doesn't work right, try a different burner.

---

### Post by bnoll on 2007-01-24
I didn't have any CD-R's on hand, but have a whole slew of RW's.  On the off chance that it would work, I started with a fresh RW (before, it was an RW that had been used, then erased, at least once, if not multiple times).... and... it works.  Valuable tidbit hopefully for someone to find in the future.


Either use a CD-R as suggested, or a brand new fresh CD-RW.

Thanks...

---

