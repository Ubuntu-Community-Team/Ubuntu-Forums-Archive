---
title: "Feisty Fawn Ubuntu 7.04 / Gnome seems sluggish"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by issai on 2007-11-26
My Ubuntu 7.04, or Gnome, running under VMWare Server 1.0.4 seems very sluggish. I've been *VERY* hesitant to kill off Ubuntu only because I'm impressed with its features and capabilities. I will unfortunately have to revert back to Windows if I can't make Feisty Fawn frolic significantly snappier in the next few days.

**My Hardware Config:**

- Dell Vostro 1500 notebook
- 4 GB RAM
- nVidia GeForce 8400MM GS 256MB RAM
- 80GB HD (20GB Free)

**My OS / Software Config:**

- Base OS: Windows XP SP2

- VMWare Server 1.0.4

- 1 VMWare VM w/ Windows Server 2003 EE w/ 1 GB RAM allocated in VMWare, UI responds almost just as quickly as base OS aka very snappy!

- 1 VMWare VM w/ Feisty w/ 1 GB RAM allocated in VMWare, everything from mouse cursor redraws to simple window maximize / minimize stutters nearly all the time, from bootup to shutdown, regardless if it's the terminal, Firefox, Evolution, or System Monitor. You name it.  Heck, it's just as slow as running it natively on my ol' Thinkpad T40 w/ 1 GB of RAM (w/ a 1st-gen Centrino CPU, etc.)

Any help would be appreciated. I've done multiple searches on these here forums using keywords such as "vmware", "gnome", "slow", "lag", "sluggish", and haven't found any suggestions or advice that jump out.

Also, I'm not interesting in very extensive "hacks" which will compromise or cripple functionality and features.  Functionality rocks and is all there-- it's really just the speed that needs a major ***-kickin'.

Thanks in advance.

---

### Post by jordanmthomas on 2007-11-26
Have you installed VMWare tools in it?
Moving windows around will still be a little slow but this should fix your mouse cursor issues (among other things)

---

### Post by issai on 2007-11-27
Yup, VMWare Tools installed quite a while ago.

---

### Post by jordanmthomas on 2007-11-27
Well, then, barring that something's eating up all the CPU or something (which it doesn't appear to be since you didn't mention it) I'm not sure what's wrong.

> Heck, it's just as slow as running it natively on my ol' Thinkpad T40 w/ 1 GB of RAM (w/ a 1st-gen Centrino CPU, etc.)
That computer sounds faster than mine and I'd say Linux is anything but sluggish for me.

---

### Post by issai on 2007-11-27
Well, I'll be.

Installed Feisty under VirtualBox, and so far, it's running like a dream!  (still downloading updates right now, but Firefox runs very nicely)

Now, a question I have is why VB allows a max video resolution of only 1024x768 for my Feisty VM when, under VMWare, I was able to take it up to the supported max resolution of 1280x800 (widescreen)...

---

