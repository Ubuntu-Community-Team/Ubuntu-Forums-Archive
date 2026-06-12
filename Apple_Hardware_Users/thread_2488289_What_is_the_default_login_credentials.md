---
title: "What is the default login credentials?"
date: 2023-06-29
forum: Apple Hardware Users
---

### Post by MadsRH on 2023-06-29
Hi
I'm trying to install [this]("https://cdimage.ubuntu.com/daily-live/current/") 23.10 arm iso in WMware on my M1 Pro, but for some reason I can't log in. Where do I find the correct login credentials?

This is a screenshot of the WM booting and it looks like there's no user called *ubuntu*
[ATTACH=CONFIG]292433[/ATTACH]

It is the same issue as described [here]("https://discourse.ubuntu.com/t/password-for-live-lunar-desktop-arm64-iso/35328").

I hope someone can help!

---

### Post by QIII on 2023-06-29
23.10 is still in development, so it is not surprising that there might be issues, particularly on Apple hardware.

Have you tried a currently supported release?  If that works, it might be worth submitting a bug report against 23.10.

Have you tired the solutions given in the article you referenced?  That may not work, since the instructions are for 23.04.

---

### Post by MadsRH on 2023-06-30
> 23.10 is still in development, so it is not surprising that there might be issues, particularly on Apple hardware.

Have you tried a currently supported release? 

I feel a bit stupid because I had tried a few different 23.10 daily images and non of them worked. I couldn't find a release of the arm desktop when looking here (only server and prebuild): [https://cdimage.ubuntu.com/ubuntu/releases/23.04/release/](https://cdimage.ubuntu.com/ubuntu/releases/23.04/release/)

BUT ofc I found the correct link here and it worked perfectly: [https://cdimage.ubuntu.com/jammy/daily-live/current/](https://cdimage.ubuntu.com/jammy/daily-live/current/)

Thanks for replying QIII

---

