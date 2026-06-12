---
title: "Split file in ubuntu and combine it window.Any application for it?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by marufai on 2007-09-05
well i trying to split a file 6gb into 3gb x2 if can and combine it under window XP. Is there any application/program can do it?

Thanks in advance

---

### Post by Oceanic on 2007-09-05
7zip

not sure though

[http://www.7-zip.org/](http://www.7-zip.org/)

---

### Post by RomeReactor on 2007-09-05
Hi. Maybe [lxsplit]("http://www.freebyte.com/download/lxsplit.tar.gz") can do it. It's a command line file splitter. You can get Linux and windows versions [here]("http://www.freebyte.com/hjsplit/") (for the windows version, look for HJ Split). To split one file in 3 GB parts, you run:
```
lxsplit -s FILENAME 3GB
```
though at the moment I'm not sure of the exact syntax; once it's installed, try:
```
man lxsplit
```
for more usage options. Or you could use the [java version]("http://www.freebyte.com/hjsplit/#java"), which has a graphical interface and can run in any OS that has java, which means that you can run this same application in Linux as well as windows.

---

### Post by yota on 2007-09-05
Hi, 
if you are not afraid of command line, and you like to use only tools provided by default with the two os you can:

(linux)
```

split -b 1000000 filename splitted-

```

(windows)
```

copy /b splitted-aa+splitted-ab+splitted-ac(...) filename

```

---

### Post by marufai on 2007-09-05
thanks man~its really help...i did use HJsplit before in window but i didnt know that there is linux version as well...Forum always the best place seek for help :D

---

### Post by marufai on 2007-09-05
with some user interface help is much better than coding hehe....

---

### Post by marufai on 2007-09-05
yota can u give me the code to split a file like max.iso ?
i dont really understand the coding...

i downloaded the hjsplit but it required some library...and after i downloaded the library it canot  run.The file name is install.sh how am i suppose to install this library?

---

### Post by BlackMeTaL on 2007-09-05
> **marufai said:**
> yota can u give me the code to split a file like max.iso ?
i dont really understand the coding...

i downloaded the hjsplit but it required some library...and after i downloaded the library it canot  run.The file name is install.sh how am i suppose to install this library?

Just use the Windows version of HJSplit with Wine. I use it and it works great.

---

### Post by marufai on 2007-09-05
HJSplit with Wine ?? can use it under ubuntu also? by the way where to find it?

---

### Post by vanadium on 2007-09-05
marufai, I am glad you start to experience the advantages of the command tools anyway. 

man split

gives a nice, though technical, overview of the usage. In yota's example, just replace "filename" by the name of your iso.

By the way, to concatenate on another Linux system, you would use

cat splitted-* > name_of_combined_file

---

### Post by BlackMeTaL on 2007-09-05
> **marufai said:**
> HJSplit with Wine ?? can use it under ubuntu also? by the way where to find it?

Yes you can also use it with Ubuntu. Just install Wine (sudo apt-get install wine). Download the Windows version of HJSplit and just double click.

---

### Post by travelinrob on 2008-01-23
Thanks, yota, very helpful. I keep my files on a shared fat32 external (from before it was safe to write to ntfs). It doesn't like files larger than 4 gb. Now it's not a problem. Also, vanadium, your comment was helpful, too.

---

