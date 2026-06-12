---
title: "Partitions"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2007-11-26
I want to install 7.10 on a Vista laptop but I don't know how to use the manual partitioner and that cool slider went away (why?). Any help?

DB

---

### Post by mikewhatever on 2007-11-26
You can't use Ubuntu partitioner to resize a Vista partition. Instead, use the Vista included tool.
[http://www.google.co.il/search?q=ubuntu+vista+dual+boot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+vista+dual+boot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by erfahren on 2007-11-26
How is you drive currently setup? The reason I ask is because many notebooks are already setup with a Windows "D" (data) drive. If you have one and can move any data off there then you can make partitions out of that using the manual partitioner without much trouble.

---

### Post by purebuilt on 2007-11-26
Yes, it has the D drive too (it is a Compaq). How can I make this simple. I really would like to use Ubuntu, but I don't know it yet. I've installed it with the slide on and ME and XP machine. Anyone have step by step instructions.?

DB

---

### Post by erfahren on 2007-11-26
ok, without going too much into partitoning rules I'll tell you this: (for more info on partitioning see: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning) )

You very most likely have a recovery partition at the beginning of your disk that will be a primary

you have Windows C - that will be primary

you have the "D" - that also may be primary 

you can use the manual partioner to resize D and then out of all the free space you'd first create a extended partiton and then divide it up into a partition for Gutsy (root) making it logical, leaving about 1GB for swap 

for example
if you had 20GB freed up for Gutsy first create an extended partition out of all of it, then divide it up -
create a 19GB partition for Gutsy itself, then create a 1GB partiton for swap
(both would be logical partitions)

see: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
[http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

---

### Post by erfahren on 2007-11-26
Oh, I forgot...

when you resize D you can format it to NTFS (or FAT32) again. You can use it for data storage and to copy files back and forth between the two OSs.

My D was 40GB and I resized it down to 20GB, using the rest for Ubuntu.

then when I went through the partitioning I reformatted it as well.

-- actually I think I used Vista's Disk Manager(part of the Administrative Tools) to resize and format mine though.

---

### Post by purebuilt on 2007-11-26
Thank you that helped. Vista has its own partitioner and it worked fine. Now I've got other bugs to hunt down.

1. The Update manager doesn't update (Yes I'm connected to the internet).
2. The ADD Programs manager won't let me add a program. It says it must update but doesn't
3. My wireless card won't enable the firmware like it says it can.
4. At least the ether card works.

DB

---

### Post by erfahren on 2007-11-26
the first two problems are related. When you're not connected to the internet during installation Gutsy will comment out the repositories in /etc/apt/sources.list it can't connect to 

that seems to be a new thing and it's confused others (including me).

you can do this the quick way

backup you current sources.list
and open it up and replace everything below the CD-ROM line with this:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted #Added by software-properties
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties

## START -- MANUALLY ADDED
##

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

``` 
save and add the key for the Mediubuntu repository, in the terminal do:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

that should help get you started. (I don't really know a heck of a lot about wireless personally)

---

