---
title: "Samba subfolders"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Scrier on 2007-12-23
Hi, 

I have added sama and configured it up to share 2 folders that I have on the ubunut machine, I can connect to it and all but I cannot access the subfolders or copy items from my windows machine to them.

> [downloads]
comment = Downloads
path = /home/scrier/Downloads
available = yes
browseable = yes
create mask = 0777

[media]
comment = media
path = /var/lib/media
available = yes
browseable = yes
create mask = 0777

that is how the samba file looks, I have managed to mount both catalogues and I can browse them in windows, although when i access one of their subfolers it won't work any more. I cannot copy to it or execute files in there.

// Andreas

---

### Post by blueridgedog on 2007-12-23
Can not copy to the sub folders or to any folder?

Let me see the permissions of the sub folders with:

ls -al /home/scrier/Downloads

and 

ls -al /var/lib/media

In the event that you just want to be certain that permissions are wide open on these two shares/folders (not recommending it, but it appears to be the setup you are going for)

chmod 777 /home/scrier/Downloads -R

chmod 777 /var/lib/media -R

If you are not the owner of the folder and the sub folders, then you may need to sudo the above.

My suspicion is that folders in there are owned by you and or root and that your users accessing it via samba do not have permissions to write there.

---

### Post by Scrier on 2007-12-23
Hmm trying to copyto the base folders fails as well.

here is ls -al /home/scrier/Downloads:
> drwxrwxrwx 18 scrier scrier 4096 2007-12-23 11:25 .
drwxr-xr-x 36 scrier scrier 4096 2007-12-23 11:24 ..
drwxrwxrwx  2 scrier scrier 4096 2007-12-23 10:01 Incoming
drwxrwxrwx  2 scrier scrier 4096 2007-12-23 09:51 Misc
drwxrwxrwx  2 scrier scrier 4096 2007-12-23 09:51 Utils
drwxrwxrwx  2 scrier scrier 4096 2007-12-23 09:51 Crap

and ls -al /var/lib/media:
> total 4
drwxrwxrwx  6 root root   61 2007-12-22 20:09 .
drwxr-xr-x 58 root root 4096 2007-12-22 20:08 ..
drwxrwxrwx  2 root root    6 2007-12-22 20:08 anime
drwxrwxrwx  2 root root  113 2007-12-23 11:24 movies
drwxrwxrwx  2 root root    6 2007-12-22 22:54 recordings
drwxrwxrwx  2 root root    6 2007-12-22 20:09 music

---

### Post by blueridgedog on 2007-12-23
You may want to make the shares public and writeable:

```
[downloads]
comment = Downloads
path = /home/scrier/Downloads
guest ok = yes
writable = yes
available = yes
browseable = yes
create mask = 0777

[media]
comment = media
path = /var/lib/media
guest ok = yes
writable = yes
available = yes
browseable = yes
create mask = 077
```

After changing share definitions, you will need to restart samba and potentially reconnect with your remote system.

---

