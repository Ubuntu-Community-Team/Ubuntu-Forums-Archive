---
title: "How to make a script?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ABX on 2007-10-10
I'd like to make some scripts for my Gnome desktop.

In windows all I need to do is to make a script.cmd or .bat file and I can run it from the desktop with a double click.

How should I name the file in gnome to make it run with a double click?

---

### Post by ronald.higgins on 2007-10-10
It's not like windows where you need a specific extension ie .bat / .exe.
Under Nix name the file whatever you want but you need to give it execute permissions.
So once you're done writing your script give it execute permissions ie. chmod +x filename .

---

### Post by finferflu on 2007-10-10
I suggest you to give a look at [LinuxCommand.org]("http://www.linuxcommand.org/"), it's one of the best guides I've seen ;)

---

### Post by ABX on 2007-10-10
Thanks.

---

### Post by dwhitney67 on 2007-10-10
You've asked a broad question, but to get you started, you need to create a "launcher" on your desktop by right-clicking (on the desktop), and then selecting **Create Launcher...**

From there you fill in the blanks and select whatever icon you want to represent the launcher. For the command, it is best to type in the full-path of the command you want to run.  But this is where it gets tricky.  Have you decided what you want to run?

If you want to build your own script, which language will you write it in (sh, bash, perl, etc.)?  Will this script require I/O?  If so, you will need to specify the Launcher Type as "Application in Terminal".

Here's a simple script that you would need to launch as an "Application in Terminal":

```
#!/bin/sh

echo Hello World
echo
echo -n Press return to continue...
read ans
```

In the Command section of the Launcher setup, the following would be specified:
[FONT="Courier New"]sh /home/user/myScript.sh[/FONT]

Or alternatively, if the script has execute permissions:
[FONT="Courier New"]/home/user/myScript.sh[/FONT]

Anyhow, decide specifically what you want to do, and if you have further questions, then ask them.

---

### Post by ABX on 2007-10-10
Perfect, I have a lot of experience in coding in Perl. I have just discovered Linux 2-3 months ago, so I need few basics to start. :)


I need to make some shortcut for programs I use with wine so I won't have to type the whole thing over and over again, even if Linux have a fantastic shell memory for previous commands.

---

### Post by ABX on 2007-10-10
> **dwhitney67 said:**
> You've asked a broad question, but to get you started, you need to create a "launcher" on your desktop by right-clicking (on the desktop), and then selecting **Create Launcher...**

From there you fill in the blanks and select whatever icon you want to represent the launcher. For the command, it is best to type in the full-path of the command you want to run.  But this is where it gets tricky.  Have you decided what you want to run?


This is what I was searching for. Easy yet powerful.

---

### Post by spliner on 2008-03-19
I'd like to make a couple of simple backup scripts on the desktop.  I'd also like to have them scheduled to run at a certain time as well.

For instance, the command:

tar -cvzf /media/disk-2/backup.tgz --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/media/disk-2 /

... is the command I use to backup my system to my removable hard drive labeled disk-2.  If I create a launcher on the gnome desktop and include gksudo in front of that command nothing seems to happen. What did I miss?  

Once I get that working, how then do I schedule that to run at midnight every night? I want both the launcher and the schedule because I always back the system up before applying major udpates.

-Spliner

---

### Post by glennric on 2008-03-19
First create a script containing that command, and make the file executable.  Then type
```
sudo crontab -e
```
go to the bottom of the file and type "o" to open a new line for editing, and enter
```
00 00 * * * /path/to/scipt-file
```
Type Shift-ZZ to exit the editor. Then your script will run at midnight.

---

### Post by dwhitney67 on 2008-03-19
> **spliner said:**
> I'd like to make a couple of simple backup scripts on the desktop.  I'd also like to have them scheduled to run at a certain time as well.

For instance, the command:

tar -cvzf /media/disk-2/backup.tgz --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/media/disk-2 /

