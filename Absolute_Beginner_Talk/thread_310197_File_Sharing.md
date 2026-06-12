---
title: "File Sharing"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-11-30
Obviously this isn't as easy as I thought. On the 6.06 desktop I selected share folder as NFS. Now, how do I access it from the 6.10 laptop?](*,)

---

### Post by bt224 on 2006-11-30
My guess is that I am doing (or not doing) something simple.

---

### Post by PilotJLR on 2006-11-30
Don't worry, it's easy. go to a terminal, then make a mount point and mount the share, like so:
```

sudo mkdir /mnt/nfs
sudo mount -t nfs 192.168.x.x:/home/username /mnt/nfs


```

Of course, substitute the "192.168.x.x" for whatever your nfs server's ip address is, and change "/home/username" to the path of what you exported.


Another easy way is to install samba, share via samba, and connect by clicking Places | Connect to Server.

---

### Post by bt224 on 2006-11-30
playing with Samba now, tells me it's not a folder
I changed to SMB on the host computer

---

### Post by PilotJLR on 2006-11-30
> **bt224 said:**
> playing with Samba now, tells me it's not a folder
I changed to SMB on the host computer

Could you elaborate what this means?

As in the exact error message, where you received the error, etc.

---

