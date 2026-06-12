---
title: "How do I write to FAT32 Partition?"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by TristanMike on 2005-06-19
Ok, a Big-Ole-Thank-You to everyone that has replied to me and others to help smooth the transition from Windon'ts OS.  It's very much appreciated.	:-D

Ok, now the problem...er....issue.....I've installed Ubuntu and done a bit of Entry Level reading, I kinda understand the terminal, a little, sort of........  I kinda understand how to work around in it as well ie. cd - change directory, ls - list, and so on.....  I don't really understand Synaptic, but installed Azureus from it just for the heck of it (well, really cause it was the only thing for me to put a check box in so I figured I couldn't go wrong) and it *seems* to be working but that was a gutsy move on my part as I had and still have, no idea HOW to choose from the 50 choices they give me (exagerating I know, but you get the point).  Now that I've rambled for a minute and gotten myself off track......I have my computer set up like this.

80 GB Drive - Partitions - 3
C: Windon'ts XP (NTFS)
F: FAT32 (No OS - Created for Hosting all of my shared files between the OS's)
ext3: Ubuntu

K, so, I wanna use my FAT32 drive for all of my shared files, which means I wanna both read and write to the FAT32 partition.  Right now, Windon'ts can read/write, but it appears that Linux can only read from it.  I think I read this is defualt for security reasons.  I am the only user on my computer and "security" from other users, at least on my FAT32 drive, is completely unnecissary.  I want to set Firefox to download the stuff there and move it from THERE accordingly, I want to move the downloaded files I have from Linux to the partition, I want to Azureus to download/seed the torrent/files directly from the FAT32 partition, I want, I want, I want, I know it sounds greedy, but well....I'm greedy....he,he,he lol.  But I can't #-o...herein lies the problem.....er....issue.

So I go to the terminal and try to apply the knowlege I've collected and here's what I get.

tristan@ubuntu:~$ cd Desktop
tristan@ubuntu:~/Desktop$ sudo mv Smileys6.exe /windows
Password:
mv: failed to preserve ownership for `/windows/Smileys6.exe': Operation not permitted
tristan@ubuntu:~/Desktop$

Oh yeah, I should say that I obviously tried to just drag and drop the file and I of course got this message:

Error while moving items to "/windows"
You do not have permissions to write to this folder.

Damn!  That didn't work, I even right click/properties the window's folder in the root directory and head over to the permissions tab and everything is greyed out and at the bottom it says "You are not the owner, so you can't change permissions."

So it's the permission thing....I've check around the fourm here and I haven't really found an answer that explained what to do in laymans terms as I'm just kinda, sorta, now grasping some of the concepts of working around the command line/terminal.  So if there is a bunch of code I need to write in the terminal or something that isn't just point and click, could someone please kinda, sorta explain what or why I'm doing what I'm doing.  Or can I even do this, or have I just been waisting my time but improving my typing skills??

Sorry for the long post but I just wanted to show that I've been trying..... ](*,) :-D 

Thank You
TristanMike

---

### Post by tread on 2005-06-19
/dev/hdaWhatever       /media/mountPointName  vfat    umask=000       0       0

Try sticking the above in your fstab, modifying the hdaWhatever and mountPointName to suit your need.
The message about not being able to preserve ownership is because fat32 does not have the concept of users owning files or permissions .. 

Hope that helps. 
Most of this is listed at [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs).
Cheers!

---

### Post by TristanMike on 2005-06-19
Thanks for the quick response but I don't understand a word of what you just said.........wait....no, I just looked at that site, but I still don't understand what "mount/unmount" means. I mean, I have a windows folder in the root, it's not a seperate Physical drive, and I can put stuff in it when I'm in XP, I guess I can read from it in Linux, cause I can listen to the music that I have there.  But what if I download music with Azureus in Linux, and wanna move it into that folder so I can set it to my Window's Media Player Library as well as my Linux Music player library, for example.

Is there no way that the /windows folder can let me drop stuff in it?  Remember, ONE drive, 3 Partitions...

Thank You Very Much
TristanMike

---

### Post by tread on 2005-06-19
Ok, lets do this one step at a time:

Open a terminal, and type:
sudo fdisk -l /dev/hda

Edited to add: what this does is lists all the available partitions on the harddrive .. since you have just one harddrive, it will be hda. If there were two, the second would be hdb .. and so on.

---

### Post by TristanMike on 2005-06-19
Thank You for helping the ignorant........ :oops:

tristan@ubuntu:~$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        7637    20386485    5  Extended
/dev/hda3            7638        9733    16836120   83  Linux
/dev/hda5            5100        7543    19631398+   b  W95 FAT32
/dev/hda6            7544        7637      755023+  82  Linux swap / Solaris
tristan@ubuntu:~$

Nice command, thanks, gonna write that one down.........

---

### Post by tread on 2005-06-19
Ok, so hda5 is the one we want to mount for read-write access.
Now, we can do this from the commandline, or set it up permanently. Lets try for the latter.

The file to edit is /etc/fstab.
You can see the contents with:

cat /etc/fstab

If there is an entry about hda5, we need to modify that for our requirement, or add one if there isn't. Try the command, and post the result here.

---

### Post by tread on 2005-06-19
Darn, I have to leave now. Let me just finish this.
Like I said before, we have to edit /etc/fstab

First: make a backup.
sudo cp /etc/fstab /etc/fstab.bak

Then open the file for editing:
sudo gedit /etc/fstab

Now, if there is an entry for hda5, modify that otherwise add a new one. It should look something like this:

/dev/hda5 /media/windows32 vfat umask=000 0 0

The /media/windows32 is the directory where the partition will be mounted, you can modify it if you want.
Hope that helps!

---

### Post by TristanMike on 2005-06-19
Ok.......another one for the yellow sticky note.......

tristan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /windows        vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tristan@ubuntu:~$

..........

---

### Post by TristanMike on 2005-06-19
NOOOOOOOOO!!!

tristan@ubuntu:~$ sudo /etc/fstab /etc/fstab.bak
Password:
sudo: /etc/fstab: command not found
tristan@ubuntu:~$ sudo /etc/fstab /etc/fstab.bak
sudo: /etc/fstab: command not found
tristan@ubuntu:~$

Gulp........

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]NOOOOOOOOO!!!

tristan@ubuntu:~$ sudo /etc/fstab /etc/fstab.bak
Password:
sudo: /etc/fstab: command not found
tristan@ubuntu:~$ sudo /etc/fstab /etc/fstab.bak
sudo: /etc/fstab: command not found
tristan@ubuntu:~$

Gulp........[/QUOTE]
 OK the syntax is incorrect. By typing 'sudo /etc/fstab /etc/fstab.bak' you are, in effect, trying to run '/etc/fstab' as root (sudo) with the perameter '/etc/fstab.bak'. fstab is a configuration file, not a program to run... 

Try this:

 In the terminal, type 'sudo gedit' - runing the gnome text editor as root. In that program go and open your fstab file in the /etc directory. Modify it to what you need and save it. Close gedit and then at the terminal first type 'sudo mkdir /windows' (if you haven't done so already), and then 'sudo mount -a'. That should mount all the entries in your fstab file. if all goes well there should be no messages. navigate to /windows and go 'ls'. This is a bit of a 'windows' way to go about things but it's good for beginners. See how you go.

---

### Post by TristanMike on 2005-06-19
Thanks m8, I though something was wrong, considering it didn't work....lol.....anyway.

I actually got it open, I just went to the directory and created a copy there and entered to edit it there as well.  What I don't understand is, do I just copy and paste the text above, as is, right to the bottom of the file and save like that, or replace another line, or what?  Do I have to line up the "categories" with the ones that are there currently or leave it as I said, as is?

Thank You
TristanMike

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Thanks m8, I though something was wrong, considering it didn't work....lol.....anyway.

I actually got it open, I just went to the directory and created a copy there and entered to edit it there as well.  What I don't understand is, do I just copy and paste the text above, as is, right to the bottom of the file and save like that, or replace another line, or what?  Do I have to line up the "categories" with the ones that are there currently or leave it as I said, as is?

Thank You
TristanMike[/QUOTE]
 The line that says '/dev/hda5 /windows vfat defaults 0 0' needs to be modified. Replace the 'defaults' with 'umask=000'. then run 'sudo mount -a" again. By the way - have you been directed to [http://ubuntuguide.org/](http://ubuntuguide.org/) yet? There's a section on just what you're trying to do and almost anything else you may want to do as well ;-)

---

### Post by TristanMike on 2005-06-19
So it looks something like this.....

/dev/hda5       /windows        vfat    umask=000 0 0

or...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /windows        vfat    umask=000 0 0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And as for the website you asked me about, yes I've been there, and I've actually made a post about how I don't find it useful if I want to know what and why I'm doing instead of copy and pasting and just accepting it. ([http://www.ubuntuforums.org/showthread.php?t=42833](http://www.ubuntuforums.org/showthread.php?t=42833))  I really want to get into Linux so knowing the details of the steps is helpful, perhaps they need a glossary or something to help clairfy a few things.

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]So it looks something like this.....

/dev/hda5       /windows        vfat    umask=000 0 0

or...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /windows        vfat    umask=000 0 0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And as for the website you asked me about, yes I've been there, and I've actually made a post about how I don't find it useful if I want to know what and why I'm doing instead of copy and pasting and just accepting it. ([http://www.ubuntuforums.org/showthread.php?t=42833](http://www.ubuntuforums.org/showthread.php?t=42833))  I really want to get into Linux so knowing the details of the steps is helpful, perhaps they need a glossary or something to help clairfy a few things.[/QUOTE]
 Ahh, now there's a can of worms! At a terminal, type 'man command' where 'command' is the part you want to know about - e.g. 'man mount' or 'man fstab' or 'man man'! 'man' displays the manual; for that command. The problem is, it's usually either cryptic or painfully verbose. This is where google is your friend... Good luck and 'down the rabbit hole' you go!  :wink:

---

### Post by TristanMike on 2005-06-19
Ok, so I saved the file as above and typed sudo mount -a and it prompted me for a password, i entered it, and it brought me back to my directory, nothing happend, like you said.  I -ls the /windows directory and there was something in there that I had tried to put in to it earlier, no prob.  So for a test I tried to move 2 files from my desktop and with a little delay and a bit of confusion, I ended up with the two files in the windows directory.  I think ok, so I try something else, and I end up with the same permissions error.....

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Ok, so I saved the file as above and typed sudo mount -a and it prompted me for a password, i entered it, and it brought me back to my directory, nothing happend, like you said.  I -ls the /windows directory and there was something in there that I had tried to put in to it earlier, no prob.  So for a test I tried to move 2 files from my desktop and with a little delay and a bit of confusion, I ended up with the two files in the windows directory.  I think ok, so I try something else, and I end up with the same permissions error.....[/QUOTE]
 go 'ls -l'. That'll show you the ownersip and permissions etc of the files and may give you a clue where the problem is. Linux is very particular about ownership and permissions of files and directories.

---

### Post by TristanMike on 2005-06-19
tristan@ubuntu:/windows$ ls -l
total 528
-rwxr-xr-x   1 root root 164401 2005-06-14 17:01 bookmarks.html
drwxr-xr-x   2 root root  16384 2005-06-15 22:49 Recycled
-rw-r--r--   1 root root 147393 2005-06-19 14:28 Smileys6.exe
drwxr-xr-x   3 root root  16384 2005-06-15 21:57 System Volume Information
drwxr-xr-x  13 root root  16384 2005-06-17 01:27 Temp Music
-rw-r--r--   1 root root 158720 2005-06-19 14:26 xxxsmileys_v6.exe
tristan@ubuntu:/windows$

Does this mean it's been locked off cause it's root?  How do I stay in "root" mode, I'm the only user of this comp. or is it unadvised cause I can break my machine?  How do I  get "owner" rights?

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]tristan@ubuntu:/windows$ ls -l
total 528
-rwxr-xr-x   1 root root 164401 2005-06-14 17:01 bookmarks.html
drwxr-xr-x   2 root root  16384 2005-06-15 22:49 Recycled
-rw-r--r--   1 root root 147393 2005-06-19 14:28 Smileys6.exe
drwxr-xr-x   3 root root  16384 2005-06-15 21:57 System Volume Information
drwxr-xr-x  13 root root  16384 2005-06-17 01:27 Temp Music
-rw-r--r--   1 root root 158720 2005-06-19 14:26 xxxsmileys_v6.exe
tristan@ubuntu:/windows$

Does this mean it's been locked off cause it's root?  How do I stay in "root" mode, I'm the only user of this comp. or is it unadvised cause I can break my machine?  How do I  get "owner" rights?[/QUOTE]
 Yup. You should be able to move files to /windows without the 'sudo' command. Using 'sudo' will create the files as owner 'root' as you can see above. You can change the ownership back by using the 'chown' command e.g. 'sudo chown tristan:tristan /windows/*.*' The first 'tristan' us the user and the second 'tristan' is the group you belong to. The *'s are wildcards like in windows. It is unadvisable to remain as root even though you can do it (sudo -s) it's easy to forget that you are root and cause MAJOR headaches for yourself in the future. In most cases the files you want to work with are owned by you so there should be no problems. I'd like to say here that as a budding Linux user you will be served well by learning about ownership, permissions and how to manipulate them. You will encounter these issues very often.

---

### Post by tread on 2005-06-19
Hehe .. looks like in my hurry I forgot to put 'cp' which is the unix command for 'copy'. I'm really sorry about that .. thanks for taking up the thread chaumurky.

---

### Post by TristanMike on 2005-06-19
Good to know.

Ok, I tried from the website and this is what it spit back to me

tristan@ubuntu:~$ sudo mkdir /media/windows
tristan@ubuntu:~$ sudo mount /devsudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
tristan@ubuntu:~$

uh.....does this mean it's been mounted?  If so, will I find this directory in /media/windows?  If so, is this where all of my sharing comes from, this is where I put all of my files that I want to share between Linux and XP? not the /windows directory?

---

### Post by tread on 2005-06-19
>  sudo mount /devsudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000 

This should be 

sudo mount /dev/hda(5?-CHECK) /media/windows -t vfat -o umask=000

You can see all the currently mounted partitions by typing:
mount

Incidentally, werent you trying to mount hda5? I'm confused now :D

---

### Post by TristanMike on 2005-06-19
See, it's this "mounting" thing that's confusing me.  I have the drive partitioned to the XP part, the FAT32 part and the Linux part, and I'm trying to be able to read/write to the F32 partition so that downloaded files can be used whether I boot in XP or Linux, I don't understand why the F32 partition, which has nothing to do with Linux, won't let me write to it, and yes, hd5 is what I guess I'm trying to "mount".

EDIT: oh, I see, I typed in 1 and not 5, see, that's what I mean about how I can mess up by just copy/paste.....lol

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Good to know.

Ok, I tried from the website and this is what it spit back to me

tristan@ubuntu:~$ sudo mkdir /media/windows
tristan@ubuntu:~$ sudo mount /devsudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
tristan@ubuntu:~$

uh.....does this mean it's been mounted?  If so, will I find this directory in /media/windows?  If so, is this where all of my sharing comes from, this is where I put all of my files that I want to share between Linux and XP? not the /windows directory?[/QUOTE]
 It's a bit confusing, I know. From a windows perspective you can mentally replace what would have been a drive letter with (in this case) '/windows'. It's kinda like a placeholder. In windows, partitions are mounted automatically at boot without user intervention. In linux it has to be specified in the 'fstab' configuration file for that to occur. On boot, those devices/partitions listed will be mounted in the same way as if you ran the 'mount' command manually - but automagically. So if it's in the fstab you don't need to run 'mount' (unless, in our case we modified the fstab so we then ran 'mount -a' instead of rebooting - one of the nice things about linux :). Now, if the partition has a directory called '/files' you go there by 'cd /windows/files'. In windows it'll be 'd:\files' or whatever. Make sense?

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]It's a bit confusing, I know. From a windows perspective you can mentally replace what would have been a drive letter with (in this case) '/windows'. It's kinda like a placeholder. In windows, partitions are mounted automatically at boot without user intervention. In linux it has to be specified in the 'fstab' configuration file for that to occur. On boot, those devices/partitions listed will be mounted in the same way as if you ran the 'mount' command manually - but automagically. So if it's in the fstab you don't need to run 'mount' (unless, in our case we modified the fstab so we then ran 'mount -a' instead of rebooting - one of the nice things about linux :). Now, if the partition has a directory called '/files' you go there by 'cd /windows/files'. In windows it'll be 'd:\files' or whatever. Make sense?[/QUOTE]

Yes, /windows is just what I thought it was, - f:\.  That I'm cool with.  Understanding that XP does it behind the curtain with out me instructing it, that's good too, I didn't get that before.  Now to be able to drop files from my desktop, lets say, to the /windows directory without having to sudo it everytime.....here's where I'm at:

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Yes, /windows is just what I thought it was, - f:\.  That I'm cool with.  Understanding that XP does it behind the curtain with out me instructing it, that's good too, I didn't get that before.  Now to be able to drop files from my desktop, lets say, to the /windows directory without having to sudo it everytime.....here's where I'm at:[/QUOTE]
 Perhaps the '/windows' directory's ownership needs to be changed not just the files? i.e. 'sudo chown tristan:tristan /windows'. If you own the folder you can write to it (and it's mounted drive).

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]Perhaps the '/windows' directory's ownership needs to be changed not just the files? i.e. 'sudo chown tristan:tristan /windows'. If you own the folder you can write to it (and it's mounted drive).[/QUOTE]

Yes, yes, ownership, that's it......

Ok, so 
/dev/hda5 /media/windows32 vfat umask=000 0 0 
is to replace
/dev/hda5       /windows        vfat    defaults        0       0
Even if though I have a /windows directory?

Then after I save this changed file, type 
sudo mount -a
then
sudo chown tristan:tristan /windows

I think we may have a winner.......

---

### Post by chaumurky on 2005-06-19
[QUOTE=chaumurky]Perhaps the '/windows' directory's ownership needs to be changed not just the files? i.e. 'sudo chown tristan:tristan /windows'. If you own the folder you can write to it (and it's mounted drive).[/QUOTE]
 By the way, creating folders off root, while possible is, again, not recommended. There is a structure that should be adhered to and mounted partitions usually are made in /mnt or /media. It doesn't affect useability but helps reduce clutter. Also, when you get this sorted out, why don't you create a link to your mounted drive in your /home/tristan directory. Just go 'ln -s /windows /home/tristan/windows'.

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]By the way, creating folders off root, while possible is, again, not recommended. There is a structure that should be adhered to and mounted partitions usually are made in /mnt or /media. It doesn't affect useability but helps reduce clutter. Also, when you get this sorted out, why don't you create a link to your mounted drive in your /home/tristan directory. Just go 'ln -s /windows /home/tristan/windows'.[/QUOTE]

I didn't create the directory, it was there after installation of Ubuntu, I created it during the partition stage of setup with the FREE SPACE I had.  And if all files are suppose to go into the /media directory, does this equate to F:\ in windows?  My goal, if possible even, is to have downloads/uploads in the same directory for XP and Linux, so they could "share".

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]I didn't create the directory, it was there after installation of Ubuntu, I created it during the partition stage of setup with the FREE SPACE I had.  And if all files are suppose to go into the /media directory, does this equate to F:\ in windows?  My goal, if possible even, is to have downloads/uploads in the same directory for XP and Linux, so they could "share".[/QUOTE]
 Oh, yeah, it doesn't matter where you mount it in Linux - in Windows it'll always be F:\ - like I said, it's just a placeholder. During the install you do actually get an option to mount it wherever you like. Some distros are more liberal than others and quite possibly may have suggested /windows. In reality, as a home PC, it doesn't really matter (well almost - don't mount it in /proc or /tmp ;-) In Linux 'directories' can be more than just windows style 'directories' as you're starting to discover...

---

### Post by TristanMike on 2005-06-19
Ok chaumurky, what I'm confused at is what seems to be a contradiction, but I'm probably just misunderstanding, but it is what tread said: (huh, that rhymes)
> Now, if there is an entry for hda5, modify that otherwise add a new one. It should look something like this:

/dev/hda5 /media/windows32 vfat umask=000 0 0
and what I thought you meant...
> The line that says '/dev/hda5 /windows vfat defaults 0 0' needs to be modified. Replace the 'defaults' with 'umask=000'. then run 'sudo mount -a" again.

Do I keep everything before "unmask...." or change it, please look at my comment #26 and let me know which is the correct proceedure.

Thank You All
TristanMike

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Ok chaumurky, what I'm confused at is what seems to be a contradiction, but I'm probably just misunderstanding, but it is what tread said: (huh, that rhymes)

and what I thought you meant...


Do I keep everything before "unmask...." or change it, please look at my comment #26 and let me know which is the correct proceedure.

Thank You All
TristanMike[/QUOTE]
 tread made the assumption you were mounting to '/media/windows32'. You're using /windows so that's what you should use. Your complete line should be:

'/dev/hda5 /windows vfat umask=000 0 0'

---

### Post by TristanMike on 2005-06-19
So after I copy/paste that line, put it into fstab, save, close, I use the following two commands....

sudo mount -a
then
sudo chown tristan:tristan /windows
 Thanks For all your help and patience everyone.

EDIT: I tried it and got this.

tristan@ubuntu:~$ sudo mount -a
tristan@ubuntu:~$ sudo chown tristan:tristan /windows
chown: changing ownership of `/windows': Operation not permitted
tristan@ubuntu:~$

but when I use the mount command I get this...

tristan@ubuntu:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda5 on /windows type vfat (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=tristan)
/dev/hdd on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=tristan)

does the (rw) mean read/write?  Do I need Samba installed?

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]So after I copy/paste that line, put it into fstab, save, close, I use the following two commands....

