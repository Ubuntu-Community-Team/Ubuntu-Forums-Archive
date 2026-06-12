---
title: "mount xfs for normal user"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by hoffimar on 2006-01-05
Hi,

i want to use a xfs partition as normal user. Best would be to mount it at boot time, but I can't tell any uid in fstab for xfs. So how would I do that? If I make regularuser the owner of the mount point (in this case /media/data/), it makes root the owner when mounting. 
So I tried to to mount it manually as regularuser. My /etc/fstab entry for it looks like this: ```
/dev/hda5       /media/data     xfs     user,noauto        0       0
```
But after a "mount /media/data" again root is owner for /media/data?! After unmounting regularuser is owner again.
Any suggestions?

Cheers, Martin

---

### Post by schilcha on 2006-01-05
This is a suggestion -- I can't verify if that works, since I don't have any spare partitions to mess around with...

Anyways: 
Change your fstab back to automount at boot, i.e.:
```
/dev/hda5       /media/data     xfs     user,auto        0       0
```
Then, reboot or mount the partition manually by executing 
```

sudo mount /media/data

```
in a terminal.

Finally change the permission of the *mounted* partition as you need it, such as:
```

sudo chown root.users /media/data

```
which will hand the partition over to the group "users", which you probably belong to. Also "chown yourusername.yourusername /media/data" might be a valid choice for you.

Finally set the appropriate permissions, e.g.
```

sudo chmod ug+rwx /media/data
sudo chmod o=rx /media/data

```
which will give the owning user and the all users in the group specified in "chown" before full rights to the partition, while all other users will have read-only-access.

I hope, this solves your problem, though I'm not really sure.

Good Luck!

---

### Post by NiTsi on 2006-01-05
[QUOTE=hoffimar]Hi,

i want to use a xfs partition as normal user. Best would be to mount it at boot time, but I can't tell any uid in fstab for xfs. So how would I do that? If I make regularuser the owner of the mount point (in this case /media/data/), it makes root the owner when mounting. 
So I tried to to mount it manually as regularuser. My /etc/fstab entry for it looks like this: ```
/dev/hda5       /media/data     xfs     user,noauto        0       0
```
But after a "mount /media/data" again root is owner for /media/data?! After unmounting regularuser is owner again.
Any suggestions?

Cheers, Martin[/QUOTE]



I'm not sure if i understood but i think you want to handle the xfs mount like a simple user : open a terminal a root, go to /etc/fstab and in the options of the xfs  write     rw-users-auto-uid=###
to find out the number of your user uid go to System->Administration->user & groups.

---

### Post by hoffimar on 2006-01-06
Thanks for ur help! :D 

@schilcha: ok, that would work, but i'd have to do the chown after every reboot, maybe in an init script. So mounting it manually as regular user works with user,noauto, and that is what i did now, and i can write on the directory. But mounting as at boot time would change the owner to root i'd say, although i didn't test it out yet.

@NiTsi: you are right, i wanted to handle the mount of the xfs filesystem as a normal user, letting him be the owner of the directory after the boot. But there is no option uid=XXXX for xfs filesystems as the manpage told me, only for filesystems like vfat.  I read that user control is built into the fs, and there are parameters like quota for a user or group but i'm not sure how i could use them for myself. It would be easier with the uid option, but i think there's another possibility i'm not aware of yet.

Bye, Martin

---

### Post by kont.raen on 2006-01-06
[QUOTE=hoffimar]Hi,

i want to use a xfs partition as normal user. Best would be to mount it at boot time, but I can't tell any uid in fstab for xfs. So how would I do that? If I make regularuser the owner of the mount point (in this case /media/data/), it makes root the owner when mounting. 
So I tried to to mount it manually as regularuser. My /etc/fstab entry for it looks like this: ```
/dev/hda5       /media/data     xfs     user,noauto        0       0
```
But after a "mount /media/data" again root is owner for /media/data?! After unmounting regularuser is owner again.
Any suggestions?

Cheers, Martin[/QUOTE]

Hi Martin,

I think that there is no real problem there - in *NIX there is no problem with root being the owner of any given partition and it's mountpoint. The trick is rather to create directories on that partition that are owned by you or any special user.

Here is what I would do with that data partition of yours :

1. create the mountpoint with root as owner

sudo mkdir /media/data

2. add the regarding line to the fstab, using vim or nano or any editor of choice

/dev/hda5       /media/data     xfs     defaults        0       0

3. mount the partition to /media/data

sudo mount /media/data

4. create a directory on that new mounted partition and transfer the ownership to the desired user - let's say to the use known as "martin" in this case

sudo mkdir /media/data/mystuff
sudo chown -R martin:martin /media/data/mystuff

And from then on the user martin will have full rights in that directory. I regularly do that with additional partitions on all of my *NIX machines :). 

If you still want to skip one "level", so to say, then you can always create a symbolic link to mystuff within the media directory :

cd /media
sudo ln -s /media/data/mystuff ./mystuff

Hope I could be of any help.

---

### Post by hoffimar on 2006-01-06
Hi kont.raen,

thanks for your ideas! I guess the creation of directories on the partition owned by the regular user would do the trick for me. That way i'd be able to write to those and automount at boot time, only needing root for creating new directories.

Bye, Martin

---

