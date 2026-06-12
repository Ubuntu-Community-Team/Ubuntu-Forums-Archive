---
title: "connecting WinXP to Internet through Ubuntu?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by dijxtra on 2007-03-18
Hello everybody,

I'm a Windows user ready to migrate to Linux. They say that Ubuntu has the biggest community these days, and I see that brand new version is planed for next month, so Ubuntu is an obvious choice. I tried to migrate to SuSe 9 a year ago, and that effort failed... but I'm quite confident that now I'm ready, provided that I figure out two things:

1. I have GRUB with WinXp as default boot option, and then SuSe 9 and some version of Ubuntu I installed for some reason a year ago. The GRUB was installed by SuSe. Is it possible for me to leave the bootloader untouched and just put the new Ubuntu in the place of the old version?

2. Now a reason why I still haven't migrated to Linux (even though I saw Richard Stallman IRL and have been infected by his "free software!" battlecry): my machine is connected to ADSL modem (LAN version), and my sister's machine is connected to my machine (by LAN cable). Getting her connected to the Net was peace of cake (with both systems running WinXP): I ran the Network Setup Wizard on both sides, and voila, she can chat with her girlfriends. Now, she won't migrate to Linux anytime soon, so I'd like to know how complicated is it to let her WinXP connect to Internet through my Ubuntu? Is there a tutorial of some kind?

And just a another one: is it better to install Ubuntu, and then compile KDE (I've done that before, it shouldn't be that much of a problem) or just to get myself Kubuntu at the first place? What's the difference?

Thanks for the input in advance. :-)

---

### Post by alamba on 2007-03-18
Here's the bit I can answer to a degree of confidence:

1. You can upgrade your current installation of ubuntu and keep the grub. Or you could use manual partitioning and delete the old ubuntu partition and reuse it for the new install. Grub would probably get re-written but it should find the other two OS's and put you back in shape.

2. The "Internet Sharing" bit u're talking about is a piece of cake in Ubuntu too. Just apt-get firestarter. A few clicks and it sets up internet sharing. A bit of google/forum search would tell you exactly what to click on.

3. Not sure about re-compiling KDE.

Good luck and welcome to the community!

A

---

### Post by AtrejuT on 2007-03-18
I don't really see why you'd want to compile KDE.
If you just want to use KDE and don't care for gnome, install Kubuntu.
If you want both install Ubuntu, then install KDE through synaptic - no reason to compile anything.

atreju

---

