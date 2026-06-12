---
title: "nfs share not mounting on boot"
date: 2009-02-05
forum: Apple Hardware Users
---

### Post by boblounsbury on 2009-02-05
I just upgraded from 6.06 to 8.04. Under 6.06 everything worked. I put an nfs mount in fstab and it would mount at boot and the nfs share would show up on the desktop once network manager connected to the wifi. With 8.04 it's not working at boot. I can manually mount the share, but I want it automatically mounted, which is why I have the share in my fstab file.

I've checked my /etc/fstab a few times, and it's exactly the same as before:

```
server:/home/Home_Share   /media/Home_Share   nfs   rsize=8192,wsize=8192,timeo=14,intr
```

Nothing on the server has changed, and I know it's working since I can manually mount the nfs share. Just don't understand why it's not automatically mounting since the upgrade :(.

---

### Post by boblounsbury on 2009-02-05
Well, I think it's working now. I was trying a bunch of different things and finally ran:

```
sudo mount -a
```

I guess this re-read the fstab file, and mounted my nfs share. I then rebooted and the nfs share automatically mounted again. So, it seems to be working now.

Strange :confused:.

---

