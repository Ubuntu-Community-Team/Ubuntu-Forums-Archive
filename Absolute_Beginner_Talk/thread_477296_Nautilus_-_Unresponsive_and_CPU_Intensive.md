---
title: "Nautilus - Unresponsive and CPU Intensive"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2007-06-18
Hello all,

I woke up this morning and found that my cpu was being used up quite a bit, and found the culprit to be Nautilus. Thinking it wasn't much, I restarted X and logged back in finding no background, no icons, no right-clicking on the desktop, or using the Nautilus file manager. My cpu is still being heavily used after the restart of X, even though I can't see it doing much of anything. I'm not sure how this happened, but how can I fix it whatever it is?

Thanks
-Tanner

---

### Post by 5-HT on 2007-06-18
You can try a 'killall nautilus && nautilus &'
If not, does a reboot help?

---

### Post by Cappy on 2007-06-18
If you have a CPU with stepping enabled it may have cut back the CPU to save power while it was idle.

---

### Post by sickpuppet on 2007-06-18
> **TannerLD said:**
> Hello all,

I woke up this morning and found that my cpu was being used up quite a bit, and found the culprit to be Nautilus. Thinking it wasn't much, I restarted X and logged back in finding no background, no icons, no right-clicking on the desktop, or using the Nautilus file manager. My cpu is still being heavily used after the restart of X, even though I can't see it doing much of anything. I'm not sure how this happened, but how can I fix it whatever it is?

Thanks
-Tanner

Hi TannerLD - 

How did you discover that the culprit was nautilus? I ask because I want to check that you actually found the right culprit!

regards
Ben

---

### Post by TannerLD on 2007-06-18
Hello,

I did a restart and all seems well.

And I found it was Nautilus by looking at the System Monitor.

Thanks
-Tanner

---

