---
title: "Hard to Drive"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Joushlol on 2007-11-20
I just cannibalized the hard drive from my old rig because I need some extra storage, but it has 20 gigs of stuff I don't need. How would I go about formating it via the terminal since the permissions on the drive are set to read only. So my question is how do I excess other hard drives on my system, how do I change read/write permissions on the hard drive, and how would I go about formating my extra drive?

kthnxby

---

### Post by bluepowder7 on 2007-11-20
could you use the partition editor to blow it clean?  or does that also cough up permission stuff?

---

### Post by jaybombalous on 2007-11-20
nvm, just use gparted...


```
sudo gparted
```


too install gparted

```
sudo apt-get install gparted
```


when using gparted make sure u are formatting the right drive

---

### Post by delphiguy on 2007-11-20
I was exactly in this situation a few months ago. you can check this thread
[http://ubuntuforums.org/showthread.php?t=495643](http://ubuntuforums.org/showthread.php?t=495643)

check the link i gave at the end of the post. hopefully this can help you.

---

### Post by banewman on 2007-11-20
I've found the easiest way is to use gparted from the live cd - the partitions aren't mounted then and can be worked on. :)

---

### Post by Joushlol on 2007-11-20
Thanks for the help, but I would like write privileges in the user account for this drive. How would I do that? My intentions were to use this drive as storage for my mp3's, after formating using gparted (thanks again), i still only have read only privileges.

---

### Post by taurus on 2007-11-20
What filesystem is that new partition?  If it's ext3, then you just change the ownership of the mount point from root to your login name with the chown command.

```
sudo chown -R username:username /media/storage
```
Replace _username_ with your real login name and replace _/media/storage_ with the actual mount point for it.

---

### Post by Joushlol on 2007-11-20
it's ext2, and when i did it, it didn't change the permissions.

---

### Post by taurus on 2007-11-20
What is the mount point of that partition?

```
id
df -h
```

p.s.  What exactly was the command that you ran to change the ownership?

---

### Post by Joushlol on 2007-11-20
```
joush@joush-desktop:~$ id
uid=1000(joush) gid=1000(joush) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(joush)
joush@joush-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  2.5G   23G  10% /
varrun                760M   88K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   72K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
tmpfs                 760M   34M  726M   5% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2              50G   52M   47G   1% /media/disk

```

And I ran:
```
sudo chown -R joush:joush /dev/sdb
```

---

### Post by taurus on 2007-11-20
```
sudo chown -R joush:joush **/media/disk**
ls -la /media
```

---

### Post by Joushlol on 2007-11-20
[[img]http://xs321.xs.to/xs321/07473/Screenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs321&d=07473&f=Screenshot.png)

---

### Post by taurus on 2007-11-20
Just close that disk window and open it again.  Or

```
ls -la /media/disk
```

---

### Post by Joushlol on 2007-11-20
<3
you fixed it.

FYI: 
I'm no slump to RTFM. i just bought like two books. one entitled "*A Practical Guide to Linux Commands, Editors, and Shell Programing*.

I just haven't gotten that far yet.

---

