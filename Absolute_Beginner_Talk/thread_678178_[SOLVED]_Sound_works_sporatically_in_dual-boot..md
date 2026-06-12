---
title: "[SOLVED] Sound works sporatically in dual-boot."
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-25
I'm dual-booting between XP(x64) and Gutsy.  As long as Ubuntu was the *last* OS running, when I boot up sound works perfectly.  However, if I boot into Windows (where the sound always works fine), then I reboot the computer into Ubuntu, I'll have no sound.  The only way I know of to get the sound back, is to reboot Ubuntu; then the sound works fine again.  If I boot back into Windows, the sound in Windows is fine.  But the next time I boot Ubuntu I'll be without sound until I reboot a second time.

I've seen similar problems around the forum but I haven't noticed any definitive solution yet.  When I load up Ubuntu (when the sounds is *not* working), **alsamixer **has my soundcard set to my Mobo card; which I don't use.  After the second reboot, alsamixer correctly lists my Creative Audigy Gamer card.

This seems like a goofy sort of bug, is there any possible way to prevent this from happening or to fix it without a second reboot?  It's a pretty big hassle.

Thanks!

---

### Post by pdxken on 2008-01-25
Your problem may be more complex than this but as a sanity check consider it.
When I first loaded linux on my dell tower, the sound started acting weird. At the same time I had opened the case and installed a 2nd hard drive. Apparently the sound card came loose in the process. The problem went away when I reseated the sound card.

Also the network interface card worked fine with XP and Fedora but not ubuntu?? until I replaced it. Maybe it was loose too. Plug-in  connectors can cause strange problems.

Ken.:lolflag:

---

### Post by Origin415 on 2008-01-25
If its just a problem of a default sound card, I had a similar problem and setting the default card in asoundconf worked for me.

Run
```
asoundconf list
```
and take the name of the card you want and then
```
asoundconf set-default-card *card*
```

---

### Post by toastysquirrel on 2008-01-27
> **Origin415 said:**
> If its just a problem of a default sound card, I had a similar problem and setting the default card in asoundconf worked for me.

Run
```
asoundconf list
```
and take the name of the card you want and then
```
asoundconf set-default-card *card*
```

That seems to have done it, thanks!

---

### Post by Redptc on 2008-01-28
Hello, Origin415, stumbled on your reply which seems to have sorted my sound problem, just wanted to say thanks!

---

