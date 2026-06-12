---
title: "How to Map Network Drives"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by uhrohraggy on 2008-01-22
I know that the address of the shared folder is:

\\lu-srv1\users\M

and a username and password are required, which I have.

but how do I get access to these folders? Any ideas, either automatically or in terminal?

Thanks.

---

### Post by dannyboy79 on 2008-01-22
you can use nautilus, then in the location bar, enter this:

smb:\\lu-srv1\users\M

(it could be smb://lu-srv1/users/M
i forget as I don't use that?)


it should then prompt you for a username/password

or you could use your fstab to automatically mount them following this guide:
[http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares)

---

### Post by emarkd on 2008-01-22
Is that a Windows share?  If so, you could:

1. Create a directory to mount it to:

```
sudo mkdir /media/win_share
```

2.  Mount the share like this:

```
sudo mount -t cifs //server/folder /media/win_share -o username=whatever,password=whatever,rw
```

You'll need samba installed first, which it probably already is

---

### Post by furball_1185 on 2008-01-22
If you are using Ubuntu (Gnome), there is a "Connect to Server" option under the Places dropdown. This will mount a network location as a drive for you, and place a link on your desktop. If the share you want is  on a Windows machine, use Samba as the connection protocol. Whats nice about this is the connection to share will persist though reboots, and can be disconnected at any time by right-clicking the drive on your desktop and unmounting it.

---

