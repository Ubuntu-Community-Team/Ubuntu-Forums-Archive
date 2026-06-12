---
title: "Copying homefolder difficulties"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-06-29
I was trying to copy my home folder to an external usb drive.
At first ubuntu didn't recognize the drive, but when I unplugged and replugged it, it got detected.
I then proceeded to copy my homefolder, but the copying go stuck on a file(something tty) and the remaining time went up to something like about 20 hours. My homefolder is no bigger than 3,5 GB, so this amount of time was ridiculous.
I then tried to stop the copy action by pressing cancel, but it would no respond. Since i didn't know what else to do, I restarted. After the restart, my external drive no longer is recognized by ubuntu, and unplugging and plugging it back in didn't help.
So.. 
Does anybody know what could be causing this? the not being recognized (I get errors on startup if I leave the hard disk plugged in, in ubuntu as wel as kubuntu live CD). And does anybody know why the copying got stuck on this file and didn respond anymore? 
I would try mounting, but I have no idea what the usb drive is called and I am appallingly lousy with the mount command.
I want to backup my homefolder, cause  there are a few other things that are not going right with this installation of ubuntu since I started running out of space last week.

---

### Post by whizbaby on 2007-06-29
Hmm, I dont know if its really a good idea to copy your homedir when youre logged in. There are some open files (e.g. your session file) which cant be copied until closed (someone please stop me if I say something stupid, but that would explain why it took soooo long). Equally problematic is turning off the computer when a disk hasnt finished its writing duty, this may frag the disks filesystem (especially microsoft based fat32 or ntfs).
So try starting your system, log in and plug in the usbdrive. Type 
dmesg| grep usb
and look out for the device the harddrive is connected to (usually the lowest free pseudoscsi device, e.g. /dev/sda when you have an IDE harddrive in your computer, /dev/sdb if you have one sata drive in your computer).
To mount it manually, (lets assume it hangs on /dev/sda) make a mountpoint (empty directory) where you want it to be mounted (e.g. /extdrive, sudo mkdir /extdrive) and type 
sudo mount -t PUT_THE_FILESYSTEM_TYPE_HERE   /dev/sda   /extdrive
Can it be mounted, or does it seem broken?

---

### Post by quinnten83 on 2007-06-29
I read somewhere that it was possible to do so, but maybe that information was wrong. I thought it was odd as well, but since my experience was with windows, I gave it the benefit of doubt.
I will try with your instructions and let you know what the result was.

---

### Post by quinnten83 on 2007-06-29
I get a very long list with errors in it.
I'm posting a small part of it as an example:

```

[ 9300.556000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[ 9300.804000] usb 3-1: configuration #1 chosen from 1 choice
[ 9302.760000] usbcore: registered new interface driver libusual
[ 9302.832000] usbcore: registered new interface driver usb-storage
[ 9302.832000] usb-storage: device found at 3
[ 9302.832000] usb-storage: waiting for device to settle before scanning
[ 9307.832000] usb-storage: device scan complete
[ 9307.872000]  sdb:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 3
[ 9339.096000] usb 3-1: device descriptor read/64, error -71
[ 9369.464000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[ 9370.576000] usb 3-1: device descriptor read/64, error -71
[ 9400.944000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[ 9402.056000] usb 3-1: device descriptor read/64, error -71


```
 I think the device is sdb6  but it's an external harddrive with a 30 gig NTF partition and a 10 gig fat32 partition.
would a reformat of the harddrive help to solve the problem?
I tried mounting but as usual I wasn't able to make it work.
Somehow my mounting skills are not that good.

---

### Post by quinnten83 on 2007-06-29
Ha, 
seems it's a bug. [see here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746")

I tried the modprobe solution, the first few times, it didn't work. The third time it worked.
Now, All I have to do is figure out how to copy my homedir to the harddrive.

---

### Post by whizbaby on 2007-06-29
> **quinnten83 said:**
> Ha, 
seems it's a bug. [see here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746")

Careful with such conclusions, I dont see any of the people on page who have a similar situation like you. For you it worked , then you broke it. Thats not a bug.
> 
I tried the modprobe solution, the first few times, it didn't work. The third time it worked.
Now, All I have to do is figure out how to copy my homedir to the harddrive.
Sometimes you are lucky and stuff turns out to work anyways...but dont make that a rule!

What I would do is:
login AS ROOT on console (ctrl-alt-f1 on login screen switches to console). To enable the root account you must first login as yourusername and type (in terminal)
sudo passwd
and then give a STRONG password because you are not going to use this account frequently.
Logout and switch to console + login as root as described above. Then copying should be no more problem.

