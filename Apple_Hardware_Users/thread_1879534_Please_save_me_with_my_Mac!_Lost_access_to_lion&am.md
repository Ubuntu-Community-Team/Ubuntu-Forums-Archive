---
title: "Please save me with my Mac! Lost access to lion&amp;recovery partition,got windows&amp;linux"
date: 2011-11-11
forum: Apple Hardware Users
---

### Post by AuP%*qb!# on 2011-11-11
My Mac has Mac os x lion 10.7.2 on with windows 8 developer preview next to it. I accidentally somehow convert all the partitions to logical partitions which made windows and lion unbootable. I have reinstalled windows, so that's bootable now,
And windows classes the lion partitions as unformatted disks and keep asking me to format them.

I have a retail copy of snow leopard install disk, a live cd of Ubuntu 11.10, and a 2TB FireWire hdd.

I cannot get to the recovery partition either as same thing has happened with that.

Tried installing snow leopard to FireWire hdd, but I get an error.

Ubuntu live cd will recognize *the lion partition but I cannot access the most important data on the partition such as work, my video editing I done etc.

Some of the folders Ubuntu classes as unknown FILES, instead of FOLDERS, *and 90% of others are coming up with I don't have the permissions to view.

The file system that lion is on is hfs+ journaled, so I am stuck what to do there.

With snow leopard install DVD, I cannot edit the partitions or anything whatsoever apart from wiping the whole drive and starting from scratch, which ain't gonna happen until my important data is safe and snug on my FireWire hdd and netbook.

I have an iPod touch 4 64gb with almost 15gb of space left so that is gonna be a big problem getting back into sync with iTunes after reinstall.

My iPod has around 15gb of very important photos, 4gb music, 5gb of movies/personal important videos, a lot of PDFs in iBooks, around 20gb of apps that use daily, and a lot of the apps have data.

The Music is all from CDs, but that I have copied to my netbook, but videos and all apps and data etc needs to be somehow not lost.

I have Sims 3 on Mac with lots of saved data, which I would love not to lose as spent so hard getting stuff perfect, including an almost exact replica of my home.

I have lost lots of personal irreplaceable data before which has really left huge holes in memories and am determined to lose much more.

I think this should be "and am determined not to lose any more" laughing out loud!

Which would be less complicated? Somehow transferring my data via Linux or windows?

And if impossible, how can I remove the journaling from within *Ubuntu or windows?

And please, please, please, PLEASE say I am not doomed, as I am so close to backing up my data, but I have permissions and journaling barring my way.

Thanks for any help,*
Jase*

---

### Post by pindar on 2011-11-12
Boy, I can understand that this is worrying. Nevertheless: stay calm. Take a deep breath. Don't get overexcited. Your post isn't quite coherent: first you talk about partitions on your mac, then about your ipod, and I don't quite see how that comes into play. 

So: your mac partition(s) on your mac (which mac?) cannot be read properly from within ubuntu, nor from the leopard install disk, is that right? I would suggest two things:

[LIST=1]
[*]If you have access to another mac and if your "doomed" mac has a firewire port, try booting it in "firewire target disk mode." That way, you should have access to your files and can copy them to a safe place.
[*]The snow leopard install cd should also offer you to start a terminal (I think it's under "Utilities"). You could then mount the partition and again copy the files to a safe place.
[/LIST]

I wish you good luck. And I hope you have now learned the importance of backups.

pindar

---

### Post by AuP%*qb!# on 2011-11-12
I personally dont have another mac, it is an iMac 27" 2010 model.

[http://www.pcadvisor.co.uk/forums/1/helproom/4094114/please-save-me-with-my-mac-lost-access-to-lionrecovery-partitiongot-windowslinux-to-help-though/?pn=1](http://www.pcadvisor.co.uk/forums/1/helproom/4094114/please-save-me-with-my-mac-lost-access-to-lionrecovery-partitiongot-windowslinux-to-help-though/?pn=1)

I have also asked on here.

And not sure what I should start with.

I know an Apple Expert, so I might wait for him to come around but I would like to see if I could get somewhere. I will post on a bit later as a bit busy at the moment.

---

### Post by AuP%*qb!# on 2011-11-12
Also, I have known the importance, but only yesterday, recieved the FireWire hdd.

---

### Post by linuxopjemac on 2011-11-12
I would boot into Linux, mount the Apple partition and copy all the contents of your home folder over. You can then burn it to a CD or so.

Good luck

---

### Post by AuP%*qb!# on 2011-11-12
I would boot into Linux, mount the Apple partition and copy all the contents of your home folder over. You can then burn it to a CD or so.

Good luck


I would if I could!

I can access the drive, but 99% of the folders/files say I don't have the permissions. So I need to some how change those permissions. I have 2TB FireWire external hdd for copying the stuff over.

---

### Post by linuxopjemac on 2011-11-12
just do it as root, then you can at least copy them over (sudo).

Use the cp command with a -p integer to copy and preserve time stamps, ownership, and -R for recursive, to go into the folders, so it would be something like:

```
sudo cp -Rp /path/to/your/home /path/to/your/backup
```

---

### Post by AuP%*qb!# on 2011-11-12
If you have access to another mac and if your "doomed" mac has a firewire port, try booting it in "firewire target disk mode." That way, you should have access to your files and can copy them to a safe place.


I hope that our apple expert has a MacBook, as that may save the day!

If not, dunno if might be able to get friend to come round with her MacBook at the same time that he comes over.

Tough one this.

---

### Post by AuP%*qb!# on 2011-11-12
ubuntu@ubuntu:~$ sudo df -h

Filesystem------------Size---Used---Avail--Use%--Mounted on

/cow------------------1.9G---53M----1.9G---3%--- /

udev------------------1.9G---4.0K---1.9G---1%----/dev

tmpfs-----------------778M---836K---778M---1%----/run

/dev/sr0--------------698M---698M----0----100%---/cdrom

/dev/loop0------------663M---663M----0----100%---/rofs

tmpfs-----------------1.9G---8.0K---1.9G---1%----/tmp

none------------------5.0M---4.0K---5.0M---1%----/run/lock

none------------------1.9G---104K---1.9G---1%----/run/shm

ubuntu@ubuntu:~$

I hope that make sense I do not really understand which is which

Does any of this help so you could help with that sudo command you mentioned?

---

### Post by linuxopjemac on 2011-11-12
- are you in a live environment ? 
- did you connect the firewire HD  (I don`t see it though)

---

### Post by AuP%*qb!# on 2011-11-14
Yes it's on a live cd

And re-reading my first post where it says:

I have lost lots of personal irreplaceable data before which has really left huge holes in memories and am **determined to lose much more.**

I think I should be a bit worried what I said there!&#128516;

I think it should of said *and am determined to not loss any more.* lol!

---

### Post by 741Baus on 2011-11-14
Hi Jwarn , you could try this, from a live cd open a terminal and 

```
sudo apt-get install hfsplus libhfsp0
```

I don't have a Mac but I have recovered data from my Ubuntu system when I did something dumb and made my system unusable , I believe Mac uses HFSP file system so perhaps this will cure your permission problems.

---

