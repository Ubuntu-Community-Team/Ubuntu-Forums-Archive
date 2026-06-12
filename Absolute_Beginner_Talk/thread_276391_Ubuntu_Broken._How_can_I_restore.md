---
title: "Ubuntu Broken. How can I restore?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-10-12
Well, after 3 days running. I logged out, only to b stuck in text-only mode, so I rebooted.

And still, I stayed stuck in text-only.

So I logged in and ran "startx"

That worked, it booted me into what looked like my xgl session (odd black and white texture before the desktop loads)

But compiz was not running.

I cant do much.


So, is there a way to restore ubuntu to a previous point? Say three days ago? (I'm guessing no.)

If not, is there a way to reinstall ubuntu witout the cd? Or just restore the computer to initial settings, deleting all programs that were there (damn......)

---

### Post by alex-desktop79 on 2006-10-12
i could really use the help

---

### Post by woob on 2006-10-12
What did you do just prior to restarting? Did you update or install anything? A little more info might help us solve this for you.

---

### Post by AndyCooll on 2006-10-12
Have you tried:

```
sudo dpkg-reconfigure xserver-xorg
```

:cool:

---

### Post by blendmaster on 2006-10-12
Were you editing your xconfig files prior to your problem?

This caused me to get stuck in command-only mode.

---

### Post by alex-desktop79 on 2006-10-12
not that i know of

---

