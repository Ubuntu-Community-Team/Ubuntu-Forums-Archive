---
title: "need help with burning iso"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ahurd on 2008-02-17
I am on Kubuntu Feisty. Tried many times to use k3b but tray button will not open tray when k3b is up (others had similar probs and some say it is fixed in Gutsy). I did manage to burn on CD by putting cd in tray before invoking k3b but this no longer works. I am now trying to burn on dvd and am told this is not a problem. Results so far:

Brasero: reports there is no disk in dvdram

Nero: initially reports "one of your devices is not accessible /dev/sg1 scsi generic" altho it shows up on next screen.  "burn" reports "invalid field in command"

Gnomebaker:  failed reporting /dev/sr0: media is not recognized as recordable dvd


Could anyone help me. Thanks.

---

### Post by 1467 on 2008-02-17
have you used any other programs then k3b ?

their are other options for burning ISO like gnomebaker, nautilus, Nerolinux, Graveman,

try it and see

---

### Post by nonewmsgs on 2008-02-17
is it an iso or is it a bin/cue

---

### Post by ahurd on 2008-02-17
It is an iso file of gparted live cd. Haven't tried graveman but will give it a shot. Just tried graveman and it failed as well. Something is obviously going wrong.

---

### Post by 1467 on 2008-02-18
dam I will have do some research on this one. and in the mean time you can try Arson it is a beta version but other than that i do not know???

---

### Post by 1467 on 2008-02-18
it sounds like a hardware compatibility  problem do you have a another computer?
 srry stoopid thing to ask but gust in case

---

### Post by JoshuaRL on 2008-02-18
Have you messed with anything lately?  Can you go to Synaptic and see if there are any broken dependencies?

---

### Post by ahurd on 2008-02-20
1467: I have a dual boot with win2000 and a virtualbox win2000 and it works fine on them.

Joshua: Could you spell out to this rank beginner how I can check dependencies.

Thanks to you both.

---

### Post by JoshuaRL on 2008-02-20
Sure man.

Go to System->Administration->Synaptic Package Manager

When that opens go to the bottom left and there should be a Filters tab.  Go there and look for the sub-tab that says something about Broken.

Anything in there should be marked for reinstallation, and then hit the Apply button in the top bar.  That should fix any broken ones.

---

### Post by ahurd on 2008-02-20
Joshua:

Followed yr instructions. No programs showing broken. Other programs, eg, gnomebaker are now exhibiting the strange behavior I reported with k3b, viz, tray not opening with button necessitating reboot.

It is strange that all burning pgms I have tried seem not to work , but possibly for different reasons. Nero works on my win2000 dual boot and it reports that the dvd drive is ok so it doesn't seem to be hardware. Anyone heve any ideas on things to try next?

---

### Post by oedha on 2008-02-20
mmm...sounds like hardware problem......
can play or open other cds which have content on them ?

---

### Post by jcitguy78 on 2008-02-20
not sure if it runs on Linux but i used Infra Recorder to burn my ISO's when I setup a dual boot with XP, which you can find on the Ubuntu site.

---

### Post by ahurd on 2008-02-20
Can read cd's on Kubuntu and can read and burn cd's on win2000 dual boot. Therefore doubt it is hardware, but who knows.

---

### Post by 1467 on 2008-02-26
cd images are not compatible with dvds i fond it on another thread 

[http://ubuntuforums.org/showthread.php?t=705962&page=2]("http://ubuntuforums.org/showthread.php?t=705962&page=2")

---

### Post by oDDWare on 2008-02-27
I'm a beginner with linux, and you've probably beat me to the thought, but have you checked /media to see if your drive is mounted? (I had a problem similar starting out.) Just keeping it simple!

---

### Post by sayakb on 2008-02-27
> **1467 said:**
> cd images are not compatible with dvds i fond it on another thread 

[http://ubuntuforums.org/showthread.php?t=705962&page=2]("http://ubuntuforums.org/showthread.php?t=705962&page=2")

Ofcourse they arent.. You need a CD to burn a CD image, and nothing else.

---

### Post by Therion on 2008-02-27
> **1467 said:**
> cd images are not compatible with dvds i fond it on another thread 

[http://ubuntuforums.org/showthread.php?t=705962&page=2]("http://ubuntuforums.org/showthread.php?t=705962&page=2")
I've burned many a LiveCD to a DVD with no problem.  Reason being I know my drive simply tends to burn DVD's better than it does CD's (go figure).

The posters in that thread are saying the OP needs to try a different *brand* of media, not that s/he can't use a DVD to burn the smaller CD .iso image.

An .iso file is an .iso file, regardless of size.  The .iso doesn't care what kind of media you burn it to, and your PC doesn't either.  It's an .iso file, it's just data.

To the OP:  Try a different brand of media.

---

### Post by sayakb on 2008-02-27
> **Therion said:**
> I've burned many a LiveCD to a DVD with no problem.  Reason being I know my drive simply tends to burn DVD's better than it does CD's (go figure).

The posters in that thread are saying the OP needs to try a different *brand* of media, not that s/he can't use a DVD to burn the smaller CD .iso image.

An .iso file is an .iso file, regardless of size.  The .iso doesn't care what kind of media you burn it to, and your PC doesn't either.  It's an .iso file, it's just data.

To the OP:  Try a different brand of media.

I never actually burnt a CD image on a DVD.. *sigh*
I know the opposite is in no way possible. But during my time with Windows, I remember Nero not allowing me to burn a 650MB MS Office iso on a DVD.. So was that some media specific iso, or was Nero going crazy?

---

### Post by Therion on 2008-02-27
> **LinuxIsInnovation said:**
> I never actually burnt a CD image on a DVD.. *sigh*
I know the opposite is in no way possible. But during my time with Windows, I remember Nero not allowing me to burn a 650MB MS Office iso on a DVD.. So was that some media specific iso, or was Nero going crazy?
Let me put it this way... You can put 5 pounds of flour in a 10-pound sack but you can't put 10 pounds of flour in a 5-pound sack.  You just can't.  So, similarly...  You can put a 700MB .iso file on a 4.7GB DVD, but you can't put a 4GB .iso on a 700/800MB CD.  

There is no such thing as a "CD .iso" file versus a "DVD .iso" file.  There are simply .iso files that are small enough to fit on a CD and ones that are too large for a CD that must then be put on a DVD for that reason: Filesize.  That's it.  No other differences.  Period.

Most likely, since you COULD burn your .iso file to a CD, Nero wanted you to.  That or you forgot to tell Nero (specifically) that you wanted to burn a DVD project.  I've used Nero extensively in the past and it can be fickle about things from time to time.

---

### Post by 1467 on 2008-02-28
srry

---

