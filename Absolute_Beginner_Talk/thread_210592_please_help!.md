---
title: "please help!"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-07
Ok, I have installed flash player 7 in terminal and it works.
But somewebsites require Flash Player 8

What do i do?

---

### Post by jordanmthomas on 2006-07-07
Unfortunately they aren't making Flash 8 for Linux.  Supposedly, they are making version 9 but who knows...

Anwyay, the only way I know to get it working is to install wine
from a terminal:
```

sudo aptitude install wine
winecfg

```

You can change the settings around if you are inclined to do so.

Then, just go and download the Windows version of Firefox.

[http://mozilla.mirrors.easynews.com/mozilla//firefox/releases/1.5.0.4/win32/en-US/Firefox%20Setup%201.5.0.4.exe](http://mozilla.mirrors.easynews.com/mozilla//firefox/releases/1.5.0.4/win32/en-US/Firefox%20Setup%201.5.0.4.exe)

If you're running Gnome, I believe installing wine sets up the MIME type so you'll just be able to double click the .exe file and be on your way.

If not, though, open up a terminal and go to where you saved the firefox installer.

```

wine "Firefox Setup 1.5.0.4.exe"

```

Now, you have the windows version of firefox installed with an icon on your desktop.  How convenient!  You should be able to install Flash 8 (or 9 for that matter) when you visit a site that requires it by either using the bar that pops up in firefox or by downloading the flash player and using the same process you used in installing Firefox.

Hope this helped.

---

