---
title: "how to add a second hd in ubuntu 704"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by awec56a8 on 2007-09-30
:confused: hi newbie question here!

i have ubuntu installed in my c: and i like add a second hdd as a data/docs storage. i formatted the new hdd with gparted (ext3, primary partition) but then it seems i can't put any docs or files onto my new hdd. any help will be appreciated.

regards,

awec56a8

---

### Post by mendingo84 on 2007-09-30
is you new hard drive detected? Paste the result of the following commands here:

```
cat /etc/fstab
```

```
sudo fdisk -l
```

---

### Post by Arthur Archnix on 2007-09-30
Sounds like you don't yet have permission to write to the drive. You need to know the name of the drive, and where it's mounted. You might find this information in your fstab.
```
cat /etc/fstab
```
Do that and send it back here if you can't figure it out. 

Once you know the mountpoint you do this:
```
sudo chown -R user:user mountpoint
```
Let's say that your new disk is mounted to /media/disk, and your login name is bob, what you would write is:
```
sudo chown -R bob:bob /media/disk
```

---

### Post by awec56a8 on 2007-10-02
hi thank you guys for your help, just got back from a trip will  post the result asap. sorry about the late reply.

regards, 
awec56a8 :)

---

### Post by awec56a8 on 2007-10-06
hi guys! 
thank you for the help i installed my 2nd hd and mount it and change ownership and now i am able to store my data onto my 2nd hd.
great help! appreciated.

regards,
awec56a8

---

