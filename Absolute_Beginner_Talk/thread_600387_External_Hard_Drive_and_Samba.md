---
title: "External Hard Drive and Samba"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by travelinrob on 2007-11-02
Greetings,

I have installed Gutsy and I share a folder on an external hard drive using 'user' security. I want to be able to log in as different users over the network. I want full access for me, but read only for others. If I try to change 'others' folder access permissions through Nautilus to 'read only', it immediately switches back to 'none'. Currently, if I log in as me through a windows box, all is well, but, as another account I can only see the shared folder but cannot open it. Both accounts are system and samba users. When Ubuntu auto mounts the drive my user owns it, but the group is root (Could this be my problem?). If I become root and try to chmod 775 the directory, it does nothing (reacts like Nautilus). If, as root, I try to change the group, it says I do not have permission. If I share the directory with 'security = share' and make it public, browseable, etc, it is available as well- I just don't want that. (Actually, I may have had to force the user and group to get that to work- it's late, err, early)

Basically, I want my wife to be able to access the files without the possibility of accidentally deleting anything and I want to be able to do what I want with them from another machine.

I appreciate the help,
Rob

---

### Post by njparton on 2007-11-02
Take ownership of the folder you mounted the drive to e.g.

```
sudo chown user /mnt/folder
```

then give yourself full permissions to that folder:

```
sudo chmod u+rwx /mnt/folder
```

then assign group and other permissions as you see fit. e.g. remove all their permissions to start with and then add them back as required. e.g. to give them read only permissions:

```
 chmod go-rwx /mnt/folder
chmod go+r /mnt/folder
```

where "/mnt/folder" is the path to your mounted drive and "user" is your username.

if you're sharing the drive via samba make sure each user has an account in ubuntu and then use the following to set a samba password for each:

```
sudo smbpasswd -a user
```
and enter the password twice. Repeat for each user.

---

### Post by travelinrob on 2007-11-02
I appreciate your post. I guess it was not clear from my post that I understand those commands. The problem I am having is that I can only change chmod for the 'user'- even as root. The command has no affect on 'other' or 'group'. I get no error, but no change in permission.

---

### Post by njparton on 2007-11-02
> **travelinrob said:**
> I appreciate your post. I guess it was not clear from my post that I understand those commands. The problem I am having is that I can only change chmod for the 'user'- even as root. The command has no affect on 'other' or 'group'. I get no error, but no change in permission.

I don't quite understand - a folder (or a drive/partition mounted as a partition) can only have one owner.

Everybody else is either group or other. 

If you can't changes permissions as root via sudo, or take ownership and then change permissions, then it sounds like the way you've mounted the drive is not allowing you to make any changes.

You haven't mounted it as read-only (or something else restrictive) have you?

Do you mount it via the command line or automatically via fstab?

Maybe post the latter here?

---

### Post by travelinrob on 2007-11-02
Basically, when I boot the OS it automatically mounts the drive (nothing that I set up). It is set up with rob as the user, but root as the group. On the local machine, I can read and write to the drive. Over the network from a Windows box, I can read and write as well, if I put in my username and password- as I am the owner. But, if I try to log in with another username (that is both an ubuntu user and a samba user) login fails with a permissions error. From the command line as either myself or root, I cannot change the rw settings for anyone other than the owner. It just won't do anything. The same thing happens if I try with Nautilus. I click 'access files' for 'others' and instantly it sets it back to 'none'.

---

### Post by njparton on 2007-11-02
Have you set a samba password for that other user?

---

### Post by travelinrob on 2007-11-02
Yes

---

