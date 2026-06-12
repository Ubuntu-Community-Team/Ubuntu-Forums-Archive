---
title: "Bad sound quality in Hardy with AlsaMixer"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by alicebtoklas on 2009-01-03
Hi all

I noticed a sound problem a few days ago. The sound in the "Front" channel is bad. It's cracking and making weird sounds, even when there's no application running. The sound is ok under Mac OS.

Model is MacBookPro3,1 and distribution Hardy Heron (in dual boot with MacOS)

Command 
```
lspci | grep Audio
``` 
gives
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I found many posts about sound issues but no one about my particular problem, and I can't find the MacBookPro3,1 wiki for Ubuntu8.04 anymore.

Could anyone help?

Thanks

A

---

### Post by Rog-Mahal on 2009-01-03
Perhaps you've found suggestions like this, but have you tried keeping the volume around 40% in OS X before switching over to Ubuntu? That helped eliminate some left channel crackling I was getting, I have the same sound card, but one revision older. It could be related to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75906") which recommends upgrading ALSA. [Here]("http://ubuntuforums.org/archive/index.php/t-611345.html") is another fix from Gutsy that I remember employing. Hope that gives a bit more information.

---

### Post by hyperboloid on 2009-01-04
> **alicebtoklas said:**
> 
I can't find the MacBookPro3,1 wiki for Ubuntu8.04 anymore.


I think it is here: [https://help.ubuntu.com/community/MacBookPro_SantaRosa]("https://help.ubuntu.com/community/MacBookPro_SantaRosa").

(It is listed in the matrix at [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), for example.)

---

### Post by alicebtoklas on 2009-01-05
Thanks for your help

Rog-Mahal,
I tried lowering the volume in MacOS, it doesn't help. As I'm not sure about how to upgrade ALSA (I have v1.0.15 which is not the latest one), I'll try to edit the /etc/modprobe.d/options file as your second link suggests.

hyperboloid,
the page you mention is for Gutsy. I think there was a wiki for Hardy on MacBookPro which disappeared when Intrepid came out.

---

### Post by hyperboloid on 2009-01-06
> **alicebtoklas said:**
>  
hyperboloid,
the page you mention is for Gutsy. I think there was a wiki for Hardy on MacBookPro which disappeared when Intrepid came out.

Are you sure? I am pretty certain that page contains info also for Hardy, although it may have started with Gutsy. In any case, have you looked at the index of ALL wiki pages?  See:
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex").

There has been a lot of work recently trying to organize the Wiki pages in a saner manner, but to my knowledge no pages were actually deleted.

---

### Post by cyberdork33 on 2009-01-06
> **alicebtoklas said:**
> hyperboloid,
the page you mention is for Gutsy. I think there was a wiki for Hardy on MacBookPro which disappeared when Intrepid came out.
It is not that specific. Please read through and try suggestions.

If you look here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

you will see that the hardy page redirects to the previously posted page. That is because it is the same.

---

### Post by alicebtoklas on 2009-01-26
> you will see that the hardy page redirects to the previously posted page. That is because it is the same. 
okay. it didn't seem so clear to me when I was already *in* the page.

Anyway:
I edited the /etc/modprobe.d/options file and reboot as both of your links suggest. I tried adding
```
options snd-hda-intel model=intel-mac-v3 position_fix=2 probe_mask=1
```
also with model=macbook-pro, model=macbook-pro-v3, model=intel_mac_v3, model=mbp3

and also
```
options snd_hda_intel model=mbp3
```
and
```
options snd_hda_intel model=mbp3 position_fix=2 probe_mask=1
```
but none of this has done any good.

Do you have any idea? Should I try to upgrade ALSA to the latest version?
What remains mysterious to me is that this problem appeared only recently, and not when I installed ubuntu.

---

### Post by alicebtoklas on 2009-01-26
Note, if this is of any help, that the cracking sound appears during the bootup, just before the login screen.

---

