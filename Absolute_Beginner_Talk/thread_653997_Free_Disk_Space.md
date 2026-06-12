---
title: "Free Disk Space"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Houseofsleep on 2007-12-30
I have just installed Feisty. I am trying to install a programme to run under WINE - it requires 3Gb of space to install. According to the installer I only have about 700mb of space to install to. 
I originally set up Feisty using Wubi and created a 10Gb partition. 
I haven't installed anything else. 
I checked the Disk Manager which says I have used around 2gb and have around 6Gb of space free. 
How can I install to this free space? 

On a related topic - can I run a programme that is installed on my windows partition from inside Ubuntu or do I have to install it on the Ubuntu partition. If so - how?

Many thanks for any help

---

### Post by taurus on 2007-12-30
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Houseofsleep on 2007-12-30
> **taurus said:**
> Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```


Is this what you mean?

Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                      8.3G  2.4G  5.5G  31% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   76K  506M   1% /proc/bus/usb
udev                  506M   76K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      939M  176M  716M  20% /home

---

### Post by taurus on 2007-12-30
Where did you try to install that program?  You cannot install it in your $HOME since you don't have enough space.  Try to install it to /opt.  To install to /opt, you need to run the command with the sudo in front since you need root privilege to write anywhere outside of your own $HOME.

```
sudo *command*
```

---

### Post by Houseofsleep on 2007-12-30
I am not entirely sure where it was trying to install to - I was trying to install Half Life 2 from Steam which didn't seem to give me an option of where to install it to. 

If Home is the default is it possible to increase the amount of space in Home?

---

