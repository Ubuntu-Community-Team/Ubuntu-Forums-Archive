---
title: "Another shutdown problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by country_ranger83 on 2008-01-29
I am a TOTAL NOOB to Lynux.  I have more than average computer experiance going back to DOS, but none in Lynux.  You will have to forgive my ignorance on some subjects.

I have a Gateway ](*,) 400 VTX laptop and I have opted for the Dual OS install so that I can have access to my Windows XP programs and learn Unbuntu 7.10

When I shutdown using the icon in the upper left (the only way I know how at this point) my computer restarts instead.  I have seen numerous threads on things like this, but none seem to be the same as my problem.

---

### Post by p_quarles on 2008-01-29
A couple things to try, which may help narrow down the problem.

1) Logout of Gnome, either by choosing that option from the shutdown menu, or by pressing ctrl-alt-backspace. At the login menu, select "options," and then select "shutdown."

2) If the above doesn't work, try shutting down from the terminal. Press alt-F1 to open a terminal, and run the following command:
```
sudo shutdown -Ph now
```

Let us know what happens.

---

### Post by country_ranger83 on 2008-03-04
ok, so after a month of dealing with a hard drive i turned into a paper weight by trying to re-write the disk label (oops) i got Ubuntu up and running again.  

p_quarles's I tried both your suggestions and came up with the same result, reboot instead of shut down.  


[Also I don't know if it is related, but when I "suspend" my computer and start it again all I get is a mouse on a black screen.  No input changes it.  ]

Thanks in advance for any help

P.S. thanks for the short-cut keys, I use those more than the mouse and I am always glad to learn more.

---

### Post by philinux on 2008-03-04
One thing you could try. System>Admin>Services

Scroll down the list and uncheck either of the power management services. Reboot and see if that cures it. I'm guessing its something to do with specific hardware/bios configuration. It seems to happen to a few people. But most dont have the problem.

---

### Post by philinux on 2008-03-04
One thing you could try. System>Admin>Services

Scroll down the list and uncheck either of the power management services. Reboot and see if that cures it. I'm guessing its something to do with specific hardware/bios configuration. It seems to happen to a few people. But most dont have the problem.

You can turn these services back on if no luck.

---

### Post by p_quarles on 2008-03-04
If all else fails, try using the lowest level shutdown command of all. If it doesn't work, that means the problem lies at that level, and fixing anything else would not help.
```
sudo init 0
```
That's a "zero," by the way, and not a capital o.

---

### Post by country_ranger83 on 2008-03-05
"Sudo init 0" yielded a reboot also... what does that mean?  Is there a hardware issue?

Ps. got the Linux for dummies desk reference (8 in 1 book) learning slowly

---

