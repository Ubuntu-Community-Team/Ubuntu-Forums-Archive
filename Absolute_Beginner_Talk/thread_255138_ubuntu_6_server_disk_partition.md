---
title: "ubuntu 6 server disk partition"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by gregkou on 2006-09-11
I am a newbie to linux, especially to ubuntu.
I was trying to install the 6 server version, but run into problem while partition the disk.
my hard drive is a 20.5 GB disk, and it will be all use for ubuntu 6 server.

the following partition is my plan
1.5 GB /
5 GB /usr
5GB /var
5GB /home
1GB /temp
512 MB SWAP
3.5 GB /backup

however, after I setup the 4th partition, the remaingin 3.5 GB space become unusable. and can't contaiue with the partition:( . I look all over the web try to find the answer but fail. is there something I did wrong? and if there is any place I can find related document for partition the drive for ubuntu? ](*,) ](*,) ](*,) 

Thanks alot for your help..
Greg

---

### Post by kidders on 2006-09-11
Lol... no matter how hard you try, you can never get away from Microsoft, can you?! It looks as though they are the reason you're having trouble.

Some time ago, Bill Gates decided that nobody should ever need any more than 4 partitions on the same physical disk. Since you're probably using Microsoft's disk partitioning scheme, there's the root of your problem.

Two solutions:

[LIST]
[*]Manually create a non-Microsoft partition map yourself, that doesn't cripple you with silly restrictions.
[*]Carry on using the Microsoft partitioning scheme, but use an "extended" partition.
[/LIST]

Using an extended partition lets you create partitions within partitions. Since the whole idea is a bit of a hack, it (albeit very slightly) affects performance. Try this:

[LIST=1]
[*]1.5 GB /
[*]5 GB /usr
[*] (BEGIN EXTENDED PARTITION)
[*] -  5GB /var
[*] -  5GB /home
[*] -  1GB /temp
[*] -  512 MB SWAP
[*] -  3.5 GB /backup
[*] (END EXTENDED PARTITION)
[/LIST]

You could do with re-arranging things a bit though ... putting your swap inside an extended partition like this *will* hit you with a noticeable lag.

**Edit:**

I should perhaps add that using extended partitions leaves you with a somewhat unexpected device numbering scheme. In the example above (assuming your disk is called /dev/sda), you'll probably wind up with something like this:

[LIST=1]
[*]/dev/sda1 /
[*]/dev/sda2 /usr
[*]/dev/sda3 (BEGIN EXTENDED PARTITION)
[*]/dev/sda4 - /var
[*]...
[*]...
[/LIST]

/dev/sda3 will essentially point noplace useful, so be careful with your /etc/fstab!

---

### Post by kidders on 2006-09-11
Sorry... I just noticed something...

> my hard drive is a 20.5 GB disk

Subdividing such a tiny hard drive to such a degree isn't clever, unless of course there's a specific reason you want to do so. Possible reasons include:

[LIST]
[*]You're planning on setting up a high-performance server that would benefit from different filesystem choices on each partition.
[*]You're installing more than 2 versions of Linux on the same machine and want to be able to share the same /usr, but not the same /home, for example.
[/LIST]

On such a small disk, the scheme you suggested will cause major headaches down the line ... so there would want to be a very good reason for putting yourself through that!

Two other comments:

1) What's /backup for? Backing up a server onto the same physical device as the parent filesystem is very risky!
2) /temp is often better stored in RAM than on disk.

I hope you don't mind all these off-topic observations ... I only mention them because you said you were a newbie.

---

