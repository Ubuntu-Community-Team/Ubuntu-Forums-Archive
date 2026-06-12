---
title: "my notebook gets really hot"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-24
ok i download stuffs at night.. so i keep my notebook on.. and i close it once i wake up in the morning.. i always do that but since i installed ubuntu.. it gets really hot like i can boil egg on it... im scared if it melts down.. i didnt have this problem with xp.. xp did make it hot but not this much.. is there anything that can make is less warm or cool ?

---

### Post by lamalex on 2007-03-24
i have this same problem but only when I close the lid and leave it on, if i leave the lid open and leave it on it does not get so hot. Something about acpi power handling I bet. Unfortunately I don't know a fix. try posting a bug report at launchpad, i've been meaning to but havn't had time :(  ... i guess i could be doing that now.

---

### Post by HunkieChan on 2007-03-24
hey i have the same problem.. it gets hotter when i close the lid.. damn it.. i wish anyone can come along and help us.. this launch pad gets the complicated.. too rough and tough for my brain

---

### Post by josephus on 2007-03-24
I haven't run into this problem myself, but couldn't you manually scale down the frequency if you are planning to leave it on at night (i'm guessing it's the cpu that generating the heat).  I use a gnome applet (EmiFreq) that allows me to monitor and set the cpu frequency.

---

### Post by raffytaffy on 2007-03-24
few things about hot notebooks ; in command line type "uname -a" and see if its "SMP".
next ..is your notebook pentium? pentium M perhaps? if so..its a common bug. you need a non-smp kernel.

---

### Post by HunkieChan on 2007-03-24
> **raffytaffy said:**
> few things about hot notebooks ; in command line type "uname -a" and see if its "SMP".
next ..is your notebook pentium? pentium M perhaps? if so..its a common bug. you need a non-smp kernel.

its not pentium.. its amd mobile sempron

is there a cure ?

---

### Post by HunkieChan on 2007-03-24
> **raffytaffy said:**
> few things about hot notebooks ; in command line type "uname -a" and see if its "SMP".
next ..is your notebook pentium? pentium M perhaps? if so..its a common bug. you need a non-smp kernel.

yeah it does say SMP.. any solution ?

---

### Post by lamalex on 2007-03-24
Mine is also AMD. Mine is a Turion 64. I posted a bug report [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/95537](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/95537) so go add your input!

---

### Post by HunkieChan on 2007-03-24
> **Iamalex said:**
> Mine is also AMD. Mine is a Turion 64. I posted a bug report [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/95537](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/95537) so go add your input!

ill do it.. right away

---

