---
title: "Why has my hard disk started to go crazy after booting up for about 15 mins?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-12-05
My harddisk is going mad for ages after i boot up, what could it be? I do have a backup script that is set to run at 4am using cron. If this task is not performed on time because PC is off, will it run when i turn the PC on? Its the only thing i can think of :/

---

### Post by philinux on 2007-12-05
More likely its trackerd, you can disable this too.

system>prefs>indexing.

Fire up system monitor though just to make sure.

---

### Post by Vadi on 2007-12-05
I _hate_ the tracker. It's default settings are absolutely horrible and looking at them, they couldn't be worse.

It even manages to lock up my new 7200rpm drive. Gah.

---

### Post by fmartinez on 2007-12-05
if your computer is not on to run cron at the specific times... it wont run again when you power on you PC.

---

### Post by dgrafix on 2007-12-06
thanks 4 the info

---

### Post by dgrafix on 2007-12-06
what does the indexing actually do, what will happen if i disable it_ im guessing it makes things like the locate command etc a lot slower,

---

### Post by philinux on 2007-12-06
I think it makes searching for stuff much quicker as it has a database index. I think its best run manually when you want it, much like updateb was in Feisty.

---

### Post by FuturePilot on 2007-12-06
> **dgrafix said:**
> what does the indexing actually do, what will happen if i disable it_ im guessing it makes things like the locate command etc a lot slower,

Tracker is not connected with the commands like locate. It's a separate search tool. If you disable it you just won't be able to use the Tracker Search Tool to search for files. But it won't effect anything else.

---