---

### Post by quinnten83 on 2007-06-30
Does the sudo command not give the same options?
also if i change the root password, does it mean that the next time I use the sudo command, I have to use the new password?

---

### Post by bobplano on 2007-06-30
they suggested opening the root account so all your files can be copied over because of the different accounts. sudo should still run on your user password though

---

### Post by smo0th on 2007-06-30
I dont think you must be as root,

try with 

sudo cp -R /your/home/folder /your/whatever/drive

---

### Post by greg_g on 2007-06-30
As someone who has a nightly cron job backing up his home dir using rsync, I am wondering what files won't be backed up if I am logged.

I guess an easy fix for me is to just edit the crontab to have "sudo" in front of the script.

Any clarification would be appreciated.

(sorry to hi-jack your thread btw)


greg

---

### Post by quinnten83 on 2007-07-01
Hijack away, 
this is more interesting than I thought.
I did try to just copy using sudo, but it was without the -R argument.
What does the -R argument stand for? I couldn't find it in the man pages.

---

### Post by greg_g on 2007-07-01
-R, -r, --recursive
              copy directories recursively


Goes into all of the sub-directories, and their sub-directories, and their.... oh, you get the idea.

---

### Post by quinnten83 on 2007-07-01
I tried with a sudo cp -R command and it seems to have copied. There we're a couple of errors, but i think i got most of it.
I did have to do the modprobe thing a few times though. So I do think it is a bug (worth checking out).

---

### Post by whizbaby on 2007-07-02
> 1)Does the sudo command not give the same options?
2)also if i change the root password, does it mean that the next time I use the sudo command, I have to use the new password?
1)No. When you use sudo you are logged in.
2)No. You just set the password for the root account with 'sudo passwd'. The password you use for sudo is your own and it will stay the same until you change that.

> As someone who has a nightly cron job backing up his home dir using rsync, I am wondering what files won't be backed up if I am logged.
I know im doing rsync backup daily AND Im logged in at the same time...it was only an idea...
which now leads me to another idea:

HOW did you copy your homefolder to the drive?

---

### Post by whizbaby on 2007-07-02
Ok, I see. If you want to do more backups of your homedir to that drive in the future you should consider using rsync to speed up (because it will only copy changed and new files, and not whats already there).

---

### Post by greg_g on 2007-07-02
> **whizbaby said:**
> HOW did you copy your homefolder to the drive?

I have a script, this is only part of it (I also backup my sources.list and xorg.conf nightly):
```

rsync -avz --exclude=".beagle/" --exclude=".macromedia/" --exclude=".mozilla/firefox/3utlfqnj.default/Cache" --exclude=".mozilla/firefox/y1vv374x.default/Cache" --exclude=".liferea_1.2/cache" --exclude=".liferea_1.2/mozilla/liferea/Cache/" --exclude=".opera/cache4" --exclude=".opera/opcache" --exclude=".thumbnails" --exclude=".Trash" --exclude=".gnupg/" --exclude=".VirtualBox/VDI/" --exclude="Media/Unsorted/" $HOME/ $BACKUP_HOME >> $CRON_DAILY_LOG

```

As you can see I have a lot of --excludes so I don't backup caches.  Also $HOME is a predefined variable, and I defined $BACKUP_HOME as my external drive backup folder (/media/Contents/Backup/home/greg/) and $CRON_DAILY_LOG is my log file for this.

I hope you were asking me ;)

greg

---

### Post by whizbaby on 2007-07-02
Thx for info greg but I was addressing to quinn :tongue:
Like I said I sync my home whilst logged in, and Im not leaving out any files...
But perhaps rsync is smarter than copy or dragNdrop, so I wanted to know about the first used method.

btw: a one-liner is barely a script, lol, but go on.

---

### Post by greg_g on 2007-07-02
> **whizbaby said:**
> btw: a one-liner is barely a script, lol, but go on.

Right, which is why that one line is only one of many:

