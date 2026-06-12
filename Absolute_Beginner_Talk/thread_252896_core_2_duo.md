---
title: "core 2 duo"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-09-07
Is it "safe" to run ubuntu dapper 686 smp on a core 2 duo laptop, or is this technology to new?

---

### Post by powder on 2006-09-07
Yes.  Just install the 686 kernel and you should have SMP.

---

### Post by arijarot on 2006-09-07
> **powder said:**
> Yes.  Just install the 686 kernel and you should have SMP.

ok...thanks powder :)

---

### Post by mostwanted on 2006-09-07
You also need to install the smp package for 686. It's supposed to be included in Edgy though, so no need to do that there.

---

### Post by arijarot on 2006-09-07
> **mostwanted said:**
> You also need to install the smp package for 686. It's supposed to be included in Edgy though, so no need to do that there.

ok, thanks ... what's edgy, btw?

---

### Post by Jukey on 2006-09-07
Edgy is the nickname for the current testing version of Ubuntu.

the full name is Edgy Eft and its scheduled to be version 6.10

---

### Post by jdong on 2006-09-07
The 686 kernel is the appropriate one to run for the Core 2 Duo. You do not need the SMP package, since Dapper. The 686 kernel is already SMP.

For the next version of Ubuntu, Edgy, the default kernel (called "generic") will be able to utilize both cores of the core 2 duo out-of-the-box, with no need to switch kernels after install.

---

### Post by Frank Golden on 2006-09-07
> **arijarot said:**
> ok, thanks ... what's edgy, btw?
Hi arijarot,
   Edgy Eft is the next major version of Ubuntu due out in October.
The version your profile shows you using is Breezy Badger which
most folks upgraded to Dapper Drake in June of this year.
Dapper and the other colorful name are code names for the different versions of Ubuntu. Dapper became Ubuntu 6.06 LTS in June. A month ago a new .iso was released called Ubuntu 6.06.1 LTS, the .1 means it has over three hundred patches and updates 
rolled into it since the initial release in June.
The LTS stands for long term support. The plan is to provide
security updates and such for several years. (5?)
Edgy development runs alongside Ubuntu 6.06.1 LTS.
Edgy will use newer kernel [2.6.17 or 2.6.18] and have some more hardware support natively.

Anyway as to the 686smp kernel it is a must if you want to get the most out of your Core Duo.

BTW the numbering scheme for the version releases are thus,
the first 6 in 6.06 is the year and the 06 is the month.
So Edgy will be Ubuntu 6.10

---

### Post by arijarot on 2006-09-07
> **Frank Golden said:**
> Hi arijarot,
   Edgy Eft is the next major version of Ubuntu due out in October.
The version your profile shows you using is Breezy Badger which
most folks upgraded to Dapper Drake in June of this year.
Dapper and the other colorful name are code names for the different versions of Ubuntu. Dapper became Ubuntu 6.06 LTS in June. A month ago a new .iso was released called Ubuntu 6.06.1 LTS, the .1 means it has over three hundred patches and updates 
rolled into it since the initial release in June.
The LTS stands for long term support. The plan is to provide
security updates and such for several years. (5?)
Edgy development runs alongside Ubuntu 6.06.1 LTS.
Edgy will use newer kernel [2.6.17 or 2.6.18] and have some more hardware support natively.

Anyway as to the 686smp kernel it is a must if you want to get the most out of your Core Duo.

BTW the numbering scheme for the version releases are thus,
the first 6 in 6.06 is the year and the 06 is the month.
So Edgy will be Ubuntu 6.10


is egdy like 6.06 to 6.06.1 or is is like breezy to dapper? will edgy be stable? what would be the rationale for going from 6.06.1 to 6.10?

---

### Post by TheMono on 2006-09-07
Dapper to Edgy will be like Breezy to Dapper. 6.06 to 6.06.1 was just security / bugfixes.

Edgy will be relatively stable by time of release, though apparently not as much so as dapper is.

---

### Post by arijarot on 2006-09-07
> **TheMono said:**
> Dapper to Edgy will be like Breezy to Dapper. 6.06 to 6.06.1 was just security / bugfixes.

