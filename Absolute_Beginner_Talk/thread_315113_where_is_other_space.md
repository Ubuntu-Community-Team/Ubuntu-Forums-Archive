---
title: "where is other space"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by zhangqing6 on 2006-12-08
Hi everyone,

installed Edgy with separate partition for /home,if I use system >Administration>Gnome Partition Edition,it will show 585 mb used in that partition.but i checked properties of my home folder,only 187 Mb,where is other space.](*,) 

thanks in advance

---

### Post by taurus on 2006-12-08
What does this command say when you run it from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by zhangqing6 on 2006-12-08
thanks,

qzhang@qzhang-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              16G  2.3G   13G  15% /
varrun                126M   80K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                126M     0  126M   0% /dev/shm
/dev/hda6              13G  378M   12G   4% /home
/dev/hda2              21G  7.9G   13G  40% /media/hda2
tmpfs                 126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
qzhang@qzhang-desktop:~$ 
:)

---

### Post by taurus on 2006-12-08
Here's the read out of your /home partition...

```
/dev/hda6   13G   378M   12G   4%   /home
```
So, /home takes up about 378MB of space on /dev/hda6.

---

### Post by zhangqing6 on 2006-12-08
thanks a lot,


585-187=398


does it mean 378 mb just for nothing? I checked with gparted say 585 used,but  when I checked home folder only 187 mb contents.

sorry, I am brand new for ubuntu/linux

qing

---

### Post by taurus on 2006-12-08
Actually, if you are using ext3 filesystem, 5% of the space is reserved for journaling...

---

### Post by zhangqing6 on 2006-12-08
that make sense.:) 

thank you very much

---

### Post by taurus on 2006-12-08
You're welcome and have fun.

---

### Post by zhangqing6 on 2006-12-08
just for fun also for you infomation:) 

I did a new installation Edgy. format hdra3 for /,format hdra6 for /home,hdra5 for swap

only install Gparted from Synaptic

df -h


qzhang@qzhang-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              16G  1.9G   14G  13% /
varrun                126M   80K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hda6              13G  130M   12G   2% /home
/dev/hda2              21G  7.9G   13G  40% /media/hda2
qzhang@qzhang-desktop:~$ 

system->Administration->Gnome Partition Editor
shows:

/dev/hda3     2.06 G used
/dev/hda6     340 mb used


thank you again
TTYL

---

