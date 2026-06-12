---
title: "Help with Shell Script + Rsync"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by kiplingw on 2008-03-11
I seem to be having two problems with a light shell script for performing backups to an external disk. If I run the script myself, I get...

```

Missing trailing-' in remote-shell command.
rsync error: syntax or usage error (code 1) at main.c(348) [sender=2.6.9]

```

If I copy and paste the rsync command that is formed in the script and run it manually, bypassing the above error, I get...

```

1 file to consider

```

But there are many files to consider. Here is the script...

```

#!/bin/sh

# Path...
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

# Files and folders to skip...
EXCLUDES=$HOME/Scripts/Backup/exclude-files.txt

# Files and folders to include...
INCLUDES=$HOME/Scripts/Backup/include-files.txt

# Our hostname...
HOSTNAME=$(uname -n)

# User and host name of ssh server to backup to...
SERVER_USER=me
SERVER_HOST=myserver
SERVER_PATH=/media/disk/$HOSTNAME
SERVER_PORT=22000

# Rsync options...
OPTS="-avnz -e 'ssh -p $SERVER_PORT' --include-from=$INCLUDES --exclude-from=$EXCLUDES --progress --stats"

# Display greeter...
echo "Preparing to backup" $HOSTNAME "in 5 seconds with..."

# Echo command to run...
echo rsync $OPTS $SERVER_USER@$SERVER_HOST:$SERVER_PATH
sleep 5

# now the actual transfer
rsync $OPTS $SERVER_USER@$SERVER_HOST:$SERVER_PATH
 

```

Inside of exclude-files.txt:

```

/home/kip/Backups/ISO/*
/home/kip/Desktop/*.iso
/home/kip/Movies/*
/home/kip/VMware

```

And inside of include-files.txt:

```

/home/kip
/home/guest
/etc

```

Thanks.

Kip

---

### Post by PinkFloyd102489 on 2008-03-11
Dont know how much this will help but this is the backup script that I use.


```

#!/bin/bash

cd /media/120GB-Storage/

# Remove existing backup
rm Stuff.tar.bz2

# Creating backup tarball
tar cvjf Stuff.tar.bz2 Stuff/

# Variables needed for rsync
THEDATE=`date '+%Y%m%d-%s'`
LOGFILE=/home/brandon/rsync-$THEDATE.log

# Get confirmation, so we know it executes properly with the full backup
zenity --info --title "Backup" --text "Press Ok to start rsync backup"

# Crap that's going to be executed
rsync -t -p -o -g -v --progress --rsh="ssh -i /home/brandon/.ssh/backup" -l -z --log-file=$LOGFILE /media/120GB-Storage/Stuff.tar.bz2

```

The rsh bit is so that it doesnt prompt for a password and makes a direct connection.

---

### Post by mrsteveman1 on 2008-03-11
Aren't you missing the recursive option?

The script i use to backup TO Linux (from vista - itunes library), has to have the -r option passed to it or it doesn't do much :D

Some of this may not apply to the linux version:

```
rsync -v -r --progress --ignore-existing --delete-during /cygdrive/c/Users/steve/Music/iTunes steve@192.168.1.2::backup
```

Also, you should try running the rsync command by itself with the variables replaced with the true values, so that you get one single rsync line, then see if it works the way you want it to, THEN put the variables back, unless you already did that....

---

### Post by kiplingw on 2008-03-11
Thanks for the script, but archiving into a tarbal probably isn't very efficient when we are talking 20 GB of data and I may need access to the files quickly.

The -r switch for recursive operation is implied with -a.

Kip

---

### Post by mrsteveman1 on 2008-03-11
Didn't know about -a 

I would work through the script by simplifying it until it works the way you want it too, then slowly add each option back, because one of them is obviously causing a problem somewhere.

---

### Post by kiplingw on 2008-03-11
The problem is with the -e 'ssh -p $SERVER_PORT' parsing by bash. My syntax is just confusing it. Don't know what to do.

Kip

---

### Post by glennric on 2008-03-11
Why don't you just make the last line of the script
```
rsync -avnz -e "ssh -p $SERVER_PORT" --include-from=$INCLUDES --exclude-from=$EXCLUDES --progress --stats $SERVER_USER@$SERVER_HOST:$SERVER_PATH
```
and drop the OPTS variable.  Is there any need to seperate things that much?

