---
title: "Not seeing internal Mac drives any more"
date: 2009-05-12
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-12
When I first installed Ubuntu on my old PPC G4 a few days ago I could see and access all my Mac drives. I could play the mp3 files on the Mac drive with no trouble. Somehow, I can't do that any more - the drives don't show up in the Places menu or the file browser at all.

So - obviously, I did something somewhere but don't know what it was. :D

Is there a "Stupid User Error Reboot" command line option I can use? :popcorn:

Ubuntu 9.04, Mac G4 Sawtooth.

---

### Post by stream303 on 2009-05-12
Hard to say, but you are running a mix now of both Kubuntu and Ubuntu I believe.  You might want to install just one environment or the other.  Multiple environments can sometimes cause issues, but like I say it's hard to tell.

BTW, with all the testing you've been doing, I'm sure your hard drive has already gone through about 25 cycles or so and has done an automatic fsck disk check.

If not, you may want to force it to happen at the next reboot:

```
sudo touch /forcefsck
```

There are other ways to do this, but this is my favorite.  On old ppc's sometimes it is better to do this sooner than later. :)

---

### Post by Benboom on 2009-05-13
Man, you should be charging for all this help! That fixed it!

I was pretty sure the problem was not the KDE package as the drives "disappeared" before I installed KDE but there was so much going on that I didn't bother trying to figure it out.

I haven't even come close to booting Ubuntu 25 times (if that's what you mean by "cycles", so I guess I need to do this every so often.

Listen, I really appreciate all the help you've given me. I have three books on Ubuntu coming from my library but nothing can replace a human with hands on experience.

---

