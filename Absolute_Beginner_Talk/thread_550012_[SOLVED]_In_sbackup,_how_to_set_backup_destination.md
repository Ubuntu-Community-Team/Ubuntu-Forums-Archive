---
title: "[SOLVED] In sbackup, how to set backup destination as external hard drive?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-13
How do I configure the backup destination in sbackup to be an external hard drive? Feisty recognizes the external hard drive just fine and it is mounted. But in the "destination" tab of sbackup config, there doesn't seem to be any option for browsing to and selecting a location on an external hard drive as the backup destination.

There are three listed options: 
1. Use default backup direction (/var/backup)-- which is on the internal hard drive.
2. Use custom local backup directory-- the browser window here only lets you browse the internal hard drive.
3. Use a remote directory (SSH or FTP) -- this seems to refer to "remote" in the sense of a location somewhere else. There is no browser window here for selecting an external hard drive.

So how do you select an external hard drive which is connected and mounted, as the backup destination?

---

### Post by Bothered on 2007-09-13
You can set it by manually editing /etc/sbackup.conf (look for "target = " in "[general]").

---

### Post by CaptainInsaneO on 2007-09-13
There are tabs at the top of the sbackup window. Click around those and see if you can find it. I'd tell you exactly what tab it is but I'm not on my Ubuntu box right now.

I back up all my stuff to my Windows hdd lol.

---

### Post by Bothered on 2007-09-13
It's on the "Destination" tab - select "Use custom local backup directory".

---

### Post by swarup on 2007-09-13
> **Bothered said:**
> It's on the "Destination" tab - select "Use custom local backup directory".

Are you saying that the browser window of the option, "Use custom local backup directory", can browse to an external hard drive? I could not get it to do that. How do you get the browser window to switch to another HD? It only seems to give scope to browse the internal HD.

Or are you still saying I need to manually configure the destination as you wrote in your first post?

---

### Post by Bothered on 2007-09-13
> **swarup said:**
> Are you saying that the browser window of the option, "Use custom local backup directory", can browse to an external hard drive? I could not get it to do that.

Once you've clicked the radio button for "Use custom local backup directory" you can choose the directory by clicking on the box beneath the button (it probably says something like "/var/backup"). You can then browse to any directory - to choose the external drive browse to the mount point for the external drive.

> **swarup said:**
> What folder is "etc" in?)

Root ("/"). The sbackup configuration file is "/etc/sbackup.conf". To edit it, type the following in a terminal:

```
sudo cp /etc/sbackup.conf /etc/sbackup.conf.bak~
gksudo gedit /etc/sbackup.conf
```

---

### Post by swarup on 2007-09-13
> **Bothered said:**
> Once you've clicked the radio button for "Use custom local backup directory" you can choose the directory by clicking on the box beneath the button (it probably says something like "/var/backup"). You can then browse to any directory - to choose the external drive browse to the mount point for the external drive.

I see. It's quite clear now. I sometimes get confused when trying to browse to another drive, because I forget that the other drives are all located under "media". Rather than how its done in Windows, and all the drives are separately visible right in the root directory.

> **Bothered said:**
> Root ("/"). The sbackup configuration file is "/etc/sbackup.conf". To edit it, type the following in a terminal:

```
sudo cp /etc/sbackup.conf /etc/sbackup.conf.bak~
gksudo gedit /etc/sbackup.conf
```

Thank you. This is also quite clear now. Before receiving your answer about how to browse to the external drive, I tried opening sbackup.config to change the default destination pathway, but it was a "read-only" file. And here is your solution to that problem above. So everything is solved now. Thanks. :)

---