---

### Post by glennric on 2008-03-11
Okay, here you go.  Make your OPTS variable the following
```
OPTS="-anvz -e ""ssh -p $SERVER_PORT"" --include-from=$INCLUDES --exclude-from=$EXCLUDES --progress --stats"
```
That worked for me.

---

### Post by kiplingw on 2008-03-11
Substituting the variables for the actual call kind of works. It gets rid of the parsing error, now it is just a problem with rsync, namely the second problem I mentioned. Using the previous substitution method with the double quotes gives me the initial problem still.

Kip

---

### Post by glennric on 2008-03-11
Ahh, I missed your initial problem.  I encountered and fixed those while testing your script.  I should have said something.  First you need to remove the -n option.  That will make rsync perform a dry-run and not actually do anything.  The other is you need to tell rsync where to copy from.  I assume that you are copying to $SERVER_USER@$SERVER_HOST:$SERVER_PATH.  So right before that you need to give rsync a path to copy from.

---

### Post by kiplingw on 2008-03-11
Yes, the dry run was deliberate. I wanted to make sure I knew what it was going to do before it did it.

As for paths, the --include/exclude-from files are suppose to specify the source, are they not?

Kip

---

### Post by glennric on 2008-03-11
Those tell rsync which files in the path to exclude and include.  It still needs a starting point to work from.

---

### Post by glennric on 2008-03-11
The way it works is first rsync uses the path you give it.  Then it excludes any files that match patterns in the --exclude-from file, then it includes and files that it may have excluded (by the --exclude-from option) if they match patterns in the --include-from file.
You can also use the --files-from=FILE to tell it which files to copy.

---

### Post by kiplingw on 2008-03-11
Thanks Glennric, but it is still getting confused on which files to copy.

```

#!/bin/sh

# Path...
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

# List of files / paths to backup...
FILES=$HOME/Scripts/Backup/files.list

# Files and folders to skip...
EXCLUDES=$HOME/Scripts/Backup/exclude-files.list

# Files and folders that would have been skipped, but special cases...
INCLUDES=$HOME/Scripts/Backup/exclude-exceptions.list

# Our hostname...
HOSTNAME=$(uname -n)

# User and host name of ssh server to backup to...
SERVER_USER=kip
SERVER_HOST=192.168.1.100
SERVER_PATH=/media/disk/$HOSTNAME
SERVER_PORT=22000

# Rsync options...
OPTS="-avnz -e ssh
      --itemize-changes
      --human-readable
      --files-from=$FILES 
      --include-from=$INCLUDES
      --exclude-from=$EXCLUDES 
      --progress 
      --stats"

# Display greeter...
echo "Preparing to backup" $HOSTNAME "in 5 seconds with..."

# Echo command to run...
echo rsync $OPTS / $SERVER_USER@$SERVER_HOST:$SERVER_PATH
sleep 5

# now the actual transfer
rsync $OPTS / $SERVER_USER@$SERVER_HOST:$SERVER_PATH
 

```

files.list
```

/home
/etc

```

exclude-files.list
```

/home/kip/Backups/ISO/*
/home/kip/Desktop/*.iso
/home/kip/Movies/*
/home/kip/VMware

```

exclude-exceptions.list empty.

Does that still not look right?

Kip

---

### Post by glennric on 2008-03-11
It looks right, but how is it getting confused?  Is it copying the wrong files, or not copying something it should be?

---

### Post by glennric on 2008-03-11
If you take the / out before $SERVER_USER@$SERVER_HOST:$SERVER_PATH does the command work or does it give an error?

---

### Post by kiplingw on 2008-03-11
I get prompted for my ssh passphrase, I enter it, and I see it consider only 2 files. Shouldn't it descend recursively finding everything specified in my files.list and removing what I had specified from that?

```

building file list ... 
2 files to consider
cd+++++++++ etc/
cd+++++++++ home/

Number of files: 2
Number of files transferred: 0
Total file size: 0 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 44
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 72
Total bytes received: 32

sent 72 bytes  received 32 bytes  29.71 bytes/sec
total size is 0  speedup is 0.00

```

Kip

---

### Post by kiplingw on 2008-03-11
If I take out the /, rsync bails out with a syntax error.

Kip

---

