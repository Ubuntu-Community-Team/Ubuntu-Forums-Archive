---
title: "Problems with flash on opera"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-20
Ok Flash works just fine in firefox but it does not run in opera or konqueror and in konqueror a error shows up when you try to go to a flash site.I am using kubuntu 7.10 with flash 9.I have tried uninstaling flash and reinstaling nothing seems to work.

---

### Post by RomeReactor on 2007-12-20
Hi. [Try this]("http://ubuntuforums.org/showpost.php?p=3977961&postcount=3"). In your case use Konsole. Make sure you have [Opera 9.50]("http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.50b&platform=Linux%20i386&local=y") beta, as Flash won't work with the current stable release. See [this thread]("http://ubuntuforums.org/showthread.php?t=644075") for more on that.

---

### Post by jonward690 on 2007-12-20
This is what I got when I ran the command.
cp: cannot stat `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory
jon@jon-desktop:~$

---

### Post by RomeReactor on 2007-12-20
In Konsole:
```
locate libflashplayer.so
```
then use the path it returns to copy Flash to the Opera directory:
```
sudo cp PATH_RETURNED /usr/lib/opera/plugins
```

Did you install flash from Konsole or Adept, or did you download it from Adobe's site?

---

