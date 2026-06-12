---
title: "Backup? System Restore Point?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-10-01
I am a Windows XP user running a Dual-Boot with Ubuntu.  My question is whether I could backup or set a System Restore Point like in Windows right from my current set up, or recommendations for a package that would do the trick.

---

### Post by aysiu on 2006-10-01
Ubuntu doesn't have a built-in restore system, but you can use a third-party program like PartImage:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Alternatively, you can *tar* everything using [this HowTo](http://www.ubuntuforums.org/showthread.php?t=35087).

---

### Post by SirShaggy on 2006-10-01
I just used the tar method that aysiu spoke of, it worked quite well for me. I then burned it to a dvd for future use.......actually I hope not to use it!
Was really straight forward and pretty easy, it took some time on my P4 2.4GHz though......2hrs, 15min.
SirShaggy

---

### Post by think13 on 2006-10-01
I used the tar method also.  I have a question about burning it to a cd though.  If I need to restore my system using a live cd, will I still be able to use the cd with the backup?  I have a laptop with only one CD drive, and I have had troubles with using cd's during live cd boot in the past.

---

### Post by SirShaggy on 2006-10-01
I too had troubles with the built in CD drive on my old HP, I bought an external sony DVD/RW drive. I use it most often. I have not crashed this particular version of Ubuntu (My desktop, yes) so I have not needed to use the disk. I understand that this will recover everything that I backed up. I will be doing my desktop later tonight, also burning to DVD for later.......um, nevermind! You get the idea. I hear it works well, not sure if you must reinstall the live CD first or not.
SirShaggy

---

### Post by tagra123 on 2006-10-01
I use partimage -- especially before installing package and updates that may break my system.

To be honest Updates have shutdown the machines more times than the odd software has.

I also use the following scripts to create daily, hourly and weekly backups of important files. Many of the settings are stored in the home directory for the software and gnome. The etc directory is also another good one for other settings too. These scripts don't show the etc backup but it could be easily added.

[http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)

For simplicity my scripts show a second hardrive partition being used but it could easily be to another computer over the network by mounting a network drive.

The script can use tar or rsync and is handy.

tar can give a quick backup but It required a little work when testing a full restore to get everything working as mentioned in the how-to by aysiu.

partimage restores work great, The machine is restorerd just the way it was with the only real drag of getting partimage from the live cd. It take about 15 minutes for the root partition and about 20 minutes for the home partition. The restores are usually faster than the backups.

Remember a backup is no good if it cant easily be restored.

 ```
sudo apt-get partimage
```

I use it to backup shared windows folders via samba too.

---

### Post by think13 on 2006-10-01
I don't have another computer to use, and I don't want to create a new partition.

The backup I am creating takes up more than a gig. Is there generally a need to create a backup of more than just personal files?

---

### Post by SirShaggy on 2006-10-01
I only backed up everything so that I don't have to re download all of the programs I use and all of the ubuntu updates that have came out since I installed Dapper in June. I just hate downloading stuff.
Only back up what you want to. It's just that if you have to start from scratch again, you will only have your files, not all the programs too.
My backup was 2.8gig and I used .bz2 for even more compression.
I hope at this point somebody more knowledgeable will chime in as to what all SHOULD be backed up, I'd just be guessing. Sorry about that.
SirShaggy

---

### Post by tagra123 on 2006-10-01
> **think13 said:**
> I don't have another computer to use, and I don't want to create a new partition.

The backup I am creating takes up more than a gig. Is there generally a need to create a backup of more than just personal files?

Yes and no.

If you open up multiverse and universe as well as external repositories you run into a better chance of having problems. I generally open up these repositories to install a program I think I need and then close them up again afterwards.

Occasionally the updates make some things unusable but this is rare and there is usually a way to get things right again if you can get access to the internet to ask or search on these forums.

If you are going to be changing a "system settings" file like /boot/grub/menu.lst or basically anything in the /etc directory you can make yourself your own system restore point for these files by using the cp (copy command)

```
sudo cp /boot/grub/menu.list /boot/grub/menulist.bak.todaysdateandtime
```

or for the /etc/samba/smb.conf

```
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.bak.01-OCT-06-0953pm
```

that way if a setting you changed causes trouble then you can fix it even if you can only get to the command line.

To restore simply

```
cp /etc/samba/smb.conf.bak.01-OCT-06-0953pm /etc/samba/smb.conf
```

My general rule of thumb is if I have to type sudo to edit a file I make a backup of it using "cp" in case it makes something not work the way its supposed to.

For documents and photos; tar should work rather well for you.

---

### Post by SirShaggy on 2006-10-01
See, tagra123 had the perfect answer (IMO). I even learned a few cool things! I think accidently backing up too much may be better than not enough, however, like tagra123 said, new packages and updates do break things too. The copy idea is a great one. Makes you able to fix your system upon a moments notice! 20 moments if it's as fast as mine:-D 
SirShaggy

---

### Post by tagra123 on 2006-10-01
> **SirShaggy said:**
> See, tagra123 had the perfect answer (IMO). I even learned a few cool things! I think accidently backing up too much may be better than not enough, however, like tagra123 said, new packages and updates do break things too. The copy idea is a great one. Makes you able to fix your system upon a moments notice! 20 moments if it's as fast as mine:-D 
SirShaggy

I like manually using partimage for my "get it the way it was before" backups. By using this in conjunction with my automatic backups script I feel fairly safe I can always keep my computer backups up to date.

The monthly partimage backup consists of my home partition and root partition, basically everything that doesnt change that much. The backup scripts are used to keep Mail backed up 4 times per day + at night, programming files (on another drive) and documents every hour the entire home folder 1 time per day. 

So to restore I restore the root.

Sometimes the home may need restored too -- if so use partimage from the monthly backup, then copy the daily home folder backup files to my home directory, copy the last hours backups to their respective folders.

The file on the other drives shouldn't be touched. Kaboom restored most files within 1 hour of when I had the problem. Mail is backed up every 4 hours and I dont backup the WebBrowser directory. If I had more haddrive space I would though. Actually I would backup the entire home directory once per hour if Ihad enough space. Maybe for Christmas:)

---

