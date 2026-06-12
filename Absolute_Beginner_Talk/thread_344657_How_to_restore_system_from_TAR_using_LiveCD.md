---
title: "How to restore system from TAR using LiveCD"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-23
EDIT: the restoring works but the system freezes after login and I get an error message for xsession, see post#9


Hi,

recently I did a ghost image of my Ubuntu system with Norton Ghost 2003. I could restore it but Ghost messed up the filesystem. Anyway I could boot into Ubuntu and I created a backup file of the whole system in a TAR file following this HowTo: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

I copied the backup on an external USB drive and now I'd like to boot on a LiveCD so that I can reformat the Ubuntu partition with Ext3 and then restore the system from the TAR file. My problem is that when booting from the LiveCD the Ubuntu partition where I want to restore the system is not mounted and I don't really know how to copy the file back on it from the TAR. The HowTo proposes to type the following command to restore the system from the TAR file backup.tgz:
tar xvpzf backup.tgz -C /

However on the LiveCD how does the system know where to untar the file content???? I guess that when using the LiveCD, the / refers to the root of the LiveCD and not the partition where I want to untar the files???? All this is a bit confused for me.

Basically my tar file is /media/BACKUP/backup.tgz. I want to untar it on an unmounted partition which is /dev/hda1. Could you please tell me how to proceed and which command I should use to achieve this??

I think that I'll use this TAR method to backup the whole system in the future. I prefer this solution over PartImage. However usually I like to reformat the partition before restoring to start on a clean filesystem, so I'll have to always restore from the LiveCD.

Thanks

---

### Post by kilou on 2007-01-23
I was thinking of mounting /dev/hda1 as /media/restore and untarring the archive on /media/restore. Then if I reboot the system should boot be restored....:confused:

---

### Post by po0f on 2007-01-23
kilou,

You are correct, you will have to mount your root partition and give that as an argument to tar's -C option.  You will have to mount any other partitions you have set up as well before extracting the archive.  Do you have a separate /home or /boot or any other partition?

---

### Post by kilou on 2007-01-23
po0f, I have 2 other partitions on my harddrive but they are not part of the linux filesystem. One is for my XP install and the other is a shared data partition (it's not /home nor is it linked to /home). These 2 other partitions are normally mounted in /media but since I'm excluding the media directory in the archive, I guess it is not required to mount them. Basically the whole filesystem (everything that is in /, except media) is mounted on hda1.

I tried to restore the system from the archive and it seemed to work i.e. I could boot again and reach the login screen. However when I attempt to login I get an error message that warns of possible system errors. I checked the details and found something as "mkdtemp: permission denied" somewhere. I don't know what this means. Using a Gnome failsafe session also makes the system freeze and I cannot reach the desktop.

Here is the list of the directories I have excluded from the archive:
/proc
/lost+found
/media (since I create the backup archive on an external USB drive, excluding media also excludes the backup file itself, which is obviously good)
/mnt
/tmp
/sys
/var/cache
/var/tmp
/var/crash

Of course while on the LiveCD, after having untarred the archive and before rebooting, I recreated all those folders (lost+found was already created when I mounted the hda1 partition). To do this I used mkdir <foldername as above> in the terminal on the LiveCD. I'm unsure if the freezing at login is because of folder permission issues (I created these folder from the LiveCD so I don't know if the permissions are correct afterwards....)

