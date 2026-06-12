---
title: "Applications crashing in Xubuntu (iMac G3)"
date: 2006-12-19
forum: Apple PPC Users
---

### Post by samden on 2006-12-19
I have Xubuntu dapper installed on my iMac G3. I am finding applications in it very unstable, which is frustrating. Firefox often crashes, as does Mozilla browser (installed as an alternative), and I have also had crashes with Open Office, Synaptic, the networking control panel and pretty well every application I have used. What could be causing this?

---

### Post by ssam on 2006-12-19
sounds like something is wrong. you should not get that many crashes. dapper is pretty stable

how much ram do you have, if you had less that 256 MB that might cause problems.

is everything up to date?

have you tried reinstalling? maybe some files are corrupted somewhere

---

### Post by samden on 2006-12-20
> **ssam said:**
> sounds like something is wrong. you should not get that many crashes. dapper is pretty stable

how much ram do you have, if you had less that 256 MB that might cause problems.

is everything up to date?

have you tried reinstalling? maybe some files are corrupted somewhere
I have 198 MB RAM, which is why I am running Xubuntu. I know some people run it on less than that, and I aren't doing anything too demanding, so that shouldn't be too much of a problem. The machine is a 500mhz iMac G3 slot loader.

Everything is up to date, and that's part of the problem - it wasn't as bad until I got it on the net and updated everything!

I may be forced to reinstall. I don't want to, because it took me about 3 weeks to get this install to work (long saga on this forum - finally worked by just reinstalling and reinstalling until it worked, lots of error messages but somehow reached the end of the installation!). So there is a good chance something could be corrupt in it somewhere, but if I try reinstalling I don't know if it will actually install again.

If I do reinstall I am tempted to have a look at Debian stable instead of Xubuntu, simply because it should have even less bells and whistles so might be more stable. Pretty new Linux user though so that is a big step for me - does anyone have any thoughts on this? If it doesn't work I can always try Xubuntu again. 

I just need this computer actually working so I can use it, I can't spend all my time reinstalling stuff! If there was a quick fix that would be great, but I think you might be right that I have to reinstall the system.

---

### Post by stream303 on 2006-12-20
I wonder if you are running out of room?  What does

df -h

show?  If I remember correctly, you had some strange partitioning issues - correct me if I'm wrong.

Hope we can find your problem without reinstalling, but the truth be known, reinstalling is a rite of passage. :)

You kids have it easy with your graphical / ncurses based installers, why I remember when...  ok enough bad humor........

---

### Post by 3rdalbum on 2006-12-20
Are you trying to run the gplflash plugin? I found that to be the single biggest cause of Firefox crashes.

---

### Post by samden on 2006-12-20
df -h
```
Filesystem                        Size   Used  Avail  Use%  Mounted on
/dev/hda3                         18G   2.3G     15F   14%    /
```
For all other filesystems the use is 1% or 0%. I am pretty sure I have loads of space!

The humour is good, anything to brighten up my day! :)

---

### Post by samden on 2006-12-20
> **3rdalbum said:**
> Are you trying to run the gplflash plugin? I found that to be the single biggest cause of Firefox crashes.
I am not sure, if the default setting is yes then yes. But my crashes are not limited to Firefox - pretty well every application I use crashes often.

---

### Post by samden on 2006-12-20
Thinking about the 'Reinstalling is a right of passage' comment above, I do think I should do this. It is likely that I have something corrupted at some fundamental level. Oh well...

First try - Debian Sarge.

Then back to Xubuntu if I feel over my head there!

Here we go...

---

### Post by stream303 on 2006-12-20
Yikes.  I was wondering what your xorg.conf looked like.  Was your G3 one of the ones that don't like DRI loaded?  What size monitor are you driving?  Perhaps dropping the default bit depth to 16 instead of the default 24 could have helped if you were just on the hairy edge of running out of video ram...

---

### Post by samden on 2006-12-21
Hmmm, might have been a bit extreme, am having problems installing again... Sarge is having as many install probs as Ubuntu had last time. My pressed Ubuntu live cd has arrived in the mail so I am trying that out, although I don't really have enough ram for it (192 rather than 256 MB). This would eliminate any problems with the touchy cd drive on these machines. The graphical installer just keeps crashing on me. I have tried to force any ram-hungry tasks I don't really need (like the panel) to close to give me more RAM but they just seem to start again straight away. Oh well, I'm sure I'll have something running on it soon, hopefully better than last time!

Good point about xorg.conf. This machine does not like dri, when I run the live cd I have to deactivate that to get it to work. I understood the alternative cd set it up correctly with dri deactivated, but I didn't check - will check with my next installation. Thanks for the tip.

---

### Post by linear on 2006-12-21
> **samden said:**
> I understood the alternative cd set it up correctly with dri deactivated, but I didn't check - will check with my next installation.

In my experience, it doesn't.

---

### Post by samden on 2007-01-05
Just in case you were wondering where I had got to, here I am again. I took the computer home for the Christmas break and spent a lot of time playing with it. I installed my personal copy of OSX on it so I could make it a dual-boot machine and have it useful while I was sorting out Xubuntu on it. After several botch-ups and reinstalls, I have a happy dual-boot computer now (fingers crossed!). OSX is on a 9gb partition, Xubuntu on a 7gb, and I have a 2gb UNIX partition that I would like to share between the two but haven't figured out how yet - will start a new thread on that. 

Thanks for all your help everyone, I have learnt a lot! The more you learn the more there is left to know though... 8)

---

### Post by ssam on 2007-01-05
using hfs+ for the shared partition may be better than UFS. UFS is more used on BSD unix than linux.

---

### Post by samden on 2007-01-05
> **ssam said:**
> using hfs+ for the shared partition may be better than UFS. UFS is more used on BSD unix than linux.
Thanks for the suggestion, will reformat it.

There is actually quite a bit of info on this subject floating around the forums, so I have printed off a few suggestions and will try them out tonight at home, will report back next week in a new thread if I have any problems.

---

