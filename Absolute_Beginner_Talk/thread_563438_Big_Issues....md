---
title: "Big Issues..."
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by naiya on 2007-09-30
Okay I've recently newly installed Xubuntu 7.04 (Have previously used Ubuntu for about a year).
I am trying to sort out my issues with wireless yet again. SOmething different has worked each time I've had to do it... BUT No luck so far. this time. Wlan0 doesn't even show up in Networking, or in the terminal... but I digress.

Being a relative noob (especially with Xubuntu) I have screwed something up. I have been used to Gedit (and now I am using Nano, which is somewhat different) when I have to edit stuff. Namely the blacklist in /etc/modprobe.d/blacklist - which I tried to edit in order to blacklist the troublesome linux version of the broadcom driver I use. (I had not yet read the fix in the sticky above, so I was trying the same old tricks I had used before....)
ANYWAY Nano did something weird, (well, I guess it was ME that did something weird)...now I have in my modprobe.d folder - 3 attempted saves of the edited list - which cannot be moved, nor deleted, nor even opened. I can't figure it out. And it tries to load those files... which are
blacklist.save
blacklist.save.1
blacklist.save.2
but I just get error messages... (and crashes)


Does anyone know how to make those go away? and make Wlan0 appear so I can use my wireless again?
__________________

---

### Post by jimrz on 2007-09-30
why not use mousepad as you used gedit, not as many frills but works pretty much the same for what you are doing. you might be more comfortable than trying to work in the unfamiliar nano.

---

### Post by naiya on 2007-09-30
I will next time. I didn't know what was available. at any rate, that doesn't solve the problem... 

help. i need to get rid of those files so i can fix the wireless issue....

---

### Post by kvonb on 2007-09-30
Is the original blacklist file still there, or did it get renamed to blacklist.???

Maybe post a listing of the foldr here just to clarify it a bit.

But you can delete/rename those files from a terminal using sudo.

Open a terminal and type:

```
cd /etc/modprobe.d
ls -hAlF  (to get a list so you know what is there)
sudo mv blacklist.save* /root/
sudo mousepad /etc/modprobe.d/blacklist
```

Notice I used *mv* which will simply move the files rather than delete them just in case.  Use *rm* if you really want to delete them forever.

---

### Post by jargoman on 2007-09-30
instead of blacklisting the module you can remove it with

<pre/>
$ rmmod name_of_module
</pre>


you could even run it as a start up script

<pre/>
#!/bin/bash
 rmmod name_of_module
</pre>

---

### Post by naiya on 2007-09-30
Here is the folder content:



file:///etc/modprobe.d/toshiba_acpi.modprobe

file:///etc/modprobe.d/options

file:///etc/modprobe.d/nvidia-kernel-nkc

file:///etc/modprobe.d/lrm-video

file:///etc/modprobe.d/libpisock9

file:///etc/modprobe.d/isapnp

file:///etc/modprobe.d/ipw3945

file:///etc/modprobe.d/ibm_acpi.modprobe

file:///etc/modprobe.d/blacklist.save.2

file:///etc/modprobe.d/blacklist.save.1

file:///etc/modprobe.d/blacklist.save

file:///etc/modprobe.d/blacklist.old

file:///etc/modprobe.d/blacklist-watchdog

file:///etc/modprobe.d/blacklist-oss

The three attempts at saving netted  the files that end in .save, .save.1 & .save.2.
These files have  red 'x's  on them an d can't be  edited. i tried to remove them with sudo, but i'll try again... i just want to start over.

file:///etc/modprobe.d/blacklist-modem

file:///etc/modprobe.d/blacklist-framebuffer

file:///etc/modprobe.d/blacklist

file:///etc/modprobe.d/arch-aliases

file:///etc/modprobe.d/alsa-base

file:///etc/modprobe.d/aliases

file:///etc/modprobe.d/arch

---

### Post by HermanAB on 2007-09-30
Remember that when all else fails, it is very easy to re-install Xubuntu and if you don't have a separate /home partition, now you know why you should always have one.

While you are new to Linux and tinkering with it to learn how it works, you'll end up re-installing a few times.  It is kinda inevitable and nothing to be ashamed of - we have all been there!

Cheers,

H.

---

### Post by naiya on 2007-09-30
naiya@naiya-laptop:~$ cd /etc/modprobe.d
naiya@naiya-laptop:/etc/modprobe.d$ ls -hAlF
total 92K
-rw-r--r-- 1 root root 4.3K 2007-04-03 10:03 aliases
-rw-r--r-- 1 root root 2.1K 2006-12-31 21:41 alsa-base
drwxr-xr-x 2 root root 4.0K 2007-04-15 09:15 arch/
lrwxrwxrwx 1 root root    9 2007-09-26 13:37 arch-aliases -> arch/i386
-rw-r--r-- 1 root root  858 2007-09-29 23:23 blacklist
-rw-r--r-- 1 root root  628 2007-04-03 10:03 blacklist-framebuffer
-rw-r--r-- 1 root root  156 2006-12-31 21:41 blacklist-modem
-rw-r--r-- 1 root root  858 2007-09-29 23:23 blacklist.old
lrwxrwxrwx 1 root root   41 2007-09-26 13:37 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw------- 1 root root  898 2007-09-29 17:57 blacklist.save
-rw------- 1 root root  861 2007-09-29 19:00 blacklist.save.1
-rw------- 1 root root  905 2007-09-29 19:36 blacklist.save.2
-rw-r--r-- 1 root root  12K 2007-09-29 19:32 .blacklist.swp
-rw-r--r-- 1 root root  838 2007-04-03 10:03 blacklist-watchdog
-rw-r--r-- 1 root root   53 2007-03-29 01:08 ibm_acpi.modprobe
-rw-r--r-- 1 root root  205 2007-04-13 14:33 ipw3945
-rw-r--r-- 1 root root  299 2007-04-03 10:03 isapnp
-rw-r--r-- 1 root root   16 2007-03-24 12:13 libpisock9
-rw-r--r-- 1 root root  294 2007-04-13 14:33 lrm-video
-rw-r--r-- 1 root root   29 2006-10-09 09:33 nvidia-kernel-nkc
-rw-r--r-- 1 root root  173 2007-04-03 10:03 options
-rw-r--r-- 1 root root   41 2007-03-29 01:08 toshiba_acpi.modprobe
naiya@naiya-laptop:/etc/modprobe.d$ 


-rw-r--r-- 1 root root   53 2007-03-29 01:08 ibm_acpi.modprobe
-rw-r--r-- 1 root root  205 2007-04-13 14:33 ipw3945
-rw-r--r-- 1 root root  299 2007-04-03 10:03 isapnp
-rw-r--r-- 1 root root   16 2007-03-24 12:13 libpisock9
-rw-r--r-- 1 root root  294 2007-04-13 14:33 lrm-video
-rw-r--r-- 1 root root   29 2006-10-09 09:33 nvidia-kernel-nkc
-rw-r--r-- 1 root root  173 2007-04-03 10:03 options
-rw-r--r-- 1 root root   41 2007-03-29 01:08 toshiba_acpi.modprobe

---

### Post by naiya on 2007-09-30
okay, cool. they have been moved to root... i'll have to try the rest...

---

