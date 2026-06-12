---
title: "KDE Apps"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by habtish on 2007-06-18
A while ago I installed some KDE packages (kde-base, kde-libs) for a specific KDE native app to work on GNOME. I have long removed that app and have removed the KDE packages that I had previously installed.

I still see processes such as```

 6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00  kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.91 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify

```still running, how do I get rid of these apps that I do not need?

Thanks

---

### Post by Clay_Banger on 2007-06-18
i think this will do what you want:
[http://psychocats.net/ubuntu/puregnome]("http://psychocats.net/ubuntu/puregnome")

---

### Post by Bachstelze on 2007-06-18
The k here stands for "kernel", not "KDE". IF you remove those things, you'll put yourself into trouble.

---

