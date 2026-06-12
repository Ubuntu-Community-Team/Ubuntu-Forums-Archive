---
title: "impossible to fix clock (strange dark screen)"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by jdimas on 2006-10-17
Hi, I installed ubuntu dapper today and it's IMPOSSIBLE to get my clock showing the correct date.

My timezone (as I chose in the installation) is America/Sao_Paulo
The installation ended and I rebooted and entered the new system. Some seconds after I logged in, my screen went dark, I moved the mouse and then, surprisingly the clock had added one hour.

Tried everything, reboot doesn't affect the problem, since the screen always goes dark and the clock always increases one hour.
Please help

---

### Post by jordanmthomas on 2006-10-17
Try running
```
sudo tzconfig
```
in a terminal.  (Applications --> Accessories --> Terminal)

I'm not sure what you mean by your screen going dark.  Is it going to the screensaver perhaps?

---

### Post by jdimas on 2006-10-21
Sorry I didn't make myself clear...
It's not the screensaver, it happens right after I login in gdm.
When I log, my desktop appears, the clock is correct, but after 2-3 seconds, the screen goes black, and when it appears again, the clock has forwarded one hour.
I correct the clock, but every reboot is the same thing. I looked at my system clock and it's ok (set to UTC), and my timezone (shown when I ran tzconfig) is correct (America/Sao_Paulo).
Actually I reinstalled ubuntu (when I saw no other option) but even then the same problem occured.
And I'm not using, not even installed ntp...

Thanks, and sorry for any mistake in my english!

---

### Post by jordanmthomas on 2006-10-21
Your English is understandable, but I don't know why your problem would be happening or how to fix it.  So, if anyone else sees this, feel free to help.  I am at a loss here.

---

### Post by CatKiller on 2006-10-21
I think that what's happening is that your clock is being set by NTP. I think this happens even when you don't have any NTP server programs installed, just as part of the date/time package. I could be wrong, though. When there's a big jump in the time with the update, the screen does fade to black - I've seen it myself. This is normal behaviour.

The hour problem seems to be a timezone issue. You could either tell it not to check the Internet to keep your clock accurate, or not use UTC, or try a different timezone/time server. I don't know enough about timezones on your side of the pond to know if you're in the right one or not.

---

### Post by jdimas on 2006-10-28
looks like it was really a timezone problem. I changed it to Cuiaba, Brazil, and now the clock is working properly. It's not a perfect solution though... But at least it works now!
Thanks!

---

