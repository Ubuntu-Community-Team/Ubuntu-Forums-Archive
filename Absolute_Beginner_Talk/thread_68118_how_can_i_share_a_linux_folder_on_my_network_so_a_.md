---
title: "how can i share a linux folder on my network so a windows can read and write to it"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-09-22
how can i share a linux folder on my network so a windows laptop or desktop can read and write to it ](*,)

---

### Post by lao_V on 2005-09-22
[QUOTE=dgrafix]how can i share a linux folder on my network so a windows laptop or desktop can read and write to it ](*,)[/QUOTE]

To the best of my knowledge Windows cannot read/write non-Windows partitions.

---

### Post by krusbjorn on 2005-09-22
edit: never mind.

---

### Post by NZ-Wanderer on 2005-09-22
[QUOTE=dgrafix]how can i share a linux folder on my network so a windows laptop or desktop can read and write to it ](*,)[/QUOTE]
 Make yourself a FAT32 partition, from what I been reading both Linux and Windows can read/write to it...

---

### Post by dgrafix on 2005-09-22
mabe i should re phrase

i didnt mean in the same box, i meant 2 separate boxes using smb or something, So on my windows machine i can create a mapped network drive to my linux box like i can with a windows folder

---

### Post by xmastree on 2005-09-22
You can make a FAT32 partition somewhere on the linux box, and share that over the network.

---

### Post by aulin on 2005-09-22
If you want to share your drives over a network to a windows machine then Samba is what you need.  Have a search around the forums I am sure there is help on here about installing and setting it up.

---

### Post by nebula on 2005-09-22
If you have samba installed, add this to your /etc/samba/smb.conf:
```

[Share name]
path = /home/user/directory
comment = This is my share

```

Share name you can choose freely, path is the absolute path to the folder(directory ;-) ) you want to share. Comment is free to. You can leave it blank or even out I think if you want

---

### Post by dgrafix on 2005-09-22
Thats what i was looking 4 thanx

---

### Post by dgrafix on 2005-09-22
Ok, ive done that and made some progress. I can see my linux machine on the network but it wont let me in!! i am using the only user and username i set up and it wont let me, Seems linux is the other extreme 2 windows its TOO secure LOL  :)

---

### Post by didit on 2005-09-22
what you can do,

sudo smbpasswd -a username

it will ask you to type password

then you can log in 

hope it is clear for you

---

### Post by dgrafix on 2005-09-22
works like a charm thx.

I had 2 create a different username tho because if i use my admin one the whole drive is visible as a separate share. (for anyone else trying to do this who doesnt know)

---

### Post by dgrafix on 2005-10-02
Im still having problems with this, i have now got a new harddisk partition (fat32) with the option in startup set to (/data) i can see the disk as a folder on my linux machine but cannot write to it by either windows over the network or locally on my linux machine as it is owned by root.

Also, i have set my smbpasswd username and passowrd, but i notice that i can view the contents of this over the network. I dont want this to happen. 

I only want to be able to access the other hard disk (fat32 partition). I want all users of the linux machine to read and write to it, and any machine connected via smb to read and write to it.

---

### Post by dgrafix on 2005-10-02
also, why do i not see the partition as a 'drive' like the 'filesystem' and cr drives

---

### Post by Error_Msg on 2005-10-02
[QUOTE=dgrafix]Ok, ive done that and made some progress. I can see my linux machine on the network but it wont let me in!! i am using the only user and username i set up and it wont let me, Seems linux is the other extreme 2 windows its TOO secure LOL  :)[/QUOTE]

It's been a while since I set up my network, and it's a part of my life I'm trying to forget :) but this how to helped me get it done:
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)

E_M

---

### Post by tageiru on 2005-10-02
[QUOTE=xmastree]You can make a FAT32 partition somewhere on the linux box, and share that over the network.[/QUOTE]
It does not need to be fat32. It can be any filesystem that linux supports, ext3, reiserfs...

Samba takes care of the data transmission so the filesystem has no relevance what so ever.

---

### Post by dgrafix on 2005-10-02
Ok, its slowly beginning to make sense, but seeing as ive created my fat32 partition i may as well use it.

What i understand kind of is that linux mounts a disk(or partition) as a folder.
in my case say i call it /data

What i dont understand is that none of my users can write to it, as it is owned by root. Ive tried runing sudo chown groupname /data but i keep getting operation not permitted. How do i change the permissions away from root to allow all users to read and write to this folder?

---

### Post by Omnios on 2005-10-02
Not shure how networking works in Linux but I have a dual boot Ubuntu/Kubuntu XP partitioned ntfs/vfat drive.  In this case it counts how you mount the drive and possibly permitions. For example with fstab counting on how you mount it it will or will not show up in your computer on your desktop etc. Also though vfat does not support permitions per say I found that there  where certain files created in win that I had problems with as it was restricted or rather protected   by permitions. Your probably all set up with networking but have  to find the proper way to mount and set up you hard drive file access. Im  hoping to get a old used lap top soon so will soon joint the club lol.

---

### Post by xmastree on 2005-10-02
[QUOTE=dgrafix]How do i change the permissions away from root to allow all users to read and write to this folder?[/QUOTE]
Read this:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
It explains how to automatically mount your FAT32 partition and allow all users to access it.

---

### Post by dgrafix on 2005-10-03
good, thanks.
One thing though, when i connect from a windows machine on the network, it does not ask me for either a username or password. 
I can both read and write to all users homes! this is not good, or is this because it logs in with the windows username and password (which is the same)

---

### Post by snowjunkie on 2005-10-03
This is interesting.  I'm simply replying to this so I can keep an eye on the thread (anyone know how to subscribe without replying?).  I'm about to attempt setting up some samba shares myself, so would like to know how you get on.

---

