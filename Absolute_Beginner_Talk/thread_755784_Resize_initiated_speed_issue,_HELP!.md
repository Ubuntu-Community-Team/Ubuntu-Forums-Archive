---
title: "Resize initiated speed issue, HELP!"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sideaway on 2008-04-15
I have one of the more abstract problems I think... but I REALLY hope someone can help me as I've spent quite a while getting Ubuntu just how I like it...

Anyway, to my problem, The speed problem only occurs when I initiate a certain action so it makes me believe it's related to window management... It happens when I try to resize a window. I get incredibly slow speeds with 50% of my cpu (100% of one core) is used and slows the computer horrendously making it unusable for around 5 seconds, The computer is completely fine up until the point I resize the window, But after that, nearly every window switch or mouse click with cause the computer to pretty much **** itself, To rectify it I can log out then log back on - but it takes AGES, XGL appears to spike in processor usage when it happens, But not sure if it's the source of the problem.

Can anyone help?

---

### Post by handydan918 on 2008-04-15
You might want to post the output of ```
lspci
``` so we can see what kind of video card you have. If you have an ATI or Nvidia card, and you don't have the proper drivers installed, you can take a big performance hit.

---

