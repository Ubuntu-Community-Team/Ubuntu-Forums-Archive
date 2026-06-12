---
title: "Firefox lost all settings by it self (configuration reset)"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Ux64 on 2008-01-18
Hello!

I'm just wondering what might have happened. Yesterday everything was ok. Today all my tuned firefox settings are simply GONE! 

First I thought that whole .mozilla directory would have been gone. But when I went trough that directory structure I found bookmark backups. Which is good.

Is there any way to recover any other settings which I have spent a lot of time tuning?

Also all plugin parameters are now gone.

And does anyone else encoutnered this problem before? And does anyone have a clue what happened?

- Thank you!

---

### Post by peabody on 2008-01-19
I had something strange happen to me recently.  My gconf settings in my home folder got zapped, along with my tomboy notes.

I would love to help on the firefox front.  I've been meaning to do some reading up on independently handling firefox profile to help move things like noscript whitelists between machines, etc.

---

### Post by Ux64 on 2008-01-19
I managed to recover bookmarks from backup. And re-setting rest of settings didn't take too long. 

It seems that I should take more often backups. Most interesting thing that refers that it wasn't about Firefox possibly. Was the fact that latest bookmark backup file was totally corrupted too. 

Bit strange, maybe there is something wrong with disk io?

Anyway, it reminds me that I should take backups more often than once / month. Maybe I need to take daily backups at home too. 

I got several disks and raid5 but that didn't help in this case, because something else than disk failure caused the data corruption.

And when getting to that point, separate backups should be kept long enough to spot any possible corruption allowing recovery of older data if required.

Now I need to check everything valuable on my computer before I take next backup.

---

### Post by asmoore82 on 2008-01-19
If one firefox instance was crashed in the background,
it could have created a new empty profile so it could run.

Open a terminal, kill firefoxes, and force firefox to show the Profile Manager:
(the P must be capitalized)
```
killall firefox-bin
firefox -P
```

^^ if the above doesn't help, try to verify the existence of multiple firefox profiles:
```
ls ~/.mozilla/firefox
```
and maybe post the output
(if there is more than one "goofy" named folder, that's multiple profiles)

---

### Post by Ux64 on 2008-01-20
Thanks profile manager hint is excellent and logic.

Unfortunately it seems that problem is in deeper waters than I expected.

It might be disk I/O or file system related. Because at least one of bookmark backup files was totally corrupted (wrong data) and evolution also lost settings.

I really wonder what's causing that. But it might be related to problems with P35 chipset and SATA devices.

I have to do more research. I just made complete backup and I won't use system disk before I have a better view what might be causing that.

Also I used writeback caching, but it shouldn't cause any real problems. Because my system doesn't usually crash or hang due failed disk I/O. I think that problem might be shutdown / cache flush or what ever related. That's just my guess.

I got message about some write trough cache during(!) fsck. That's something that I haven't ever seen and it did wake me up that something strange might be happening.

Problem isn't caused by bad sectors etc, because disk is properly readable. And I have used this computer for two months. If there would be "normal" disk problems. I think I would have spotted those already. I have also wiped disk a few times, so entire disk is working.

There has been also xfermode problems. 

Thread about that: [http://ubuntuforums.org/showthread.php?t=637721](http://ubuntuforums.org/showthread.php?t=637721)
[http://georgia.ubuntuforums.org/showthread.php?t=670700](http://georgia.ubuntuforums.org/showthread.php?t=670700)

---

### Post by Ux64 on 2008-01-23
Boot problem has been fixed, data corruption not. 

I did change journaling mode in fstab without all required procedures, which caused system to mount read-only.

But I'll stard new thread about it, it's hardware / driver / disk cache issue.

- Thank you!

---

