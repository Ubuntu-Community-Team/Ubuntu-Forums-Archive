---
title: "Dell 6400 ATi X1400 Gutsy Gibbon &quot;Suspend Hibernate&quot; how to make it work? help"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-10-31
Hi
Dell now ships out with Ubuntu, but I guess not with an ATi X1400
Ubuntu doesn't simply work, it's frustrating and takes hours to work around the problems.
That's a fact
but slowly with the newer releases things are getting better

but for now I'm stuck with a laptop that can't** suspend** or **hibernate**

**Please is there a workaround to this problem?**

thanks

---

### Post by ronald.higgins on 2007-10-31
Had similar issues with suspend / hibernate but dont have an ATI card.

Anyway, check out this link:

[http://ubuntuforums.org/showthread.php?t=471855&highlight=s2ram](http://ubuntuforums.org/showthread.php?t=471855&highlight=s2ram)

---

### Post by felixfurtak on 2007-11-02
Create this file:
   /etc/modprobe.d/blacklist-fglrx

Put this in it:
   blacklist fglrx

Reboot

---

### Post by MozartlovesUbun2 on 2007-11-02
> **felixfurtak said:**
> Create this file:
   /etc/modprobe.d/blacklist-fglrx

Put this in it:
   blacklist fglrx

Reboot

hmm. i dunno, did as you said, didn't work for me :(

is suspend and hibernate both supposed to work with it?

---

### Post by toxigenicpoem on 2007-11-06
The problem is with Gutsy Gibbon its self. The kernel now uses SLUB instead of SLAB. 

Black listing your driver as stated, would only force you to move to the open source ATI driver, which should run the SLUB, instead of calling for the SLAB, but its going to leave you with bad performance for the family line of your card, compared to the ATI one.

Your choices are, 

1) wait for 8.43 which will hopefully have SLUB support.
2) downgrade to Fiesty Fawn (I've heard this resolved some of the problems)
3) recompile the ubuntu kernel to use SLAB instead of SLUB.

I'm in the same boat, so don't worry! I'm just finally glad that someone created a hotfix for the intel-hda sound cards, so I can finally use headphones, even if they dont work too well in Ubuntu, as they do in Debian stable. ugh linux :) love it, hate it.

---

### Post by Casual Fan on 2007-11-06
The above poster is correct--I have an ATI radeon xpress 1100 and can't suspend or hibernate, and neither can most folks running Gutsy with ATI cards on a laptop. It's not you or Dell, it's an Ubuntu-ATI problem.

IMHO, you DON'T want to use the open-source driver, which is what blacklisting fglrx will do. That driver made my system literally creep. And it looked awful too.

If you absolutely must suspend or hibernate, I would revert back to Feisty, or if you're up to it, recompile the kernel. Personally, I'm going to wait for ATI to release a driver patch that solves the problem and just shut down when I don't need the laptop. It boots fast anyway.

---

### Post by MozartlovesUbun2 on 2007-11-06
goodness me, well what a pain in the butt

i might just change over to open suse 10.3, or does that have suspend hibernate problems too?

well in ubuntu since drapper drake suspend hibernate has never worked for me and this just sucks

---

### Post by Casual Fan on 2007-11-07
> **MozartlovesUbun2 said:**
> goodness me, well what a pain in the butt

i might just change over to open suse 10.3, or does that have suspend hibernate problems too?

well in ubuntu since drapper drake suspend hibernate has never worked for me and this just sucks

The culprit is the SLAB/SLUB issue. Feisty uses SLAB, Gutsy SLUB. Not sure if OpenSuse uses either. So to be more correct, it's a SLUB/ATI issue. If SLUB and fglrx can learn to play nice, the problem is solved.

---

### Post by MozartlovesUbun2 on 2007-11-07
> **Casual Fan said:**
> The culprit is the SLAB/SLUB issue. Feisty uses SLAB, Gutsy SLUB. Not sure if OpenSuse uses either. So to be more correct, it's a SLUB/ATI issue. If SLUB and fglrx can learn to play nice, the problem is solved.

ok thanks for the detailed info

well i guess i'll wait a little longer and stick to ubuntu for the time being

spent 3 hours last week trying to get a dial up connection through the laptop

just to find out that its disabled or what ever under ubuntu

still havnt managed to get it running

---

### Post by kids_pro on 2007-11-14
> **MozartlovesUbun2 said:**
> goodness me, well what a pain in the butt

i might just change over to open suse 10.3, or does that have suspend hibernate problems too?

well in ubuntu since drapper drake suspend hibernate has never worked for me and this just sucks

My friend loaded openSUSE 10.3 on his laptop with ATI card, Suspend & Reboot work well.

---

### Post by NotTheMessiah on 2007-11-14
> **MozartlovesUbun2 said:**
> ok thanks for the detailed info

well i guess i'll wait a little longer and stick to ubuntu for the time being

spent 3 hours last week trying to get a dial up connection through the laptop

just to find out that its disabled or what ever under ubuntu

still havnt managed to get it running
There is a free driver for internal winmodems(for conexant -and intel HD audio) from dell support website.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
Then just use wvdial or G-ppp

---

### Post by MozartlovesUbun2 on 2007-11-15
> **NotTheMessiah said:**
> There is a free driver for internal winmodems(for conexant -and intel HD audio) from dell support website.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
Then just use wvdial or G-ppp