Any clue why the system hang after login??? Should I not exclude these folders (especially I'm unsure if I should exclude sys and proc...)???

Thanks

---

### Post by po0f on 2007-01-23
kilou,

When you extracted the backup, did you use tar's -p option?  What it does is preserve the permissions of the original files when extracting.  The man page says that -p is the default if run as root, but I don't know if the user the live CD sets up has root privileges (it should, I would guess).

[EDIT]

Yeah, it's good to exclude /sys and /proc from your backups; /proc is a representation of the kernel's memory (probably could have worded this better), and /sys is a way to control the kernel.

---

### Post by kilou on 2007-01-23
po0f, yes I did use the p option to create the tar. Here is the command I used to backup the system:

tar cvpzf /media/backup/backup.tgz --exclude=/proc  --exclude=/lost+found  --exclude=/media  --exclude=/mnt  --exclude=/tmp  --exclude=/sys  --exclude=/var/cache  --exclude=/var/tmp  --exclude=/var/crash /

I excluded /var/cache and I wonder if this could be the problem??? I think most people exclude /var/cache/apt but not the whole /var/cache. However I can't understand why this would cause a problem after login. I think the error message I got right after login mentionned a problem in /etc/gdm but this had been backed up correctly....

Weird

---

### Post by po0f on 2007-01-23
kilou,

What was the command used to *extract* (untar) the backup?

---

### Post by kilou on 2007-01-24
What I did is to mount my Ubuntu partition (after having reformatted it in Ext3 with GParted) on /media/restore. Then I untarred the file this way:

tar xvpzf /media/backup/backup.tgz -C /media/restore/

and rebuilt the excluded folders from the terminal of the LiveCD by doing:
mkdir /proc
mkdir /lost+found
mkdir /media
mkdir /mnt
mkdir /tmp
mkdir /sys
mkdir /var/cache
mkdir /var/tmp
mkdir /var/crash

---

### Post by kilou on 2007-01-24
I tried again without excluding the /var/cache folder but still get the same error right after login. Here is what it says:

/.xsession-error file
-----------------------------
/etc/gdm/PreSession/Default: registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/X11R6/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/ :0.Xservers" -h "" -l ":0" "kilou"

/etc/gdm/Xsession: Beginning session setup...

mkdtemp: private socket dir: Permission denied



For me the problem lies with the permissions on folders that were recreated after having excluded them from the backup (like /tmp and others). I recreated them as root but from the LiveCD. When logged as root on the LiveCD, the terminal displays root@ubuntu while it is root@kilou-laptop when logged as root on my Ubuntu system. To me the problem may thus be the computer name which is ubuntu on the LiveCD and kilou-laptop on my system. When I do the tar archive, all included folders get backed up with their own permissions (-p option of tar). Folders with root permissions probably refer to root@kilou-laptop. However when I create the excluded folders on the LiveCD, I create those with root@ubuntu permissions and NOT with root@kilou-laptop. Therefore I guess that after login the system needs to write to one of these recreated folders and cannot do that because the owner is root@ubuntu while it should be root@kilou-laptop.

A bit difficult to explain but I guess this is my problem. Now I have no idea how it is possible to recreate excluded folders from the LiveCD and giving them a permission of root@kilou-laptop instead of root@ubuntu. One other solution would be to only exclude the content of these folders but not the folders themselves! This would preserve their permissions and would avoid the need to recreate them from the LiveCD.

Is there a way to create the tar archive and excluding only the content of some folders but not the folders themselves?? For now the --exclude=/tmp option will remove the whole /tmp folder from the archive but what I'd like is only remove its content while leaving /tmp as an empty folder in the archive. I tried with --exclude=/tmp/* or --exclude=/tmp/*.* but this doesn't seem to work. Any way to do it???

---

### Post by Malac on 2007-01-24
> **kilou said:**
> What I did is to mount my Ubuntu partition (after having reformatted it in Ext3 with GParted) on /media/restore. Then I untarred the file this way:

tar xvpzf /media/backup/backup.tgz -C /media/restore/

and rebuilt the excluded folders from the terminal of the LiveCD by doing:
mkdir /proc
mkdir /lost+found
mkdir /media
mkdir /mnt
mkdir /tmp
mkdir /sys
mkdir /var/cache
mkdir /var/tmp
mkdir /var/crash
Just to double check. From the LiveCD you  would have to use:
mkdir /media/restore/proc
mkdir /media/restore/lost+found
mkdir /media/restore/media
mkdir /media/restore/mnt
mkdir /media/restore/tmp
mkdir /media/restore/sys
mkdir /media/restore/var/cache
mkdir /media/restore/var/tmp
mkdir /media/restore/var/crash
Otherwise you are making them in the LiveCD system.

---

### Post by kilou on 2007-01-24
You're right Malac. I made that, just wrote it down wrong here. I checked with nautilus in /media/restore and all the excluded folders were recreated but this doesn't solve the problem. I tried to change the computer name in the LiveCD to kilou-laptop (the computer name of my backed up system) and recreating these excluded folders but it still doesn't work :( I can't understand what is the problem. It certainly is related to a permission somewhere since this is what is written on the error message (mkdtemp) but I can't figure out where does the problem come from.

---

### Post by kvonb on 2007-01-24
Erm, just my 2 cents:

you DID use sudo to create those folders?

eg:

sudo  mkdir /media/restore/proc
etc'

I know some files in the (/media/restore)/tmp folder cause problems, maybe look at those, ie delete (or rather move to a backup location) all the files in there and see if it makes a difference!

Also I believe the .xsession file in your home folder will need deleting, it's a sort of "lock" file.  I don't know the exact thing to do, maybe search the forums for ".xsession" and see what turns up.

Good luck, Kev :)

