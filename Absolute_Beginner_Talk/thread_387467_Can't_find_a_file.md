---
title: "Can't find a file"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-18
Hi,
How do I find this file?


~/.beagle/Log/current-Beagle

In particular, what does the ~ and the dot in front of beagle mean?

Thanks,
Phil from Wales.

---

### Post by taurus on 2007-03-18
The ~ means your $HOME directory.  In other words, if your login name is john, then ~ is the same as /home/john.  

So if you want to view current-Beagle in .beagle/log, you can do either one of the followings from a terminal:

```
cat ~/.beagle/Log/current-Beagle
-or-
cat /home/john/.beagle/Log/current-Beagle
-or-
cd
cat .beagle/Log/current-Beagle
-or-
cd ~/.beagle/Log
cat current-Beagle
```
The . in front means it's a hidden directory/file.  You can see them all on your $HOME directory with

```
ls -la ~
```

---

### Post by mahiyar on 2007-03-18
~ stands for home directory. Like it will be in /home/"user name" directory. .beagle will be a hidden folder , "." signifies hidden, so if you are using nautilus press "Ctrl + h" to see hidden files.

---

### Post by h0ax on 2007-03-18
~ refers to your home directory ~/ rather
. before a directory is a hidden directory

If you're looking for a file you can do 
"locate name-of-file"
or 
"whereis name-of-file"

---