... is the command I use to backup my system to my removable hard drive labeled disk-2.  If I create a launcher on the gnome desktop and include gksudo in front of that command nothing seems to happen. What did I miss?  

Once I get that working, how then do I schedule that to run at midnight every night? I want both the launcher and the schedule because I always back the system up before applying major udpates.

-Spliner
I think backing up the "entire" system is overkill, especially on a daily basis.  You probably should consider only backing up the areas where changes are occurring.  A system can always be restored from the repository, however user-added stuff cannot.  Thus I would focus on that area only.

If you still insist on backing up your system, I would recommend that you skip (that is, exclude) the /dev and /var directories as well.

If you add your tar command (which btw, is fine) to a script file, then follow glennric's advice, you will not need to precede your command with "sudo".

A sample script file (let's call it backup.sh):

```
#!/bin/sh

# make sure 'disk-2' is mounted in /media
if [ -x /media/disk-2 ]
then
    tar czf /media/disk-2/backup.tgz --exclude=/dev --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/var --exclude=/media/disk-2 /
fi
```

Then make the script executable:

```
chmod 744 backup.sh
```

---

### Post by spliner on 2008-03-19
> **dwhitney67 said:**
> I think backing up the "entire" system is overkill, especially on a daily basis.  You probably should consider only backing up the areas where changes are occurring.  A system can always be restored from the repository, however user-added stuff cannot.  Thus I would focus on that area only.

If you still insist on backing up your system, I would recommend that you skip (that is, exclude) the /dev and /var directories as well.

If you add your tar command (which btw, is fine) to a script file, then follow glennric's advice, you will not need to precede your command with "sudo".

A sample script file (let's call it backup.sh):

```
#!/bin/sh

# make sure 'disk-2' is mounted in /media
if [ -x /media/disk-2 ]
then
    tar czf /media/disk-2/backup.tgz --exclude=/dev --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/var --exclude=/media/disk-2 /
fi
```

Then make the script executable:

```
chmod 744 backup.sh
```

Actually, that brings me to a totally off the subject question...

Would anyone know why a removable disk would be mounted 3 times as disk, disk-1, and disk-2?  It's a RD1000 removable hard drive, and for some reason it's mounted 3 times.  When I originally set up the drive I formatted it as ex3 filesystem and named it disk (because that was its default name).  I'm a bit worried that it'll end up mounted as disk-3 and the backup script will fail.

I had orignally used the "Simple backup config" that I installed from the repositories.  It backed up the system once, then creates incremental backups daily.  It's likely that would have worked, but I am leaning toward using tar instead (which is why I am working with tar scripts).  It was originally set up to backup nightly to disk-1, then last week it stopped working and I noticed the disk was then mounted as disk-2.  Upon further inspection I noticed it was still mounted as disk-1 but had totally different files (on the same drive).  So the simple backup was running still and adding files to disk-1 (I looked and they were there).

Anyone have a clue why this is happening?  Is there a default number of files per disk or something that is causing it to re-mount as a new volume?  It's a 300GB cartridge, so it has massive amounts of space available.

Ok, back to the subject at hand...

Once I create the backup.sh script and chmod it to be executable, I can run it easily from a terminal, but when I make a launcher it does not run.  I then added gksudo to the command in the launcher and it seems to run, but I cannot see what its doing.. IE:  I can tell it's running, but is there some way to make it echo the directories its backing up in a shell while it's running (kind of like windows does when running a batch file)?

By the way.. thanks all for the suggestions.. I'm getting much closer to getting this done!

-Spliner

---

### Post by dwhitney67 on 2008-03-19
Ooops... I should've tested with a -d, not the -x, when checking for the existence of the directory.

Btw, it would seem that your "disk" is being mounted over and over again.  Do you properly unmount it before attempting to remount it again?

---

### Post by spliner on 2008-03-19
> **dwhitney67 said:**
> Ooops... I should've tested with a -d, not the -x, when checking for the existence of the directory.

Btw, it would seem that your "disk" is being mounted over and over again.  Do you properly unmount it before attempting to remount it again?

Changed it to -d instead of -x in the script.

Also.. I use Gnome to unmount it.. right click on the drive and select "Unmount Volume".  I can then eject the cartridge with the button on the front of the bay.

Here's the wierd thing, just for grins, I changed the cartridge with a brand new one... loaded up GParted, created/formated the partition as ex3 and mounted it.  It mounted as disk-2.  So.. I started poking around.. disk and disk-1 are still in /media.  So, I look in disk, and there's nothing there, but properties on that folder show the total amount of space in my main drive on which the filesystem resides... so I look at disk-1, and it's the same, same file size as my main drive.  So both of those are different mounts or volumes of the main drive?  I'm a bit confused here.  /media/disk has nothing in it, however /media/disk-1 shows those backup files I was talking about earlier.  They only show up as folders in /media though.  Can I just delete them?

It's really starting to look like either on a reboot of the system, or ejecting the cartridge somehow didn't un-mount them in the past and it left a directory named disk in the /media folder.  Then when it happened again, it left disk-1 in the /media folder.  Now they are just folders.  I still don't have a clue why they are there, or why they are still there.  Think I could just delete them?  But if I do that, the cartridge might mount as "disk" and my script would fail lol.

I'm positive my own newbie antics caused this somewhere along the line, and everything is functional, but I just wondered why those were still there, and why they were created in the first place.  The external drive cartridges are nothing more than SATA 2.5" drives.. they simply pop into the bay and are in a cartridge.  Maybe Ubuntu doesn't like the Dell RD1000 bay, or a different driver needs to be installed.

Anyway, thanks for the script!  I have it scheduled through crontab as posted here.  I was also able to finally get my Launchers on the desktop to run by putting "gksudo" in front of the command.  I am prompted for the root pass and the script runs just fine.  It doesn't really tell me it's running but I can see the drives flashing and watch the file being created on the drive.  It'd be nice if I could see what it is backing up (verbose echo to a shell window like windows) but it works so I won't complain.

-Spliner

---

### Post by dwhitney67 on 2008-03-19
Spliner -

You can verify what is mounted on your system using this command:

```
$ mount
```

If something is mounted in /media, you will see it.  To unmount it, run:

```
$ sudo unmount /media/somedir
```

If there is a directory in /media that is not mounted, then by all means, feel free to delete it if you do not want it anymore.  The command for this is:

```
$ sudo rm -rf /media/somedir
```

On my system (Ubuntu 7.10), I have the following in /media, which I do not think you should delete:
```
lrwxrwxrwx 1 root root    6 2008-02-18 13:16 cdrom -> cdrom0/
drwxr-xr-x 2 root root 4096 2008-02-18 13:16 cdrom0/
```

As far as running the script from a desktop icon, and seeing the output, modify your script as follows:
```
#!/bin/sh

if [ -d /media/disk ]
then
    xterm -e 'tar czvf /media/disk/backup.tgz --exclude=/dev --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/var --exclude=/media/disk /; echo "Press <enter> to continue..."; read ans'
    exit 0
else
    xterm -e 'echo "Directory /media/disk does NOT exist!"; echo "Press <enter> to continue..."; read ans'
    exit 1
fi
```

---

### Post by spliner on 2008-03-26
Very nice!  I appreciate the help!

Now I have another quick question....

My backups are running each night as anticipated, however I have decided to keep a week at a time on each removable hard drive.  So each morning, I have to go to /media/disk-2 and rename my backup file to something like backup_3-26-08.tgz.  Is there a way to automatically append the date to the filename using the tar command?  The backups would then be completely automatic, and I could simply swap out the drives once a week.  I can of course see the file creation date, so it wouldn't have to be the date that is appended to the filename, just a number each day would do.  As it stands right now, my script below overwrites the backup if I don't remember to rename the file each morning:

#!/bin/sh

# make sure 'disk-2' is mounted in /media
if [ -d /media/disk-2 ]
then
    xterm -e 'tar czvf /media/disk-2/LDAPhome_bak.tgz /ldaphome; echo "Press <enter> to continue..."; read ans'
    exit 0
else
    xterm -e 'echo "Directory /media/disk-2 does NOT exist!"; echo "Press <enter> to continue..."; read ans'
    exit 1
fi

Also, would you happen to have a link to the scripting language you are using?  I'd love to learn more.  For instance, ending an "if" statement with "fi" is new to me, so is "read ans".  I am old school, and have written a few thousand DOS scripts in my time, so I learn quickly, but could use a manual if there is one available.

Thanks again dwhitney67!

-Spliner

---

### Post by Dr Small on 2008-03-26
> **spliner said:**
> Very nice!  I appreciate the help!

Now I have another quick question....

My backups are running each night as anticipated, however I have decided to keep a week at a time on each removable hard drive.  So each morning, I have to go to /media/disk-2 and rename my backup file to something like backup_3-26-08.tgz.  Is there a way to automatically append the date to the filename using the tar command?  The backups would then be completely automatic, and I could simply swap out the drives once a week.  I can of course see the file creation date, so it wouldn't have to be the date that is appended to the filename, just a number each day would do.  As it stands right now, my script below overwrites the backup if I don't remember to rename the file each morning:

#!/bin/sh

# make sure 'disk-2' is mounted in /media
if [ -d /media/disk-2 ]
then
    xterm -e 'tar czvf /media/disk-2/LDAPhome_bak.tgz /ldaphome; echo "Press <enter> to continue..."; read ans'
    exit 0
else
    xterm -e 'echo "Directory /media/disk-2 does NOT exist!"; echo "Press <enter> to continue..."; read ans'
    exit 1
fi

Also, would you happen to have a link to the scripting language you are using?  I'd love to learn more.  For instance, ending an "if" statement with "fi" is new to me, so is "read ans".  I am old school, and have written a few thousand DOS scripts in my time, so I learn quickly, but could use a manual if there is one available.

Thanks again dwhitney67!

-Spliner
```
man bash
```

It has LOADS of information on Bash scripting.

---

### Post by spliner on 2008-03-26
> **Dr Small said:**
> ```
man bash
```

It has LOADS of information on Bash scripting.

Holy cow!  You're not kidding!  Thanks!

I also found this site:  [http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

Chapter 2 seems to be a big help as well.

-Spliner

---

### Post by spliner on 2008-03-26
Ok, I've made two scripts.. test1.sh and test2.sh.

Test1.sh:
> 
#!/bin/sh

#Test script to create a filename with the date

#Set the date variable
today=$(date +"%m-%d-%Y")
#Set the new FILENAME variable
FILENAME="backup_$today.tgz"
#Print the new FILENAME
echo $FILENAME


The output is:  "backup_3-26-2008.tgz"

Test2.sh:
> 
#!/bin/sh

# make sure 'disk-2' is mounted in /media
if [ -d /media/disk-2 ]
then
    xterm -e 'tar czvf /media/disk-2/tempfile.tgz /ldaphome; echo "Press <enter> to continue..."; read ans'
    exit 0
else
    xterm -e 'echo "Directory /media/disk-2 does NOT exist!"; echo "Press <enter> to continue..."; read ans'
    exit 1
fi


Both scripts work, but how would I combine those into a single script so that tar writes the file with the date appended to the filename?  I've tried several variations like:

> 
#!/bin/sh

# This is a script for a DATE Variable in the filename

# Set the veraible for the date
today=$(date +"%m-%d-%Y")
# Set the FILENAME variable
FILENAME="backup_$today.tgz"

# make sure 'disk-2' is mounted in /media
if [ -d /media/disk-2 ]
then
    xterm -e 'tar czvf /media/disk-2/$FILENAME /ldaphome; echo "Press <enter> to continue..."; read ans'
    exit 0
else
    xterm -e 'echo "Directory /media/disk-2 does NOT exist!"; echo "Press <enter> to continue..."; read ans'
    exit 1
fi


But the script doesn't really run at all.

I then tried replacing $filename in the tar command with "tempflie.tgz" and adding a line after the first semicolon in that command like "mv /media/disk-2/tempflie.tgz /media/disk-2/$FILENAME".

Anyone know where I'm going wrong?  

-Spliner

---

### Post by spliner on 2008-03-26
[SOLVED]

Well.. it was much easier than I originally thought... adding `date +%m-%d-%Y` (note those are back-ticks that are located under the tilda ~ key) appends the date in the MM-DD-YYYY format at the end of the filename.

The command:

tar cvzf "/media/disk-2/backup_`date +%m-%d-%Y`" --exclude=/proc --exclude=/lost+found --exclude=/media/disk-2 --exclude=/mnt --exclude=/sys /

Seems to work just fine.  It makes  a file with the date in the filename.

So.. create a script with your favorite text editor that says (some recommend excluding /var and /dev directories as well.. up to you):

> 
#!/bin/sh

# Full Backup Script - Daily at midnight

# Check to see that the device /media/disk-2 is present

if [ -d /media/disk-2 ]
    then
        tar cvzf "/media/disk-2/backup_`date +%m-%d-%Y`" --exclude=/proc --exclude=/lost+found --exclude=/media/disk-2 --exclude=/mnt --exclude=/sys /
fi


Then make it executable:

chmod +x filename.sh

...and schedule it with chron as stated in this thread.

Seems to be working for me each night!

Thanks to all who helped!

PS:  I'd still love to know how to do it with variables like I was trying earlier, but it may not be do-able that way at all.  At least I could not get it to work.

-Spliner

---

### Post by spliner on 2008-04-03
I ran into a problem with my scripts I had created...

Both of my scripts, backup_ful.sh and ldaphome_bak.sh were running just fine each night (I check them every morning) until a few days ago.  Now, the archives the scripts create are only a few hundred K in size, and cannot be opened (unexpected EOF errors).  If I manually go to a terminal that morning, and 'sudo sh /backup_full.sh' and 'sudo sh /ldaphome_bak.sh' the backups run just fine and are the correct size.  I can also verify the files in the archive are complete.

Is there any way for me to find out what is going on at midnight and 1am for those two scripts running through crontab?  They are simple tar scripts for backup.  I went into syslog.conf and uncommented out the cron log and restarted.. so tomorrow i should get cron logs.  Think that'll be sufficient to find my problem, or will I need the tar command in the scripts creating a log file?

Thanks,

-Spliner

---

### Post by dwhitney67 on 2008-04-03
It is hard to surmise what the problem could be when the scripts are ran using cron, but perhaps one thing you might consider doing is spacing the start times apart by more than an hour.  Perhaps the first script is not finished when the second starts up?

---

### Post by spliner on 2008-04-03
I'll give that a shot.  I don't think that's the problem because the files created are less than a megabyte in size now.  It shouldn't take it long to do those.  If they were several gig but incomplete I would think that could be the case.

I've been researching a way to log the tar command to a file so I can take a look, but havn't found anything yet.  Wierd thing is that it was working just fine, then one day the file sizes were way small and they were incomplete.

-Spliner

---

### Post by spliner on 2008-04-04
Spacing out the scripts didn't seem to help.  It may be something with tar, but the scripts run fine when I manually run them.

Anyone else have an idea what might be going on?  Anyone know how to change my tar scripts so they log to a file?

-Spliner

---

### Post by spliner on 2008-04-04
I may have found the answer here:  [http://ubuntuforums.org/showthread.php?t=289158](http://ubuntuforums.org/showthread.php?t=289158)

Will try putting /bin/tar in the script instead of just tar.. also added > /var/log/cron_tar.log to output it to a log file.

Will see what happens.

-Spliner

---

