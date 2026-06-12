---
title: "not privilaged to mount seagate free agent"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Vega on 2008-03-23
hey guys, I'm having some trouble mounting my ext. seagate free agent drive which is NTFS.

It says I don't have permission to mount

I'd appreciate some help on this ^^

---

### Post by wormser on 2008-03-23
Do you have the NTFS package installed?

```
sudo apt-get install ntfs-config
```

Applications> System Tools> NTFS Configuration Tool> Enable write support for external device.

---

### Post by Vega on 2008-03-24
I have it installed now but now my ext disc isn't even shown up in computer

---

### Post by wormser on 2008-03-24
Try restarting your PC or if you are sure that it is unmounted, unplug it and plug it back in.

---

### Post by bumanie on 2008-03-24
There is a problem with seagate free agent and ubuntu. Read this:
"SEAGATE'S latest batch of drives, the ironically titled Free Agent series
are not compatible with the Open Sauce operating system Linux....
There are a few work-arounds but Seagate Tech Support says they do not know what they are.
Instead they are telling man plus dog that their latest drives do not support Linux..." Also look here:
[http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux](http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux)
The only work around I have seen is to use it with an esata port
"I've also used the drive with the eSATA connection, and in that case the linux kernel does appear to be able to restart the drive correctly".

---

### Post by wolfen69 on 2008-03-24
> **bumanie said:**
> There is a problem with seagate free agent and ubuntu. Read this:
"SEAGATE'S latest batch of drives, the ironically titled Free Agent series
are not compatible with the Open Sauce operating system Linux....
There are a few work-arounds but Seagate Tech Support says they do not know what they are.
Instead they are telling man plus dog that their latest drives do not support Linux..." Also look here:
[http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux](http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux)
The only work around I have seen is to use it with an esata port
"I've also used the drive with the eSATA connection, and in that case the linux kernel does appear to be able to restart the drive correctly".

gotta love it.... :mad:

i hope you can return it. i just searched google, and it seems certain western digital "mybook" hard drives are also snubbing linux.

---

### Post by Vega on 2008-03-24
geh.. I had this drive for over a year now..

seriously that is the most ludicrous thing I've ever read, hell I even adjusted the power settings in windows to never spin down and I'm still stuck in this situation.

Is there a chance Hardy Heron could fix this problem?

---

