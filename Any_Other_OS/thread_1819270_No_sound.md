---
title: "No sound?"
date: 2011-08-05
forum: Any Other OS
---

### Post by adamhum3 on 2011-08-05
Probably about my thousandth problem with Linux so far!

I've recently installed Elementary OS, and just installed the Flash Player, however I've realised I'm not getting any sound.

I get a little sound but very quiet through headphones. 

I've checked in my sound preferences, and in the output there's only 'Internal Audio', nothing else. 

I'm running on an Acer Aspire 7730, everything (sound drivers) is just straight out of the box.


Please help! :|

Cheers,

Adam

---

### Post by wildmanne39 on 2011-08-05
Hi, here is a link on sound issue maybe it will help.
[http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966)
[http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/](http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/)

---

### Post by adamhum3 on 2011-08-06
Hi, thanks for the help. Tried both of them, still nothing, which is making me believe it's most likely something simple.

The thing bothering me is the fact I can't see my sound card in sound preferences?

---

### Post by adamhum3 on 2011-08-06
Bump. Someone? Help?!

---

### Post by adamhum3 on 2011-08-06
Bump. 90+ views and no one has a clue?

---

### Post by wildmanne39 on 2011-08-06
Hi, I am sorry it did not work I have no other ideas.

You are only suppose to bump a thread once every 24 hours.
Thank you

---

### Post by Elfy on 2011-08-06
Thread moved to Other OS/Distro Talk.

You're going to need to give people more information if you want help. Try goin to the > General Help - Start here if you have no idea why sound is not playingpart of [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and see how far it goes till it fails.

---

### Post by adamhum3 on 2011-08-06
> **wildmanne39 said:**
> Hi, I am sorry it did not work I have no other ideas.

You are only suppose to bump a thread once every 24 hours.
Thank you

My apologies. Rather frustrating when you receive no response on the only two sources of support you have. 

Can't deal with waiting 24 hours each time with no reply, without sound.

> **forestpiskie said:**
> Thread moved to Other OS/Distro Talk.

You're going to need to give people more information if you want help. Try goin to the part of [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and see how far it goes till it fails.

Thanks, I'll give it a try.

---

### Post by 23dornot23d on 2011-08-06
[COLOR=Blue][B]OK I have the same computer and the simple answer is probably to do the following and then reboot ..... to see if it works ....

[/B][/COLOR]gksudo gedit /etc/modprobe.d/alsa-base.conf
 

( then add this line at the end and of it then "save" the file)
 **options snd-hda-intel model=auto**
[COLOR=Blue][/COLOR]

---

### Post by 23dornot23d on 2011-08-06
[COLOR=Blue][B][COLOR=Red][COLOR=Black]I only just went through this again here the other day - [_*Link*_]("http://ubuntuforums.org/showpost.php?p=11107380&postcount=57")

What was that .conf file ... ? search on soundcard problems and 23dornot23d ,,,,

got it ...... [COLOR=Blue][U][I][LINK]("http://ubuntuforums.org/showthread.php?t=1515200")

[/I][/U][/COLOR][/COLOR][/COLOR][/B][/COLOR]> 
[COLOR=Blue][B][COLOR=Red][COLOR=Black][COLOR=Blue][U][I] 
and the solution was to add one line to a file

[/I][/U][/COLOR][/COLOR][/COLOR][/B][/COLOR]gksudo gedit /etc/modprobe.d/alsa-base.conf

[B]options snd-hda-intel model=auto

[/B][B] 

I hope it works ok for you too .... ;)

[/B]As you will see from the links the problem was reported to the developers ..... on launchpad.

And every fresh install ..... 

I have to set it up again. 

( luckily its only one line of code to add ..... but it does give stereo output but not full surround sound )
( if the developers looked into it they may be able to get it working properly ..... maybe ..... )

---

