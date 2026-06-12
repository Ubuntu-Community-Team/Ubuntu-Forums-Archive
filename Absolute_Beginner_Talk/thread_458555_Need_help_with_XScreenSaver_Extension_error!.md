---
title: "Need help with XScreenSaver Extension error!"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by raccoonone on 2007-05-29
I'm trying to install Pidgin 2.0.1, and I was able to compile and install it just fine, but I found that it needs XScreenSaver Extension for the auto-idle features to work correctly. I installed libxss-dev which sounded like it was the right file, but when I run "./configure" for Pidgin it still says that XScreenSaver Extension support was not detected.

Can anyone help me install this? I know that I can just use GAIM, but Pidgin has a number of fixes for interfacing with AIM that would be nice to have.

---

### Post by potentia on 2007-11-12
Bump (2.2.2)

---

### Post by visionofarun on 2007-12-01
Hi guys,

Same problem, while building Jabbin.. :(

```
arun@Jammer:~/Documents/jabbin-2.0beta2a$ ./configure 
Configuring Jabbin ...
Verifying Qt 3.x Multithreaded (MT) build environment ... ok
Checking for Qt >= 3.1 ... yes
Checking for the XScreenSaver extension ... no

Error: need the XScreenSaver extension!

arun@Jammer:~/Documents/jabbin-2.0beta2a$ 

```

Help, please.

---

### Post by Majorix on 2007-12-01
It's a package.
```
sudo apt-get install xscreensaver
```

---

### Post by nega on 2007-12-14
> **Majorix said:**
> It's a package.
```
sudo apt-get install xscreensaver
```

Or if you wan to on compile XScreenSaver yourself, you can install the  *XScreenSaver Extension* with:

```
sudo apt-get install libxss-dev
```

---

