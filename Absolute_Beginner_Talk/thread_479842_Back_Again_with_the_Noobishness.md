---
title: "Back Again with the Noobishness"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Bleak Outlook on 2007-06-20
i swear i look about and read lots of posts but they all seem to give me more credit then im due

so im back again to ask stupid questions and hope you will all forgive my complete lack of brain skills

1st 
how do i sign in as/or use root option,

2nd
i have a driver that i need to change into a .deb from a .rpm
ive got hold of alien it says its installed but i cant find it to use 
(how do i add it to my applications list)

3rd
ive set up my comp with 3 partitions on my 1st drive
1st being XP
2nd being Ubuntu
3rd being Vista

they all seem to work but for storage reasons
ive partitioned my 2nd drive into 2
1st partition is NTFS for saving stuff from XP and Vista
2nd partition is ext3 for saving stuff from Ubuntu

although the ext3 partition appears on my desktop im unable to write to it
and im told in property's that its a root only option 
how do i access it or change the propertys

thanks for you time
all the best
be lucky
Bleak:(

---

### Post by Sushubh on 2007-06-20
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

u can also try automatix...

---

### Post by Bleak Outlook on 2007-06-20
sorry i should have made that more clear 
i cant access the ext3 partition im happy not using the NTFS one while using Ubuntu
they are ment to be kept seperate

---

### Post by bobplano on 2007-06-20
well for #1, you should use sudo. then you just type in your pasword (it won't show anything in the command line but just keep typing). 
#2. you need to use the command line 'cause thats the easiest. ```
sudo alien -i something.rpm
```

---

### Post by Sushubh on 2007-06-20
duh. i need to go and get my eyes checked! sorry mate for the noobish answer!

---

### Post by Bleak Outlook on 2007-06-26
So does anybody know how i can get to use my storage partition
how do i take ownership of it? how do i take ownership of anything come to think of it?

---

### Post by seshomaru samma on 2007-06-26
taking ownership of partitions depends on the file system the partition is formated as.
check out aysiu's tutorials [here ]("http://www.psychocats.net/ubuntu/")
if you partition is ntfs or fat32 look for the 'mount windows' tutorial , if your storage is ext3 or other linux file systems look for the 'mount linux' tutorial....

---

### Post by Pizzarth on 2007-06-26
just a tip. if you're gonna be working on it for a while (more than 15 minutes, which is the default for sudo) you could use sudo -s to actually BECOME root for a little whie. you won't need to keep typing sudo. well it says root@[computername]!~... so yea.

---

