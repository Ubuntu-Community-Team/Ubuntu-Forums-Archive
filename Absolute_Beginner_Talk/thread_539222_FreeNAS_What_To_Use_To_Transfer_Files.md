---
title: "FreeNAS What To Use To Transfer Files?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by dhughes on 2007-08-30
I have FreeNAS installed on an older PC, it's on my LAN, I can ping it and it can ping my host with about 400GB of storage.
 
 My question is what do I use to move files back and forth between my FreeNAS fileserver and my main Ubuntu box?

  I tried SSH but I'm not sure how to make directories or move files around, I'm sure all that's possible with SSH but I'm wondering if that's the right tool to use or is there a better method?

---

### Post by arsya on 2007-08-31
I don't have any experience with FreeNAS. Seems like it's based on FreeBSD.
From the website it states:
FreeNAS is a free NAS (Network-Attached Storage) server, supporting: CIFS (samba), FTP, NFS, AFP, RSYNC

So, I believe you can transfer the files between both system by using FTP, rsync, or you could mount the storage using either CIFS, NFS, which one you already configured and then you could just transfer the file to that mount point.

If you have also ssh server running, you could try copy the file using "scp".
for example if you are in your ubuntu box you could do:
```
 # scp file_to_be_copied  your_username@ip_of_freenas:/tmp/  
```

Hope it helps.

---

### Post by dhughes on 2007-08-31
Thanks for the advice, I'll have to learn how to use SSH or use NFS to mount the filerserver shared folders on the drives, I tried to setup NFS but I found there were a lot of steps and configurations to do and I got lost along the way and now it half works.

 I think I can do it but I just wasn't sure if I was on the right track.

 Thanks.

---

