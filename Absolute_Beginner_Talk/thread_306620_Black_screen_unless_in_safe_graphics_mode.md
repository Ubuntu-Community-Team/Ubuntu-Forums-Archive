---
title: "Black screen unless in safe graphics mode??"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by wonneil on 2006-11-25
Hi all,

My second post as I also have internet problems.

I can test Ubuntu with the live cd in safe mode but when I try to boot normally my screen is blank after loading and the only way I can do anything is to switch my laptop off.

Any ideas what I need to do please?

I have an Acer Aspire laptop with a 2 GHz pentium processor and an ATI Mobility Radeon graphics card.

Thanks

Neil

---

### Post by taurus on 2006-11-25
Try to reconfigure your X again in the recovery mode...

```
dpkg-reconfigure xserver-xorg
```

---

### Post by wonneil on 2006-11-25
Sorry forgot to say how much of a newbie I was!

How do I go about that, what is x?

Is it a question of copy and paste the line you attached?

Thanks for the speedy reply!

---

### Post by taurus on 2006-11-25
When your screen goes black, can you get to a console by pressing <Ctrl><Alt>F2?  That's where you type that command to reconfigure your X again.

---

### Post by wonneil on 2006-11-25
i can get into the command screen although that line doesn't work, says something about having to type sudo or something???

I still don't know what x is though, does it reconfigure this automattically??

Thanks

---

### Post by taurus on 2006-11-25
```
sudo dpkg-reconfigure xserver-xorg
-or-
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

