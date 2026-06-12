---
title: "KDE Help Center? Service not found."
date: 2006-06-22
forum: Bug Reports / Support
---

### Post by Metroid48 on 2006-06-22
Okay, I just recently installed Ubuntu onto a external USB drive and got it working fine. However, I've encountered some problems.

****EDIT, THIS ONE SOLVED. LOOK DOWN****
```
Could not launch the KDE Help Center:

Could not find service 'khelpcenter''.
```

Anyway, it's happening in multiple programs and I'm wonderin' if there's something I should have installed, or what. I've completely updated it, but it still occurs.


****EDIT****:

First problem, logging in as root:

```
su root
```

It asks for a password. I tried the password I used for installing (my main user password), but it didn't work. Is there any particular password it has by default?

Anyway, onto the touch pad. It's an Alps brand, and it has the annoying thing that tapping is enabled, meaning I keep accidentally selecting stuff. For example, my cursor moved to random places 4 times during typing this post. The movement works fine, it's just the tapping that's annoying.

Thanks,
-Metroid48

---

### Post by aysiu on 2006-06-22
Maybe try this? ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` It'll make sure you have all the appropriate Kubuntu packages, including documentation.

Or if you want just the documentation: ```
sudo aptitude update
sudo aptitude install kubuntu-docs
```

---

### Post by Metroid48 on 2006-06-22
Hey, I tried that and the first one failed, but when I got the docs it actually installed the full thing for some reason.:-k Anyway, thanks!

Two new problems, really. First, logging in as root. Second, my laptop's touch pad is messin' up.

Logging in as root:

```
su root
```

It asks for a password. I tried the password I used for installing (my main user password), but it didn't work. Is there any particular password it has by default?

Anyway, onto the touch pad. It's an Alps brand, and it has the annoying thing that tapping is enabled, meaning I keep accidentally selecting stuff. For example, my cursor moved to random places 4 times during typing this post. The movement works fine, it's just the tapping that's annoying.

Anyway, thanks again!
-Metroid48

---

### Post by aysiu on 2006-06-22
Why do you need to log in as root?

---

### Post by Metroid48 on 2006-06-22
Nevermind the root login, I found out how to adjust the password.

Anyway, anyone know about disabling Alps touchpad tapping? I'm running a Dell Inspiron 6000 and the tapping is really annoying. Any ideas?

Btw, thanks everyone for the quick responses!

---

### Post by Metroid48 on 2006-06-24
Hey everyone, the Alps tapping is still annoying but there's a larger problem that I have no clue about, as it just... well..... crashes.

Sometimes, when I boot the system from hibernation, this happens (during the waiting for file system step..... I think that's the name, it's the third one anyway). The screen suddenly blanks and then verticle bars of ubuntu-orange and black appear accross the screen.

Any ideas?

---

