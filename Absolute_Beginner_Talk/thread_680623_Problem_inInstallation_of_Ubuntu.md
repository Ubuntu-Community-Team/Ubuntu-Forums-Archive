---
title: "Problem inInstallation of Ubuntu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by kamlesh mohan raul on 2008-01-28
I am new to linux ,I had install ubuntu linux on my pc a month before having windows XP First and then ubuntu.But virus occured in my
windows the n I formatted my c drive  only and also remove the ubuntu.
After installing windows Xp again in C: drive I tried to install ubuntu on 
my pc again.
I had 160GB hard disk & 2 GB ram,in which i  kept 10GB drive free with 
Ntfs partition free for linux.
I booted live CD of Ubuntu 7.10 it shows installation screen and I start installation of it nicely.
I follow the steps which it gives
1)In first step ,I select language as U.S. English 
2)in secong step ,I select calcutta
3) in third step ,i select keyboard layout as U.S.English

after that I am stuck,because It does not asking me for partioning 
wheater to follow manual,or free space it directly scan the disk 
and show the window of partition in which it does not show any
information of any drive as hda1 or sda it is completely blank.

I try to use other cd kubuntu,Ubuntu 7.04 also it also show same problem.
It happend for this time only.When I instal Ubuntu 7.04 before two month it does not show that problem.it is easy tha t time 
but after formatting windows this problem has ocurred.
So please help me ...l

---

### Post by jan quark on 2008-01-28
try using the alternate cd 

or try to shrink your partition in windows and install ubuntu in the new created partition

---

### Post by kamlesh mohan raul on 2008-01-30
I have also tried other CD of ubuntu ,Kubuntu also write that CD's on
other blank Cd's and make bootable to them but same problem had 
occur again and again.Is there is any problem to my hardware because 
i ,install new Dvd writer to my pc just 1 week before.

Please help me immediately if any you know how to solve this problem 
because i have surf on web for finding this problem's solution many have that problem but no solution has been given

---

### Post by Jammy4041 on 2008-01-30
Use gParted (System>Administative>gParted. use this to partion your hard drive then click install.

Do everything how you did it before, except when you get to the partion screen, select "Use continuous free Space."

Hope this helps

PS. It might be an idea to check your CD for defects. this can be done by selecting Check Cd for Errors when you first boot up from the CD.

---

### Post by kamlesh mohan raul on 2008-01-31
Thank for giving answer but that solution had not been worked
I tried as you say Jammy.
I first detect for defect in cd it doesnot give me error
then i start installation
i go to first System>Administrative>gparted
but it giving me answer as >>>no device has been found

---

### Post by dstew on 2008-01-31
Boot the Live CD. Open a terminal window. Post the forum the output of the command```
sudo fdisk -l
```That will list the partitions that the Live CD linux system can see, and may give us a clue as to why the partitioner is having problems.

---

### Post by kamlesh mohan raul on 2008-02-01
I give the command as:

sudo fdisk -l

but it not giving any output

---

### Post by dstew on 2008-02-01
Your command seems to have a long hyphen in it, when I cut and paste it into my word processor. Try to cut and paste my command. It is -l with a minus sign, and a small "L".
EDIT: actually, I think it is my word processor that is changing it. I don't know why the command doesn't work. Try **ls** just to get a directory listing, see what that does. Maybe I don't understand what command line you are using.

---

### Post by kamlesh mohan raul on 2008-02-03
:):):):):guitar::guitar:
Friends this problem is solved now.

The problem occurs due to hardware.I don't know anything about hardware but somehow manage .
As you say my Live cd not able find my hardisk .I just change the socket in which
red coloured flat cable coming from hard disk attached to  mother board and after doing that I able to do my installation very easily


But i amused by that, because I able to install XP on that without any problem but not ubuntu.

It's strange..

---

