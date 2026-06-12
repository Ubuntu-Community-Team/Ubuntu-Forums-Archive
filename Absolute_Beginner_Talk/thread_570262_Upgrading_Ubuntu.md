---
title: "Upgrading Ubuntu"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by hurleyint1386 on 2007-10-08
I'm fairly new to Ubuntu. I recently installed it on my ThinkPad, and since 7.10 is being released very soon, what will I need to do to upgrade from 7.04? Will it be as simple as 'sudo apt-get update' then 'sudo apt-get upgrade'? or will there be much more to that?

---

### Post by hurleyint1386 on 2007-10-08
wow, this got bumped to the bottom pretty quick. can anyone tell me?

---

### Post by hyper_ch on 2007-10-08
did you use the search function?

---

### Post by Circus-Killer on 2007-10-08
well, if you wait till release day, then after release day update-manager will automatically let you know that there is a new version available, and give you the option to upgrade.

if you want to force upgrade-manager to see that theres a new version of ubuntu **before release day** then you can just press alt + f2 and then enter the command:

```
update-manage -d
```

that command will start update manager in a way that will allow you to upgrade to the next version while its still beta.

before upgrading though, i highly recommend you backup all your personal files, as upgrading doesn't work for everyone. i tend to stick to fresh installs most of the time myself, but to each their own.

PS: hyper_ch, if you dont have something on topic to add, then don't say it. posts like "search for your problem" does not help anyone.

---

### Post by misfitpierce on 2007-10-08
I'd recommend you wait till release day Oct. 17th for stable release of 7.10. Update manager will notify you on that glorious day. :)

---

### Post by hurleyint1386 on 2007-10-08
> **Circus-Killer said:**
> well, if you wait till release day, then after release day update-manager will automatically let you know that there is a new version available, and give you the option to upgrade.

if you want to force upgrade-manager to see that theres a new version of ubuntu to see then you can just press alt + f2 and then enter the command:

```
update-manage -d
```

that command will start update manager in a way that will allow you to upgrade to the next version while its still beta.

before upgrading though, i highly recommend you backup all your personal files, as upgrading doesn't work for everyone. i tend to stick to fresh installs most of the time myself, but to each their own.

PS: hyper_ch, if you dont have something on topic to add, then don't say it. posts like "search for your problem" does not help anyone.

hey, i appreciate it a lot. I wasn't sure if this would be an update that would be in the update manager. i'm sure i'll be asking plenty of questions. i'm a mac person, and im looking to triple boot. i've been using linux for years (mainly gentoo) but not extensively, just to mess around and learn. i really like ubuntu. i've now got my macbook pro with os x, my thinkpad t42 with windows and my thinkpad x31 with ubuntu. i'm a software/web developer, so having everything right in front of me is very useful

---

### Post by hurleyint1386 on 2007-10-08
> **misfitpierce said:**
> I'd recommend you wait till release day Oct. 17th for stable release of 7.10. Update manager will notify you on that glorious day. :)
absolutely. i plan on it. that's why i didnt download the beta and install it. i'll wait for the stable relase

---

