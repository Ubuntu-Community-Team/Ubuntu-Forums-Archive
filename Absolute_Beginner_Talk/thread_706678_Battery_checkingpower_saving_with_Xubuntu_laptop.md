---
title: "Battery checking/power saving with Xubuntu laptop"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-24
I have an IBM X32 laptop running on Xubuntu. After searching this forum, I know I can check the battery status with command line:
```
acpi -V
```
However, is it possible to get a small icon on the panel to show the battery status in Linux so that I can monitor the baterry status all the time? Since two weeks ago when I just installed Xubuntu, I didn't pay attention to the battery status and my laptop just died. :)

Also, how do I manage the power (saving) setting with Xubuntu? I don't mean to really 'save' the power such as tuning CPU frequency, but I need to see how to let Xubuntu not shut my monitor down when I don't really leave it alone for a long time. Now it seems it shut itself down (only monitor) if I just leave it for 3 min or so even it's plugged in. How to make this longer?
Also, how to manage if it hybernates or not while unplugged?

Thanks for all the help!

---

### Post by zerhacke on 2008-02-24
gdesklets has a battery monitor applet.

Oh wait, you're using Xubuntu.

---

### Post by incen on 2008-02-24
HAHA~ yeah... I have Xubuntu on my laptop. :P
Actually I search for the threads and all of them were written for Ubuntu, I think. They refer to System -> Preference -> Power Management, which I don't really have. :P
I tried to look through my menu but didn't really find one.

---

### Post by incen on 2008-02-25
Hi, does anyone get an idea?
Thanks for help!

---

### Post by jan quark on 2008-02-25
Right click on the top panel, "add new item" and battery monitor should be in there.

---

### Post by incen on 2008-02-25
Thanks for reply!
And how can I set the automatic shut-down for my monitor? Thanks!

---

### Post by jan quark on 2008-02-25
hmm do not know off the top of my head

but try to search for an appropriate application the same way you have added the battery monitor to the panel

---

### Post by Cifra on 2008-02-25
I don't think there is one for xfce. Try Gshutdown.

---

### Post by incen on 2008-02-25
I google this package and take a look at it. However, I didn't mean to shut down my laptop.

Now, my Xubuntu works like:
If I didn't do anything with it, it will shut the screen down in like 5 min even the AC is plugged in. However, I never set it to be like this while installing. I'm wondering where/which parameter to modify so that I can probably change it to 10 min or 20 min while plugged in and 3 min while on battery. Something like this...

---

### Post by fuzzyworbles on 2008-03-03
Yeah, I never found anything non-gnome to suite this, so I just use gnome-power-manager. I actually sort of think that xubuntu developers have using this in mind anyway because gnome-screensaver installs by default (which opens the gnome power manager when clicking 'power options')

Once upon a time the battery tab used to appear on gnome-power-manager, but now it doesn't. i guess i shouldn't be too bummed though, seeing how there's a better chance of getting monkeys to fly out of my *** than my IBM T30 performing any power function like standby, etc...

---

