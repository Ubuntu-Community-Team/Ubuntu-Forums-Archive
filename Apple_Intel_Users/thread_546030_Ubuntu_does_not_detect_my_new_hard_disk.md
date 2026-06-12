---
title: "Ubuntu does not detect my new hard disk"
date: 2007-09-08
forum: Apple Intel Users
---

### Post by macboontu on 2007-09-08
Hello everybody,
I've a strange problem with the Ubuntu 7.04 installation on my macbook. I clarify that I've already installed it successfully and with no problems, but then I changed mac's hard disk with a 160gb samsung, I've installed successfully MacOSX, followed this instructions ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)), but starting Ubuntu live cd no hard disk was detected!

Still now I'm not able to install Ubuntu on my macbook :(

---

### Post by undead-monkey on 2007-09-08
I am having the exact same issue as you. I just upgraded to a 160Gb drive, and am unable to do a new install of Ubuntu on it.

---

### Post by macboontu on 2007-09-09
It's really frustrating :(

---

### Post by undead-monkey on 2007-09-09
I had posted my issue  not long before you, and still haven't found an answer.
[[My Thrread]]("http://ubuntuforums.org/showthread.php?t=544626")
I've searched the forums, and tried a few little tricks here and there, but no dice.

---

### Post by undead-monkey on 2007-10-27
Finally figured out the issue.

I did a clean install of OSX on my MacBook (which brought it back down to 10.4.6) and gparted saw my disk just fine. I than did the OSX system updates and brought it up to date and ran the live CD again, and it was a no go.

Conclusion:
You need to be running an earlier version of OSX in order for Ubuntu to see the partitions.

I never would have thought that it was Apple software causing the problem.

---

