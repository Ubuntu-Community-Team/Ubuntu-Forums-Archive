---
title: "Upgrading Dapper to Edgy"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-26
I can update Dapper to Edgy using **gksudo "update-manager -c -d"** right? And if I do so, will I lose certain configs like my wireless network one? Thanks.

Also, is Edgy stable like Dapper?

---

### Post by ishimaru_kaito on 2007-03-26
From experience, you do tend to lose some custom settings.  Best to either note the FAQ's/HowTo's or back up the relevant config files.  :(

---

### Post by .oops on 2007-03-26
I configured my wireless network through **iwconfig**, so it shouldn't be hard to do it again. If something fails, can I downgrade?

---

### Post by jem7v on 2007-03-26
"Downgrading" isn't really an option, but if you move your /home folder to a seperate partition and things go nasty, you can just reinstall Dapper and leave your /home folder untouched.

I find Edgy a lot more stable in some ways, but I also know that a fresh install of Edgy is usually more stable/less buggy than a Dapper-Edgy upgraded installation.  Thus, rather than upgrading I just put my /home folder in a different partition and do a clean install when new releases come out. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) talks about how to do this, I believe.

You Could just wait 3 or 4 weeks and do a fresh Feisty install instead of moving to Edgy, but Edgy might possibly maybe be more stable than Feisty for the first couple of weeks after it's released.

---

### Post by zvacet on 2007-03-27
upgrade command is
```
gksu "update-manager -c" 
```

---

### Post by .oops on 2007-03-27
I guess I'll wait for the end of April for Feisty. Should be kinda stable by then, and by then I should have a better understanding of how things work in a linux distro. Thanks.

---

### Post by kethtejoh on 2007-03-30
this is my first time posting in this forum, and i'm a total noob when i'm in linux..
can anyone tell me how can i upgrade to 6.10 as my update manager can't detec it.... can anyone help me out?

---

### Post by gardara on 2007-03-30
> **kethtejoh said:**
> this is my first time posting in this forum, and i'm a total noob when i'm in linux..
can anyone tell me how can i upgrade to 6.10 as my update manager can't detec it.... can anyone help me out?

check this out: [http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html)

:)

---

