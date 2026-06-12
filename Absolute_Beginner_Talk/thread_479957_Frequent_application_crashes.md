---
title: "Frequent application crashes"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-20
Certain applications keep crashing (forcing me to "Force Quit").

I'm running Feisty 64. The applications that crash the most are Thunderbird (not sure if it's 32 or 64), F-Spot, and Sunbird (not sure if it's 32 or 64) won't even open anymore.

Am I doing something wrong?

---

### Post by DBStevens on 2007-06-23
Please define crash.

Do they lockup, seg fault, just exit, do they provide any error messages?

Decribe what you were doing and where you were (if browsing) when they went funny.

---

### Post by Phixion on 2007-06-23
Try opening the offending apps via terminal so you can see the error output.

---

### Post by Johnny K on 2007-06-25
Thanks for the replies!

The two most frequent problems are with Thunderbird and Sunbird.

**Thunderbird**
Thunderbird freezes up whenever I receive a new email. I click "Inbox" and the app just freezes, so I click X and get the Force Quit dialog. If I force quit, and then relaunch Thunderbird, I am able to read the new emails. But the same thing happens again if I recieve another new email. Typing "thunderbird" in terminal gives this error:
```
(thunderbird-bin:12175): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory
```


**Sunbird**
Sunbird won't even launch. Trying to launch Sunbird just brings up the Netscape Feedback thing. Typing "sunbird.sh" in terminal gives this error:
```
(sunbird-bin:12311): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory
*** Calendar schema version is: 5
Starting calendar alarm service
observer added
Segmentation fault (core dumped)

```

---

### Post by DBStevens on 2007-06-25
You appear to be missing some gail components in particular libart-2.0-2.

If you install it using Synaptic things might go a bit better for you.

---

### Post by Johnny K on 2007-06-25
> **DBStevens said:**
> You appear to be missing some gail components in particular libart-2.0-2.

If you install it using Synaptic things might go a bit better for you.

It was already installed. I reinstalled it, but that didn't fix the problem

---

