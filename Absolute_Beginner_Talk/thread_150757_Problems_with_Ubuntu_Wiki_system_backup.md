---
title: "Problems with Ubuntu Wiki system backup"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-03-26
Hi:

I have Breezy installed and have used the Ubuntu backup Wiki located here

[https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29](https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29)

which worked fine until I wanted to change the directory where the backup file was created and wanted to add my own "exclude" locations.

I changed directories (CD /) until I was in the location I wanted to be, a folder called 

"musicbackup1" located at /

This is the command I used:

<code>
user@ubuntu1:~$ sudo tar -cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/data1a --exclude=/musicbackup1 --exclude=/media --exclude=/mnt --exclude=/sys /
</code>

Files flew by and I thought all was going well until I noticed nothing was being written to the

/musicbackup

folder and instead everything was being written to

/

which is what I used previously but I wanted to change the location - which, as I said, I thought I could do by CD'ing to it and then running the backup command.

Then I noticed the system was backing up the locations I had marked to exclude, specifically

/data1a

and

/media

/media is the location of the folder/mount point for my external firewire hard drive. I thought marking to exclude /media would keep the computer from backup up the data on the firewire drive - but it didn't. Perhaps I need to exclude the firewire drive with something like

--exclude=/dev/sda1

???

The

/data1a

backup was my fault - the folder is actually called

/data1A

so my mistake.

What it comes down to is I need to know how to write the backup file to a location other than

/

and how to exclude the firewire drive.

I'm going to give it another try now but if anyone can answer these questions I'd appreciate it immensely.

Thanks.

Edit: Ok, I already noticed that I must not have changed directories into /musicbackup1 which I did this time - but the backup file is still being written to /

Second edit: Ok, so I figured out the first command has to be /musicbackup1/backup.tgz 

and now files are being backed up to

/musicbackup1

I guess it helps to read the instructions more carefully.

Triple edit: Just for the record, everything worked perfectly. I split the main backup file so that the resulting files were <2GB and then burned them to a DVD.

---

