---
title: "Help with monitor settings"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zostra on 2007-05-15
hi everyone

i was trying to correct a power management issue in which my monitor would not turn off even though i had it setup to turn off after 1 minute of inactivity
my monitor was being detected as plug and play
i thought that was the problem so i selected my monitor as samsung 753s
which it is (may be a different version) 
after i rebooted my computer
my display is corrupt
i am sure that if i can change that back to plug and play the display would correct itself
but how do i do that when the display is corrupt

i have kubuntu 7.04 and a samsung 753s
i know the monitor is fine cause i booted with the live cd and everything is fine

:( zostra :(

---

### Post by reidms on 2007-05-15
Well there are 2 options I can think of-

If you had ssh installed you could log in(not requireing monitor really- username enter password enter)
and login to it from a remote machine.

or you can mount the file system from the live cd and edit the configuration files from there

---

### Post by zostra on 2007-05-15
thanks for replying

doing a remote is not really a possibility because i am new to ubuntu and linux in general and that is not gonna be easy

how to get around mounting the filesystem and which files do i need to edit
treat me like a n00b, i really am.

:confused:  zostra :confused:

---

### Post by veloce on 2007-05-15
> **zostra said:**
> hi everyone

i was trying to correct a power management issue in which my monitor would not turn off even though i had it setup to turn off after 1 minute of inactivity
my monitor was being detected as plug and play
i thought that was the problem so i selected my monitor as samsung 753s
which it is (may be a different version) 
after i rebooted my computer
my display is corrupt
i am sure that if i can change that back to plug and play the display would correct itself
but how do i do that when the display is corrupt

i have kubuntu 7.04 and a samsung 753s
i know the monitor is fine cause i booted with the live cd and everything is fine

:( zostra :(

Reboot your computer, then use CTL+ALT+F1 to get a text console.

once you have logged in, run:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by reidms on 2007-05-15
> **veloce said:**
> Reboot your computer, then use CTL+ALT+F1 to get a text console.

once you have logged in, run:

```
sudo dpkg-reconfigure xserver-xorg
```

That is the best method, but I do not think you can get a display at all can you?

Try doing this method first, since it is the best.

---

### Post by zostra on 2007-05-16
sudo dpkg-reconfigure xserver-xorg

worked
thanks

:D zostra :D

---

