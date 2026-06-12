---
title: "XGL, maybe? Help! please? :("
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sideaway on 2008-04-15
I have one of the more abstract problems I think... but I REALLY hope someone can help me as I've spent quite a while getting Ubuntu just how I like it...

Anyway, to my problem, The speed problem only occurs when I initiate a certain action so it makes me believe it's related to window management... It happens when I try to resize a window. I get incredibly slow speeds with 50% of my cpu (100% of one core) is used and slows the computer horrendously making it unusable for around 5 seconds, The computer is completely fine up until the point I resize the window, But after that, nearly every window switch or mouse click with cause the computer to pretty much **** itself, To rectify it I can log out then log back on - but it takes AGES, XGL appears to spike in processor usage when it happens, But not sure if it's the source of the problem.

Can anyone help?

---

### Post by roaldz on 2008-04-15
> **sideaway said:**
> I have one of the more abstract problems I think... but I REALLY hope someone can help me as I've spent quite a while getting Ubuntu just how I like it...

Anyway, to my problem, The speed problem only occurs when I initiate a certain action so it makes me believe it's related to window management... It happens when I try to resize a window. I get incredibly slow speeds with 50% of my cpu (100% of one core) is used and slows the computer horrendously making it unusable for around 5 seconds, The computer is completely fine up until the point I resize the window, But after that, nearly every window switch or mouse click with cause the computer to pretty much **** itself, To rectify it I can log out then log back on - but it takes AGES, XGL appears to spike in processor usage when it happens, But not sure if it's the source of the problem.

Can anyone help?

I have also noticed that resizing windows in ubuntu is quite slow. I can´t possibly find a solution to this problem..

---

### Post by forrestcupp on 2008-04-15
If you're using Xgl, it's because you are using Compiz.  So go to System->Preferences->Advanced Desktop Effects Settings and in the Window Management section make sure the 'Resize Window' option is checked.

If you don't have Advanced Desktop Effects Settings then install it
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by sideaway on 2008-04-15
I have the compiz config manager...

But i can't use it... :S - all the boxes are grayed out, see?

[IMG]http://img153.imageshack.us/img153/4900/screenshot1yb8.png[/IMG]

---

