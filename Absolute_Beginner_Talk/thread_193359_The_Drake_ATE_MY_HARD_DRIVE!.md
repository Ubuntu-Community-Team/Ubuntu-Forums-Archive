---
title: "The Drake ATE MY HARD DRIVE!"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Trurl on 2006-06-09
The gist of my situation is as follows:

I have an Inspiron 8600 that I wanted to dual boot XP and Dapper. The hard drive is 60 GB. My adventure occured in the following order:

1. Spent most of the day backing up and preparing to install Dapper next to XP.
2. Started installation and set partition tables manually according to a tutorial. 
3. Midway through resizing the existing XP partition, I got a blank error box. Closing it took me back to the partition wizard where I then find that my hard drive has no known file systems on it any longer (NTFS side was wiped). This is bad. 

What I want to know now, since I have to start from scratch, is how to dual boot XP and Dapper? I was planning on installing Dapper first onto a 15 GB partition and then putting XP on later in the remaining 45 GB. If this sounds reasonable, how do I control what partition XP installs to? I've never dual booted before and I'm not sure what to expect. 

Thank you for your time.

-Trurl

---

### Post by jason.b.c on 2006-06-09
> I was planning on installing Dapper first onto a 15 GB partition and then putting XP on later in the remaining 45 GB. If this sounds reasonable

Hu Uh no, Do it the other way around..

Could you please go into a little further detail of what happened..??

---

### Post by bsell on 2006-06-09
[QUOTE=Trurl]The gist of my situation is as follows:

I have an Inspiron 8600 that I wanted to dual boot XP and Dapper. The hard drive is 60 GB. My adventure occured in the following order:

1. Spent most of the day backing up and preparing to install Dapper next to XP.
2. Started installation and set partition tables manually according to a tutorial. 
3. Midway through resizing the existing XP partition, I got a blank error box. Closing it took me back to the partition wizard where I then find that my hard drive has no known file systems on it any longer (NTFS side was wiped). This is bad. 

What I want to know now, since I have to start from scratch, is how to dual boot XP and Dapper? I was planning on installing Dapper first onto a 15 GB partition and then putting XP on later in the remaining 45 GB. If this sounds reasonable, how do I control what partition XP installs to? I've never dual booted before and I'm not sure what to expect. 

Thank you for your time.

-Trurl[/QUOTE]

XP must be installed first. It won't recognize your Linux partitions and if you install it after Dapper, you'll wipe your Ubuntu install. Check to see if XP is still there. If not, reinstall it then install Dapper. You may want to let Dapper partition your drive for you.

---

### Post by Trurl on 2006-06-09
I had a 55.8 GB NTFS XP partition.
I resized it to 46 GB.
Of the remaining space:
3 GB went to /
7 GB to /home
Remainder to swap

After confirming these choices, the installer attempted to resize the XP partition. Then the blank error box appeared and what I described early occured.

So I should install XP first and then Ubuntu?

-Trurl

---

### Post by bsell on 2006-06-09
[QUOTE=Trurl]
So I should install XP first and then Ubuntu?

-Trurl[/QUOTE]
 Yes.

---

### Post by r3st on 2006-06-09
[COLOR="Red"][SIZE="7"]AND LINUX STOLE MY NTFSES!!!!!11[/SIZE][/COLOR]

[http://ubuntuforums.org/showthread.php?t=177891](http://ubuntuforums.org/showthread.php?t=177891)

---

