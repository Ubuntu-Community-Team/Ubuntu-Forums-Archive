---
title: "Is it possible to mount a device twice in two folders?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Georgie.Mathews on 2008-02-18
Hello all

I was wondering if i could mount my NTFS partition twice in ubuntu. For example in /media/sda5 as well as in /media/sda7.

The reason i want to do this is to put rights for /media/sda5 as umask=022 and for /media/sda7 as umask=007. This is because i want to share that particular partition via FTP as read only, but at the same time be able to have read and write access on my machine in /media/sda7. Please advise.

Thanks :KS

---

### Post by zerhacke on 2008-02-18
You can do that, no problem.  Just issue the mount command twice or put two entries in /etc/fstab

---

### Post by Georgie.Mathews on 2008-02-18
YAY thanks. My FTP worries have all gone now lol. Take care ;]:guitar:

---

### Post by Georgie.Mathews on 2008-02-19
Hey again,

I tried adding a duplicate entry in fstab yesterday for mounting the NTFS drive (as i have indicated earlier) and i rebooted, but nothing appears in /media/sda8. Here are the entries in fstab.

```

# /dev/sda5
UUID=7E08A70D08A6C40D /media/sda5     ntfs    defaults,umask=022,gid=46 0       1
# /dev/sda5 (Copy of sda5 with different permissions)
UUID=7E08A70D08A6C40D /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
#FTP bind
/media/sda5/Stuff /home/FTP-shared/download vfat bind 0 0


```

Is there anything that should be different for the second mount entry?

---

### Post by aeiah on 2008-02-19
could you read/write before? because i thought you needed ntfs-3g to write and you need to reference it in your fstab. additionally, have you created the folder sda8 in /media/ ?

---

### Post by aeiah on 2008-02-19
additionally, you seem to have sda5 as ntfs and sda5/stuff/ as vfat?

---

### Post by Georgie.Mathews on 2008-02-19
Hery again,

Ok, the whole idea to have two permissions for the same partition is so that i can share it on one instance via pure ftpd with umask=022 rights and also with umask=007 (so that i can actually read and write onto it)

It loads fine with /media/sda5, but with read rights only (hence i share /media/sda5 on proftpd. About the vfat part (under FTP-bind), i just grabbed that line fro the proftpd how to on these forums, i should change that to ntfs right?

And yes, i could read and write fine (ntfs was the default settings) before changing frm umask=007 to umask=022. That was what Gutsy generated in fstab after i installed ubuntu.

Moreover i havent created a /media/sda8 folder...maybe thats why it wasnt working..My ubuntu machine is back at home so will confirm tonight.

---

### Post by aeiah on 2008-02-19
if you could write to your ntfs before then no need to worry about the ntfs-3g bit. i assumed you still needed that to be able to write to ntfs on ubuntu but perhaps its encorporated now.

yea you'll need to change the vfat to ntfs, since it has an ntfs filesystem. i dont know if the bind settings are different or whatever but that'll be something to look at later. does it mount the /stuff part to your downloads folder ok as is?

but yes, you'll need to create your new mount point at sda8. it wont create the folder automatically. just do:

sudo mkdir /media/sda8

---

### Post by Georgie.Mathews on 2008-02-19
Yep, it bound /media/sda5/Stuff  fine to /home/FTP-shared/download..users can access that folder fine via ftp. 

Ill change the vfat bit to ntfs, hope it wont cause any physical failure to my hard drive when i used vfat ;[

Will create that folder when i get back home this evening (ie /media/sda8 ) then ill report back ;D. Thanks for your time again.

---

### Post by kpkeerthi on 2008-02-19
If you need true write support for NTFS partitions, consider using ntfs-3g.The old ntfs driver has only basic write support. You just have to change ntfs to ntfs-3g in /etc/fstab.

---

### Post by The Cog on 2008-02-19
Does it complain if you manually say
**sudo mount /media/sda8**
?

I wonder if there's some error (fstab looks OK to me although I would change the trailing 1 to 0)  or if it's just too clever and knows that it;s already mounted that UUID.

---

### Post by Georgie.Mathews on 2008-02-20
Ok i tried adding the additional entry in fstab for mounting onto /media/sda8. This is after i created the sda8 folder as root in terminal.

However, the drive mounted in /media/sda8 has the same rights as /media/sda5 despite me setting umask=007 for /media/sda8. /media/sda5 still has umask-022 as its settings.

Please advise.
Thanks.

---

### Post by Georgie.Mathews on 2008-02-20
Hey the cog, didnt try your suggestion will try that, maybe thats why /media/sda8 had the same privilages as /media/sda5 without changing that value. Which 1 to 0 change are u suggesting though? Thanks again

---

### Post by The Cog on 2008-02-20
The last 0/1 is a flag indicating whether a filesystem check needs performing before mounting. I'm not sure if it is dumb enough to check the same partition twice if both mount points say it need checking, but I would be inclined to set one to 0 jsut to head off the possibility. Doesn't really matter which.

---

### Post by jordanmthomas on 2008-02-20
The way I would go would just be to make a symbolic link.
Say I have /dev/sda1 mounted /media/something and I also want it "mounted" at /home/jordan/somethingelse
```
ln -s /media/something /home/jordan/somethingelse
```

Now, as far as I am concerned /dev/sda1 is mounted at /media/something and at /home/jordan/somethingelse.  Doing an ls in either directory will give me the same thing.

I don't know if you might want to go this route instead of having two mountpoints in /etc/fstab.

My two cents.

---

### Post by The Cog on 2008-02-20
That would be OK except that he wants one mount-point to be read-only. You can't do that with symlinks.

---

### Post by jordanmthomas on 2008-02-20
That's what I get for not reading the whole question.

---

### Post by Georgie.Mathews on 2008-02-21
Ill post my fstab tomorrow then u guys can see where im going wrong with this ;) Thanks for your input guys.

---

