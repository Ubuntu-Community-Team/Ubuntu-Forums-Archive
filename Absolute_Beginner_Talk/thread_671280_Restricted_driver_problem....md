---
title: "Restricted driver problem..."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Edgewalker_001 on 2008-01-18
While installing ubuntu on another computer, I remembered that I hadn't enabled restricted drivers on my laptop, I enabled the ATI driver for my x700 mobility card and restarted, and now it only boots to a black screen... Can anyone give me some advice on the proper command lines to shut the driver down again or alternatively get it to work?

I'm a complete beginner when it comes to Linux commands...

---

### Post by PmDematagoda on 2008-01-18
You can return the X-Server configurations back to the defaults by:-

1) Booting Ubuntu in Recover Mode.

2) Executing:-
```
dpkg-reconfigure -phigh xserver-xorg
```

3) Check the GUI by executing:-
```
startx
```

---

### Post by Edgewalker_001 on 2008-01-18
Well, that fixed my graphics problem, but now I'll need to reenter all settings again...

Oh well, better than a black screen anyhow, thank you ^_^

EDIT: I just restarted, it seems I was mistaken about that too XD

Thanks a lot ^_^

---

### Post by caravel on 2008-01-18
With ATI cards you're probably going to have to work at getting the driver installed and you'll likely need to do a manual install.  Personally I gave up in the end and got an Nvidia card because I simply could not get the ATI driver to work on my old 9800.

---

### Post by stchman on 2008-01-18
> **Edgewalker_001 said:**
> While installing ubuntu on another computer, I remembered that I hadn't enabled restricted drivers on my laptop, I enabled the ATI driver for my x700 mobility card and restarted, and now it only boots to a black screen... Can anyone give me some advice on the proper command lines to shut the driver down again or alternatively get it to work?

I'm a complete beginner when it comes to Linux commands...

I recommend using Envy.  It will install the drivers for you.  You will need to make sure all the restricted driver is gone.

---

