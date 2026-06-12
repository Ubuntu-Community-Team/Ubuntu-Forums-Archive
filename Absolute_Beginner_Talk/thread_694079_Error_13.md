---
title: "Error 13"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by SoccerCmp5 on 2008-02-11
This morning when I tried to boot my computer, I got a message saying "Error 13: Invalid or unsupported executable format" when I try to select that I want to boot into Windows XP.  I googled the error as well as looked through these forums for help, but all of the ones I found pertain to Ubuntu errors in starting up.

Also along these lines, is there a way to set my computer up so that I have the option of booting Windows into safe mode?

Thanks in advance for any help.

---

### Post by Mark_in_Hollywood on 2008-02-11
Is this a GRUB error? sorry I don't have any help, more than this. Some time ago, I had big problems with Grub errors.

Please google: grub error 13, I see lots of stuff about dual-booting.

---

### Post by polmir on 2008-02-11
Try reinstall grub
[http://ubuntuforums.org/showthread.php?t=694079]("http://ubuntuforums.org/showthread.php?t=694079")

---

### Post by SoccerCmp5 on 2008-02-12
Ok so just tried re-installing GRUB but still I get the same error.  I've asked a few people and they think it might be that my NTFS partition is messed up, but I'm not sure how I could go about fixing that.  Any ideas?

Also, could this also be the reason I'm having a hard time mounting the NTFS partition in Linux?  That it's messed up in some way?

---

### Post by polmir on 2008-02-12
> **SoccerCmp5 said:**
> ...I've asked a few people and they think it might be that my NTFS partition is messed up, but I'm not sure how I could go about fixing that.  Any ideas?
```
sudo apt-get install ntfs-3g
```

---

