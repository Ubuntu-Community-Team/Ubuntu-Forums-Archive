---
title: "uninstalling xwindows"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by X-Windows_Guy on 2008-04-19
I installed Ubuntu 7.10 on a Sun Enterprise 250 server last night no issues, but today I wanted to have the GUI interface and messed it up. Is there a way I can reverse my mistake by removing xwindows and starting fresh???

Your assistance would be greatly appreciated.

---

### Post by LaRoza on 2008-04-19
> **X-Windows_Guy said:**
> I installed Ubuntu 7.10 on a Sun Enterprise 250 server last night no issues, but today I wanted to have the GUI interface and messed it up. Is there a way I can reverse my mistake by removing xwindows and starting fresh???

Your assistance would be greatly appreciated.

Reinstall.

Or post what you did so it can be undone.

---

### Post by X-Windows_Guy on 2008-04-19
I would tell you, but unfortunatly I didn't write down the steps. Yes I know I'm not to bright, but none the less.... There must be a way to un-install x-windows.

I do recall a screen giving me the options of resolution, I chose to high of a resolution, resulting in my system locking up. I edited the xorg.conf file and lowered it to a much lower setting. Same issue happens. So I thought that a reinstall would fix the problem, but when I re-install at the command line it tells me there is already a new version running????

Hence my wanting to uninstall ...re-install!

---

### Post by LaRoza on 2008-04-19
> **X-Windows_Guy said:**
> I would tell you, but unfortunatly I didn't write down the steps. Yes I know I'm not to bright, but none the less.... There must be a way to un-install x-windows.

I do recall a screen giving me the options of resolution, I chose to high of a resolution, resulting in my system locking up. I edited the xorg.conf file and lowered it to a much lower setting. Same issue happens. So I thought that a reinstall would fix the problem, but when I re-install at the command line it tells me there is already a new version running????

Hence my wanting to uninstall ...re-install!

Run
```

sudo tasksel

```

Uncheck what you don't want.

Or run:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by X-Windows_Guy on 2008-04-19
Thank's....Tryed running reconfig three times now the four Took, now I'm walking through it many thank

---

### Post by X-Windows_Guy on 2008-04-19
Thank you for the dpkg-reconfigure xserver-xorg ....ran it and it asked me a series of questions, last question I got is desired color depth in bits, I used 24 it spit the dummy with "FATAL: Module battery not found".
Ran it again and used 16 bits same issue.

Any idea's???

---

