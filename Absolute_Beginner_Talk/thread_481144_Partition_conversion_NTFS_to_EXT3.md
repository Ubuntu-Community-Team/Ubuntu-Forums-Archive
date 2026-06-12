---
title: "Partition conversion NTFS to EXT3"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by neo.patrix on 2007-06-22
Hi

Untill now i was using both windows and ubuntu on same machine. but I finally decided to completely get rid of XP. I have also reformated all NTFS partition to EXT3.

My problem is that I want to define mountpoint for this new EXT3 partitions like conventional /bin or more likely /usr and mount them during boot-up. I have idea about fstab. but after upgrading to Feisty the file was modfied to use some UUIDs.

More importantly I want to know what should i do with already existing /usr folder on same partition as root (/)

---

### Post by hyper_ch on 2007-06-22
you know that /usr does not stand for "user"?

---

### Post by neo.patrix on 2007-06-22
I think so, i does not stand for "user". But I have /home , on separate harddisk partition, i am interested in doing something similar for /usr and possibly create an SVN repo with proper right settings.

---

### Post by Bachstelze on 2007-06-22
Of course, /usr stands for "User", what else ?

---

### Post by neo.patrix on 2007-06-22
It may or may not, This is what i found about /usr from [here]("http://www.linuxjunkies.org/articles/file-system.html")

> 
/usr

/usr is normally a separate file system, and may even be remotely mounted from a file server. In many ways it mirrors the root file system in subdirectory layout. It is used to hold applications, libraries, and configuration files that are not necessary to boot the system.

/usr/local is very much like /usr within /usr. It is used to hold applications that are installed by the administrator, rather than provided by the operating system vendor. /opt is now used to perform this function.


but anyway that does not matter to me. I just want /usr to be a mount point for a certain  EXT3 partition that does not load automatically during Boot-up.

Also I expect that I need to safely move my current /usr to that partition. But problem is I don't know how. Also i have clue how  to modify fstab with UUIDs . 

All I want to do is make /usr as mountpoint for parition /dev/sda6. Just like /home is mountpoint for my /dev/sda5. The main reason to do it was to have enough memory for my Home Driectory and keep it separate from from applications and system files.

But since I had done that while installing ubuntu It was easy , but now I want same procedure to be applied for /usr so that I have enough memory to create SVN repository in /usr/share.

---

### Post by ajgreeny on 2007-06-22
**U**nix **S**ystem **R**esource, or something very similar!

---

### Post by Bachstelze on 2007-06-22
> **neo.patrix said:**
> but anyway that does not matter to me. I just want /usr to be a mount point for a certain  EXT3 partition that does not load automatically during Boot-up.

Sounds like a weird thing to do, as /usr contains binaries that are necessary to get a usable multi-user system. If you do not mount it, you'll get a very minimal system on which you can do pretty much nothing.

---

### Post by drivel on 2007-06-22
> **ajgreeny said:**
> **U**nix **S**ystem **R**esource, or something very similar!

What a imagination!!

---

### Post by Bachstelze on 2007-06-22
> **drivel said:**
> What a imagination!!

Agreed :p

---

### Post by neo.patrix on 2007-06-22
Oh Sorry ther has been misunderstnaing

There is currently an EXT3 partition that does not load during Boot..... without any name freshly conveted from NTFS to EXT3

Now i want it to be mounted as /usr and load it automatically during boot...

I hope that is clear enough

---

### Post by Bachstelze on 2007-06-22
I see. Well, you could try to mount the partition to, say /mnt/usr and copy all of /usr onto it, then have it mounted as /usr in your fstab but I'm not sure it would work.

---

### Post by neo.patrix on 2007-06-22
Ok i will try that...but with fiesty fstab uses some UUIDs I do not know what to do with it.

Is there any utility in Feisty repos to deal with this UUIDs for disk partitions?

I think /usr is logical choice , /home already has enough harddisk space. It is more risky to move /boot /bin /etc /opt. 

/tmp /var will never require entire harddisk partition

---

### Post by Inxsible on 2007-06-22
> **neo.patrix said:**
> Ok i will try that...but with fiesty fstab uses some UUIDs I do not know what to do with it.

Is there any utility in Feisty repos to deal with this UUIDs for disk partitions?

I think /usr is logical choice , /home already has enough harddisk space. It is more risky to move /boot /bin /etc /opt. 

/tmp /var will never require entire harddisk partition

You can use UUIDs or device names or LABELS in fstab. Device name, IMHO, is the way to go, since i think its more human readable and you know what device you are changing if at all

---

### Post by ajgreeny on 2007-06-22
OK, I was wrong in detail, (user, not unix), but got it nearly right about the meaning of usr-
From [http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/usr.html](http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/usr.html)
1.17. /usr

/usr usually contains by far the largest share of data on a system. Hence, this is one of the most important directories in the system as it contains all the user binaries, their documentation, libraries, header files, etc.... X and its supporting libraries can be found here. User programs like telnet, ftp, etc.... are also placed here. In the original Unix implementations, /usr was where the home directories of the users were placed (that is to say, /usr/someone was then the directory now known as /home/someone). In current Unices, /usr is where user-land programs and data (as opposed to 'system land' programs and data) are. The name hasn't changed, but it's meaning has narrowed and lengthened from "everything user related" to "user usable programs and data". As such, some people may now refer to this directory as meaning **'User System Resources'** and not 'user' as was originally intended. 

Just defending my memory and making sure I did not dream the whole thing up.

---

### Post by neo.patrix on 2007-06-25
Thank you, but too late.... 

I crashed entire system trying to move /usr. There must some trick involved in changing all those hard links and soft links ..... 

I did use "find" command and piped output to "cpio" for copying. Well I thnk because of using pipe i probably filled up /tmp or /var. My partition which had root(/) ran out of required memory. 

That was the end of story....

---

