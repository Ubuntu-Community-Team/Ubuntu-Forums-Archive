---
title: "[SOLVED] flashplugin-nonfree anomalies"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by DCmartiX on 2007-12-15
I was able to install flashplugin under Ubuntu using the zipped tar file and running the installer. I switched to Xubuntu (PC is at least 5 years old) and tried same method. No such like. Here is what I tried:

manual install which failed (3 times)

apt-get which failed on md5 checksum error

"install plugins" button which indicated (on a new screen)  it already was installed

package manger (which i checked later) said it WAS already installed but the flash test page will not display the version of the player

I have SOME UNIX experience from work but this is baffling me.

This is curious to me:

My firefox is a binary at /usr/bin. It is a symbolic link to /lib/firefox/fox, but I cannot cd to /lib/firefox because it is NOT a directory.

Thanks,

Marti

---

### Post by daimaru on 2007-12-15
EDIT to clarify:
```
rm ~/.mozilla/firefox/pluginreg.dat
rm ~/.mozilla/plugins/flashplayer.xpt
rm ~/.mozilla/plugins/libflashplayer.so
```

had something similar on my laptop. (firefox popup window saying that flash-nonfree is already  installed, while not showing the flash content on the page :D ) 
i went to my .mozilla/firefox dir in my home dir and deleted the flash"something".xpt or dat or whatever file. after that i went to a flash page hit the firefox popup screen and this time flash installed and worked afterwards.

---

### Post by DCmartiX on 2007-12-15
Fixed. I found more posts, and even an official bug. Somehow, despite my "ls -la" indicating /lib/firefox/firefox, there is also a /usr/lib/firefox directory. I redownloaded for the 4th time, haha, the tar,gz file. The test page now indicates that flash IS installed.

I thank you very much.

---

### Post by daradib on 2007-12-15
More information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by llamakc on 2007-12-15
> **DCmartiX said:**
> I was able to install flashplugin under Ubuntu using the zipped tar file and running the installer. I switched to Xubuntu (PC is at least 5 years old) and tried same method. No such like. Here is what I tried:

manual install which failed (3 times)

apt-get which failed on md5 checksum error

"install plugins" button which indicated (on a new screen)  it already was installed

package manger (which i checked later) said it WAS already installed but the flash test page will not display the version of the player

I have SOME UNIX experience from work but this is baffling me.

This is curious to me:

My firefox is a binary at /usr/bin. It is a symbolic link to /lib/firefox/fox, but I cannot cd to /lib/firefox because it is NOT a directory.

Thanks,

Marti

You're reading the output of `ls -l /usr/bin/firefox` wrong:

```

 ls -l /usr/bin/firefox 
lrwxrwxrwx 1 root root 22 2007-12-05 07:29 /usr/bin/firefox -> ../lib/firefox/firefox

```

Which is actually pointing to /usr/lib/firefox/firefox if you notice the .. at the beginning.

---

### Post by DCmartiX on 2007-12-15
NOW I see the "..".

Thank you very much for pointing that out. I feels purty dang stoopid about rite now..  :)

Marti

---

