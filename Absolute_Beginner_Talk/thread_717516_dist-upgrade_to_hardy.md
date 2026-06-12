---
title: "dist-upgrade to hardy"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by adredz on 2008-03-07
I know its alpha, so please spare your words...:)

So, how do I upgrade from gutsy to hardy? Someone told me to add the source.list thing and all, but I didn't understand it. I am pretty new to Linux so please be newbie friendly. If possible provide your answer in detail. I'd really appreciate your help..:)

Thanks!

---

### Post by kesman on 2008-03-07
Best way would be a fresh install, since there's usually problems with updating your ubuntu version. 

**Note that dist-upgrade doesn't mean upgrading to the newest ubuntu version.**

---

### Post by adredz on 2008-03-07
kesman: 
ok, I didn't know that...

Thanks!

---

### Post by Madpilot on 2008-03-07
> **adredz said:**
> . I am pretty new to Linux so please be newbie friendly.


Honestly, if you're 'pretty new to Linux', leave Hardy alone until it's actually released in April. Personally, I try the alpha versions off LiveCD, but I never update/upgrade my installed Ubuntu until final release...

If you want to try it, and it breaks, just remember that you get to keep all the pieces!

---

### Post by gfg on 2008-03-07
> **adredz said:**
> kesman: 
ok, I didn't know that...

Thanks!

If you would like to update before it's officially released, you can open the terminal, type in gksudo gedit /etc/apt/sources.list, and change all gutsy to hardy. As mentioned this can be a bit risky and I wouldn't recommend it if you are not familiar with ubuntu. When Hardy is officially released you can go to the update manager and chose upgrade to Hardy. It may cause some problems for some people, but for me it worked.

---

### Post by skymera on 2008-03-07
if you want to know.

```
 update-manager -d 
```

note, this most likely will break your system.

but good luck, my firend uses and he says everything works sort of good, apart from bash.

---

### Post by overdrank on 2008-03-07
> **adredz said:**
> I know its alpha, so please spare your words...:)

So, how do I upgrade from gutsy to hardy? Someone told me to add the source.list thing and all, but I didn't understand it. I am pretty new to Linux so please be newbie friendly. If possible provide your answer in detail. I'd really appreciate your help..:)

Thanks!

Hi and I would suggest using a separate partition if you are going to install Hardy, this link may help also
[https://wiki.ubuntu.com/HardyHeron/Alpha6](https://wiki.ubuntu.com/HardyHeron/Alpha6)

---

### Post by kesman on 2008-03-07
> **Pokerface1969 said:**
> No I'm not.. Should I be?  What is Ubuntu?

This made me laugh so hard =DD

---

### Post by Paqman on 2008-03-07
> **kesman said:**
> Best way would be a fresh install, since there's usually problems with updating your ubuntu version. 


That depends. Both times i've upgraded  i've had no breakage at all. If you've not messed about with your system too much and you're only using packages from the repos you should be alright. Best to disable any weird repos before performing the update as a precaution.

**adredz:**
When an upgrade to Hardy is available it will show up automatically in the updater. The update takes a while though, so some people like to just to the fresh install.

---

