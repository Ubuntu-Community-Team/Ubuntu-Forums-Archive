---
title: "Backup Advice"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2006-11-09
I would like some advice on backup software.

What I would like to be able to do is backup to a seperate partition on my hard drive [at the moment FAT32] with the ability after the initial backup to just add changes.
I would also like to be able to make complete backups to an external [USB] hard drive [at the moment NTFS].
Changing file systems if necessary is not a problem.

I have a copy of Norton Ghost 10 which I use to backup Windows, it can be used with Linux but when I tried it I was unable to recover files, in any event the only way I could see the files was either to boot into Windows or the CD, neither being very satisfactory.
Like my Ubuntu Partition the [FAT32] partition I want to use for the backup does not show up in Windows.

Does anyone use a program that they would recommend to fit my requirements?

---

### Post by xyz on 2006-11-09
Many ways to do backups! How about this one:
[How To Backup A Ubuntu System with hourly, daily, and weekly backups.]("http://www.ubuntuforums.org/showthread.php?t=240326")

---

### Post by pilgrim-online on 2006-11-09
Hi xyz,

Not sure that fits the bill.
I should have mentioned that I do all my backing up manually as the PC is not always on.

---

### Post by jeffathehutt on 2006-11-09
Check out rdiff-backup.  It is very easy to use, and it only saves the changes like you wanted.

---

### Post by xyz on 2006-11-09
**jeffathehutt's link:**
[Rdiff-backup]("http://packages.ubuntulinux.org/dapper/utils/rdiff-backup")

I use this for a complete backup + excluding whatever I want (f.inst. Win partition)
Originally posted by **Heliode**
```
sudo su
cd /
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
And to restore:
```
 tar xvpfz backup.tgz -C /
```
Then "mkdir" whatever_you_excluded.

Also using a Live-CD and Partimage:
Here: [Psychocats]("http://www.psychocats.net/ubuntu/partimage")

> It comes in handy for two situations:

    * Creating a simple backup of your installation in case you're planning to make major changes to it. That way, in case the upgrade or other major change causes problems, you can easily restore your partition to exactly the way it was before.
    * Using the same Ubuntu configuration on several of computers that have the exact same hardware.
I hope you'll find something helpful here!
Good luck!

---

### Post by pilgrim-online on 2006-11-09
Your replies have given me a lot to think about, Rdiff-backup looks more complicated to set up and I can already see a number of questions if I decide to use it.

Partimage seems a lot more straight forward, but in either event I need to do a lot more reading.

One question I have for now is that my normal practise, as I said, is to create incremental backups, as needed, to my internal hard drive, and complete backups, usually once a month, to my external hard drive. From what I have read so far it seems that I would need both programs, Rdiff-backup internally, and Partimage externally. Does that make sense?

A second question regarding Partimage, if I want to make a second backup to the same location is that possible without overwriting the first backup, and would both be available for recovery?

Thank you both for your help.

---

### Post by xyz on 2006-11-09
> A second question regarding Partimage, if I want to make a second backup to the same location is that possible without overwriting the first backup, and would both be available for recovery?
Give your 2nd backup a slightly different name.
I've never used rdiff!
Sorry but I have little time right now -gotta go- but I'll check on you tomorrow. Let us know how it goes as you read on the subject.

---

### Post by Drakkor on 2006-11-09
This is just me,maybe others,but I use Acronis True Image in Windows to make an exact image of my whole Ubuntu drive and store it on another partition.
I have restored it many times without any errors whatsoever. just another thing to think about........ :p 
[http://www.acronis.com/homecomputing/products/trueimage/features.html](http://www.acronis.com/homecomputing/products/trueimage/features.html)

---

### Post by pilgrim-online on 2006-11-10
Drakkor,

Thanks for the reply, I actually downloaded a free copy of True Image 7 recently [full version complete with registration key] but as I already have Norton Ghost 10 I have not found a need for it. [I just liked the idea that it was free.]


I have decided to start by trying to set up rdiff-backup with /dev/hda4 as the target. [Now formatted as ext3 and labelled Ubuntu Backup.]
According to Synaptic the latest version of rdiff-backup is already installed.
Size and speed are not a problem so I want to back-up as much as is possible, only excluding things that need to be excluded and things like temporary files.

I understand that I need to create a script and I could use some advice on what to actually put in it.
EXCLUSIONS: I am not sure what directories I want to exclude as I am not sure where temporary files are stored. The only directory it seems I need to exclude is /proc and I would appreciate it if someone could tell me why this is so, and what it actually is?
SOURCE DIRECTORY: Is this something I need to create? Where and how?
DESTINATION DIRECTORY: Same questions as above.

It appears that you can set up a command to delete older files, I normally keep backups for 3 months. Again, I could use some advise on what to actually enter.

One other thing for now, is it possible to preview backups before restoration?

Sorry there are so many questions but the nearest I got to programming in Windows was editing two registry keys.
Until a year ago I had never owned, and hardly ever used, a computer.

Before posting this I have spent several hours reading up on rdiff-backup and I still come up with the same questions.

---

