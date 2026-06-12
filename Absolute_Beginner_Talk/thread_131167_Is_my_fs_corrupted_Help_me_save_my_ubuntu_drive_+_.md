---
title: "Is my fs corrupted? Help me save my ubuntu drive + data!"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-02-15
[http://ubuntuforums.org/showthread.php?p=739134#post739134](http://ubuntuforums.org/showthread.php?p=739134#post739134)

^ See the above thread for various output I have had with mount, dmesg, etc.

Here's the situation: I have 2 sata HDDs in my computer, and one is a 160gb NTFS formatted drive with windows on it. This is on my first sata channel is /dev/sda. My second drive has, or should I say had ubuntu on it. The second drive was 300gb, ext3 formatted, and was /deb/sdb with ubuntu on the /dev/sdb1 partition.

A while ago, I tried to make my windows setup functional by copying ntldr and some other needed files to the drive from the win install cd in recovery mode. Unless there's something else going on here, this should not have affected my ubuntu drive at all. Anyway, when I got windows loaded, I saw again how crappy it was and then installed an ext2 driver so I could see my linux drive. Well, the driver didn't work. Oh well, windows sucks anyway, so I rebooted and was waiting for the grub prompt when... Win2k boot screen? WTF? OK, so the windows boot loader is on my first drive, no big deal, I'll use SBM and get my grub prompt. (I'm still not sure what was happening here, since grub and the windows loader couldn't have been on the same drive, yet with SBM I selected drive 0 and was greeted with my grub menu.) I selected ubuntu and watched as the boot began until... The nice image and status text disappeared around "mounting root file system (something like that" and I got some errors. Here is where the real trouble started. Somehow, I got grub COMPLETLY erased, and so I couldn't boot ubuntu at all. I tried booting the breezy install cd in rescue mode so that I could install grub. The trouble was, when it came time to mount my drive I couldn't do it... this was curious so I spawned a shell and tried to mount the drive manually. Didn't work. dmesg returned a message along the lines of what I posted in the thread I referenced above. 


So, here I am on my ubuntu livecd, unable to access my 300gb drive. I can mount and read my win2k drive just fine, but the 300gb one won't mount no matter what. Due to some of the errors I've been getting I think I have corrupted data, or a corrupted superblock if someone could explain what that is. 

(For specific errors, check near the bottom of the post I linked to at the top)

---

### Post by wr0x2 on 2006-02-15
*bump*

---

### Post by wr0x2 on 2006-02-16
No replies? Someone must know what's going on here...

---

### Post by newuser111 on 2006-02-16
did you try running fsck on the drive

---

### Post by nelposto on 2006-02-16
Hi wr0x2 .. 

Sounds poor, but not like something that should be unrecoverable... I had a similar-ish problem just days ago, where I (well mandriva installer's attempt at resizing an ntfs partition) ended up corrupting my partition table.

Eventually I was at the point where windows wouldn't boot but I had grub .. when i jumped into recovery console and fixed a few things I lost my friend grub and windows would boot as normal. 

First you should check what windows disk manager has to say about your partition table. Just because it could show something that is obviously incorrect on the ubuntu driver.

Perhaps booting a liveCD and trying gpart could help .. [http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

run it on the ubuntu partition .. see if it can guess the partitions correctly and have it rewrite the table.

This may not be helpful ... perhaps I'm not addressing the problem, but have a look at things.

---

### Post by wr0x2 on 2006-02-16
Here's the output from the second time I ran gpart:
```

ubuntu@ubuntu:~$ sudo /home/ubuntu/Desktop/gpart.linux /dev/sdb

Begin scan...
Possible partition(Linux ext2), size(283200mb), offset(0mb)
Possible extended partition at offset(283200mb)
   Possible partition(Linux swap), size(2965mb), offset(283200mb)
End scan.

Checking partitions...
Partition(Linux ext2 filesystem): primary
Partition(Linux swap or Solaris/x86): primary
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 283200mb #s(579994632) s(63-579994694)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(36102/254/63)r

Primary partition(2)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 2965mb #s(6072504) s(579994758-586067261)
   chs:  (1023/254/63)-(1023/254/63)d (36103/1/1)-(36480/254/60)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```
I ran it a time before that and wrote the new table, but I still can't mount my data partition. Gives same error as before.

---

### Post by wr0x2 on 2006-02-17
*bump*

---

### Post by wr0x2 on 2006-02-20
OK, come on. It's been two days and I've gotten no replies. Someone must have an idea of what to do here.

---

