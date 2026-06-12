---
title: "why Xorg become worst in time on PowerPc G5 ?"
date: 2016-09-04
forum: Apple Hardware Users
---

### Post by luigiburdo on 2016-09-04
Guys i dont understand why on PowerMac  G5 we are facing time by time a regression on Xorg org...
ox letz explain:
from 13.10 to today i sow a big regression on video compatibility on powermac g5 ...
in 14.04.3 i was able to have on my G5 quad full 2d and 3d accelerated xorg with radeonhd 4xxx, 5xxx and 6xxx serie.
today it is not possible ... or better is possible only with 4xxx but you will face system freeze 
will be possible for us have one day a finally G5 machine without issue?

one of my friend yesterday reported me r300 are start gaving again rings errors .
some one can help finally us to have our G4 and G5 full operational and without issue?

I sow many bug reported on bugtracker on xorg ... but many without reply or fixes.

---

### Post by ajgreeny on 2016-09-04
This is actually an AMD problem, not specifically one for you PowerPc G5 users.

For some time AMD has been leaving older graphics chips unsupported by its proprietary fglrx driver and in 16.04 support has been lost completely.

However, AMD is working hard to open the source for its drivers and for many users who are not using graphically challenging applications they are now very good, either the radeon driver that has been around for many years, or now, the amdgpu driver which I have heard is progressing very well, and may be even better than the older fglrx driver for some.  I have not used an AMD card for many years so pass this info on second hand, and for you to consider.

Don't blame Ubuntu, blame the hardware makers if anybody, but also don't forget that  PowerPc G5 machines are pretty old, having been discontinued 10 years ago, and it is difficult to retain full support for all hardware no matter its age.

---

### Post by gsahli on 2016-09-04
PowerPC has never been able to use the fglrx driver, so that doesn't seem to explain the issues.
On the other hand, my G4 with Radeon 9600XT is now working fine in 16.04.

---

### Post by luigiburdo on 2016-09-04
im not blaming ubuntu, this situation is on all linux distros.
powerpc have issue with xorg and mesa on new machines too and never fixed.
i dont understand why after 4 years no one fix the wrong endianess in colors on mesa egl and egl2... reported hundred times

yes g5 quad are old machine but work exactly like the newest machine with new class of powerpc cpus

---

### Post by ajgreeny on 2016-09-04
OK, you all know more about graphics on a PowerPc G5 than I do.  I have never used a PowerPc or mac of any kind, but I'm afraid I assumed that the drivers for a "normal" PC would also be used on a PowerPc G5.

Sorry if I got that wrong.

---

### Post by ernsteiswuerfel on 2016-09-10
> **luigiburdo said:**
> im not blaming ubuntu, this situation is on all linux distros.
powerpc have issue with xorg and mesa on new machines too and never fixed.
i dont understand why after 4 years no one fix the wrong endianess in colors on mesa egl and egl2... reported hundred times

yes g5 quad are old machine but work exactly like the newest machine with new class of powerpc cpus
Well, only thing you can do to help upstream Kernel and Xorg devs to sort the problems out is:

Do some git-kernel and git-mesa building to test any ppc-patches in git and report back to [https://bugs.freedesktop.org](https://bugs.freedesktop.org).

r300-type cards are old, but if the AMD-devs have time they still do r300 and PPC patches! Unfortunately building and installing packages from git is not exactly easy on Ubuntu nor it's especially fast on legacy PPC-hardware. ;)

But they need people to actually verify that patches work. Current problems reported upstream: [https://bugs.freedesktop.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=PLEASETEST&field0-0-0=product&field0-0-1=component&field0-0-2=alias&field0-0-3=short_desc&field0-0-4=status_whiteboard&field0-0-5=content&order=changeddate%20DESC%2Cbug_status%2Cpriority%2Cassigned_to%2Cbug_id&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&type0-0-5=matches&value0-0-0=powerpc&value0-0-1=powerpc&value0-0-2=powerpc&value0-0-3=powerpc&value0-0-4=powerpc&value0-0-5=%22powerpc%22](https://bugs.freedesktop.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=PLEASETEST&field0-0-0=product&field0-0-1=component&field0-0-2=alias&field0-0-3=short_desc&field0-0-4=status_whiteboard&field0-0-5=content&order=changeddate%20DESC%2Cbug_status%2Cpriority%2Cassigned_to%2Cbug_id&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&type0-0-5=matches&value0-0-0=powerpc&value0-0-1=powerpc&value0-0-2=powerpc&value0-0-3=powerpc&value0-0-4=powerpc&value0-0-5=%22powerpc%22)

---

### Post by eastone on 2016-09-10
It's very sad that older r300 at least works, and newer r500 does not.

---

### Post by luigiburdo on 2016-09-11
> **eastone said:**
> It's very sad that older r300 at least works, and newer r500 does not.

not only ... you will not belive in what i will write now :

on ubuntu 14.0 on quad g5 you can run without issue radeon hd cards 4xxx,5xxx,6xxx little tricks but run where the 4xxx was perfect running 
on ubuntu 14.0 libglamour dont crash ... i dint made a full investigation but probably we can have (r700)radeonsi 7xxxx running on g5 too. 

from 15.0 ... 5xxx, 6xxx dont work any more or better run but only in fbdev
libglamor crash .
r 4xxx freeze ...

i call this a great wonderful regression ... i dont have extra money but i have the feeling the nvidia will run better ... because on Power8,Power9 there are nvidia last gen gpus

---

