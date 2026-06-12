---
title: "What updates to avoid after successful restoration?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-21
Hello everyone,
My system was getting to be a mess and, not finding any solution to this situation, I decided to run a restoring job using my backup I created a while back. All went smoothly; Ubuntu rocks again.

I followed this HowTo:
[A-star]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive")


Of course I'm not really keen on installing updates, more precisely, _which updates to avoid installing_ since, following the restoration, the update icon appeared...obviously!
Here are the updates that "I should" install:
> 1. linux-image-2.6.15-27-386 
2. linux-image-2.6.15-27-686 
3. linux-image-386 
4. linux-image-686 
5. linux-restricted-modules-2.6.15-27-386 
6. linux-restricted-modules-2.6.15-27-686 
7. linux-restricted-modules-386 
8. linux-restricted-modules-686 

Any advice/help on this would be greatly appreciated.

---

### Post by benfindlay on 2006-09-21
You're fine installing updates like kernel updates, and the only reason you should experience any slow down is due to the fact that the hard drive is getting clogged up with the old kernel and old versions of updated software.

I believe there is a way to remove the old stuff by either purging or uninstalling it from the command line, but someone else had better confirm this before you try it, as the last time I purged my old kernel files after an upload, it screwed the whole system and it wouldn't reboot.

Thankfully my hard drive is much bigger than I need in my ubuntu pc, so I'm not worried about leaving the old files there.

---

### Post by wieman01 on 2006-09-21
My honest opinion? I try to avoid all updates with one exception: security patches. I wrote a little howto a while ago on how to disable updates & "pin" your kernel version, perhaps that is helpful:

[http://www.ubuntuforums.org/showthread.php?t=259280]("http://www.ubuntuforums.org/showthread.php?t=259280")

I don't see a reason why I should need a higher kernel version than I have. At least for the time being I don't think it's necessary since all changes are fairly intangible. But this is merely my personal opinion.

---

### Post by xyz on 2006-09-21
Thank you for your quick and well-oriented answers!
**benfindlay** I checked for unnecessary mess and I seem OK there.

I tend to ageee with **wieman01**...besides, if a pbm occurs, I guess I can unlock them!

I may be wrong there but I seem to recall that, a while back when I downloaded/installed these kernel updates, more updates came up for installation and my problem may have been due to those!

One thing for sure, I'm sure glad I backed up! A strange thing: restoring didn't completly delete all my files and I didn't have to 'mkdir' the ones I had excluded form my backup!

---

### Post by benfindlay on 2006-09-21
> I tend to ageee with **wieman01**...besides, if a pbm occurs, I guess I can unlock them!

Indeed! If it isn't broken, don't fix it!

With regards to downloading new updates, I tend to give it a few days before I upgrade stuff, just to make sure there are no problems with the new upgrades (like the last X-server release! ;))

My tactic is to have my /home directory on another partition, so I can format the OS and still keep as much stuff as possible. I put everything I can in /home, docs, files, music etc etc, then theres no problem if I need to reformat anything, I'll set it going, go get a drink, come back, and its almost done! :D

Anyways, hope this helps

---

### Post by wieman01 on 2006-09-21
> **benfindlay said:**
> Indeed! If it isn't broken, don't fix it!

With regards to downloading new updates, I tend to give it a few days before I upgrade stuff, just to make sure there are no problems with the new upgrades (like the last X-server release! ;))

My tactic is to have my /home directory on another partition, so I can format the OS and still keep as much stuff as possible. I put everything I can in /home, docs, files, music etc etc, then theres no problem if I need to reformat anything, I'll set it going, go get a drink, come back, and its almost done! :D

Anyways, hope this helps
Good suggestion. I am doing it pretty much the same way. Also I only upgrade when I am prepared for it... meaning that I have time to go through a lot of trouble-shooting if you know what I mean. But again, I consider security updates important, that's the exception (to the rule).

Never change a running system my prof at university used to say...

---

### Post by xyz on 2006-09-21
> With regards to downloading new updates, I tend to give it a few days before I upgrade stuff, just to make sure there are no problems with the new upgrades (like the last X-server release! )


The X-server release, _which gave me no problems whatsoever (and nobody was able to explain why so far!),_ led me to believe I was spared...for once!
So I didn't have the usual precautionary approach to updates.

I opened Synaptic > Installed and locked the current kernels with the little green square and the small yellow star.
However, I saw a whole bunch of "old" kernels, modules and all in there only with the little green square!!
**benfindlay** was this you were referring to in a previous post and that I should mark for complete removal?

Many thanks guys!

---

### Post by benfindlay on 2006-09-21
They may well be listed in synaptic as previous modules, so it might work. However, when I last did it, I stumbled across a quide that gave me a command line to enter into terminal to remove them. You could always try completely removing them and seeing whether it tries to mark the other, more updated ones for removal too. If it does, then just shut synaptic, descarding changes to undo your actions!

It was quite a while ago that I last tried it, and since it went catastrophically wrong I haven't wanted to try it since! ;)

With regards to the X server, you may well have just been lucky, it did work for a few people so I've heard

---

### Post by xyz on 2006-09-21
Was this what you did by any chance:
[Ubuntu_deamon]("http://www.ubuntuforums.org/showthread.php?t=24403&highlight=unnecessary+files")

By the way, thanks a lot for having taken the time to help! :D

---

### Post by benfindlay on 2006-09-21
That sort of thing, what I was specifically looking at before was getting rid of all the extra kernel options in the GRUB boot loader, without simply removing them fromt the GRUB config file, doing this leaves the files behind, but prevents you from accessing them without re-editing GRUB's config settings. Since wrecking that installation, I've got rid of Microsoft Winbloat from my computer, so the hard drive space saved goes towards storing the extra kernels! ;)

It turns out too that they're handy to have still isntalled, in case a new kernel upgrade is dodgy, you just boot the old one! :D

Hey, helping's no problem! There are plenty of really helpful people on this forum! Working in a really quiet call centre this holiday to get some cash for university next year, so I'm keeping busy between calls on this forum! ;)

---

