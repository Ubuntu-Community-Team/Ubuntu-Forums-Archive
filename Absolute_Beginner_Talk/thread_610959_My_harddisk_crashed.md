---
title: "My harddisk crashed"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Marysart on 2007-11-12
Hello Everyone,

I'm a new user to Ubuntu and for the past 6 months everything was just working ok.
I have Ubuntu 7.04 installed on a seperate 120 GB hitachi HD.
I was downloading from the internet and my system froze. After I restarted I got the following error message:

GDM could not write to your authorization file.
This could mean that you are out of disk space or
that your home directory could not be openen for writing
In any case is not possible to log in. Please contact 
your system administrator.

Well, I am the system administrator and I don't know what to do. :-(.
I can get into recovery mode where I am logged in as root, but I do not speak linux I'm sad to say.
I only know ls and  cd...

Btw It is very well possible that my harddisk is full, as I got the feeling that the amount of space left shown by the system was somehow not correct.
Does anyone know if there is an issue with ubuntu and my HD?
Does anyone know anything I could try to at least maybe retrieve some of my information..?

Any help would be much appreciated.

Regards, Marysart

---

### Post by taurus on 2007-11-12
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by Marysart on 2007-11-12
Taurus, thank you for replying,
I typed the command and got the following message:

Filesystem             Size          Used          Avail              Use              Mounted on
/dev/sdb1              112G        107G              0           100%              /
varrun                    248M          16k       248M              1%              /var/run
varlock                  248M             0        248M               0%             /var/lock
procbususb            248M         104k      248M               1%             /proc/bus/usb
udev                      248M         104k      248M               1%             /dev
devshm                  248M              0      248M                0%             /dev/shm
lrm                         248M         33M      215M             14%              /lib/modules/2.6.20-16-generic/volat-
ile

It seems my HD is actually full. Would you or anybody know how I could reach my files? i have tried ls but get nothing

---

### Post by SmartRutter on 2007-11-12
What I did when I couldn't access my files was to boot up ubuntu off of a LiveCD and mount my partitions.  I did that by: right-clicking on a panel, clicking "Add to Panel...", and by adding disk mounter to a panel.  The disk mounter should display your partitions and all you have to do is click on it and then click on "Mount <insert drive name here>"

After that, you should see an icon on your desktop that will be your hard drive.  Just click on it and you should be able to access everything on there.  This worked great for me when Windows XP wouldn't boot for me and I needed to get all my files off of there.  I just put them all a flash drive and re-installed.

---

### Post by taurus on 2007-11-12
> **Marysart said:**
> Taurus, thank you for replying,
I typed the command and got the following message:

Filesystem             Size          Used          Avail              Use              Mounted on
**[COLOR="Blue"]/dev/sdb1              112G        107G              0           100%              /[/COLOR]**
varrun                    248M          16k       248M              1%              /var/run
varlock                  248M             0        248M               0%             /var/lock
procbususb            248M         104k      248M               1%             /proc/bus/usb
udev                      248M         104k      248M               1%             /dev
devshm                  248M              0      248M                0%             /dev/shm
lrm                         248M         33M      215M             14%              /lib/modules/2.6.20-16-generic/volat-
ile

It seems my HD is actually full. Would you or anybody know how I could reach my files? i have tried ls but get nothing

Yip.  You just maxed out your 112GB of space on /dev/sdb1!  You can do some cleanup, freeing up some space so you can at least log in and removing even more files that you don't need.

From the recovery mode, run

```
apt-get clean
df -h
shutdown -r now
```

---

### Post by mcduck on 2007-11-12
> **Marysart said:**
> Taurus, thank you for replying,
I typed the command and got the following message:

Filesystem             Size          Used          Avail              Use              Mounted on
/dev/sdb1              112G        107G              0           100%              /
varrun                    248M          16k       248M              1%              /var/run
varlock                  248M             0        248M               0%             /var/lock
procbususb            248M         104k      248M               1%             /proc/bus/usb
udev                      248M         104k      248M               1%             /dev
devshm                  248M              0      248M                0%             /dev/shm
lrm                         248M         33M      215M             14%              /lib/modules/2.6.20-16-generic/volat-
ile

It seems my HD is actually full. Would you or anybody know how I could reach my files? i have tried ls but get nothing

Try running 'apt-get clean' in recovery mode. This will delete all package files apt-get has cached when you have installed programs. If you are lucky that will clear enough disk space so you can log in normally again.

After that it might be a good idea to remove some less necessary stuff to gain a bit more available disk space..

---

### Post by Marysart on 2007-11-12
*I'm doing the Snoopy dance* :)

It worked. Thank you so much for your help.

Regards, Marysart.

---