ok i'll give it a try

---

### Post by MozartlovesUbun2 on 2007-11-15
> **kids_pro said:**
> My friend loaded openSUSE 10.3 on his laptop with ATI card, Suspend & Reboot work well.

thats great, i guess i'll change over to SUSE then, but this is one thing I dont understand about Linux, its supposed to be open, so if suse has managed to get it working then why ubuntu doesnt just copy it or learn from 

isnt that the meaning of Linux to improve the work done before, it seems they are just all reinventing the wheel over and over again.

---

### Post by Casual Fan on 2007-11-26
From what I've gathered, SLUB didn't have to be used on the version of the kernel that Ubuntu used for 7.10, but they added it. However, it's supposed to be standard now and will replace SLAB on later versions of the kernel, so all of the drivers will have to work with SLUB.  ATI claims to have fixed this with the new 7.11 driver (replaces 8.42.x)...I've seen posts from folks who say they can suspend with 7.11, especially those who are running newer versions of the kernel.

---

### Post by MozartlovesUbun2 on 2007-11-26
> **Casual Fan said:**
> From what I've gathered, SLUB didn't have to be used on the version of the kernel that Ubuntu used for 7.10, but they added it. However, it's supposed to be standard now and will replace SLAB on later versions of the kernel, so all of the drivers will have to work with SLUB.  ATI claims to have fixed this with the new 7.11 driver (replaces 8.42.x)...I've seen posts from folks who say they can suspend with 7.11, especially those who are running newer versions of the kernel.

lol, well i can only kick my buttt for it now, coz last night in fustration i overwrote gutsy with suse 10.3

and it's no where near as good as i thought it would be, anyway i am having massive problems with suse, it's not working out of the box, updates are horrible with lots of windows openening up, menu bars are terrible where one has to scroll through, doesnt seem intuitive, am having a terrible time finding things, anyway after spendings hours on it, it has still hasnt recognized my graphic card properly, no 3d, and wireless features are very bad.

---

### Post by MozartlovesUbun2 on 2007-11-26
> **Casual Fan said:**
> From what I've gathered, SLUB didn't have to be used on the version of the kernel that Ubuntu used for 7.10, but they added it. However, it's supposed to be standard now and will replace SLAB on later versions of the kernel, so all of the drivers will have to work with SLUB.  ATI claims to have fixed this with the new 7.11 driver (replaces 8.42.x)...I've seen posts from folks who say they can suspend with 7.11, especially those who are running newer versions of the kernel.

thank you for the info, i'm still a bit confused now with the ATI drivers, are there restricted and open source drivers available at the same time? so which to choose from?

i want the one in which **desktop effects, suspend/hibernate and 3d** works

I don't understand: "7.11 driver (replaces 8.42.x)"

thanks

---

### Post by MozartlovesUbun2 on 2007-11-26
> **NotTheMessiah said:**
> There is a free driver for internal winmodems(for conexant -and intel HD audio) from dell support website.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
Then just use wvdial or G-ppp

i tried everything possible, seems the modem will not work under gutsy!

---

### Post by Casual Fan on 2007-11-26
> **MozartlovesUbun2 said:**
> thank you for the info, i'm still a bit confused now with the ATI drivers, are there restricted and open source drivers available at the same time? so which to choose from?

i want the one in which **desktop effects, suspend/hibernate and 3d** works

I don't understand: "7.11 driver (replaces 8.42.x)"

thanks

see my PM

---

### Post by MozartlovesUbun2 on 2007-11-26
> **Casual Fan said:**
> see my PM

hi ya, ok thanks

i will post your reply here so others can benefit from it too

> Re: ATi X1400 Gutsy Gibbon 
Hi Mozart,

I'm pretty new to all this myself, but I'll try to answer your questions. There is both an open source and a restricted driver for the ATI cards. You can use one or the other, but not both. The open source driver (in my experience) is very slow and almost unusable on my computer. The restricted driver (called "fglrx") works well, but due to its inability to work well with a program called SLUB in the Linux kernel, you can't suspend or hibernate with it. SLUB was just added to the Ubuntu Linux kernel with release 7.10 (Gutsy Gibbon). SLAB had done the same job as SLUB before then. The fglrx drivers had been numbered with an 8, as in 8.37, 8.40, and 8.42.3, etc. Now, ATI has changed the numbering so that it matches up with their driver releases for Windows, so the latest version of fglrx is called Catalyst 7.11. 

At this time, if you have an ATI card and are using Ubuntu 7.10, you probably can't suspend, have desktop effects, AND have 3-D. You have to choose between suspending (using the open-source driver) or having 3-D and desktop effects (fglrx).

I hope that helps...

CF

thanks again

---

### Post by MozartlovesUbun2 on 2007-11-26
why are restricted and open **ATI drivers** being developed at the same time for linux?

shouldn't they be joining forces?

*(in gutsy i couldn't enable desktop effects under restricted ATI drivers)*

---

### Post by MozartlovesUbun2 on 2007-11-27
question: if i enable the backports in Gutsy would it then update to the latest ATI 7.11 driver?

is that advisable?

---

### Post by MozartlovesUbun2 on 2007-11-28
question: if i enable the backports in Gutsy would it then update to the latest ATI 7.11 driver?

is that advisable?

---

### Post by MozartlovesUbun2 on 2007-12-05
just got latest envy, suspend hibernate still not working for me.

---

