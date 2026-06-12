---
title: "Ubuntu no longer &quot;sees&quot; NTFS volumes"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by sid351 on 2008-01-09
Hi guys...

I've had some problems with my Ubuntu 7.10 install, and have had to resort to using XP for the time being...

Anyway, I was having problems where the system would lock up, and I had to hard-reboot a couple of times, and now when I boot into Ubuntu the partitions I've created in XP (NTFS) aren't listed under "Computer".

I had edited Fstab so they would be mounted on boot, but now they no longer appear at all.

However when I run the command to view all Partitions by volume name, and fdisk -l, they show as there...and in XP everything is working fine.

Any ideas?

Do you need any more info?

---

### Post by taurus on 2008-01-09
Maybe you didn't shut down XP cleanly so Ubuntu won't mount it from /etc/fstab.  Therefore, you can add a force option in /etc/fstab or you can mount it by hand from a terminal.

What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sid351 on 2008-01-09
When I've had chance to mess around with the machine I'll let you know, I'm not ignoring you guys, I'm just a bit busy atm.

Cheers for the rapid responce.

If you subscribe to this thread I'll probably be about tmz.

Cheers again,
Sid

---

### Post by sid351 on 2008-01-10
Ok...this is odd. 

I booted into Ubuntu today, and they're all there again, and mounted on boot.

...I'm perplexed, but I suppose now there is no issue.

Thanks anyway.

Sid

---

### Post by iris_v on 2008-01-10
I'm confronted with the same issue. Yesterday when I last used Ubuntu, my NTFS drives were still there; today, they seem to have vanished. Or they are not mounted for some reason. Or whatever. Any which way, they were no longer listed as 'Places', no longer on the desktop, no longer everywhere they showed up yesterday.

> **taurus said:**
> Maybe you didn't shut down XP cleanly...

Yup, that may very well be the reason. I started Ubuntu because my Win2K froze, and I had to restart anyway. So that's one confirmation for that theory. 

But you can imagine how that works: dual boot user frustrated with poor Windows performance is confronted with a choice of OS at startup. Just let down by MS, he obviously picks Ubuntu, only to find out half his drives are AWOL. So I wouldn't necessarily say it's *not *an issue, even if the drives eventually re-appear.

[SIZE="1"](writing this from windows where of course all drives work fine. will shut down tidily and start up ubuntu, and hopefully all drives will be back - will report back shortly - UPDATE: restarted ubuntu and all is well once more)[/SIZE]

---

### Post by taurus on 2008-01-10
> **iris_v said:**
> I'm confronted with the same issue. Yesterday when I last used Ubuntu, my NTFS drives were still there; today, they seem to have vanished. Or they are not mounted for some reason. Or whatever. Any which way, they were no longer listed as 'Places', no longer on the desktop, no longer everywhere they showed up yesterday.



Yup, that may very well be the reason. I started Ubuntu because my Win2K froze, and I had to restart anyway. So that's one confirmation for that theory. 

But you can imagine how that works: dual boot user frustrated with poor Windows performance is confronted with a choice of OS at startup. Just let down by MS, he obviously picks Ubuntu, only to find out half his drives are AWOL. So I wouldn't necessarily say it's *not *an issue, even if the drives eventually re-appear.

[SIZE="1"](writing this from windows where of course all drives work fine. will shut down tidily and start up ubuntu, and hopefully all drives will be back - will report back shortly)[/SIZE]

You can still mount your ntfs partitions if you don't shut down your windows cleanly.  You just have to include the force option in /etc/fstab or from the command line.  It's not like you cannot access your ntfs partitions again under Ubuntu.

---

### Post by iris_v on 2008-01-10
> **taurus said:**
> You can still mount your ntfs partitions if you don't shut down your windows cleanly.  You just have to include the force option in /etc/fstab or from the command line.  It's not like you cannot access your ntfs partitions again under Ubuntu.

Yes, I got that from your earlier post. Can you explain though *why* Ubuntu behaves this way? Is it some sort of precautionary action? Is there a technical reason for it?

I just shut down Windows properly and rebooted and all is well again, just as all was well again for sid351. Though the point that I tried to make - and perhaps I wasn't quite clear on this - is that contrary to what he says ("I suppose now there is no issue"), I think there *is* an issue. Because the first time this happens, you're thinking what on earth happened to my drives? 

If it's so easy to mount them manually, or force a mount, why aren't the drives being mounted at start-up as usual? I can understand if it's a precautionary safety sort of thing, but then it shouldn't be so easy to manually mount them. The ease with which the issue can be corrected or even prevented makes me wonder why it exists in the first place. 

Hope that's clearer. Jist of it is that I don't like surprises (especially when they have to do with the working of my hard drives, and when the surprise could easily have been prevented, as seems to be the case).

---

