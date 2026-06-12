---
title: "big problem with sudo"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by mav.it on 2005-11-30
Hi guys,
I have a big problem.
I don't know what happened, but someone that knew my password changed my uid in the /etc/passwd file and now I cannot do sudo anymore.

And therefore I cannot restore the passwd file as well!

I'm really stuck and I don't know how to get root privileges on the system, because I was just using sudo and don't have any root account!

Is there anybody that can help me?

---

### Post by 23meg on 2005-11-30
You can try reversing the changes by booting in recovery mode.

---

### Post by mav.it on 2005-11-30
so you mean that by booting in recovery I get the old passwd file or I am root by default?

---

### Post by 23meg on 2005-11-30
You're root when you boot in recovery mode and you can add yourself to /etc/sudoers as well as reverse changes to your passwd file.

---

### Post by mav.it on 2005-11-30
Great! It's a relief..

Now I've learned a new thing...

Many thanks for the very quick reply

---

