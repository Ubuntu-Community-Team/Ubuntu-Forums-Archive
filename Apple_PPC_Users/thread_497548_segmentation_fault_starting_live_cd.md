---
title: "segmentation fault starting live cd"
date: 2007-07-10
forum: Apple PPC Users
---

### Post by rushrtb2112 on 2007-07-10
I'm getting a segmentation fault when trying to start the live cd on a powerbook g4.  The fault occurs when loading manual drivers.  caused by (from srr1=141030): Transfer error ack signal.  I've tried ubuntu cd and kubuntu cd.  I'd like to get ubuntu loaded on my g4, how can I get it to work?

---

### Post by pxwpxw on 2007-07-10
The short answer might be to use the Alternate install CD, but where (how long ) into  the install is "loading manual drivers", I cant recall seeing that. And have you partitioned for macos and ubuntu?

---

### Post by rushrtb2112 on 2007-07-10
it doesn't even get to starting the live cd, I'll see the splash screen, then it shows:

* Setting preliminary keymap...                                             [ok]
* Preparing restricted drivers....                                            [ok]
* Starting basic networking...                                                [ok]
* Starting kernel event manager...                                         [ok]
* loading hardware drivers...
firmware_helper[6758]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0001:10:12.0' with dirver '(unkown)'  (shows this three times)
udevd-event[6983]: run_program: '/sbin/modprobe' abnormal exit 

* Loading kernel modules...                                                 [ok]
* Load manual drivers....
Segmentation fault

It then shows a modules linked in, call trace and instruction dump...


I'll download the alternative cd and see if i can get it to work also.

---

### Post by stmiller on 2007-07-10
What model powerbook do you have, exactly? ( [www.apple-history.com](www.apple-history.com) )

---

### Post by rushrtb2112 on 2007-07-12
I have the powerbook G4 15" 1.67 GHz

---

### Post by rushrtb2112 on 2007-07-12
I was able to get kubuntu installed with the alternative cd, it crashed twice in the middle of installation but not at the same spots.  It is runnig kosher now.  I'd still like to know why the live cd won't work though,

---

### Post by stmiller on 2007-07-12
> **rushrtb2112 said:**
>  I'd still like to know why the live cd won't work though,

The live CD doesn't work on many machines. Not enough testing by Ubuntu PowerPC dev team, and I'm afraid there will be even less testing now that Ubuntu is more focused on x86.

Edgy *never* worked on a Powermac G5, nor most iMac G5s. You had to compile your own kernel for thermal/sound, and other things to work! Despite lots of pleads and cries from us on the forum, including bug reports, the Ubuntu PowerPC dev folks did not care to make any fixes. This was when PowerPC was 'officially supported.'

---

### Post by rushrtb2112 on 2007-07-13
> **stmiller said:**
> The live CD doesn't work on many machines. Not enough testing by Ubuntu PowerPC dev team, and I'm afraid there will be even less testing now that Ubuntu is more focused on x86.

Edgy *never* worked on a Powermac G5, nor most iMac G5s. You had to compile your own kernel for thermal/sound, and other things to work! Despite lots of pleads and cries from us on the forum, including bug reports, the Ubuntu PowerPC dev folks did not care to make any fixes. This was when PowerPC was 'officially supported.'

Thanks for the update. 

I've noticed some freaky stuff happening, like it usualy freezes at the login screen if you have the network cable plugged in.  Kinda sucks that their dropping support for the powerpc but, i really don't blame them.  Now there's more of a reason to get a new mac. :) No sweat tho, just have to stick with ubuntu on my PC   Again, thanks for the input.

---