Edgy will be relatively stable by time of release, though apparently not as much so as dapper is.

cool, thanks for the info ! this is my first linux distro , im curious to know what another ubuntu will be like...

---

### Post by Frank Golden on 2006-09-07
> **arijarot said:**
> cool, thanks for the info ! this is my first linux distro , im curious to know what another ubuntu will be like...
Get the Dapper (Ubuntu6.06.1 LTS) desktopCd (liveCD)and try it on your machine. Dapper has a much more polished look compared
to Breezy with more stability. If your machine works well with
Dapper, upgrade. You can do an Upgrade from Breezy but
a fresh install may be better.

---

### Post by arijarot on 2006-09-07
> **Frank Golden said:**
> Get the Dapper (Ubuntu6.06.1 LTS) desktopCd (liveCD)and try it on your machine. Dapper has a much more polished look compared
to Breezy with more stability. If your machine works well with
Dapper, upgrade. You can do an Upgrade from Breezy but
a fresh install may be better.

no no, Dapper is my OS (i.e., my 1st linux distro)... i'm curious to know what another ubuntu (i.e., edgy) is like... but thanks for the advice, i did that and it was helpful the first time round ;)

---

### Post by jdong on 2006-09-08
[http://www.ubuntu.com/testing/knot2](http://www.ubuntu.com/testing/knot2)

If you want to get a "preview" for what Ubuntu Edgy will have to offer over Dapper, you can take a glance at the release notes linked above.

If you are really hands-on curious, every night a snapshot of Edgy is made automatically into a LiveCD, so you can boot into it and try it without disturbing your existing Ubuntu setup. [http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

---

### Post by arijarot on 2006-09-08
> **jdong said:**
> [http://www.ubuntu.com/testing/knot2](http://www.ubuntu.com/testing/knot2)

If you want to get a "preview" for what Ubuntu Edgy will have to offer over Dapper, you can take a glance at the release notes linked above.

If you are really hands-on curious, every night a snapshot of Edgy is made automatically into a LiveCD, so you can boot into it and try it without disturbing your existing Ubuntu setup. [http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

those are two really cool links, thanks, jdong! will this be lts too? can i just upgrade via the terminal?

---

### Post by jdong on 2006-09-08
Edgy Eft will not be a LTS release. It will be supported for "only" 18 months, rather than Dapper's 3 or 5 years. However, I will guarantee you that by the time Edgy's successor comes out, you'll be looking at its release notes, drooling over the new features and anxious to upgrade ;). 18 months is plenty of time for the average user to find a comfortable window of time to upgrade.


And yes, once Edgy comes out, you will be able to upgrade via either graphical tools or the terminal, and there will be easy-to-follow instructions with the Edgy release notes on upgrading.

For the daring, it's even now possible to upgrade to Edgy, but the upgrade procedure is still riddled with hiccups, not to mention Edgy is being actively worked on so that there may be the occasional breaking of something that's sure to tick you off :).. So, it's best to hold off until Edgy's release, or release candidate if you're really impatient!

---

### Post by arijarot on 2006-09-08
> **jdong said:**
> Edgy Eft will not be a LTS release. It will be supported for "only" 18 months, rather than Dapper's 3 or 5 years. However, I will guarantee you that by the time Edgy's successor comes out, you'll be looking at its release notes, drooling over the new features and anxious to upgrade ;). 18 months is plenty of time for the average user to find a comfortable window of time to upgrade. 

yeah, i guess you're right. 18 months is a long time. how'd you know that i was drooling over the release notes ;) i got to say, they really sound amazing!

> **jdong said:**
>  And yes, once Edgy comes out, you will be able to upgrade via either graphical tools or the terminal, and there will be easy-to-follow instructions with the Edgy release notes on upgrading.  

i love how accessible this is!

> **jdong said:**
>  For the daring, it's even now possible to upgrade to Edgy, but the upgrade procedure is still riddled with hiccups, not to mention Edgy is being actively worked on so that there may be the occasional breaking of something that's sure to tick you off :).. So, it's best to hold off until Edgy's release, or release candidate if you're really impatient!

i'll wait till octobre, i'm still breaking in Dapper...i'm not good with hiccups :)

---

