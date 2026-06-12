---
title: "Attempt to Install Debian 6.0.5"
date: 2012-07-30
forum: Any Other OS
---

### Post by UltimateCat on 2012-07-30
Yesterday I attempted to install Debian; the install failed because there is something that I do not understand about the partition manager.

I am currently in a dual boot Windows XP : Ubuntu 10.04 UE
During the install I choose the options to manually install.
I choose the partition that I thought was Ubuntu for the swap.
Didn't know till today that swap in not recommended.  I tried to undue the changes to the partition that I choose as the swap; but it did not work. It takes me to the screen of all partitions on my system when I choose Finish partitioning and write changes to disk. (  I'm going in circles)

I realize that I must choose a file for root /  but the partition manager just takes me back to the screen where all partitions are listed and will not let me continue
```
No root file system is defined Please correct this from the partition menu

```
I know  the fat 32 and ntfs are my Windows XP partitions.
What I don't know and am having difficulity determining is which one of these partitions is Ubuntu-
```
logical  97.5 GB  ext 4
logical  4.2 GB  F  swap swap
logical  248.1 GB

```
I think I choose the wrong one for the swap 
Not sure what to do here.....any advise would be great

---

### Post by levlaz on 2012-07-30
> **UltimateCat said:**
> Yesterday I attempted to install Debian; the install failed because there is something that I do not understand about the partition manager.

I am currently in a dual boot Windows XP : Ubuntu 10.04 UE
During the install I choose the options to manually install.
I choose the partition that I thought was Ubuntu for the swap.
Didn't know till today that swap in not recommended.  I tried to undue the changes to the partition that I choose as the swap; but it did not work. It takes me to the screen of all partitions on my system when I choose Finish partitioning and write changes to disk. (  I'm going in circles)

I realize that I must choose a file for root /  but the partition manager just takes me back to the screen where all partitions are listed and will not let me continue
```
No root file system is defined Please correct this from the partition menu

```I know  the fat 32 and ntfs are my Windows XP partitions.
What I don't know and am having difficulity determining is which one of these partitions is Ubuntu-
```
logical  97.5 GB  ext 4
logical  4.2 GB  F  swap swap
logical  248.1 GB

```I think I choose the wrong one for the swap 
Not sure what to do here.....any advise would be great

I am pretty sure the ext4 is your ubuntu partition. 

The 248.1 GB one seems like free space to me since there is no file system. 

The error you are getting is because you did not specify a root mount point. 

When you make the partition for the debian install -- in the option for mount point simply but a backslash... "/"

Hope that makes sense.

---

### Post by UltimateCat on 2012-07-30
If I understand you; I should be able to highlight the 97.5 GB ext partition add the / and click Finish partitioning and write to disk-....?

---

### Post by levlaz on 2012-07-31
> **UltimateCat said:**
> If I understand you; I should be able to highlight the 97.5 GB ext partition add the / and click Finish partitioning and write to disk-....?

Are you trying to REPLACE Ubuntu with Debian? 

If so.. yes. 

If not.. no. 

If you are trying to install Debian along with Windows and Ubuntu then you need to use the remaining space (200 something GB...) and make a partition out of that for the debian distribution. 

Also -- I noticed you said swap space is not recommended. I am not sure where you heard that but it is not true - swap space is very important and highly recommended. I am not even sure if you are able to install without some swap space.

---

### Post by levlaz on 2012-07-31
If you are trying to simply replace Ubuntu with debian I would do the following. 

1. In the partition manager delete every partition except for the Windows stuff. 
2. Make a new partition for the Debian Install. (include / for the mount) 
3. Make a new partition for the swap space (1GB should be more than enough) 
4. Install Debian.

As QIII would say -- BACKUP BACKUP BACKUP :)

---

### Post by UltimateCat on 2012-07-31
> **levlaz said:**
> If you are trying to simply replace Ubuntu with debian I would do the following. 

1. In the partition manager delete every partition except for the Windows stuff. 
2. Make a new partition for the Debian Install. (include / for the mount) 
3. Make a new partition for the swap space (1GB should be more than enough) 
4. Install Debian.

As QIII would say -- BACKUP BACKUP BACKUP :)

I Backed up all of my files; documents, pictures etc....onto my 500GB External Toshiba last week.  Thank You for helping me :D

---

### Post by levlaz on 2012-07-31
> **UltimateCat said:**
> I Backed up all of my files; documents, pictures etc....onto my 500GB External Toshiba last week.  Thank You for helping me :D

You're welcome! 

If you are making the switch to debian[ this book]("http://debian-handbook.info/") is an excellent resource. It's free too! 

I have always had a soft spot for debian in my heart.  Best of Luck! :)

---

### Post by UltimateCat on 2012-07-31
> **UltimateCat said:**
> I Backed up all of my files; documents, pictures etc....onto my 500GB External Toshiba last week.  Thank You for helping me :D

When I make the new partition for Debian install will it be clear how to include the /  ?

---

### Post by levlaz on 2012-07-31
> **UltimateCat said:**
> When I make the new partition for Debian install will it be clear how to include the /  ?

Yes it will be clear. 

It will say "mount point" and you put the / 

See [this picture]("http://blog.coldtobi.de/gallery/1/blog_me23.jpg") -- I am not sure if Debian has a GUI install - last time I used it it was text based only... so you should see a screen similar to this one.

---

### Post by UltimateCat on 2012-07-31
I went to a few Google searches to make sure how much I should allocate for the new partition for Debian.  I have decided to make the new partition 10 GB.  That should be enough.

Hope the install this time goes well.  It's to late but I will install tomorrow.

Thanks for the link to the free book.

Looking forward to a new os :popcorn:

---

### Post by VanR on 2012-08-01
I would suggest SolusOS 1 instead of Debian. It is Debian Squeeze with up-to-date applications. It's just great. 

[www.solusos.com](www.solusos.com)

---

