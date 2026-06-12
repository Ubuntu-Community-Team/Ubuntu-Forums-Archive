---
title: "Ubuntu freezing for no reason"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by kitsuna on 2007-09-15
So yeah, just got convinced to dual boot 64 bit Ubuntu on my comp the other day.

 I was reformatting my computer anyway, and now I'm running WinXP and Ubuntu. So, after I've got everything installed nice and fresh, (after getting GRUB loader to find both windows and ubuntu, a process that took much editing of menu.lst and rebooting of Ubuntu with no problem)

 I restart, log on to XP to put all my stuff back where it was. No problemo. I restart my computer and then leave it, knowing full well it will automatically boot into ubuntu by default and go and have my breakfast.

I come back, at the user login screen, and everything is frozen. No mouse, no keyboard, nada. So I shrug my shoulders, hit the reboot and wait for ubuntu to show up again. I manage to log in this time, and start going about my business. I open up Firefox and everything is fine. At some point, it just freezes again. No mouse, no keyboard. Nada. I turn over my mouse, and the optical mouse light has gone out. It's not even registering anymore. Fine. Reboot, retry. Get all of 5 minutes worth of use out of Ubuntu before the same thing happens again. WHY!?

It worked fine yesterday straight after install. I know it's not my hardware, because windows has no problem with either my mouse or keyboard and (believe it or not) has yet to freeze. Any ideas why?

I'm running:

AMD Athlon 64 3700+ 
2gb Corsair RAM (2x 1024)
GeForce 7800GT

I've got Beryl installed but not running. I have no idea why this is happening because it was working fine while I was messing around with menu.lst to get the grub loader to find my windows partition last night. 

The version of Ubuntu I'm running is the 64 bit version of Feisty Fawn 7.04

---

### Post by Hospadar on 2007-09-16
I had a similar problem a while ago and for some reason It was being caused by the wifi reciever I was using, got a different reciever and no more problems.  I really couldn't tell you why It was doing that though.  You might either, try sytematically removing peripherals to see if one is causing some error, or try 32 bit ubuntu.  For 99% of users I think you will find that the added stability of 32 bit far outweighs the generally not noticible drop in performance.  (usually you are only using <2-5% of your cpu anyways)

---

### Post by asmoore82 on 2007-09-16
It's the nVidia video card...
I'm actually looking at one right now that will do the same thing;
freeze in Linux but not in Windows.

That would seem to prove some bug in the nVidia driver;
however when it happened before I bought the same model nVidia card again
and the problem was solved. That's the same computer, same RAM, same HD,
same OS, same drivers, new Video Card, no problem which would seem
to prove some problem with the card.

I know it won't help you out,  but being a non-Windows user;
I like to point to this situation as proof that Linux actually uses
the whole card but Windows does not.

---

