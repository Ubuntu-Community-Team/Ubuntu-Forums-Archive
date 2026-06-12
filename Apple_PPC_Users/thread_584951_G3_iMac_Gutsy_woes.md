---
title: "G3 iMac Gutsy woes"
date: 2007-10-21
forum: Apple PPC Users
---

### Post by ffooky on 2007-10-21
I've installed Gutsy on my 600MHz G3 iMac and encountered the being dropped to BusyBox issue. I ran```
modprobe ide_core
exit
```and things looked good. I get to the user and then password fields but here is where it gets sticky. My desktop loads but incredibly slowly, maybe ten minutes until it looka how I imagine it should. If I move the mouse it takes around 10-15 seconds to register and clicking on anything in the menubar has no effect. I'm guessing that maybe the desktop effects are too processor hungry but once on my desktop all I can do is hit the force restart button.

 Has anyone else encountered this or has an idea as to what I can do.

 I installed from the alternate BTW, having reformatted my (perfectly functioning :() Feisty partition.

---

### Post by nkbj on 2007-10-21
I have installed Gutsy on a 350MHz G3 iMac without any major problems (except the ide_core thing). It works reasonably fast except when I hit the icon in the top right corner it takes about one minut before the shut-down window appears.

Try to look at the System -> Preferences -> Appearance (?) menu and set desktop effects to "None".

Regards,
Niels Kristian

---

### Post by Caraibes on 2007-10-21
First, thank you for the tip, as I was stuck at the busybox stage while booting !

I have a G3 iBook. 

I experimented this week-end, as I had 2 alternate cd's for ppc: Dapper & Gutsy.

Dapper installed fine, no problem whatsoever. it worked good. But it is slightly outdated today, so this morning I wiped it and installed Gutsy. The install was about the same.

But the very bad surprise is that it won't boot normally. First, one has to wait about 5 mn, seeing a paralyzed boot-bar. Then it goes into Busybox. I am glad I read this post, as I would never have found an answer ! I can't imagine keeping a system that way !

Once inside, there's no sound. There's an error message with some Gnome daemons... Sound worked perfect with Dapper...

I am wondering if Ubuntu PPC is going down the drain...

---

### Post by ffooky on 2007-10-21
> **nkbj said:**
> Try to look at the System -> Preferences -> Appearance (?) menu and set desktop effects to "None"That's the annoying thing...I'm pretty sure that that's what the problem is but I can't get anything to respond once it boots to the desktop. I've tried hitting control-F1 to try to get something, anything accessible but it just won't play nice. Thanks for the advice though.

---

### Post by linear on 2007-10-22
> **ffooky said:**
> That's the annoying thing...I'm pretty sure that that's what the problem is but I can't get anything to respond once it boots to the desktop. I've tried hitting control-F1 to try to get something, anything accessible but it just won't play nice. Thanks for the advice though.

Fresh install? Did you remember to disable DRI? See the [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70").

---

### Post by ffooky on 2007-10-22
> **linear said:**
> Fresh install? Did you remember to disable DRI? See the [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70").Yep, fresh install. I can't get to disable DRI etc because once booted nothing will respond.

---

### Post by linear on 2007-10-23
If you boot from the alternate install you should be able to get into recovery / rescue mode and edit xorg.conf from there.

---

### Post by nkbj on 2007-10-25
Or just type "Linux single" at the boot prompt. Ubuntu will start in single user mode then and give you a shell prompt with root permissions.

Regards,
Niels Kristian

---

