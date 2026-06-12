---
title: "Feisty - 'Development Branch'?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by dboyd13 on 2007-04-20
Hi All,

Last night (GMT+8 ) Update Manager on my Egdy installation informed me that the new 07.04 version was available. I performed the update via the GUI update manager... but strange thing is that **lsb_release -a** displays the following:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu feisty ([COLOR="Red"]development branch[/COLOR])"

Why would it show development branch? as I believe that I updated to the final release not the beta?

Any ideas on how to update and/or correct?

Thanks.

---

### Post by dboyd13 on 2007-04-23
Any idea's on this one please?

---

### Post by zvacet on 2007-04-23
I must say that I don´t understand what is going on.Try with this and see 

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by igknighted on 2007-04-23
> **zvacet said:**
> I must say that I don´t understand what is going on.Try with this and see 

```
sudo aptitude update && sudo aptitude upgrade
```

No, he upgraded and it worked, but now it reports to be Feisty (development branch).

@ the OP: I would guess it was an oversight by the devs, if you are using feisty repos and are fully upgraded/dist-upgraded etc. then you are running feisty final.

---

### Post by dboyd13 on 2007-04-24
Thanks for the feedback. I'm afriad that I've been experiencing quite a few issues after the upgrade from edgy. Once I get a chance to backup my data, I will do a fresh install of 7.04 from the live CD.

---

