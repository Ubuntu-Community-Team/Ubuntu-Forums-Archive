---
title: "Full Ubuntu system backup software and/or strategy"
date: 2023-07-13
forum: Apple Hardware Users
---

### Post by rdnublx on 2023-07-13
I am running Ubuntu 22.04 LTS on Mac, single boot.

I am looking for a software that possibly exists, which would manage incremental backups, pre-scheduled or manual, to an external drive connected via USB-C.

The objective is obvious, i.e. that if disk is lost, to have software which would restore the entire system in one step, or at least with a minimum amount of steps, rather than a tedious setup of a new system piece by piece.

Maybe it's a fantasy, but I have to ask. Thanks.

---

### Post by ajgreeny on 2023-07-13
Moved to **Apple hardware users** for a better fit.

---

### Post by rdnublx on 2023-07-13
It may be that this question is not Mac dependent, because the functionality I am referring to is on the application level. I specified Mac just because it's customary I guess to provide the hardware reference.

---

### Post by rdnublx on 2023-07-13
> **ajgreeny said:**
> Moved to **Apple hardware users** for a better fit.

Respectfully, please consider my point that this question is not confined to Mac users only. Moving my question to this specialized area limits its exposure. It's a Ubuntu / Linux system backup question, IMHO. Thank you

---

### Post by CharlesA on 2023-07-13
See here:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I just use [tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR") for my "backups" but I have no idea how that would handle snaps, since I do not use them.

---

### Post by rdnublx on 2023-07-15
I replied yesterday but it did not get posted for some reason (token something).
Anyway, thank you for the link, good info

---

### Post by DuckHook on 2023-07-15
I note that you want to avoid the "tedium" of restoring your apps. Since this is not my own philosophy, I can only give you a bird's&#8209;eye view of my thoughts.

[LIST]
[*]I back up only my critical data, but I back that up religiously. In fact, I both back up and separately clone such data for redundancy. I've learned from past experience that there's no such thing as too many backups.
[*]On the other hand, I never back up apps. What I do instead is keep a list of the apps that I have installed in my system. When (not if) I suffer a catastrophic disk/system failure, it is a simple matter to just reinstall the apps.
[*]In my case, reinstalling apps is made almost painless by my practice of keeping the base OS absolutely pristine with as few apps added as possible. Frankly, my bare metal OS is basically a virgin install kept in its default state.
[*]Pretty well all of my apps are all hived off into containers. These are backed up and cloned separately. This keeps their settings exactly the way I like them. If my main box goes down, it is child's play to spin up my backup box and I have all of my apps (and data) exactly the way they were on the main box.
[*]Essentially, by keeping my base OS free of apps, I avoid most of the trouble that brings users to these forums. Network upgrades are also trouble&#8209;free, since they are basically being applied to a default configuration.
[/LIST]

Before I segregated all of my apps to containers, I still followed the above measures and only backed up data. I found that backing up the whole system was not worth the effort and was often counterproductive. It takes me less than an hour to reinstall a brand new system and the all of the apps that I use (which are a large number). In the process, I will improve on app configurations that I was too lazy to change before. I also have the assurance of cleaning out cruft, problematic cache data and even possible malware that may have made it into the system. When a system bites the dust, it is too time consuming and frustrating to chase down cause, so a pristine install is usually preferred anyway.

My philosophy is opposite to yours and may not suit you at all. Hopefully, it at least gives you a different perspective and serves as food for thought.

---

### Post by rdnublx on 2023-07-18
Thank you for your perspective, it certainly should help me find a balanced approach.
You  and I are not that opposite wrt a backup approach as it appears to be. I  am also just slightly paranoid about losing data, hence always try to  have redundant and repeatable backup process, which I would not need to  reinvent every other day. Hence my question about a tool or a "one  button" process of backing up the entire system. I guess it's driven by  my experience of using Mac for many years, where Time Machine provides  that, albeit with some quirks and idiosyncrasies. I just don't like to  create open ended situations, where my recovery from a disk failure  would be a character building, tedious, piecemeal project. Your  perspective plus the link posted by CharlesA provide a good start for  me. Thank you.

---

