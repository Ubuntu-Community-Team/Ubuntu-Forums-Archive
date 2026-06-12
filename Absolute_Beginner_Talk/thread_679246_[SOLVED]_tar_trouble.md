---
title: "[SOLVED] tar trouble"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-26
i have recently downloaded ubuntu gutsy and my wireless card wont work. after making a post about that i have discovered that alot of people have the same RTL8187b card that i have and they all have the same problems that i have with it. after reading someone elses thread i have found the correct driver for my card but it is a .tar.gz file  

after reading about how to install it  i went to my terminal and went to the correct dirrectory which in this case is 

tj@tj-laptop:~/Desktop/rtl8187b-modified$

and i typed make which is what a website instructed me to do but this is what happened

tj@tj-laptop:~/Desktop/rtl8187b-modified$ make
make: *** No targets specified and no makefile found.  Stop.
tj@tj-laptop:~/Desktop/rtl8187b-modified$ 

what does this mean? what do i have to do to install this modified driver?
on the thread where i found the driver everybody already knows how to compile tars so they sorta skipped over that part. Please help

---

### Post by taurus on 2008-01-26
While you are still in that directory, ~/Desktop/rtl8187b-modified, can you post the output of this command?

```
ls -la
```
Perhaps you need to run ./configure first before make.

---

### Post by sub2007 on 2008-01-26
You can only run make if there is a makefile. There is obviously no makefile here as they have said that.

Normally you would have to run ./configure before you run make. The steps should be as follows:

./configure
make
sudo make install

If you get an error with any of these steps then post the error message back here (it may be that there is no configure script and so we'll have to try something else).

---

### Post by tjwoosta on 2008-01-26
tj@tj-laptop:~$ cd Desktop/rtl8187b-modified
tj@tj-laptop:~/Desktop/rtl8187b-modified$ ls -la
total 64
drwxr-xr-x 5 tj tj 4096 2007-10-11 15:35 .
drwxr-xr-x 3 tj tj 4096 2008-01-26 18:40 ..
drwxr-xr-x 3 tj tj 4096 2008-01-26 18:59 ieee80211
-rwxr-xr-x 1 tj tj   54 2007-08-22 03:21 ifcfg-wlan0
-rwxr-xr-x 1 tj tj  196 2007-09-27 12:24 install
-rwxr-xr-x 1 tj tj  124 2007-08-22 03:21 makedrv
-rw-r--r-- 1 tj tj  681 2007-10-11 15:35 README.FIRST
-rwxr-xr-x 1 tj tj 5117 2007-08-22 03:51 ReadMe.txt
-rwxr-xr-x 1 tj tj  538 2007-08-22 03:46 release_note
drwxr-xr-x 3 tj tj 4096 2008-01-26 18:59 rtl8187
-rwxr-xr-x 1 tj tj  294 2007-08-22 03:21 wlan0dhcp
-rwxr-xr-x 1 tj tj  471 2007-08-22 03:21 wlan0down
-rwxr-xr-x 1 tj tj   75 2007-08-22 03:21 wlan0rmv
-rwxr-xr-x 1 tj tj  611 2007-10-11 15:35 wlan0up
drwxr-xr-x 6 tj tj 4096 2007-08-22 03:52 wpa_supplicant-0.5.3
tj@tj-laptop:~/Desktop/rtl8187b-modified$ 

yea i forgot to mention it but i did run ./configure this is what happened

tj@tj-laptop:~/Desktop/rtl8187b-modified$ ./configure
bash: ./configure: No such file or directory
tj@tj-laptop:~/Desktop/rtl8187b-modified$

---

### Post by taurus on 2008-01-26
Looks like you have to run the install file to install it.

```
sudo ./install
```
However, have a look at the README.FIRST first to see what does it say.

```
cat README.FIRST
```

---

### Post by tjwoosta on 2008-01-26
What does this mean?

tj@tj-laptop:~/Desktop/rtl8187b-modified$ sudo ./install
[sudo] password for tj:
cp: missing destination file operand after `ieee80211-rtl.ko'
Try `cp --help' for more information.
cp: missing destination file operand after `ieee80211_crypt-rtl.ko'
Try `cp --help' for more information.
cp: missing destination file operand after `ieee80211_crypt_ccmp-rtl.ko'
Try `cp --help' for more information.
cp: missing destination file operand after `ieee80211_crypt_tkip-rtl.ko'
Try `cp --help' for more information.
cp: missing destination file operand after `ieee80211_crypt_wep-rtl.ko'
Try `cp --help' for more information.
cp: missing destination file operand after `r8187.ko'
Try `cp --help' for more information.
tj@tj-laptop:~/Desktop/rtl8187b-modified$

---

