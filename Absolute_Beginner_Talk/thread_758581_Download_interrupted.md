---
title: "Download interrupted"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by mak_20789 on 2008-04-18
Hi,
    i was downloading ubntu on my laptop using Download Express. The download had reached 65% . And  someone closed the lid of laptop thinking its idle. This puts the laptop in sleep mode. Then I opened it and again connected to net, but it got hanged and I had to restart.
After restarting, I again connected to net and started download using Download Express. And it quickly reached 65% , i.e. from where it was interrupted.
   Will this cause any problems?
Thank you.

---

### Post by mikewhatever on 2008-04-18
Don't know, but it's a good idea to md5sum check the downloaded iso anyway [https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum](https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum)).

---

### Post by unutbu on 2008-04-18
My guess is that there will not be a problem. But why guess?

After you download the file, let's say gutsy-desktop-i386.iso, then run the command
```

md5sum gutsy-desktop-i386.iso
```

You'll get a hex string as output. Something like

```
d2334dbba7313e9abc8c7c072d2af09c    gutsy-desktop-i386.iso
```

Next go to 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

See
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fubuntu.cs.wisc.edu%2Fpub%2Fmirrors%2Flinux%2Fubuntu%2Freleases%2F&debug=&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fubuntu.cs.wisc.edu%2Fpub%2Fmirrors%2Flinux%2Fubuntu%2Freleases%2F&debug=&download-button=)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
for more information.

---

