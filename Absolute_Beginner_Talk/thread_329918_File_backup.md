---
title: "File backup"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Balaam's Miracle on 2007-01-02
I wish to make a backup of my MP3 collection, the medium will be DVD's.
I have over 12,000 tracks (possibily more but i don't care to count right now) and i was wondering if there is a backup program that:
1: Can backup to DVD
2: Just copies the files to DVD so that individual files can be restored without the use of backup software.
3: Fills the disk with files (keeping the paths intact) to capacity.

Here's the idea: Suppose i have 3 directories with files. Let's call them "Rock", "Paper" and "Scissors". All three folders contain 3 GB worth of files.
- The backup program would copy the "Rock" folder to a DVD, sees that there's 1.7 GB left, does some math and adds (almost) exactly 1.7 GB of the "paper" dir to that disk.
- Since there's about 2 MB left that can't be filled with files from the "Paper" folder, it adds a 2 MB file from the "Scissors" folder.
- The remaining 1.3 GB of the "Paper" folder gets written to the next disk and adds the rest of the "Scissors" folder too.
- When inserting any of the DVDs into another system (say an OS2 or a Win3.11 system), the contents of the disk can be read without the need to install extra software.

Does such software exist for Linux? It would help me out so much, because right now i do it all by hand and i'm getting fed up doing this.
In the distant past i have been using backup software for this task, but when one disk failed to burn right, the entire backup becomes useless...

P.S. an additional cool feature would be incremental backups so that i won't have to sift through my collection for what's new and what's not.

P.P.S. I know that, in spite of what the packaging says, DVDs hold less than 4.7 GB, i've just used 4.7 GB because i'm too lazy to do math :-).

---

### Post by rekahsoft on 2007-01-02
Hmmm...if you don't want a program to have to restore the files then you will have to do the backup either manually or write a script that does it for you. (or you could look on [http://gnomefiles.org/](http://gnomefiles.org/) to see if you can find a program that meets your needs that i missed)

---

### Post by indytim on 2007-01-02
If you've got your impressive collection on one partition, you might want to check out partimage.  It's a shell to allow backing up at the partition level.  Within the GUI, you can specify the file size (I use 4000M for DVD).

