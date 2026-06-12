---
title: "[SOLVED] Screen resolution rolls back on startup"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by LiNoah on 2007-07-07
Hi all,

My preferred screen resolution is 1280x1024, so i set it to that value using NVIDIA settings that i installed via automatix. But every time I boot, the resolution is set back to 1024x768, and i have to adjust it to my preferred resolution again.

Any idea's on how to fix this?

I tried the option "Save to X configuration file" in NVIDIA settings but that makes no difference.

I'm using a NVIDIA 7600GS on an AMD X2 3800 running feisty x64.

---

### Post by Qwerty_ on 2007-07-07
Hi LiNoah if you try running sudo nvidia-settings in the terminal. You should fix your problem

---

### Post by LiNoah on 2007-07-07
Indeed, that simple solution did the job.

Thanks for the hint!

---

### Post by Qwerty_ on 2007-07-07
Not a problem glad to help :)

---

