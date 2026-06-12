---
title: "[SOLVED] installing wine from a jump drive"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by piperdown10 on 2008-03-12
What files would I need to download to install wine from a jump drive? I followed the repository links and got a *.gz file. I extracted it to my desktop and turned out to be a text file.

Unfortunately I don't have access to the internet from home (I'm at work now) and can not use the conventional method. If getting it through apt-get is the only way, I'll get online tomorrow from my 'rents.

---

### Post by piperdown10 on 2008-03-12
So I went to WineHQ's site and looked for any other files that I might have missed and didn't see anything. I also looked at tutorials here in the Wine section and I can't seem to find anything.

---

### Post by mc4man on 2008-03-12
Your best bet is to install the first time online, then you can use your flash drive for future updates. If you want to try you can get the wine deb here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
your problem will be depends that aren't installed and if those have depends of their own ect. which leads to an impossible situation
You _may_ have everything you need with the exception of 2 packages which would need to be installed first   (for gutsy)
binfmt-support    1.2.10
libaudio2            1.9.2
pay attention to versions

[http://packages.ubuntu.com/gutsy/admin/binfmt-support](http://packages.ubuntu.com/gutsy/admin/binfmt-support)
[http://packages.ubuntu.com/gutsy/libaudio2](http://packages.ubuntu.com/gutsy/libaudio2)

---

### Post by piperdown10 on 2008-03-12
Okay, I'll just do it the regular way.

Thank you.

---