### Post by glennric on 2008-03-11
It seems that the --files-from option does not allow wildcards and you still have to give an absolute path to start from.

---

### Post by kiplingw on 2008-03-11
I think you are right. I modified the other two input files to take care of that and it appears to work. Thanks =)

Kip

---

### Post by glennric on 2008-03-11
Oh, by the way your files.list should contain
```
/home/
/etc/
```
Then rsync will descend recursively into those directories.

---

### Post by kiplingw on 2008-03-11
Thanks but I think I tried that and it did the same thing. Maybe just bad memory. I will wait till this rsync session is over and then try again.

Kip

---

### Post by glennric on 2008-03-11
That works for me in the tests I ran.

---

### Post by kiplingw on 2008-03-13
Thank you. It worked with --files-from now. A word to the wise, apparently one must explicitly specify -r, even though it is suppose to be implied with -a when using one of the --*-from switches (not sure which, but perhaps all of them).

Kip

---

### Post by CIEN on 2008-03-20
Thanks Kip and Glennric, I've run into the same difficulties and this thread has helped me alot. Kip would you mind showing what your final script looked like? I am writing a similar script in PHP yet I have never used rsync before, so I am quite curious to see how your actual rsync command looks like when you've included the from path and whether you added or removed some of the variables.

---

### Post by kiplingw on 2008-03-20
Sure thing. To backup offsite:

```

#!/bin/sh
## Kip's script for his laptop to backup offsite

# Path...
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

# Files and folders to backup...
FILES=files.list

# Files and folders to skip...
EXCLUDES=exclude-files.list

# Files and folders that would have been skipped, but special cases...
INCLUDES=exclude-exceptions.list

# Our hostname...
HOSTNAME=$(uname -n)

# Make sure we are being run as root...
if [ "$(id -u)" != "0" ]; then
   echo "You must run the script as root, since it needs to backup stuff system wide." 1>&2
   exit 1
fi

# Location to store backup...
REMOTE_HOST=my-backup-server
REMOTE_PORT=22
REMOTE_USER=me
REMOTE_PATH=/home/$REMOTE_USER/$HOSTNAME

# Rsync options...
OPTS="-avrz
      --compress-level=9
      --itemize-changes
      --delete
      --delete-excluded
      --human-readable
      --files-from=$FILES
      --include-from=$INCLUDES
      --exclude-from=$EXCLUDES 
      --progress 
      --stats"

# Display greeter...
echo "Preparing to backup" $HOSTNAME "in 5 seconds with the following command..."

# Echo command to run...
echo rsync -e \"ssh -p ${REMOTE_PORT}\" $OPTS / $REMOTE_USER@$REMOTE_HOST:$REMOTE_PATH
sleep 5

# now the actual transfer
rsync -e "ssh -p ${REMOTE_PORT}" $OPTS / $REMOTE_USER@$REMOTE_HOST:$REMOTE_PATH


```


And to backup to an external USB drive.
```

#!/bin/sh
## Kip's script for his laptop to backup to a usb disk...

# Path...
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

# Files and folders to backup...
FILES=files.list

# Files and folders to skip...
EXCLUDES=exclude-files.list

# Files and folders that would have been skipped, but special cases...
INCLUDES=exclude-exceptions.list

# Our hostname...
HOSTNAME=$(uname -n)

# Make sure we are being run as root...
if [ "$(id -u)" != "0" ]; then
   echo "You must run the script as root, since it needs to backup stuff system wide." 1>&2
   exit 1
fi

# Location to store backup...
BACKUP_PATH=/media/disk/$HOSTNAME

# Make sure it exists...
if [ ! -d $BACKUP_PATH ]
then
    mkdir $BACKUP_PATH
fi

# Rsync options...
OPTS="-avr
      --itemize-changes
      --delete
      --delete-excluded
      --human-readable
      --files-from=$FILES
      --include-from=$INCLUDES
      --exclude-from=$EXCLUDES 
      --progress 
      --stats"

# Display greeter...
echo "Preparing to backup" $HOSTNAME "in 5 seconds with the following command..."

# Echo command to run...
echo rsync $OPTS / $BACKUP_PATH
sleep 5

# now the actual transfer
rsync $OPTS / $BACKUP_PATH

```

Hope that helps.

Kip

---

### Post by CIEN on 2008-03-21
It does, thank you.

---