sudo mount -a
then
sudo chown tristan:tristan /windows
 Thanks For all your help and patience everyone.

EDIT: I tried it and got this.

tristan@ubuntu:~$ sudo mount -a
tristan@ubuntu:~$ sudo chown tristan:tristan /windows
chown: changing ownership of `/windows': Operation not permitted
tristan@ubuntu:~$

but when I use the mount command I get this...

tristan@ubuntu:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda5 on /windows type vfat (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=tristan)
/dev/hdd on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=tristan)

does the (rw) mean read/write?  Do I need Samba installed?[/QUOTE]
 Hmm, maybe you can't change the permissions while the partition is mounted. Try:

'sudo umount /windows'

then

'sudo chown tristan:tristan /windows'

and finally

'sudo mount -a'

---

### Post by TristanMike on 2005-06-19
tristan@ubuntu:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy
tristan@ubuntu:~$

hmmmmm, what did I do?  I only have Firefox open....

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]tristan@ubuntu:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy
tristan@ubuntu:~$

hmmmmm, what did I do?  I only have Firefox open....[/QUOTE]
 clutching at straws here. go:

sudo sync

then the other commands.

---

### Post by tread on 2005-06-19
Even if you are running a terminal and are in /windows, it will show up as busy. I think :)

---

### Post by TristanMike on 2005-06-19
Try this one...

tristan@ubuntu:~$ sudo unmount /windows
Password:
sudo: unmount: command not found
tristan@ubuntu:~$

havin fun yet? ](*,)

---

### Post by chaumurky on 2005-06-19
[QUOTE=chaumurky]clutching at straws here. go:

sudo sync

then the other commands.[/QUOTE]
 If that doesn't work, open /etc/fstab as root (sudo gedit /etc/fstab) and put a '#' before the line we're working with so it looks like:

#/dev/hda5 /windows vfat umask=000 0 0

Save it and reboot. What we're doing here is commenting out the line so it doesn't mount on reboot. Once rebooted, open a terminal and do the chown line as above, go back to the fstab and remove the comment symbol '#'. Save it and then go 'sudo mount -a' at the terminal. Phew!!

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]Try this one...

tristan@ubuntu:~$ sudo unmount /windows
Password:
sudo: unmount: command not found
tristan@ubuntu:~$

havin fun yet? ](*,)[/QUOTE]
 umount, not unmount...

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]umount, not unmount...[/QUOTE]

 #-o d'oh! :???: mmmm, need coffee, long time.......

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]#-o d'oh! :???: mmmm, need coffee, long time.......[/QUOTE]
 LOL! We all do it. Why the hell isn't it unmount anyways?!? That would make too much sense ;-)

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]Hmm, maybe you can't change the permissions while the partition is mounted. Try:

'sudo umount /windows'

then

'sudo chown tristan:tristan /windows'

and finally

'sudo mount -a'[/QUOTE]

DING, DING, DING, DING, DING!!!!!! LADIES AND GENTLEMEN, WE HAVE A WEINER!!!!!!! :p  :p  :p

That's it, it did it.  I can now copy files to the /windows directory. Hopefully it'll stick, but now I know and there's a pretty detailed thread about this now for all the noobs like me who are having trouble, maybe I'll make a quick laymens guide to this, if someone might check it over when I'm done, I might typo or something, yeah, sure, me, typo, that'll be the day.  :) 

THANK YOU EVERYONE!!!  Thank you for your support, training, and experience, (oh, yeah, and quick eyes....*chaumurky* :wink: ) I will do everything I can to pass on the knowledge you have all given me and sorry for taking up such a large part of everyone's time.

TristanMike  :)  :)

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]DING, DING, DING, DING, DING!!!!!! LADIES AND GENTLEMEN, WE HAVE A WEINER!!!!!!! :p  :p  :p

That's it, it did it.  I can now copy files to the /windows directory. Hopefully it'll stick, but now I know and there's a pretty detailed thread about this now for all the noobs like me who are having trouble, maybe I'll make a quick laymens guide to this, if someone might check it over when I'm done, I might typo or something, yeah, sure, me, typo, that'll be the day.  :) 

THANK YOU EVERYONE!!!  Thank you for your support, training, and experience, (oh, yeah, and quick eyes....*chaumurky* :wink: ) I will do everything I can to pass on the knowledge you have all given me and sorry for taking up such a large part of everyone's time.

TristanMike  :)  :)[/QUOTE]
 You're welcome. Believe it or not, i'm still on the steep learning curve too and this thread helped me solidify and trust what I've learnt so far so we both win from this. Hopefully what you learnt here makes your next steps easier as well. :)

---

### Post by rla128 on 2005-06-21
[QUOTE=chaumurky]You're welcome. Believe it or not, i'm still on the steep learning curve too and this thread helped me solidify and trust what I've learnt so far so we both win from this. Hopefully what you learnt here makes your next steps easier as well. :)[/QUOTE]
 So, I just also went through all of this, and it FINALLY WORKS.

I didn't see this on the ubuntu guide.

This _REALLY_ needs to be in the guide, so others like myself don't have to wade through these forums to find the somewhat simple instructions:

comment out the command to mount the drive by running 'sudo gedit /etc/fstab' and putting # before the line of the drive.  also, change 'default' to 'umask=000' before saving

restart

run 'sudo chown user:user /drive'

uncomment the line in fstab

run 'sudo mount -a'


Again, really needs to put laid out like that somewhere.

---

### Post by chaumurky on 2005-06-21
[QUOTE=rla128]So, I just also went through all of this, and it FINALLY WORKS.

I didn't see this on the ubuntu guide.

This _REALLY_ needs to be in the guide, so others like myself don't have to wade through these forums to find the somewhat simple instructions:

comment out the command to mount the drive by running 'sudo gedit /etc/fstab' and putting # before the line of the drive.  also, change 'default' to 'umask=000' before saving

restart

run 'sudo chown user:user /drive'

uncomment the line in fstab

run 'sudo mount -a'


Again, really needs to put laid out like that somewhere.[/QUOTE]
 That commenting out business shouldn't have been necessary - nor a restart. If, for example, we had /dev/hda5 mounted to /windows - a simple 'umount /windows' should unmount it as long as there are no processes using it at the time. The "drive busy" issue was what forced me to suggest the above option.

---

### Post by rla128 on 2005-06-24
I had the same problem, though.

---

### Post by ign on 2005-07-09
hello to all, i'm new to linux and have been able to make a lot of things work thanks to the people in this formus.
i mounted my fat32 partition in the way described on [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)
so i added this line to fstab:

/dev/hda5	/media/data	vfat	iocharset=utf8,umask=000	0	0

on boot i can see an error related to the "iocharset=utf8" part, can somebody explain me what it stands for and if it would be ok to delete it?

thx

EDIT: actually it's not an error, it only says utf8 charset may not be a good system for the fat32 partition becuase it wull be case sensitive. i think that's all.

---

