---
title: "[help] fs format"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-08
Hi,

I have a second hard drive that is mounted /home
with ext3 file system. 

 I want to reformat this as reiserfs and remount it 
as /home.  So, I commented out the current /home
line in /etc/fstab and copied data files from /home
into another folder on another hard drive.

Now, using gparted tool, I'm getting the following
error:

GParted 0.2.5

   **Create Primary Partition #1 (reiserfs, 76.69 GiB) on /dev/hdd**    ( ERROR )             
create empty partition    ( SUCCES )             
[I]path: /dev/hdd1
start: 63
end: 160826714
size: 76.69 GiB[/I]          
set partitiontype    ( SUCCES )       
create new reiserfs filesystem    ( ERROR )
             ***mkreiserfs -f /dev/hdd1***             [I]A pair of credits:
Many persons came to [www.namesys.com/support.html]("http://www.namesys.com/support.html"),  and got a question answered
for $25, or just gave us a small donation there.

Lycos Europe  ([www.lycos-europe.com]("http://www.lycos-europe.com"))  had  a  support  contract  with  us  that
consistently came in just when we would otherwise have missed payroll, and that
they kept doubling every year. Much thanks to them.


[/I]       [I]mkreiserfs 3.6.19 (2003 [www.namesys.com]("http://www.namesys.com"))

'/dev/hdd1' looks mounted.Continue (y/n):[/I]             
========================================

What should I do?

I'm using ce 3.2 (christian edition 3.2).

Thanks.

---

### Post by NeoLithium on 2007-06-08
sudo umount /dev/hdd1

---

### Post by pcandpc on 2007-06-08
Hi,

Well, umount /dev/hdd1 says nothing's mounted there.

But, I've noticed a disk icon on the desktop that is mounted
as /media/disk.  Thinking that this might be the drive I'm
trying to mount as a new /home, I looked at its properties
and copied the uuid value to /etc/fstab's /home, and changed
the mount point to /home with the new reiserfs file system
on the volume and disk tabs.

After rebooting, I think I have a new reiserfs /home on my
second hard drive now, and it appears working nicely so far.

By the way, the gui gparted tool should have let me
choose a new mount point after formatting a drive 
with a file system.  Instead, it kept giving me the same 
error as before while trying formatting a drive.

Thanks.

---

