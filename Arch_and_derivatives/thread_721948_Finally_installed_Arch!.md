---
title: "Finally installed Arch!"
date: 2008-03-11
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-03-11
I even have my wireless card working! I started the endeavor at about noon today. It took me three hours! And the worst part is, I don't think I fumbled too much! I think that even if I got "good" at installing Arch, it would take 2.5 hours.

Anyway, pat me on the back or something! I love the idea of everything to do with Arch. I like that it's i686 optimized; I like the idea of rolling releases; I like pacman; I like how there are a few main config files.

My only question now is, how can I setup acpi for my laptop. I just installed it via pacman, but didn't do anything. I would like to enable some power-saving features because I plan on running off of my battery often.

I'm glad to be an official part of the Arch community now!

---

### Post by MisfitI38 on 2008-03-11
Welcome home.

```
pacman -S acpid laptop-mode-tools pm-utils cpufrequtils
```

[http://wiki.archlinux.org/index.php/Cpufrequtils](http://wiki.archlinux.org/index.php/Cpufrequtils)
[http://wiki.archlinux.org/index.php/Pm-utils](http://wiki.archlinux.org/index.php/Pm-utils)
:)

---

### Post by PurposeOfReason on 2008-03-14
If you feel up to it you can compile your own kernel with this patch for powersaving. With all my configs and the few patches I use I went from two hours to 4.25 hours. An hour and ten minutes of that from patching the kernel.

---

### Post by NullHead on 2008-03-14
I'm interested in Arch but I'm more interested in this patch you're talkking about. Where can I find it?

---

### Post by PurposeOfReason on 2008-03-14
> **NullHead said:**
> I'm interested in Arch but I'm more interested in this patch you're talkking about. Where can I find it?
You'll need the one for your kernel version. The newest is here.

[http://forums.gentoo.org/viewtopic-t-667148.html](http://forums.gentoo.org/viewtopic-t-667148.html)

---

### Post by Pogeymanz on 2008-03-14
I'm a little confused about the cpu-freq utility. I installed it and set it to ondemand, which is the recommended one, I believe. 

But it just makes my CPU a lot slower. Down to 183MHz, according to the cpufreq info command. Is that what's supposed to happen? I can see this as useful for extending battery life, but is it supposed to be used when on AC power?

---

### Post by mips on 2008-03-14
Have you tired Klaptop yet ?

---

### Post by PurposeOfReason on 2008-03-14
> **EmosSuck777 said:**
> I'm a little confused about the cpu-freq utility. I installed it and set it to ondemand, which is the recommended one, I believe. 

But it just makes my CPU a lot slower. Down to 183MHz, according to the cpufreq info command. Is that what's supposed to happen? I can see this as useful for extending battery life, but is it supposed to be used when on AC power?
That is correct. Cpufreq is always running and ondemand means it will uses the lowest frequency your processor allows unless it needs more. Powersave is the same but it favors lower frequencies. You can have it switch depending on AC state with laptop-mode-tools.

---

### Post by Pogeymanz on 2008-03-14
Okay, good. I will look into switching it with laptop-mode-tools.

My hibernate/suspend screw up my network manager... But other than that, everything is cool. And I'm sick of tweaking for this week.

---

