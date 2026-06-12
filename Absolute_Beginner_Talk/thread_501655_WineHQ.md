---
title: "WineHQ"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-07-15
I can't get Counter-Strike: Source via Steam to run properly on Ubuntu 6.06 Dapper. It stop's at 26% on Updating Steam and says only one instance of steam can be run. Is there some way that I could copy all the files from a windows partition and run the game from there? The "WINDOWS" directory I am talking about, would this work? Would it be illegal?

---

### Post by benx009 on 2007-07-15
people have had a lot of problems trying to get steam to work w/ linux through wine, so even if u did manage to copy the windows files to ur ubuntu partition, it probably wouldn't work anyway.  [a HOWTO]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam") from linuX-gamers is available, but u might still run into problems along the way... :???:

---

### Post by amrclutch1 on 2007-07-15
This is bullshit. Why the **** doesn't valve release a native linux client. Now I have to setup a partition with windblows.

---

### Post by TheExplorer on 2007-07-15
I think it's illogical to use wine for games that were made for windows since it's not an emulator. It just creates a near-windows environment to deal with some urgent matters such as program tools and the like. Wine is naked and such games require real win32 libraries, directx code etc etc. If the developers put all these inside then it will be just another windows distribution... well, open source :)

---

### Post by TheExplorer on 2007-07-15
> **amrclutch1 said:**
> This is bullshit. Why the **** doesn't valve release a native linux client. Now I have to setup a partition with windblows.

That would be better indeed :)

---

### Post by Vague on 2007-07-15
> **amrclutch1 said:**
> This is bullshit. Why the **** doesn't valve release a native linux client. Now I have to setup a partition with windblows.

Same reason they don't have a Mac client?  I've said it before, but I'll say it again here.  Steam is the only reason I still have an XP partition.

That said, this is apparently a workaround:  ```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```  Taken from this bug report: [http://bugs.winehq.org/show_bug.cgi?id=3084](http://bugs.winehq.org/show_bug.cgi?id=3084)  You might want to take a look at that, and also at the "Troubleshooting" section of the How-to on this page: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)  There are a couple workarounds on those two pages that may or may not work for you.

---

