---
title: "Backup from windows shared folders"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-01-13
Hello, please see my config oin my signature. I want to backup shared folders of Win98 and WinXP machines to my 80Gb hdd automatically. how can I do this. i just want to sync so that I have a backup copy.
All the Win89 and WinXP machines are shared through passwords and I can access them from Samba. I want to use a software similar to SyncBack with scheduled backups.
I also want to know what should I backup on my Ubuntu installation. I have read that it is important to backup the /home partition. How do I achieve this?

---

### Post by mattismyname on 2008-01-13
Jesrani

This is more of a windows question, but if it were me, I would use rsync to copy files from the windows machine to the linux machine.  There is a Windows GUI frontend for rsync called deltacopy (google it).  You would need to run an rsync or ssh server on your Linux machine also.

Also, you would need a way to schedule the backup at a certain time each day on the windows machines.  I think windows XP provides a service called "scheduled tasks" in the control panel.  Don't know if 98 has that though.

Regarding the Linux backups, yes, backing up /home would be most important.  But really, it depends where you store most of your important data.  Also, if it is important to you to have your OS install itself backed up, you would want to back up all of /usr /bin /sbin /var, etc.

---

### Post by jesrani on 2008-01-15
Thanks for the reply. Maybe I framed the question incorrectly. I have a number of XP / Win98 machines with folders shared through a password. I am able to access these from the Ubuntu machine. I want to put a software on the ubuntu machine that will do the backup on the 2nd HDD that I have installed in the Ubuntu machine. I dont want to put softwares on many machines.
At present I am also doing a similar thing from an XP machine using SyncBack. So I want to do the same thing from Ubuntu machine so that I will have 2 sets of backups at separate places.
I installed the software "Simple Backup" for backing up my Ubuntu machine and by default it is backing up the /var/, /home/, /usr/local/, /etc/ folders. I have also opened a separate thread about imaging the installation so I think I will have my Ubuntu installation also backed up.

---

### Post by mattismyname on 2008-01-15
Aha...then rsync is exactly what you want.  You won't even need to install a server.

1) Make sure rsync is installed on the Ubuntu box: "sudo apt-get install rsync"
2) Figure out the command necessary to back up the windows clients.  It will be something like:  rsync -avz /media/windows_machine/path/to/folder/you/want/to/backup /media/destination/for/backup/files
3) Automate it to run daily by adding an entry to your crontab: crontab -e.  You can google for the format of the crontab file.

Let me know how it goes...

---

### Post by hyper_ch on 2008-01-15
syntax of crons is very simple. I prefer not to edit the crontab directly but going through a cron.txt file.

(1) create/edit the backup script file
```

edit ~/rsync_backup.sh

```

(2) add the rsync code
```

#!/bin/bash
BACKUPFROM=/media/windows_machine/path/to/folder
BACKUPTO=/path/to/backup/location
rsync -avzp $BACKUPFROM $BACKUPTO

```

(3) Save and exit file
Press ctrl-x and you'll be asked if you want to save the file and what filename it shall have.

(4) make it executable
```

chmod 0755 ~/rsync_backup.sh

```

(5) create/edit the cron.txt file
```

nano ~/cron.txt

```

(6) add crons
```

0 9,21 * * * /home/USER/rsync_backup.sh

```
The syntax is:
Minute | Hour | Day of Month | Month | Weekday | Command
a * means it will run at any given value.
The above code means it will run at the full hours of 9 and 21h --> 09:00 and 21:00 every day.
45 5 * * * --> that would mean it would run every day at 05:45h

(7) exit and save the file
Press  ctrl-x

(8) add the cron.txt to the crontab
```

crontab cron.txt

```

---

### Post by jesrani on 2008-01-15
I have installed Flyback which uses rsync. But I am unable to see the windows shares anywhere. I can see them when I go to "Places --> Network" and then use the username and password. But how to add this to the include list.

---

### Post by mattismyname on 2008-01-15
I think the gnome file manager somehow talks directly to the windows share without actually mounting it in your local filesystem.

To mount it so that it is visible in the standard filesystem, you can follow the guide on this wiki:  [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by mattismyname on 2008-01-15
Also, here's a related thread: [http://ubuntuforums.org/showthread.php?t=12306](http://ubuntuforums.org/showthread.php?t=12306)

---

### Post by mattismyname on 2008-01-15
Looks like rsnapshot ([http://rsnapshot.org/](http://rsnapshot.org/)) is also a viable alternative you might want to check out.

---

### Post by jesrani on 2008-01-15
Thanks for the replies. But it means I have to mount all the shares first, seems something like "Map Network Drive" in XP. When I am using Cobian Backup on my XP machine for backing up other machines I do a similar thing. Is there any backup software like SyncBack which can directly allow reading windows shared folders and put a password in the software to access it. Is something like this possible in Linux. Can I read windows shared folders through wine?

---

### Post by jesrani on 2008-01-20
hello, being a complete newbie to Linux, the explaination by hyper_ch was a bit difficult for me.
So I started searching for backup programs with GUI.
Then I ran into mounting troubles. Had to take out time do do some reading. I have both 98 and XP folders shared through password on the network. After lot of difficulties I found how to mount these. I have to add wins to the hosts: line in etc/nsswitch file. Then I have to edit /etc/fstab and enter the path with username and password. The machine is used by me only so I dont need to create special file for this. I was using the cifs systax and it was just giving errors. Turned out that it is not very compatible with Win98. As soon as I replaced it with smbfs, I could mount Win98 folders.
So I though all my problems were over. I created a folder called network and then sub-folders in this for each machine I had to backup. Each machine's shared folder (1 per machine) was to be mounted in these sub-folders. I downloaded SyncBack to run through Wine for the backups. But then I discovered that some drives which were not present all the time. In this scenario the folder under network would be empty. In this case it would make my backup folder also empty due to the synchronization. So I am stuck again. I can use the option "do not delete file from destination" but dont want to do this. Also, SyncBack cannot be scheduled.
Reading hyper_ch's suggestions, I am now tempted to try our rsync through CLI.
Another problem is that the computer takes long time to boot now as there are 10 drives to mount. Is there any solution to this? Is it possible that if the network drive is not mounted, its folder under /network also not be visible.
It seems XP is easier in this or maybe I am wrong. It is taking me time to understand the syntax and it is frustrating.
Why cant different drives be seen different and why can't the programs have access to network. Why the need to mount as local drives when they are not local.
Please advice.

---

### Post by jesrani on 2008-01-21
I was trying the rsync commands. But it seems that I need to first mount the network drives. In this case I still have the problem of slow boot and empty folder for a drive that may not be present. Any suggestions on this.
In XP one can just give the network path in programs directly, can this be done in Ubuntu.

---

### Post by jesrani on 2008-01-27
hello, i have solved the mounting problems. now i need to try rsync. what is the best location to crete rsync_backup.sh and cron.txt files. can i give any other names? can i put it in my /home folder? what is the code to do the backup at 12.30pm and 4.30pm everyday.
i want to backup 2 different mounted folders to 2 different locations. how do i put multiple locations in the rsync_backup.sh file?

---

