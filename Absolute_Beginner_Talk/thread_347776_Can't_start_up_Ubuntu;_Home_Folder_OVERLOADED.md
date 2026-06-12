---
title: "Can't start up Ubuntu; Home Folder OVERLOADED"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-27
What started as a very innocent pursuit has ended in DISASTER...........I cannot start up Ubuntu except in Recovery Mode.

I was preparing to install Beryl and had run the following commands:

```

sudo apt-get install ubuntu-desktop
sudo apt-get update
sudo apt-get upgrade  
```

Just after the Upgrade step had started I got a message claiming that the Home Folder was 99% full.But what could I do?
The Upgrade continued for about 30 minutes after which it errored out almost certainly because of lack of disk space.

After this, the desktop was essentially inactive with very little actually functioning. The Home folder showed 0% Free Space.

OK, so I rebooted into Recovery Mode and tried an Autoclean and a Deborphan Purge in addition to deleting practically everything from the Home folder (including a lot of desktop stuff that appeared to have been installed by the first command above).
By my calculations, the Home folder contained, at this stage, no more than 15 MB of files..

However, rebooting to Ubuntu I couldn't get past the login step.

My Ubuntu installation is spread across three partitions:
Root: 5 MB
Swap: 2 MB
Home: 8 MB

Note that the Home folder is on the Root partition and not the Home partition. It seems that all of the other upgrade stuff that was installed basically left no space for the Home folder.

At this stage, I think I'm looking at a reformat and re-installation of Edgy.......unless, of course, somebody out there knows how I might extricate myself from this more painlessly???

Any thoughts?

---

### Post by kingmonkey on 2007-01-27
This sound all wrong to me.

Are u sure the above values are MB?

Is the below correct:
/ 5GB
swap 2 GB
/home 8GB

or is that wrong?

I dont understand if ur home partition is a partition on its own or a part of / partition?

---

### Post by taurus on 2007-01-27
Boot into recovery mode and run

```
apt-get clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
(replace the actual login name of your system for the **username**...)
df -h
```

---

### Post by PaulFXH on 2007-01-27
Sorry kingmonkey but it's late here and I've had a rough day.
What I called Megabytes (MB) are of course Gigabytes (GB).
Also, my Home partiton is indeed a separate parttiton all on its own.

---

### Post by PaulFXH on 2007-01-27
Many thanks for the suggestion taurus. That worked very nicely and I'm back in Ubuntu.
Seems that apt-get clean does an awful lot more than apt-get autoclean which is what I had tried before.

Cheers

---

### Post by kingmonkey on 2007-01-27
lol no worries. Glad you got it sorted.

---

