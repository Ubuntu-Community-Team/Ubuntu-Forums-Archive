---
title: "real player download problem"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-06-10
hi... ubuntu is absolutely rockin... 

me am a totally linux idiot.. and have jus downloaded the real player for linux on my desktop... but it is something called a binary file and when i double click to open cannot open it.. no program.. basically i need real player for firefox plugin for real player... please show me the light

---

### Post by taurus on 2007-06-10
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]You can also get the Ubuntu package from the PLF repository. Link explains how.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29)
[/COLOR]

---

### Post by drshrikant on 2007-06-10
shrikant@shrikant-desktop:~$ cd ~/Desktop
shrikant@shrikant-desktop:~/Desktop$ chmod 755 RealPlayer10GOLD.bin
shrikant@shrikant-desktop:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
Extracting files for RealPlayer installation.....tar: Skipping to next header

xxextract.tmp: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Error exit delayed from previous errors
shrikant@shrikant-desktop:~/Desktop$

---

### Post by Mazza558 on 2007-06-10
Try the link that p_quarles suggested.

---

