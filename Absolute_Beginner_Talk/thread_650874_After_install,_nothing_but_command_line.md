---
title: "After install, nothing but command line?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by gruss on 2007-12-26
Went ahead and tried to throw a copy of xubuntu on an old pIII machine, set up the partitions started the load walked away for a bit came back answered a couple questions and it asked for a reboot.  Started up got the Hamster ball thingy, stuck for a little bit on installing hardware drivers but continued then only came up to command line, no errors.  I'll admit I didnt mess around with it a whole lot afterword...not my primary pc, just wondering if there is something I can try real quick to get to the gui before I try to reinstall?
Is this a vid card problem?  I think I have an old (like at least 4 years old) nVidia in it.I have an old ATI all in wonder I could throw in too if Nvidia and xubuntu dont gel well.  Would be a performance hit but this is just gonna be a file server/kids playing on barbie pc anyway so I don't really care.  Easy way out is fine by me ;)  Any hints would be appreciated!

---

### Post by overdrank on 2007-12-26
> **gruss said:**
> Went ahead and tried to throw a copy of xubuntu on an old pIII machine, set up the partitions started the load walked away for a bit came back answered a couple questions and it asked for a reboot.  Started up got the Hamster ball thingy, stuck for a little bit on installing hardware drivers but continued then only came up to command line, no errors.  I'll admit I didnt mess around with it a whole lot afterword...not my primary pc, just wondering if there is something I can try real quick to get to the gui before I try to reinstall?
Is this a vid card problem?  I think I have an old (like at least 4 years old) nVidia in it.I have an old ATI all in wonder I could throw in too if Nvidia and xubuntu dont gel well.  Would be a performance hit but this is just gonna be a file server/kids playing on barbie pc anyway so I don't really care.  Easy way out is fine by me ;)  Any hints would be appreciated!

HI and could you tell us the graphics card that is install?

---

### Post by p_quarles on 2007-12-26
nVidia cards work *much* better with Linux than ATI cards. Intel cards work better than either of them.

Anyway, try starting the GUI. It may not work, but the error output could lead to a clue:
```
sudo /etc/init.d/xdm start
```

---

### Post by chebuntu on 2007-12-26
Hi Gruss, 

Try typing "startx" (without quotes) at the command line.
If that doesn't work try "init 5"

(These commands should both take you to the graphical logon screen.)

Hopefully...

Cheers,
Che

---

### Post by gruss on 2007-12-27
Sweet, I'll try that before re-installing.  If I get an error message I'll post that so hopefully someone can give me a clue where I screwed up.  If its really bombed it'll have to wait until the weekend when I have some time to geek then I'll be on here pestering ;)

Gotta say again, this place rawks.

---

### Post by gruss on 2007-12-27
None of those commands worked, so I just re-installed.  After that I realized I didnt set a password up.  I could log in as root <blank> before the re-install but couldnt do anything.  I set up a password this time and viola.  I guess ya gotta have a password?  I feel kinda silly now but hopefully someone will learn from this...unless of course it was just a glitch and I'm talkin out my butt.  Issue resolved nonetheless

---

