---
title: "KDE Won't Shut Down"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-05-13
I'm using Ubuntu Feisty Fawn 7.10, and I recently started using KDE 3.5 in favor of GNOME. However, there does not seem to be any "shut down" option in KDE, I can only log out, and from the login screen I have the option to shut down. I'd really like to boot the middleman so to speak and shut down straight from KDE. I checked the "Log Out" options and checked the box that said something along the lines of "show shut down options" but I am still only given the choice to Log Out when I click the shut down icon I added to my main applet (or by clicking the K menu for that matter.)

Man, KDE is awesome, by the way.

---

### Post by x64Jimbo on 2007-05-13
Did you install the "kubuntu-desktop" package, or did you install kde? there's a big difference.

---

### Post by mikewhatever on 2007-05-13
Have you removed ubuntu desktop after installing KDE? I remember having the same problem while having Ubuntu and Kubuntu installed. There were more cosmetic issues with the splash screen. It seems you can only have those buttons in Kubuntu or in Ubuntu, but not in both. Hope you'll find some solution, but meanwhile, you can shutdown or reboot from the terminal.
> sudo shutdown -h now
> sudo shutdown -r now

---

### Post by SavageFreedom on 2007-05-13
All I did was ```
sudo apt-get install kde
```

> **x64Jimbo said:**
> Did you install the "kubuntu-desktop" package, or did you install kde? there's a big difference.

---

### Post by x64Jimbo on 2007-05-14
From a PM sent by the OP:
[quote=SavageFreedom]Hello, you replied to a thread I had started regarding KDE. you asked if I installed kubuntu-desktop or KDE, I installed KDE using ```
sudo apt-get install KDE
```Was that not the right thing to do? I prefer KDE over GNOME, so I wasn't sure if I should be switching to kubuntu or just using the KDE session.[/quote]
Ubuntu has its own special ways of implementing packages, and if you installed KDE by itself without the kubuntu-desktop metapackage, there is a good chance that you are missing a lot of essential things.  If you prefer KDE to Gnome, you should probably just switch to kubuntu anyway, but in the case that you want both sessions available, you can install either of them and then install the other on top of it and then switch back and forth whenever you want.

---

### Post by jd65pl on 2007-06-13
To install the kde desktop environment
```
sudo aptitude install kubuntu-desktop
```

---