```

## My Daily cron script
## Backs up system files used by 
## my Restore script (restore.sh)
##	Xorg.conf
##	sources.list
##
## Also the Backing-up of /home/greg

## Let's set up some script variables
## May seem redundant, but when I change
## the location of something, I only have
## to change one variable. And I know
## where that variable is.

CRON_DAILY_LOG="/home/greg/UserLogs/cron_logs/cron_daily.`date +%Y%m%d`.log"
BACKUP_SCRIPT="/media/Contents/Backup/Script/"
BACKUP_HOME="/media/Contents/Backup/home/greg/"
MUSIC_LOCAL="/home/greg/Media/Music/"
MUSIC_REMOTE="/media/Contents/Backup/home/greg/Media/Music/"
PICTURES_LOCAL="/home/greg/Media/Pictures/"
PICTURES_REMOTE="/media/Contents/Backup/home/greg/Media/Pictures/"
UNSORTED_LOCAL="/home/greg/Media/Unsorted/"
UNSORTED_REMOTE="/media/Contents/Backup/home/greg/Media/Unsorted/"
PODCAST_LOCAL="/home/greg/Media/Podcats/"
PODCAST_REMOTE="/media/Contents/Backup/home/greg/Media/Podcasts/"
DELETE_LABEL="\n\n################################\n#--------Rsync --delete--------#\n# `date` #\n################################"
XORG_LABEL="################################\n#--------Xorg.conf-------------#\n# `date` #\n################################"
SOURCES_LABEL="\n\n################################\n#--------Sources.list----------#\n# `date` #\n################################"
HOME_LABEL="\n\n################################\n#---------Home Folder----------#\n# `date` #\n################################"

## Backup Xorg.conf
echo $XORG_LABEL >> $CRON_DAILY_LOG
rsync -avz --backup --suffix=".`date +%F`" /etc/X11/xorg.conf $BACKUP_SCRIPT >> $CRON_DAILY_LOG

## Backup sources.list
echo $SOURCES_LABEL >> $CRON_DAILY_LOG
rsync -avz --backup --suffix=".`date +%F`" /etc/apt/sources.list $BACKUP_SCRIPT >> $CRON_DAILY_LOG

## What if I just backup /home using one command??
## seems like it will save some work.
## Yes, there are a ton of "--excludes" in it,
## is there a better way?
echo $HOME_LABEL >> $CRON_DAILY_LOG
rsync -avz --exclude=".beagle/" --exclude=".macromedia/" --exclude=".mozilla/firefox/3utlfqnj.default/Cache" --exclude=".mozilla/firefox/y1vv374x.default/Cache" --exclude=".liferea_1.2/cache" --exclude=".liferea_1.2/mozilla/liferea/Cache/" --exclude=".opera/cache4" --exclude=".opera/opcache" --exclude=".thumbnails" --exclude=".Trash" --exclude=".gnupg/" --exclude=".VirtualBox/VDI/" --exclude="Media/Unsorted/" $HOME/ $BACKUP_HOME >> $CRON_DAILY_LOG

## Rsync --delete the directories I want to be exactly the same
echo $DELETE_LABEL >> $CRON_DAILY_LOG
echo "\nMusic\n" >> $CRON_DAILY_LOG
rsync -avz --delete $MUSIC_LOCAL $MUSIC_REMOTE >> $CRON_DAILY_LOG
echo "\nPictures\n" >> $CRON_DAILY_LOG
rsync -avz --delete $PICTURES_LOCAL $PICTURES_REMOTE >> $CRON_DAILY_LOG
echo "\nUnsorted\n" >> $CRON_DAILY_LOG
rsync -avz --delete $UNSORTED_LOCAL $UNSORTED_REMOTE >> $CRON_DAILY_LOG
echo "\nPodcasts\n" >> $CRON_DAILY_LOG
rsync -avz --delete $PODCAST_LOCAL $PODCAST_REMOTE >> $CRON_DAILY_LOG

```

Yes, very basic.  Just multiple rsyncs, with some fancy labels for the log file (I like pretty logs).
And of course, anyone reading this is free to use this.

greg

---

### Post by smo0th on 2007-07-03
i haven't used rsync but just by inserting sudo into the script won't work fully automatic, unless you find a way to insert the password in your batch code too. then if you use sudo, type your pass and run the mod script it should run smoothly.

---

### Post by quinnten83 on 2007-09-07
> **whizbaby said:**
> 1)No. When you use sudo you are logged in.
2)No. You just set the password for the root account with 'sudo passwd'. The password you use for sudo is your own and it will stay the same until you change that.


I know im doing rsync backup daily AND Im logged in at the same time...it was only an idea...
which now leads me to another idea:

HOW did you copy your homefolder to the drive?

Forgive the late reply
I tried with a sudo cp -R command and it copied.
I don't remember exactly what I did to have the disk boot up, but I will check, and get back to you later.

---

