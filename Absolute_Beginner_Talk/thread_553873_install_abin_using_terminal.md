---
title: "install a*bin* using terminal"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by dubs on 2007-09-18
HI all


Having a huge problem installing a program using terminal. 


I'm trying to follow some simple step but not having great success. This is are the step that I use

Open a Terminal it come up as this line:
dis622@ubuntu:~$

Second step:
I enter the command line.
/home/dis622/desktop/test.bin
The answer or reply is 
bash: /home/dis622/desktop/test.bin: No such file or directory

What to do. The operating system is Ubuntu Studio 7.04


Thank you 

Steven

---

### Post by justleen on 2007-09-18
apperenty, the file is not there, or is not executable.
if you do a ```
 ls -la /home/dis622/desktop/test.bin 
```
it must have an x (for execute) at the begining
(for example: ```
[leen@leen perl]$ ls -la
total 60
drwxrwxr-x 2 leen leen  4096 2007-09-18 16:35 .
drwxrwxr-x 6 root adm   4096 2007-09-14 21:20 ..
-rwxr-xr-x 1 leen leen   765 2007-09-18 13:04 df.pl
-rw-rw-r-- 1 leen leen  4648 2007-09-16 21:33 elec.txt
-rwxr-xr-x 1 leen leen  1137 2007-09-18 16:23 new.pl
-rw-rw-r-- 1 leen leen  7987 2007-09-17 15:48 output.txt
-rwxr-xr-x 1 leen leen   384 2007-09-18 14:54 route.pl
-rwxr-xr-x 1 leen leen  1104 2007-09-18 16:35 system.pl
-rw-r--r-- 1 leen leen 12288 2007-09-18 16:50 .system.pl.swp
-rwxr-xr-x 1 leen leen   434 2007-09-16 22:04 test.pl
-rwxr-xr-x 1 leen leen    89 2007-09-17 15:05 xx

``` the files with --x--x--x are executable by everyone.

```




do a [code] chmod 755 /home/dis622/desktop/test.bin 
```
and try again to execute is

---

### Post by Lexyboy on 2007-09-18
Isn't the desktop under ~/Desktop rather than ~/desktop ? (note case - it matters).  Try entering:
```
cd Desktop
./test.bin

```

---

### Post by dubs on 2007-09-18
Thank You


for both reply but, is not working.

---

### Post by dubs on 2007-09-18
Sorry the second one was wright.


I put a D instead of a small d and it did install. 

/home/dis622/Desktop/test.bin


Thank you


Steven

---

