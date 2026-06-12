---
title: "Monitor HDD Activity Light"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-21
In the days gone when I used Windows I had an icon in the system tray to show me the HDD and DVD activity lights so there was never any need to peer at the floor to see if anything was happening.

Does anyone know of anything similar for Ubuntu?

---

### Post by bollix47 on 2007-11-21
Right click on the panel of your choice and select 'add to panel'

Look for System Monitor under System and Hardware and double click on it to add it to the panel.

Right click on the new icon and select preferences.

Click on the box next to Hard Disk.

---

### Post by expatCM on 2007-11-21
I had not even thought of looking there ... easy, thank you, that sorts out the hdd activity.  Are there any more items to add .... the DVD activity does not appear to be supported...?

---

### Post by bollix47 on 2007-11-21
Sorry but I know of no CD/DVD activity monitor.  Perhaps someone else can help you with this one.

---

### Post by expatCM on 2007-11-21
You have helped me solve 50% of the need so thank you.  Perhaps I will get lucky with the other 50% :)

---

### Post by mridkash on 2007-11-22
there is a software called gkrellm something. I think it does what you want. Search for it.

---

### Post by expatCM on 2007-11-22
searched for it and found it .....  wow this is very comprehensive indeed.  Thank you for suggesting this ... I had never come across this one at all ...

The only thing that appears to be missing is a CD activity monitor ....

---

### Post by mridkash on 2007-11-23
There is one command line software I found that can see how much data, and at what rate is written or read off drives including cd drive.
Install it.

```
sudo apt-get install sysstat
```

Then insert a CD into the drive and run this command,

```
iostat -d
```

it'll list all drives on your pc. On my laptop the cd drive came as sr0

If you want to monitor continuously at 1 sec interval. 
```
iostat -d 1
```

try man iostat to know more about the options.

PS. I came to know from somewhere that /proc folder contains all system and drive information on linux. and the monitoring tools read from /proc directory, not sure about this.

---

### Post by expatCM on 2007-11-27
hmm ... something not quite the same here .... if I compare the output of iostat -d with the list in /media there is a difference ...

iostat-d gives me 

hda
hdb
sda
sdb

whereas /media shows me 

cdrom
hda
sda
sdb

It may be that hdb is the cdrom which would fit in nicely.

Back to me to read the man pages ...  just had a look and whilst they are very comprehensive they appear to have all the promise of being hard to read :)

Thanks for your help

---

### Post by mridkash on 2007-11-27
```
$ iostat -d
Linux 2.6.22-14-generic (mridul-laptop)         Wednesday 28 November 2007

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              31.80       635.32       216.33    1199732     408520

```
This is the output before I insert a CD into drive. And Below is the output after inserting one.
```

$ iostat -d
Linux 2.6.22-14-generic (mridul-laptop)         Wednesday 28 November 2007

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              30.84       614.26       211.82    1203420     414992
sr0               0.04         0.20         0.00        392          0

```

---

### Post by expatCM on 2007-11-28
This is mine ...  a little different ...

Before```

:~$ iostat -d
Linux 2.6.22-14-generic (ga-m55s-s3)    28/11/07

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              31.02       101.38         0.02     229606         34
sdb               1.82        24.03        15.46      54424      35016
hda              27.22       520.34        45.39    1178501     102793

```
After```

~$ iostat -d
Linux 2.6.22-14-generic (ga-m55s-s3)    28/11/07

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              30.47        99.56         0.01     229606         34
sdb               1.79        23.60        15.18      54424      35016
hda              26.83       513.60        45.90    1184421     105857
hdb               0.07        12.15         0.00      28020          0

```

---

