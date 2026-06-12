---
title: "Can't run Jungledisk"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by markxpearce on 2008-03-15
Help! I've spent hours trying to run Jungledisk from the command line, but to no avail.

I've downloaded fron the jungledisk site, extracted the tar file to my home directory, but when I run ./jungledisk from the command line, nothing happens. The command line just moves to the next line. No errors, but nothing happens. Is ./jungledisk the correct way to run the program?

Any help would be greatly appreciated!

---

### Post by krendar on 2008-03-15
> **markxpearce said:**
> 
I've downloaded fron the jungledisk site, extracted the tar file to my home directory, but when I run ./jungledisk from the command line, nothing happens. The command line just moves to the next line. No errors, but nothing happens. Is ./jungledisk the correct way to run the program?

Any help would be greatly appreciated!

I never tried that application but try:

```
./jungledisk --help
./jungledisk -v
man jungledisk
```

and see if any of the commands will help you. Otherwise look if there is a README or .txt file contained in the archieve you can read for further instructions.

---

### Post by markxpearce on 2008-03-15
Krendar, thanks for replying so quickly. I've run the code and this is what I get:

root@Ubuntu-Server:~/jungledisk# ./jungledisk --help
jungledisk: [options] mountpoint
Options:
  -h                        print this help
 -version                  print version
 -d                        enable debugging
 -f                        stay in foreground (don't fork)
 -o config=/path/file.ini  use configuration file at this location
 -o opt[,opt...]           additional FUSE mount options
root@Ubuntu-Server:~/jungledisk# ./jungledisk -v
root@Ubuntu-Server:~/jungledisk# man jungledisk
No manual entry for jungledisk

Does this mean I have to mount jungledisk?

---

### Post by Riffer on 2008-03-15
[SIZE="2"]  Maybe try sudo? [/SIZE]

---

### Post by markxpearce on 2008-03-15
Like this?

root@Ubuntu-Server:~/jungledisk# sudo jungledisk
sudo: jungledisk: command not found

---

### Post by CodeWraith on 2008-04-01
You shouldn't have to run from the command line. Just double-click on **junglediskmonitor** in the extracted folder.

---

