---
title: "Upgrading Ubunut 6.06 LTS"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by slwory on 2008-01-19
I type this in terminal:

gksu "update-manager -c"

and get:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

It says my system is up-to-date also. If I add in -d, I am able to upgrade to 8.04. Obviously I'd rather not use that version as it's not even beta yet.

I upgraded 6.06 before on another PC but it won't work on my laptop (dell vostro 1500). Any ideas?

---

### Post by akniss on 2008-01-19
> **slwory said:**
> I type this in terminal:

gksu "update-manager -c"

and get:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

It says my system is up-to-date also. If I add in -d, I am able to upgrade to 8.04. Obviously I'd rather not use that version as it's not even beta yet.

I upgraded 6.06 before on another PC but it won't work on my laptop (dell vostro 1500). Any ideas?

You might consider waiting until Hardy (8.04) is released.  There will be a supported upgrade path from LTS to LTS, so Dapper > Hardy will be supported officially.  If you really want to get gutsy running, you'd probably be better off with a fresh install.  An upgrade from Dapper to Gutsy is not supported, so you would have to go through the whole Dapper > Edgy > Feisty > Gutsy path... not worth the time in my opinion.

---

### Post by slwory on 2008-01-20
Ah, I see! Thanks! I'll wait then. 

If I install programs will they run through the update fine?

EDIT: Also when I upgraded my 6.06 it upgraded programs, ex: gaim -> pidgin. How do I do this?

---

### Post by candtalan on 2008-01-20
> **slwory said:**
> Ah, I see! Thanks! I'll wait then. 
If I install programs will they run through the update fine?
EDIT: Also when I upgraded my 6.06 it upgraded programs, ex: gaim -> pidgin. How do I do this?

A version upgrade process will typically  be able to upgrade most things particularly if they were in the original version. However, I notice when upgrading 7.04 to 7.10 that some things I had were declared as  not upgradeable, and I decided to keep it simple and gave the upgrade process permission to remove them. The upgrades I have done on several machines have gone well.

---

### Post by Papa-san on 2008-01-20
Watch out for letting the upgrade manager (?) have permission to change things! If you have had to fuss with anything like wireless or video, you need to tell it to keep your previous settings. If you don't, you will be starting from ground zero to make those things work again! I learned this the hard way... on a Dell...

---

### Post by slwory on 2008-01-20
Thanks guys. Any idea of how I can get Pidgin? I found a thread here but the links they gave aren't working

---

### Post by akniss on 2008-01-21
> **slwory said:**
> Thanks guys. Any idea of how I can get Pidgin? I found a thread here but the links they gave aren't working

You might try this site.  It seems to give good instructions on building pidgin from source.
[http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

---

### Post by Majorix on 2008-01-21
I wouldn't rely on the fact that it will be supported to upgrade from 6.06 to 8.04 too much. There is appr. 2 years of time in between, tens of thousands of updates, and so on. If you are an LTS camper, I would still wait for 8.04 but then do a fresh install. You won't regret it as otherwise you will have too many problems updating and even if you successfully update in some magical way you will have terrible speed issues.

---