It is still a program.  If you decide to go this route, would appreciate a report back on any restores (so far I've only had to go one way).

IndyTim

---

### Post by kebes on 2007-01-02
This is a really good question and something that I've often wanted. I've often thought of creating a script to do this, but in the end just did it manually.

There was an article in Linux Journal awhile back that described various backup solutions:
[http://www.linuxjournal.com/article/8931](http://www.linuxjournal.com/article/8931)

In particular it mentions "KDar":
[http://kdar.sourceforge.net/](http://kdar.sourceforge.net/)

This program lets you "do full and incremental backups, and it can break up the archives into slices to fit on the storage media with which you choose to work." It is very neat, however (even with compression set to "none"), it places all the files within an archive file of some sort. I agree with you that raw files is the way to go, so that you can access them from any computer running any OS at any time!.


Let me know if you find a program that works (as I said, this is something I'd be interested in having...).

---

### Post by kebes on 2007-01-02
Well I wasn't satisfied with the programs available so I made a little script to do backing-up the way *Balaam's Miracle* requested. The script, with comments, looks like this:

```

#!/bin/sh

# mediabackup
# version 0.1

# SOURCE
#------------------------------------------------------------
# January 2, 2007
# This script was created by user "kebes" from ubuntuforums.org
# (see http://ubuntuforums.org/member.php?u=145068 ) for performing
# DVD-based backups. This was in response to the thread:
# http://ubuntuforums.org/showthread.php?p=1958625
# The script is hereby released under the terms of the GNU General 
# Public License (GPL) version 2.0. Full terms can be found at:
# http://www.gnu.org/copyleft/gpl.html


# DESCRIPTION
#------------------------------------------------------------
# The purpose of this script is to make it a bit simpler to make
# backups to CD/DVD. The script generates a directory structure with
# the files to be backed-up. In particular, it makes sure that
# each "diskN" directory is less than a set size, so that it will
# fit on the desired storage media (e.g. 650 MB for CD or 4500 MB
# for DVD).
#
# The resultant directories can be burned each to a DVD. The script
# includes support for using the "growisofs" command-line program to
# automatically burn the disks (although, of course, user intervention
# is required to actually put in each new disk).




# VARIABLES
#------------------------------------------------------------
# Change the variables below to fit your computer/backup setup:


# Name of this script (for log files)
SCRIPTNAME="Media backup script:"

# Directory to backup
SOURCE="$HOME/music"

# Temporary directory to accumulate list of files
TEMPDIR=$HOME/tmp/

# Name of your DVD device
DVDDEV=/dev/dvd

# Size (in MB) of storage media
# (the prepared backup will not be allowed to exceed this value)
MEDIASIZE=4400

# Print lots of messages? (0=false 1=true)
VERBOSE=1

# Burn disk? (0=false 1=true)
# WARNING: THIS FEATURE HAS NOT YET BEEN EXTENSIVELY TESTED AND MAY NOT
# WORK PROPERLY. (You should leave it turned off until you've made sure
# that "growisofs" works properly from the command line.)
BURNDISK=0


# In most cases, you should not have to change anything below here
#------------------------------------------------------------



# FUNCTIONS
#------------------------------------------------------------


# This function burns a DVD based on a DISKNUM
function burndvd {
	if [ $BURNDISK = 1  ]; then
		# Prompt user and wait
		echo $SCRIPTNAME
		echo "----------------------------------------"
		echo "Insert a blank DVD into your DVD writer."
		echo "Press enter when ready..."
		echo -n "----------------------------------------"
		read

		echo "$SCRIPTNAME attempting to write disk $1..."
		echo "------------------------------------------"

		# Burn the directory to DVD
		growisofs -R -Z $DVDDEV $WORKDIR/disk$1

		echo "------------------------------------------"
		echo "$SCRIPTNAME done with writing disk $1..."
		
	else
		echo "$SCRIPTNAME Skipping DVD burning step..."
	fi
}




# CODE
#------------------------------------------------------------

# Create a new temporary directory based on PID
WORKDIR=$TEMPDIR/work$$
mkdir $WORKDIR

# Note that "file-links" are created in the work directory, but the file
# contents are not copied. Thus, this work directory will not consume
# much disk space. It is essentially just a list (with links!) of the
# files to be backed up.


echo "$SCRIPTNAME Now starting..."
echo "$SCRIPTNAME Processing $SOURCE"

# Create a list of every file to backup
# (You can modify the "find" arguments to suit your backup needs)
find $SOURCE -iname "*" -type f -fprint $WORKDIR/filelog.txt
cat $WORKDIR/filelog.txt | sort > $WORKDIR/sortedlog.txt

# Count number of files to process
FILECOUNT=$(cat $WORKDIR/sortedlog.txt | wc -l)




CURFILE=1	# Keeps track of the file we are copying
DISKNUM=1	# Keeps track of which disk we are working on
SIZESOFAR=0	# Keeps track of the size of files added so far

echo "$SCRIPTNAME Starting disk $DISKNUM"

# For each identified file...
while [ $CURFILE -le $FILECOUNT ]
do
	FILE=`head $WORKDIR/sortedlog.txt -n $CURFILE | tail -n 1`

	# Copy the file to the current disk prep area
	if [ $VERBOSE = 1  ]; then
		echo "Adding $FILE to disk$DISKNUM..."
	fi
	FDIR=`find "$FILE" -printf %h`
	mkdir -p "$WORKDIR/disk$DISKNUM/$FDIR"
	cp -dpl "$FILE" "$WORKDIR/disk$DISKNUM$FILE"
	

	# Calculate size of files added so far
	SIZESOFAR=`du -m --max-depth=0 $WORKDIR/disk$DISKNUM | awk '{ print $1 }'`
	if [ $VERBOSE = 1  ]; then
		echo "Added file $CURFILE of $FILECOUNT. Size of disk $DISKNUM is: $SIZESOFAR MB"
	fi
	

	if [ $SIZESOFAR -gt $MEDIASIZE ]; then
		# This prep area is getting too big!
		#  1. Remove the last added file
		rm -f "$WORKDIR/disk$DISKNUM/$FILE"

		#  2. Burn this area to disk
		burndvd $DISKNUM

		#  3. Create a new disk prep area
		DISKNUM=$(($DISKNUM+1))
		echo "$SCRIPTNAME Starting disk $DISKNUM"
		
	else
		# Go to next file
		CURFILE=$(($CURFILE+1))
	fi

done

# Burn last area to disk
burndvd $DISKNUM


# Clean up, if burning to disk was enabled
if [ $BURNDISK = 1  ]; then
	rm -rf $WORKDIR
fi

```

As with all shell scripts, after saving the above in a text file, you'll need to use the commandline and go:
$ chmod +x mediabackup
so that it will be executable. As you can see from the script you'll need to change a few variables to suit your needs, and then to run it just go:
$ ./mediabackup

Hopefully the comments in the script make it clear what it's supposed to be doing. If not, feel free to ask questions. I have not yet tested the script much, so there may be some bugs in it. As always: use this freely provided code at your own risk! I have tried to make sure that the code works properly but it is provided without warranty of any kind! You are encouraged to review the code before running it.

Hope someone finds that helpful!

---

### Post by Balaam's Miracle on 2007-01-03
Wow, thanks a heap for the trouble! I am iching to take this script for a spin, using DVD-RW until we know that growisofs works as we hope/expect.

One question though: should DVDDEV be the actual device in /dev or may it also be the mountpoint of the DVD burner? (did i get my terminology right?)

---

### Post by kebes on 2007-01-03
DVDDEV is passed as a parameter to growisofs. You can find the manpage here:
[http://www.linuxcommand.org/man_pages/growisofs1.html](http://www.linuxcommand.org/man_pages/growisofs1.html)

I'm pretty sure it has to refer to the device in /dev/ (not the mountpoint), because it needs to access the device itself (and not merely copy files to a location). That having been said, you can use a symlink to the device rather than the device itself. (Not the same thing as a mountpoint or symlink to mountpoint!!) 

I've used growisofs (to make movie DVDs), and I've always used "/dev/dvd". On my Kubuntu machine, this is actually a symlink that points to "/dev/hda" (since my DVD-writer is the first IDE device). So either of those would probably work.


Short answer: if you're running Ubuntu, then DVDDEV="/dev/dvd" will probably work.


Let me know how it works out. I'm gonna use this script myself the next time I need to do a DVD backup.

---

### Post by Balaam's Miracle on 2007-01-03
I'm having some problems using the script, i will PM you about it because it could turn this topic into a slowchat...

---

### Post by Balaam's Miracle on 2007-01-12
Since Kebes posted his first version of the script, he and i have worked together on extending the script and making it more user friendly.

To post a changelog would be too much to ask, there have been too amny changes to kaeep track of (besides, we were too lazy to keep a log anyway :-))
However, here are a few of changes off the top of my head:
- FEATURE: Added GUI using Zenity. Gotta love Zenity!
- FIX: When burning to disk fails, a new attempt will be made.
- FIX: Media is burned with additional Joliet extentions to make it more compatible. For instance, to stand-alone DVD players.
- FIX: When ~/ was on a different drive or partition than where the files were that you wanted to back up, the backup failed.
- FIX: If ~/tmp/ did not exist, backup failed.

KNOWN BUGS/LIMITATIONS:
- BUG: If the path to the files that you want to back up contains a space, the backup fails. No known workaroud yet.
- BUG: Files larger than the backup medium will send the script in a loop. creating lots of empty directories.
- IMPERFECTION: If you choose not to burn the disks, you will need to manually clean up the resulting dirs. Option needed to make this automatic.
- IMPERFECTION: In some places, the script refers to the backup media as a DVD, even if you choose CD as medium.
- IMPERFECTION: You can backup only one directory (with or without subdirectories) at a time.

TODO:
- Kil bugs (duh :-)) and iron out the imperfections.
- Add progressbars.
- When canceling one of the steps at the beginning of the script, return to previous step instead of aborting the backup altogether.
- Find ways to around some of the limitations.
- Get the verbose output to display in Zenity boxes and/or open teminal to display status messages.
- Add more media types.
- Add code for the script to automatically select the backup device.

PLEASE NOTE: If you make any changes and/or modifications to this script, please show us what you did so that we may include your modifications in a next version!

ATTENTION DAPPER USERS: This script is using bash. If the script fails to run, change the first line to "#!/bin/sh".
```
#!/bin/bash

# mediabackup.sh
# version 0.5.1

# Set version number
VERSION="0.5.1"


# SOURCE
#------------------------------------------------------------
# January 2, 2007
# This script was created by user "kebes" from ubuntuforums.org
# (see http://ubuntuforums.org/member.php?u=145068 ) for performing
# DVD-based backups. This was in response to the thread:
# http://ubuntuforums.org/showthread.php?p=1958625
# The script is hereby released under the terms of the GNU General 
# Public License (GPL) version 2.0. Full terms can be found at:
# http://www.gnu.org/copyleft/gpl.html
# The script was greatly extended by user "Balaam's Miracle"
# (see http://ubuntuforums.org/member.php?u=203094 ), specifically
# with the addition of zenity user interface elements.


# DESCRIPTION
#------------------------------------------------------------
# The purpose of this script is to make it a bit simpler to make
# backups to CD/DVD. The script generates a directory structure with
# the files to be backed-up. In particular, it makes sure that
# each "diskN" directory is less than a set size, so that it will
# fit on the desired storage media (e.g. 650 MB for CD or 4500 MB
# for DVD).
#
# The resulting directories can be burned each to a DVD. The script
# includes support for using the "growisofs" command-line program to
# automatically burn the disks (although, of course, user intervention
# is required to actually put in each new disk).


# VARIABLES
#------------------------------------------------------------
# Change the variables below to fit your computer/backup setup:


# Name of this script (for log files)
SCRIPTNAME="Media backup script:"


# ===========================
# Welcome text
# ===========================

zenity --text "Welcome to MediaBackup v.$VERSION.

This backup program will make a backup of the files of
your choice to a medium/drive of your choice.

The main difference with other backup programs is that with
MediaBackup, the resulting backups can be read by most other
computers with similar drives.
This means that if you back up to a CD, the backups can be
read on other computers that have a CD-ROM drive.

Press ''OK'' When ready.
" --info


# ===========================
# Select dir
# ===========================

SOURCE=$(zenity --title "Please browse to the directory to be backed up and press OK" --file-selection --directory)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac
# ===========================
# Select backup device
# ===========================

DVDDEV=$(zenity --text "To what device should the backup be written?
(when in doubt, try going with the default) " --entry --entry-text "/dev/dvdrw")
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac

# ===========================
# Select media type
# ===========================
MEDIATYPE=$(zenity --height=250 --text "What kind of medium will you use?" --list --radiolist --column " " --column "Medium" TRUE CD FALSE DVD FALSE DVD9)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac

if [ $MEDIATYPE = DVD ];then
   MEDIASIZE=4400
elif [ $MEDIATYPE = DVD9 ];then
   MEDIASIZE=8800
elif [ $MEDIATYPE = CD ];then
   MEDIASIZE=640
fi

# ===========================
# Verbose mode selector
# ===========================

VERBOSEMODE=$(zenity --text "Use verbose mode? 
Please note that verbose mode will show lots of messages."  --list --radiolist --column " " --column "Verbose" TRUE No FALSE Yes)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info
           exit ;;
    esac
    if [ $VERBOSEMODE = "Yes" ]; then
        VERBOSE="1"
    else
        VERBOSE="0"
    fi

# ===========================
# To burn or not to burn...
# ===========================

BURNMODE=$(zenity --text "Do you wish to write the backup to your media?
If you choose ''No'', directories (sized based on the selected media) 
will be created, but will not be written to disk. You can then write the
backup to disk manually."  --list --radiolist --column " " --column "Burn" TRUE No FALSE Yes)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info
           exit ;;
    esac
    if [ $BURNMODE = "Yes" ]; then
        BURNDISK="1"
    else
        BURNDISK="0"
    fi

# In most cases, you should not have to change anything below this line
#----------------------------------------------------------------------
#----------------------------------------------------------------------

# Temporary directory to accumulate (list of) files
# This will always be in a folder in your home directory.
TEMPDIR=$HOME/tmp

# Check if temporary directory is on same partition (device)
# as source directory:
DEVBCK=`stat $SOURCE --format=%D`
DEVTMP=`stat $TEMPDIR --format=%D`
if [ $DEVBCK = $DEVTMP ]; then
	METHOD=0
else
	METHOD=1
fi

echo "========================================================"
echo "Choosing Caching method #"$METHOD
echo ""
echo "SOURCE = "$SOURCE
echo "DEVBCK = "$DEVBCK
echo ""
echo "TEMPDIR = "$TEMPDIR
echo "DEVTMP = "$DEVTMP
echo "========================================================"


# FUNCTIONS
#------------------------------------------------------------


# This function burns a DVD based on a DISKNUM
function burndvd {
	if [ $BURNDISK = 1  ]; then
		# Prompt user and wait
		zenity  --info --text "Insert a blank $MEDIATYPE into your CD/DVD writer and click OK when ready..."
		

        echo "$SCRIPTNAME attempting to write disk $1..."
		echo "------------------------------------------"

		# Burn the directory to DVD. 
        # The DVD will be an ISO9660 volume and have Joliet and Rock Ridge extensions
        # To disable Joliet extensions, change the line below to :
        # growisofs -R -Z $DVDDEV $WORKDIR/disk$1
		growisofs -R -joliet-long -Z $DVDDEV $WORKDIR/disk$1
		
        if [ $? <> 0 ]; then
        zenity --text "Write failed!

Please insert another medium and hit Enter to retry." --error
    burndvd $1

    else
        echo "------------------------------------------"
		echo "$SCRIPTNAME done with writing disk $1..."
		
        if [ $METHOD = 1 ]; then
            # Remove temporary files when using method 1
            echo "Removing cached files from temp dir to save space..."
            rm -rf $WORKDIR/disk$1
        fi    
    fi
	else
		echo "$SCRIPTNAME Skipping DVD burning step..."
	fi
}


# CODE
#------------------------------------------------------------

# Create a new temporary directory based on PID
WORKDIR=$TEMPDIR/mediabackup$$
mkdir -p $WORKDIR

# Note that "file-links" are created in the work directory, but the file
# contents are not copied. Thus, this work directory will not consume
# much disk space. It is essentially just a list (with links!) of the
# files to be backed up.

zenity --text "Now starting.
$SOURCE will be backed up.

Click OK to start or cancel to quit" --question
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac

# Create a list of every file to backup
# (You can modify the "find" arguments to suit your backup needs)
find $SOURCE -iname "*" -type f -fprint $WORKDIR/filelog.txt
cat $WORKDIR/filelog.txt | sort > $WORKDIR/sortedlog.txt

# Count number of files to process
FILECOUNT=$(cat $WORKDIR/sortedlog.txt | wc -l)

CURFILE=1	# Keeps track of the file we are copying
DISKNUM=1	# Keeps track of which disk we are working on
SIZESOFAR=0	# Keeps track of the size of files added so far

echo "$SCRIPTNAME Starting disk $DISKNUM"

# For each identified file...
while [ $CURFILE -le $FILECOUNT ]
do
	FILE=`head $WORKDIR/sortedlog.txt -n $CURFILE | tail -n 1`

	# Copy the file to the current disk prep area
	if [ $VERBOSE = 1  ]; then
		echo "Adding $FILE to disk$DISKNUM..."
	fi
	FDIR=`find "$FILE" -printf %h`
	mkdir -p "$WORKDIR/disk$DISKNUM/$FDIR"
        if [ $METHOD = 0 ]; then
           cp -dpl "$FILE" "$WORKDIR/disk$DISKNUM$FILE"
        else
           cp -dp "$FILE" "$WORKDIR/disk$DISKNUM$FILE"
        fi

	# Calculate size of files added so far
	SIZESOFAR=`du -m --max-depth=0 $WORKDIR/disk$DISKNUM | awk '{ print $1 }'`
	if [ $VERBOSE = 1  ]; then
		echo "Added file $CURFILE of $FILECOUNT. Size of disk $DISKNUM is:
        $SIZESOFAR MB"
	fi
	

	if [ $SIZESOFAR -gt $MEDIASIZE ]; then
		# This prep area is getting too big!
		#  1. Remove the last added file
		rm -f "$WORKDIR/disk$DISKNUM/$FILE"

		#  2. Burn this area to disk
		burndvd $DISKNUM

		#  3. Create a new disk prep area
		DISKNUM=$(($DISKNUM+1))
		echo "$SCRIPTNAME Starting disk $DISKNUM"
		
	else
		# Go to next file
		CURFILE=$(($CURFILE+1))
	fi

done

# Burn last area to disk
burndvd $DISKNUM


# Clean up, if burning to disk was enabled
if [ $BURNDISK = 1  ]; then
	rm -rf $WORKDIR
fi
rm -f $WORKDIR/filelog.txt 
rm -f $WORKDIR/sortedlog.txt 

zenity --text "Backup process finished." --info

```

WARNING!!!
When pasting the code in your text editor, make sure that you've set automatic wrapping to OFF or the script might break!

---

### Post by gfolkert on 2007-01-16
A change that will help out with multi-disk.

```
		growisofs -R -joliet-long -Z $DVDDEV $WORKDIR/disk$1
		
        if [ $? <> 0 ]; then
        zenity --text "Write failed!
```

Needs to be changed to:

```
		growisofs -R -joliet-long -Z $DVDDEV $WORKDIR/disk$1
	retval1=$?	
        if [ $retval1 -ne 0 ]; then
        zenity --text "Write failed!
```

This is what works in Debian Sid. Also, this accounts for using "wodim"

Cheers.

---

### Post by bcdaus on 2007-01-24
Love the script - but it seems to barf when trying to burn CDs.  I think growisofs can't handle CD-Rs.  I get a message that the media type is wrong.  I was thinking of seeing if I could hack the script to use CD-Record if we choose to burn CDs rather than DVDs.

I might also look at doing a version that could be run as a cron job to do the scheduling for the jobs - you'd need to give it some command line options though.

Biting off more than I can chew ?  Probably, but you got to learn somehow !!

Any thoughts ?

Bill.

---

### Post by kebes on 2007-01-24
> **bcdaus said:**
> the script seems to barf when trying to burn CDs. I was thinking of seeing if I could hack the script to use CD-Record if we choose to burn CDs rather than DVDs.

Hmm.... I just assumed growisofs worked with CDs and DVDs ... although I must admit I have not tried using it for CDs.

The script should certainly be updated to fix this. The script could probably choose between using "growisofs" and "cd-record" depending on what mediatype is selected. If you're interested in modifying the script, that's great! Please post your changes back to this thread or in a private message to me or Balaam's Miracle.

You may also be interested to know that we have the script posted on a website:
[http://bmgip.gotdns.com/mediabackup/](http://bmgip.gotdns.com/mediabackup/)

You'll find the latest version there, which includes a few bugfixes. If you're going to make modifications, you should probably use the latest version of the script.


If you run into problems with your coding changes, feel free to post questions. I think this is a really good idea for added functionality to the script!

---

### Post by Balaam's Miracle on 2007-01-31
An emergency bugfix has been posted on [http://bmgip.gotdns.com/mediabackup](http://bmgip.gotdns.com/mediabackup)

Please note that even though the script now works with CD-ROM as backup medium, burning is currently rather slow. A later version of the script will let you set the burn speed.

P.S. My apologies for noty fixing this sooner, i was out cold with the flu (get it? cold... flu...? :-& )

---

### Post by bcdaus on 2007-02-05
Just updated to Version 0.5.7 and discovered a typo on line 211 that prevents it from using growisofs. CDrecord then tries to burn a dvd (I am using DVD+RW which is only supported in cdrecord-ProDVD..)

```
if [ $MEDIATYPE = "DVD" || $MEDIATYPE = "DVD9" ]; then
```
should be
```
if [ $MEDIATYPE = "DVD" ] || [ $MEDIATYPE = "DVD9" ]; then
```

It then seems to work to burn both DVDs and CDRs !!

Hooray !!

Bill.

---

### Post by Balaam's Miracle on 2007-02-05
I think a "whoops!" is in order. 
The typo is hereby corrected.

Thanks for the heads up!

---

### Post by .nedberg on 2007-07-07
Is this program still being developed?

If it is: Would you be interested in a way to make it keep track of files already copied to a CD/DVD (I mean on a previous run) and only add new or modified files? I just started working on this and I am getting closer to a solution. I am using sqlite though, and it is not in a standard install of ubuntu...

---

### Post by .nedberg on 2008-01-12
Hi

I just made some additions to the script. It now does incremantal backups, remembering what files was backed up last run and does not add them if they have not been altered.

You need sqlite and zenity for the script to work.

```

#!/bin/bash

# mediabackup
# version 0.6.0
#
# Set version number
VERSION="0.6.0"


# SOURCE
#------------------------------------------------------------
# January 2, 2007
# This script was created by user "kebes" from ubuntuforums.org
# (see http://ubuntuforums.org/member.php?u=145068 ) for performing
# DVD-based backups. This was in response to the thread:
# http://ubuntuforums.org/showthread.php?p=1958625
# The script is hereby released under the terms of the GNU General
# Public License (GPL) version 2.0. Full terms can be found at:
# http://www.gnu.org/copyleft/gpl.html
# The script was greatly extended by user "Balaam's Miracle"
# (see http://ubuntuforums.org/member.php?u=203094 ), specifically
# with the addition of zenity user interface elements.


# DESCRIPTION
#------------------------------------------------------------
# The purpose of this script is to make it a bit simpler to make
# backups to CD/DVD. The script generates a directory structure with
# the files to be backed-up. In particular, it makes sure that
# each "diskN" directory is less than a set size, so that it will
# fit on the desired storage media (e.g. 650 MB for CD or 4500 MB
# for DVD).
#
# The resulting directories can be burned each to a DVD. The script
# includes support for using the "growisofs" command-line program to
# automatically burn the disks (although, of course, user intervention
# is required to actually put in each new disk).


# VARIABLES
#------------------------------------------------------------
# Change the variables below to fit your computer/backup setup:


# Name of this script (for log files)
SCRIPTNAME="Mediabackup v. $VERSION:"


# Directory to hold the database
DBDIR=$HOME/.mediabackup

if [ ! -d $DBDIR ]; then
	mkdir $DBDIR
fi

db=""


# This function lets the user select a database previously used or create a new one
function selectDataBase() {

# 	Gets a listing of every exising database
	int=0
	for f in $(find $DBDIR/*.db -type f); do
		f=$(echo $f | sed "s%$DBDIR/%%g" | sed "s/.db//g")
		db_array[$int]="$f"
		int=$(($int+1))
	done

	n=0
	i=${#db_array[*]}

# 	Ask user what databse to use
	selectedDB=$(zenity --height=250 --text "What database do you want to use?" --list --radiolist --column " " --column "DataBase" TRUE "Create new" $(while [ $n -lt $i ]; do echo FALSE; echo ${db_array[$n]}; n=$(($n+1)); done))
	retvar=$?

# 	Did the user make a choice?
	if [ "$selectedDB" = "" ] || [ $retvar = 1 ]; then
		echo "Operation canceled, exiting"
		exit

# 	Did the user want to create a new database?
	elif [ "$selectedDB" = "Create new" ]; then
		createNewDatabase

# 	Build filename and path for the new database.
	else
		db=$DBDIR/$selectedDB.db
	fi
}


# This function creates a new database
function createNewDatabase () {

	if [ $VERBOSE = 1 ]; then
		echo "Need to create a new database"
	fi

# 	Ask for a name for the new database
	newdb=$(zenity --text "Please enter a name for the new database." --entry)
	retvar=$?

# 	Check if a name was given
	if [ "$retvar" = "1" ] || [ "$newdb" = "" ]; then
		if [ $VERBOSE = 1 ]; then
			echo "No name for the new database supplied. Exiting..."
		fi
		exit
	fi

# 	Build filename and path for the new database.
# 	If the filename contains spaces it will be converted to underscore
	db=$(echo $newdb | sed "s/ /_/g")
	db=$(echo "${DBDIR}/${db}.db")

# 	Create the new database
	sqlite "$db" "create table files (key INTEGER PRIMARY KEY,filename TEXT,modTime DATE);"

}

# This function checks if a file exists in the selected database and gives a return value indicating if it should be backed up or not
function checkFile () {

# 	Check if the function was called correctly
	if [ -z "$1" ]; then
		echo "No filename passed to function, somthing went wrong"
		echo "Usage: checkFile /path/to/filename.ext"
	fi

# 	Get filename from argument
	filename="$1"

# 	Check if the file exists
	if [ ! -f "$filename" ]; then
		if [ $VERBOSE = 1  ]; then
			echo "File with name $filename does not exist, skipping"
		fi
		return 1
	fi

# 	Gets the modification time from the database and from the file
	mod=`sqlite $db "select modTime from files where filename='$filename';"`
	lastMod=`stat --format=%Y "$filename"`

# 	If the file is not in the database it should be added to the new disk
	if [ "$mod" = "" ]; then
		if [ $VERBOSE = 1  ]; then
			echo "Adding new file $filename"
		fi
		sqlite $db "insert into files (filename, modTime) values ('$filename', '$lastMod');"
		return 0

# 	If the file has been modified since last run
	elif [ ! "$lastMod" = "$mod" ]; then
		if [ $VERBOSE = 1  ]; then
			echo "File with name $filename has been modified since last run, adding it"
		fi
		sqlite $db "update files set modTime='$lastMod' where filename='$filename';"
		return 0

# 	File is in the database and has not been modified since last run
	else
		if [ $VERBOSE = 1  ]; then
			echo "File with name $filename was backed up on last run, skipping"
		fi
		return 1
	fi

}




# ===========================
# Welcome text
# ===========================

zenity --text "Welcome to MediaBackup v.$VERSION.

This backup program will make a backup of the files of
your choice to a medium/drive of your choice.

The main difference with other backup programs is that with
MediaBackup, the resulting backups can be read by most other
computers with similar drives.
This means that if you back up to a CD, the backups can be
read on other computers that have a CD-ROM drive.

Press ''OK'' When ready.
" --info

echo "========================================================"
echo "============== MEDIABACKUP VERSION $VERSION ==============="
echo "========================================================"
echo "Console logging started."
echo " "


# The user must first select a database
selectDataBase


# ===========================
# Select dir
# ===========================

SOURCE=$(zenity --title "Please browse to the directory to be backed up and press OK" --file-selection --directory)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac
echo "SOURCE = $SOURCE"

# ===========================
# Select media type
# ===========================
MEDIATYPE=$(zenity --height=250 --text "What kind of medium will you use?" --list --radiolist --column " " --column "Medium" TRUE CD FALSE DVD FALSE DVD9 FALSE QUICKTEST)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info
           exit ;;
    esac

if [ $MEDIATYPE = DVD ];then
   MEDIASIZE=4400
elif [ $MEDIATYPE = DVD9 ];then
   MEDIASIZE=8800
elif [ $MEDIATYPE = CD ];then
   MEDIASIZE=640
elif [ $MEDIATYPE = QUICKTEST ];then
   MEDIASIZE=100
fi
echo "MEDIATYPE = $MEDIATYPE ($MEDIASIZE MB)"


# ===========================
# Select backup device
# ===========================

if [ $MEDIATYPE = "DVD" ] || [ $MEDIATYPE = "DVD9" ]; then
	DVDDEV=$(zenity --text "To what device should the backup be written?
(when in doubt, try going with the default) " --entry --entry-text "/dev/dvdrw")
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac
else
	DVDDEV=$(zenity --text "To what device should the backup be written?
(when in doubt, try going with the default) " --entry --entry-text "/dev/cdrw")
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac
fi
echo "DVDDEV = $DVDDEV"

# ===========================
# Verbose mode selector
# ===========================

VERBOSEMODE=$(zenity --text "Use verbose mode?
Please note that verbose mode will show lots of messages."  --list --radiolist --column " " --column "Verbose" FALSE Yes TRUE No)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info
           exit ;;
    esac
    if [ $VERBOSEMODE = "Yes" ]; then
        VERBOSE="1"
    else
        VERBOSE="0"
    fi
echo "VERBOSE = $VERBOSE"

# ===========================
# To burn or not to burn...
# ===========================

BURNMODE=$(zenity --text "Do you wish to write the backup to your media?
If you choose ''No'', directories (sized based on the selected media)
will be created, but will not be written to disk. You can then write the
backup to disk manually."  --list --radiolist --column " " --column "Burn" FALSE Yes TRUE No)
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info
           exit ;;
    esac
    if [ $BURNMODE = "Yes" ]; then
        BURNDISK="1"
    else
        BURNDISK="0"
    fi
echo "BURNDISK = $BURNDISK"

# In most cases, you should not have to change anything below this line
#----------------------------------------------------------------------
#----------------------------------------------------------------------

# Temporary directory to accumulate (list of) files
# This will always be in a folder in your home directory.
TEMPDIR=$HOME/tmp
if [ ! -d $TEMPDIR ]; then
	mkdir $TEMPDIR
fi
echo "TEMPDIR = $TEMPDIR"

# Check if temporary directory is on same partition (device)
# as source directory:
DEVBCK=`stat "$SOURCE" --format=%D`
DEVTMP=`stat $TEMPDIR --format=%D`
if [ $DEVBCK = $DEVTMP ]; then
	METHOD=0
else
	METHOD=1
fi
echo "Caching method = $METHOD"

# FUNCTIONS
#------------------------------------------------------------


# This function burns a disk based on a DISKNUM
function burndvd {
	if [ $BURNDISK = 1  ]; then
		# Prompt user and wait
		zenity  --info --text "Insert a blank $MEDIATYPE into your CD/DVD writer and click OK when ready..."


        echo "$SCRIPTNAME attempting to write disk $1..."
		echo "------------------------------------------"

		if [ $MEDIATYPE = "DVD" ]||[ $MEDIATYPE = "DVD9" ]; then
			# Burn the directory to disk.
			# The disk will be an ISO9660 volume and have Joliet and Rock Ridge extensions
			# To disable Joliet extensions, change the line below to :
			# growisofs -R -Z $DVDDEV $WORKDIR/disk$1
			growisofs -R -joliet-long -Z $DVDDEV $WORKDIR/disk$1
			eject $DVDDEV
		else
			echo "Starting CD image for disk$1 ."
			mkisofs -R -joliet-long -o $WORKDIR/disk$1.raw $WORKDIR/disk$1
			#	cdrecord -v dev=$DVDDEV -dao -overburn $WORKDIR/disk$1.raw
			cdrecord -v dev=$DVDDEV driveropts=burnfree -dao -overburn $WORKDIR/disk$1.raw
			eject $DVDDEV
		fi
        retval1=$?
        if [ $retval1 -ne 0 ]; then
		eject $DVDDEV
        zenity --text "Write failed!

Please insert another $MEDIUMTYPE and hit Enter to retry." --error
    burndvd $1

    else
        echo "------------------------------------------"
		echo "$SCRIPTNAME done with writing disk $1..."

        if [ $METHOD = 1 ]; then
            # Remove temporary files when using method 1
            echo "Removing cached files from temp dir to save space..."
            rm -rf $WORKDIR/disk$1
			rm $WORKDIR/disk$1.raw
        fi
    fi
	else
		echo "$SCRIPTNAME Skipping $MEDIATYPE burning step..."
	fi
}


# CODE
#------------------------------------------------------------

# Create a new temporary directory based on PID
WORKDIR=$TEMPDIR/mediabackup$$
mkdir -p $WORKDIR

# Note that "file-links" are created in the work directory, but the file
# contents are not copied. Thus, this work directory will not consume
# much disk space. It is essentially just a list (with links!) of the
# files to be backed up.

zenity --text "Now starting.
$SOURCE will be backed up.

Click OK to start or cancel to quit" --question
retval=$?
    case $retval in
        0) ;;
        1) zenity --text "Backup aborted" --info

           exit ;;
    esac

# Create a list of every file to backup
# (You can modify the "find" arguments to suit your backup needs)
find "$SOURCE" -iname "*" -type f -fprint $WORKDIR/filelog.txt
cat $WORKDIR/filelog.txt | sort > $WORKDIR/sortedlog.txt

# Count number of files to process
FILECOUNT=$(cat $WORKDIR/sortedlog.txt | wc -l)

CURFILE=1	# Keeps track of the file we are copying
DISKNUM=1	# Keeps track of which disk we are working on
SIZESOFAR=0	# Keeps track of the size of files added so far

echo "$SCRIPTNAME Starting disk $DISKNUM"
DONTCHECK=0
# For each identified file...
while [ $CURFILE -le $FILECOUNT ]
do
	FILE=`head $WORKDIR/sortedlog.txt -n $CURFILE | tail -n 1`
	if [ "$DONTCHECK" = "0" ]; then
		checkFile "$FILE"
		ADDFILE=$?
	else
		DONTCHECK=0
	fi
	if [ "$ADDFILE" = "0" ]; then
		# Copy the file to the current disk prep area
		if [ $VERBOSE = 1  ]; then
			echo "Adding $FILE to disk$DISKNUM..."
		fi
		FDIR=`find "$FILE" -printf %h`
		mkdir -p "$WORKDIR/disk$DISKNUM/$FDIR"
		if [ $METHOD = 0 ]; then
		cp -dpl "$FILE" "$WORKDIR/disk$DISKNUM$FILE"
		else
		cp -dp "$FILE" "$WORKDIR/disk$DISKNUM$FILE"
		fi
	
		# Calculate size of files added so far
		SIZESOFAR=`du -m --max-depth=0 $WORKDIR/disk$DISKNUM | awk '{ print $1 }'`
		if [ $VERBOSE = 1  ]; then
			echo "Added file $CURFILE of $FILECOUNT. Size of disk $DISKNUM is $SIZESOFAR MB"
		fi
	
	
		if [ $SIZESOFAR -gt $MEDIASIZE ]; then
			# This prep area is getting too big!
			#  1. Remove the last added file
			rm -f "$WORKDIR/disk$DISKNUM/$FILE"
	
			#  2. Burn this area to disk
			burndvd $DISKNUM
	
			#  3. Create a new disk prep area
			DISKNUM=$(($DISKNUM+1))
			echo "$SCRIPTNAME Starting disk $DISKNUM"
			DONTCHECK=1
	
		else
			# Go to next file
			CURFILE=$(($CURFILE+1))
		fi
	else
		CURFILE=$(($CURFILE+1))
	fi

done

# Burn last area to disk
burndvd $DISKNUM


# Clean up, if burning to disk was enabled
if [ $BURNDISK = 1  ]; then
	rm -rf $WORKDIR
else
CLEANIT=$(zenity --text "You chose not to burn the disks.
As a result, the files have been cached and sorted in
directories just as they would be on a $MEDIATYPE.
Do you wish to remove the cache?"  --list --radiolist --column " " --column "Cleanup" TRUE Yes FALSE No)
retval=$?
    case $retval in
        0)
		echo "CLEANIT = $CLEANIT"
		if [ $CLEANIT = Yes ]; then
			echo "Removing $WORKDIR"
			rm -rf $WORKDIR
			if [ $? = 0 ]; then
				echo "Successfully removed $WORKDIR."
			else
				echo "Directory $WORKDIR could not be removed. Please try to remove the directory manually."
			fi
		else
			zenity --text "Please remember to clean up the cache files manually." --info
		fi;;
		1)
			zenity --text "Action canceled. Please remember to clean up the cache files manually." --info
			echo "Cancel pressed in cleanup dialog.";;
    esac
fi

rm -f $WORKDIR/filelog.txt
rm -f $WORKDIR/sortedlog.txt


zenity --text "Backup process finished." --info

exit 0


```

---