---

### Post by kilou on 2007-01-24
Thanks for your replies. It's slowly getting sorted. Yes I used the sudo command to recreate the folders but the problem definitely lies with permissions. After running sudo chmod 777 -R /media/restore/tmp, I can log in correctly so the problem was definitely with a wrong permission on /tmp.

However I don't like the idea of giving a 777 permission on /tmp and other folders. I would really prefer having these backed up as empty folders with the right permission within the TAR archive. I only changed the permission on /tmp but probably that the other recreated folders may also need another permission. 

The next problem is that my other partitions are not mounted automatically. The system mounts my external USB drive but not the partitions on the same disk. If I mount them manually they only appear in the media folder but not in the "Places" menu :( I guess this is because I excluded the media folder from the TAR archive???

So basically what I'd need is a way to create the archive by excluding** the content** of some folders BUT leave these folders in the archive as empty folders (so that permissions on these folders are backed up). Also the archive should not back up the other mounted volumes (found in media) but these other volumes should be automatically mounted and accessible in "Places" right after restore. Any clue about these??

Thanks

PS: also is there a way to do incremental backups using TAR in the terminal (I don't want to use sbackup or rsync if possible, just the terminal command with tar)

---

### Post by Malac on 2007-01-24
To backup the media folders and thus preserve your permissions on those folders, etc. but without backing up the contents of those partitions. I would first run umount on the devices that are mounted in media.
E.G. on my system I unmount my WinXP disk just before running the backup with: ```
sudo umount /dev/hdb2
```If you don't know what the partitions are check in /etc/fstab and it should tell you, it may have UUID instead of /dev/.

Also I can't remember what command you used to extract the file but there may be a switch you left out to recreate permissions on extracting otherwise it may use the user permissions being run at the time. Not Sure On This Though, Sorry.

---

### Post by kilou on 2007-01-24
> **Malac said:**
> 
Also I can't remember what command you used to extract the file but there may be a switch you left out to recreate permissions on extracting otherwise it may use the user permissions being run at the time. Not Sure On This Though, Sorry.

The tar command used to extract the file can effectively rebuild permissions. The problem is only for the folders I had to manually recreate using mkdir, this is why I'd like to avoid this step and exclude only the content but not the actual folders. Yes for media I may unmount all volumes but it means that I need to know whar are the mounted volumes every time. I'd like to make a script to run these backup steps so it would be easier to just exclude the content of media but leave media as an empty folder with the right permissions. 

Is there really no way in Linux to delete the content of a folder but leave the folder in place??? In windows this would be something as delete folder/*.* (but I think just would just delete files and not subfolders as well, not sure about that).

Also unmounting my other partitions in media before doing the archive would probably prevent them from being autoremounted after restore as well....?

---

### Post by Malac on 2007-01-24
> **kilou said:**
> Also unmounting my other partitions in media before doing the archive would probably prevent them from being autoremounted after restore as well....?
Not if they are still listed in /etc/fstab.
Here is the output of rmdir --help:
```
Usage: rmdir [OPTION]... DIRECTORY...
Remove the DIRECTORY(ies), if they are empty.

      --ignore-fail-on-non-empty
                  ignore each failure that is solely because a directory
                  is non-empty
  -p, --parents Remove DIRECTORY and its ancestors. E.g., `rmdir -p a/b/c' is
                  similar to `rmdir a/b/c a/b a'.
  -v, --verbose output a diagnostic for every directory processed
      --help display this help and exit
      --version output version information and exit
```I think you would need to use something like:
```
rmdir --parents --ignore-fail-on-non-empty *[COLOR=DimGray]<name of folder>[/COLOR]*
```

I've never tried this so don't know if "--ignore-fail-on-non-empty" means it will still delete it or just bypass that folder, sorry.

---

### Post by kilou on 2007-01-24
@Malac

fstab was backed up in the TAR achive and contained my other mounted partitions. However after restoring the system these partitions were not automounted for some reasons. 

Interesting stuff about rmdir. However I'd need something similar to run as an option in the tar command because I need to empty some folders in the archive but not in the actual system itself. The only command seems to be exclude=/folder in the tar command but this completely remove the folder, it doesn't just empty it.

Probably that the TAR way to backup things is to backup some part of the system but not to restore the whole system from a LiveCD (unless including all the folders in the archive). Too bad because I really prefer this TAR way to backup/restore because it could be done on a running system as well, something that PartImage or other softwares can't do (they can backup live but not restore).

---

### Post by Malac on 2007-01-24
> **kilou said:**
> @Malac

fstab was backed up in the TAR achive and contained my other mounted partitions. However after restoring the system these partitions were not automounted for some reasons. 

Interesting stuff about rmdir. However I'd need something similar to run as an option in the tar command because I need to empty some folders in the archive but not in the actual system itself. The only command seems to be exclude=/folder in the tar command but this completely remove the folder, it doesn't just empty it.

Probably that the TAR way to backup things is to backup some part of the system but not to restore the whole system from a LiveCD (unless including all the folders in the archive). Too bad because I really prefer this TAR way to backup/restore because it could be done on a running system as well, something that PartImage or other softwares can't do (they can backup live but not restore).
I think you can also exclude=/folder/*.* or exclude=/folder/*

---

### Post by kilou on 2007-01-24
> **Malac said:**
> I think you can also exclude=/folder/*.* or exclude=/folder/*

I tried this and none seem to work:

exclude=/folder/*.* doesn't exclude anything (all files in folder are in the archive)

exclude=/folder/* is similar as exclude=/folder (the folder itself is also removed)

EDIT: actually exclude=/folder/* seems to create the empty folder because it is listed in the verbose mode. However it does not appear in the tar archive. There is probably a rule somewhere that delete empty folders automatically in a tar....

---

### Post by Malac on 2007-01-25
> **kilou said:**
> There is probably a rule somewhere that delete empty folders automatically in a tar....

There probably is but I'm afraid I have no idea try the tar man page:```
man tar
```
a quick glance gave me this:
```
        --show-omitted-dirs
              mention directories that are being skipped over
```
which may be useful??

---

### Post by kilou on 2007-01-25
I tried that and it doesn't solve the problem :( There must be a way to achieve this otherwise people wouldn't be able to restore the system with a TAR from a Live CD if they excluded some folders (unless recreated those with full permissions...which is not good)

Also I've just seen another issue: the partition on which the backup is copied must be Ext3 and not FAT32 because FAT32 is apparently not able to store permissions. I don't think that was my problem but at least I'll have to reformat my USB disk to Ext3 so that I don't screw up file permissions. What I don't know is if the permissions were restored when I did the restore from the Ghost image because the Ghost image was stored on an FAT32 disk.......

---

### Post by Malac on 2007-01-25
Yeah early Ghost doesn't work with ext3 it sees them as ext2 so mucks up the file permissions completely.
If you first restored from that Ghost image then I'd say you are knackered and a fresh install is what you need to do then open the tar with archive manager and just restore the files you need.

---

### Post by kilou on 2007-01-25
I don't think I got a problem with the Ghost restore because m home folder is owned by myself not by root. If the permission were lost it should have been set too root probably. Also a ghost image stores the filesystem as well so it's likely the image was stored with Ext3 (or at least Ext2) and the permissions were saved. This is the advantage of imaging over TAR for backup. 

Too bad there is no way to not delete the excluded folders in the archive :(

---

### Post by Malac on 2007-01-25
> **kilou said:**
> Too bad there is no way to not delete the excluded folders in the archive :(

GUI is your friend :)
You can delete individual files, groups of files and/or folders using Archive Manager.

---

### Post by kvonb on 2007-01-25
Nothing to say here, just that your Avatar makes me laugh malac, hahahah :)

---

### Post by dtoader on 2007-05-15
I use cpio because tar doesn't archive special files.
I telinit 1, then cpio everything except dev to a gzipped file on an adhoc mounted nfs share.
Then I telinit 6 and resume from there.

---

