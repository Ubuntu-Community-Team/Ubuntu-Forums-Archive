---
title: "I installed &quot;wine&quot;, now where is it??"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by MSlaveubu on 2007-02-01
lol.  I have been having this problem a lot today.  But I installed wine (I think), I did what this said, [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)  so where can I find it??   or is there something else I need to do first?

---

### Post by jimbren on 2007-02-01
```
wine /path/to/setup.exe
```

make sense?

---

### Post by MSlaveubu on 2007-02-01
> **jimbren said:**
> ```
wine /path/to/setup.exe
```

make sense?

it says it cant find it??  maybee I should reinstall, or try installing it again?

---

### Post by LarryGB on 2007-02-01
Check out this website for some help in setting up diff applications with examples.

[http://frankscorner.org/](http://frankscorner.org/)

---

### Post by crazybrit4967 on 2007-02-01
You probably typed the path wrong somehow.  Try putting quotes around it.

---

### Post by MSlaveubu on 2007-02-01
Ok, I figured it out, the command was under the installed files list in the synaptic installer.

/usr/bin/winelauncher

thanks for your help, wasnt sure if that kind of thing would work.

Any way to make it easier to access? like a desktop icon or something?

---

### Post by Patrick K on 2007-02-01
You don't actually use wine directly. It is a sort of shell that allows win programs to run. Try typing ```
winefile
``` in a terminal window. That will bring up a Win style file browser (It's more like Win 3.1's File Mangler, but it works). Wine created a fake C:\ drive for you. This is where all your windows programs will reside. Notice on the top of winefile that there is a drive icon marked "C". Click on it to open Wine's "C:\" drive. From winefile you can install win programs to run under wine, just double click the setup program. There are probably other ways to do this but this is very easy. 

If you enter ```
winecfg
``` in a term it will bring up the configuration applet. Here you can select the version of windows you want to emulate. You can do this for individual programs, too. You can map the other drive on your system, too, so the windows programs can find them. . 

Once you have your win app running from the term, you can put a link to it on a panel or in the menus. Don't panic if your windows programs don't jump on the screen right away. At least on my system, they take several seconds to come up. 

That should get you started.

---

### Post by MSlaveubu on 2007-02-02
> **Patrick K said:**
> You don't actually use wine directly. It is a sort of shell that allows win programs to run. Try typing ```
winefile
``` in a terminal window. That will bring up a Win style file browser (It's more like Win 3.1's File Mangler, but it works). Wine created a fake C:\ drive for you. This is where all your windows programs will reside. Notice on the top of winefile that there is a drive icon marked "C". Click on it to open Wine's "C:\" drive. From winefile you can install win programs to run under wine, just double click the setup program. There are probably other ways to do this but this is very easy. 

If you enter ```
winecfg
``` in a term it will bring up the configuration applet. Here you can select the version of windows you want to emulate. You can do this for individual programs, too. You can map the other drive on your system, too, so the windows programs can find them. . 

Once you have your win app running from the term, you can put a link to it on a panel or in the menus. Don't panic if your windows programs don't jump on the screen right away. At least on my system, they take several seconds to come up. 

That should get you started.

thanks, I would not have figured that out ever.  good thing for these forums.  hooray.

---

### Post by Patrick K on 2007-02-02
Glad to be of help.

---

