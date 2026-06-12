---
title: "Why is KDE such a memory hog?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-12-12
I am already running Ubuntu 6.10 on my older PC (PIII 1.2 GHz, 384 MB RAM) and before that I was running 5.10 then 6.06, but before upgrading to 6.10 I tried to install Kubuntu 6.10. I kept it for a few days then installed Ubuntu.

KDE was such a system resources hog. I know that this old PC is not the best out there, but GNOME ran fine. (At rest, KDE will use ALL of the 384 MB RAM)

I decided to give KDE another try and installed it along with Windows XP (but on another HDD) on my main PC (P4 2.4 GHz, 1 GB RAM). But again at rest, the memory usage is close to 400 MB, and I was running Automatix2 to install some packages (downloading, not installing) and checked the Performance Monitor and found that the memory usage was about 950 MB!!! The CPU load was about 10-20% and there was no swap memory used, but 950 MB RAM, come on! This never happened to me in Windows XP (even when running a system hog application like Azureus) and even when I was playing Battlefield 2 and press Alt-Tab the total memory usage then was about 800 MB with 500 MB allocated to BF2. Hell, on my old PC (running Ubuntu) even with Azureus running and Firefox running, memory usage is about 250 MB (out of the 384 MB on that system).

So my question is: WHY? What does KDE do with all that RAM? I do confess that I am a GNOME fan, but after this, I am a GNOME *exclusive* user. Or is there something I am doing wrong?!!!

---

### Post by HokeyFry on 2006-12-12
i dont know why, but i do know that KDE uses alot more memory than gnome, though it *does* look somewhat nicer

---

### Post by Amorphous_Snake on 2006-12-12
But don't you agree that this is *too much* RAM?!

There must be a *leak* somewhere!

---

### Post by aysiu on 2006-12-12
Actually, the general Linux principle is "unused memory is wasted memory."

Read more here:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

If you're worried about *performance*, though, instead of just numbers, I would advise using *kde-core* instead of *kubuntu-desktop*:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by Arisna on 2006-12-12
Kubuntu uses a lot of memory on my PC, too.  It isn't your fault, but KDE is a big, heavy environment.  A lot of people, such as yourself, do not like that.  Personally, I think it's worth it for the neat little details in KDE such as advanced Samba configuration from the GUI, KIOSlaves, and some other cool little apps that have really grown on me.

---

### Post by kinematic on 2006-12-12
it's a myth that kde is a memory hog.
read this [http://ktown.kde.org/~seli/memory/](http://ktown.kde.org/~seli/memory/) ;)

---

### Post by Amorphous_Snake on 2006-12-14
So, I guess that it's safe to have all the free RAM used as long as this doesn't decrease performance?!

---

### Post by muep on 2006-12-14
Actually using the RAM increases performance, because the stuff loaded there can then be fetched faster. If more memory is needed by a program and no free is available, it is very quick to shink the cache a bit.

---

### Post by Amorphous_Snake on 2006-12-14
That's not what I have seen in Windows! The more RAM Windows used, the lower the performance I get. But anyway, that's in Windows! Long live Linux!

---

### Post by tumler on 2006-12-15
Being a KDE user myself, I remember you gotta be weary of what program you use to monitor the performance, (I'm not on KDE atm) IIRC Ksysinfo jacks up the load on the system quite abit which in turn doesn't give complelety true results of performance.

---

### Post by talkingwires on 2006-12-15
> **Amorphous_Snake said:**
> But anyway, that's in Windows! Long live Linux!Whiskey. Tango. Foxtrot.

---

### Post by Amorphous_Snake on 2006-12-16
I take it back!

It turns out that KDE is not that bad. I sure like GNOME better but when I got a little more into KDE and learned how to tweak things a little, it turns out to be pretty good.

And regarding RAM consumption, I did "free -m" on Ubuntu on my old PC and I found that out of the 384 MB available, only 2 were free. So, I guess that all Linux uses up RAM a lot but without degrading performance. And also the graphical ways to see RAM consumption are not reliable.

---

### Post by lucky_chouhan on 2006-12-18
my system is running ubuntu 6.06 with KDE and system use only 60 - 70 MB in my total 512 MB.

---

