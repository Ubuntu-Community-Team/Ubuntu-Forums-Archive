---
title: "hard drive full"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by matadams on 2008-01-13
my hard drive is full. i went through all the posts. some would help but i have no idea what they are talking about.
so, it happened before, but it was the log files. so i cleaned those and it happened again. i assumed it was those again, but it's not.
my 40gig hard drive says 99% full but there's only a couple gig used and disk usage analyser doesn't show anything wierd, it's not even accounting for all the missing space. and my home dir is only 600mb.

i typed in ```
df -h
```
that showed me this, 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G   33G  1.2G  97% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   17M  490M   4% /lib/modules/2.6.22-14-generic/volatile


but i can't find /dev/sdb1
any help is appreciated.
mat

---

### Post by Digger78 on 2008-01-13
Open a terminal and enter

```
cd /
```

```
sudo du -s -m *  [COLOR="Red"](this will list the disk usage in MB's)[/COLOR]
```  

copy and paste the ouput here

---

### Post by matadams on 2008-01-14
5       bin
18      boot
0       cdrom
1       dev
10      etc
325     home
1       initrd
0       initrd.img
145     lib
1       lost+foundry
256857  media
1       mnt
56      opt
0       proc
29895   root
7       sbin
1       srv
0       sys
1       tmp
2121    usr
234     var
0       vmlinuz



it's not media, cause my external was plugged in and it's raising that file size.
so, basically, in a basic ubuntu install, should root, and usr be so big?

also, i've read stuff about the trash not emptying, but, i've ran the command to empty it from terminal.

---

### Post by matadams on 2008-01-14
here's a screen shot of disk analyzer too.
[IMG]http://www.silverlinemusic.com/Screenshot.png[/IMG]

this shows at the same time one says 29 gig and the other 3.1mb

---

### Post by articpenguin on 2008-01-14
you still have 13.9GBs left
 
you can reclaim that by doing

> sudo tune2fs -m 1 /dev/x

where x  is the partition where you have no space left.

---

### Post by matadams on 2008-01-14
the 13 that's left is cause i have 2 hard drives. the one i'm talking about is a 40 gig. and it's all used up, except for less then 800 mb now. even if i salvage that much, i want to use the full potential of my hard drive. is there any way to search for an invisible file that could be in root? :)

---

### Post by Digger78 on 2008-01-14
Can you try installing **kdirstat**  (its a kde app. but should work)

```
sudo apt-get install kdirstat
```

when you start it, it will ask you what to open, choose /

it will take a while to calculate, and will display the results like in my screenshot

you will be able to see the size of all files.

---

### Post by hyper_ch on 2008-01-15
you have 29GB in your /root folder. Check that.

```

cd /root
sudo du -m * > /home/USER/Desktop/output.txt

```

replace "USER" with your username!

---

