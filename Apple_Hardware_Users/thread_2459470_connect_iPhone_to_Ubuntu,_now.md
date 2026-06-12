---
title: "connect iPhone to Ubuntu, now"
date: 2021-03-19
forum: Apple Hardware Users
---

### Post by archeryrob2 on 2021-03-19
So I take pictues and videos on my iPhone 8 of my blog and video accounts. I would just plug my apapter cord into the USB, hit trust and password on the phone and it would pop up in files. NOW, it is not doing that any more. Even a restart and no go. I am assuming apple chnaged something to screw this up. 

I there any software solutions to download to make this work better? 

Using 20.04.2 LTS

---

### Post by workaround on 2021-04-08
Same here, it worked and NO more! Did you resolve it? Thanks

---

### Post by workaround on 2021-04-09
Try this:  [https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/](https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/)

---

### Post by nitinpatel on 2021-05-09
Not working tried many times but failed.

---

### Post by oldfred on 2021-05-09
I used to use ppa, but now just install from repostitory.

```
sudo apt-get install ideviceinstaller libimobiledevice-utils ifuse libimobiledevice6  libplist3

sudo apt-get install heif-gdk-pixbuf heif-thumbnailer libheif1 gimagereader gpicview

```

I prefer to mount to a location that does not by default show in file browser, but you could mount anywhere you like.
```

#iphone First time
sudo mkdir /mnt/iPhone
sudo chown  $USER:$USER /mnt/iPhone 
sudo chmod  a+rwX,o-w /mnt/iPhone

idevicepair pair
ifuse /mnt/iPhone/
ls  /mnt/iPhone
ideviceinfo -d

#to unmount:
fusermount -u /mnt/iPhone
idevicepair unpair
```

I prefer to use rsync to copy photos. Not my exact command as I have already created folders in my data partition for my Pictures.
rsync -aruvlP /mnt/iPhone/DCIM/100APPLE/  /mnt/data/Pictures/All2021

You may have other folders in DCIM.

---

