---
title: "boot fall help me plz"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by polppol on 2007-09-04
I can't boot up my ubuntu 

when i boot up its like scan some thing about  (/dev/sda1) and  "fsck" and some file system damage of some thing like that (sda1 is partition that install my ubuntu)  

about 90% it say fall in red color 

and it ask me to put root password for repair or recover some thing like that 

after i put down is say "apt-get is not install u can install by 'apt-get install apt'" something like this
and when i put  'apt-get install apt' down its say old word for me - -"

what can i do i try recover mode its say the same thing to me

plz help me

can u fix it with out format HDD 
can i do like repair only file system with out reinstall a whole new system plz

now i runing on live-cd I can't find some thing like repair or reinstall its only "lnstall" with format my HDD `T-T

---

### Post by Goodson1974 on 2007-09-04
Hi Polppol
 
What were you doing before this problem happened?
 
Had you installed any new software or hardware?

---

### Post by polppol on 2007-09-04
I just run VMprogram and it not respont i just use System Monitor to end it up and i try to restart my system

now i can browser in to my sda1 with live-cd but i dont know how todo with it

---

### Post by polppol on 2007-09-04
I forgot one thing my sda1 system is change in to ext2 i don't know why

---

### Post by jjasonj on 2007-09-04
my gf has the same problem,everytime it comes to the 30 times powered up check...it will not boot up,says apt-get is not installed..blah blah....i fixed it for her before with help off the forum but i cant find the answer this time...please someone if u can explain why this keeps doing to her pc everytime it does the check......

---

### Post by polppol on 2007-09-04
ext2 is not my problem now
so 
can i run  "sudo fsck /dev/sda1 -a"
on live-cd to fix it idontknow how tu use this command is it correct?

now i get this 

im going to restart right now and i'll post result

sorry for my english ^-^
> ubuntu@ubuntu:~$ fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ fsck /dev/sda1 -a
fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo fsck /dev/sda1 -a
fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: Backing up journal inode block information.

/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Unattached inode 67571


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 67571
Connect to /lost+found<y>? yes

Inode 67571 ref count is 2, should be 1.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  +155924 -216773
Fix<y>? yes

Free blocks count wrong for group #4 (8179, counted=8178).
Fix<y>? yes

Free blocks count wrong for group #6 (4044, counted=4045).
Fix<y>? yes

Inode bitmap differences:  +67571 -82544
Fix<y>? yes

Free inodes count wrong for group #4 (13418, counted=13417).
Fix<y>? yes

Free inodes count wrong for group #5 (14184, counted=14185).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 185264/1849536 files (0.8% non-contiguous), 1435492/3729080 blocks
ubuntu@ubuntu:~$ 


---

### Post by polppol on 2007-09-04
hay!! i can boot back to my system`!!!!!!

`with that command on live-cd

but i still get 

fsck1.40
/dev/sda1/ contains a files system with error, check forced.
/dev/sda1/ |===============>     90%| [Fail]

but it did ask my to do any thing and just a second it boot back to my ubuntu

do i need to do any thing ???
any one know why it going like this??

ps. i using  sudo fsck command again on my systhem and it say notting error
> polppol@polppol-nbl:~$ sudo fsck
Password:
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
/dev/sda1: clean, 185249/1849536 files, 1435643/3729080 blocks
polppol@polppol-nbl:~$ 


---

