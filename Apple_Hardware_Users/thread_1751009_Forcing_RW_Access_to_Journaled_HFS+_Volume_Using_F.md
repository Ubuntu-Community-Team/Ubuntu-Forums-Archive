---
title: "Forcing R/W Access to Journaled HFS+ Volume Using FSTAB?"
date: 2011-05-06
forum: Apple Hardware Users
---

### Post by Nopstnz8 on 2011-05-06
Hey guys... I'm trying to enable read/write access from my Wubi installed Ubuntu 11.04 through bootcamp so I can access my Mac partition. I know you can disable journaling on the Mac side to accomplish this, but there is no way I will do that because I can't afford data loss if my system hangs randomly. After doing some research, I came across this thread:

[http://ubuntuforums.org/showthread.php?t=1723857](http://ubuntuforums.org/showthread.php?t=1723857)


The OP there was able to force read/write support to his journaled HFS+ volume using the FSTAB command. He listed the commands he used to exectute this, but his goal was to access a time machine drive or something, so the second command is slightly different in my case. My problem is I'm not very familiar with FSTAB, and was wondering if anyone could help me with executing the correct command? I believe my Mac partion is in /dev/sda2

If I want to access the entire partition is the next part:

media/username ?

So my home folder name is: corey (Is this case sensitive?)

I understand what the rest of the elements in the command mean, but what does this part mean? 

gid=100 0 0 

Permissions of my folder are 501, so that's correct.

Overall, should my command be:

/dev/sda2 /media/corey  hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 0


Any help would be greatly appreciated. Thanks.

---

### Post by Nopstnz8 on 2011-05-09
Bump. Anyone?

---

### Post by Silmathoron on 2011-05-09
Sorry, I never found a way of writing on a journaled partition... I'm not sure it's possible

---

### Post by pindar on 2011-05-09
> **Nopstnz8 said:**
> I know you can disable journaling on the Mac side to accomplish this, but there is no way I will do that because I can't afford data loss if my system hangs randomly. 

[...]

force read/write support to his journaled HFS+ volume

I have trouble understanding these two parts - you're afraid of data loss, yet want to force writing to a journaled file system? This doesn't seem like a good plan to me. linux doesn't handle the journal of hfsplus, so every time you write to it, OS X would consider the state inconsistent when you boot up. I've disabled the journal on my OS X partition, and apart from the occasional fsck I've never seen bad consequences. I keep frequent backups, however, so YMMV.

---

### Post by Nopstnz8 on 2011-05-09
> **pindar said:**
> I have trouble understanding these two parts - you're afraid of data loss, yet want to force writing to a journaled file system? This doesn't seem like a good plan to me. linux doesn't handle the journal of hfsplus, so every time you write to it, OS X would consider the state inconsistent when you boot up. I've disabled the journal on my OS X partition, and apart from the occasional fsck I've never seen bad consequences. I keep frequent backups, however, so YMMV.

I keep frequent backups too, but if my system were to hang or something while I'm in the middle of a paper and forgot to save, although I save after every pause, I'd lose what I had written, or whatever process I was running. Did you read the thread I posted a link to? The OP there confirms he got it working. I'm just not 100% sure about the correct command to do it myself.

---

### Post by drowsyhaze on 2011-05-13
The line you posted in your first post looks right, just remember to use tabs instead of spaces when you insert the line into FSTAB. Time machine is irrelevant to FSTAB, I was just commenting on netatalk (AFP) implementations of time machine for non HFS+ disks.

FSTAB mounts the disk and nothing else. The UID and GID parameters determine the permissions for user and group respectively. OS X uses UID 501 (for the first user, 502 for the second, so on) and GID 100 by default, so I use those permissions to be sure that everything is accessible from OS X/Ubuntu doesn't lock me out.

Explanation:

1. First parameter is the disk's location - "df -l" in terminal to find your disk's location (/dev/sda2)

2. Second parameter is the volume's mount point - this does not have to be your username, I generally use whatever name you've given the disk (herbert mounts at /media/herbert). Ubuntu mounts HFS+ Journaled even though it can't write to it, so if you go into your /media/ folder you should find a folder already there with whatever name you gave your disk when you formatted it. That said, you can use whatever name you want without any worry as it's just a human readable representation of the disk's location, but I would use the same name you formatted the volume with to avoid confusion.

3. The rest: hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 0
"file system type" "force mounting of file system,authorize read/write,automatically mount at login,allow multiple users,user's id,group's id" "dump check/backup disk?" "disk's place in fsck queue when checking files"

Note: fsck does not work on HFS+, you have to use fsck.hfsplus for all HFS+ volumes. For journaled HFS+ you have to use the force option (fsck.hfsplus -f /dev/sdxx).

Hope this helps and good luck!

Edit: Noticed your question regarding the mount point - almost every system/terminal command is case sensitive.

---

### Post by drowsyhaze on 2011-05-13
Just remembered: the UID and GID should work for you with the "users" option, but I'd recommend doing the following if you're going to be dual-booting:

Login to Ubuntu, open up a terminal, create a temporary user and create a password when prompted
```
sudo useradd -d /home/tempuser -m -s /bin/bash -G admin tempuser
sudo passwd tempuser
```

Logout, login as tempuser, open a a terminal and change the permissions of your home directory
```
sudo usermod --uid 501 yourusername
sudo chown -R 501:yourusername /home/yourusername
```

Your permissions are fine now, but Ubuntu won't show your user ID at the login screen because it's < 1000, so you have to edit the login screen parameters. from terminal:
```
gksudo gedit /etc/login.defs
```
or
```
sudo nano /etc/login.defs
```
search for "UID_MIN" and change "1000" to "501"

Log out, login as normal user, and delete tempuser.
```
sudo userdel -r tempuser
```

Ripped from/More info: [http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by srs5694 on 2011-05-13
> **drowsyhaze said:**
> The line you posted in your first post looks right, just remember to use tabs instead of spaces when you insert the line into FSTAB.

The /etc/fstab file (note that it's lowercase; Linux filesystems are case-sensitive) supports either spaces or tabs between its elements, so use whichever you like.

> The UID and GID parameters determine the permissions for user and group respectively. OS X uses UID 501 (for the first user, 502 for the second, so on) and GID 100 by default, so I use those permissions to be sure that everything is accessible from OS X/Ubuntu doesn't lock me out.This is somewhat true for filesystems that don't support Unix-style permissions, such as FAT, NTFS, or the pre-X HFS; however, HFS+ does support Unix-style permissions. Thus, for the most part this parameter has no effect. The documentation for hfsplus (in /usr/src/linux/Documentation/filesystems/hfsplus.txt, if you've installed the kernel source) does say that these options have an effect for "all files on the filesystem that have uninitialized permissions structures." I'm not sure what files would qualify for that designation. In a quick check, I couldn't find any on an OS X disk.

Also, for non-Unix filesystems, your interpretation is backwards; these options set the UID and GID values *in Linux*.

Overall, these options seem to have no practical effect, at least not in quick tests I've performed. If I understood what files might have uninitialized permissions, I might have a better idea of when they might have an effect, but I suspect that's in some pretty obscure circumstances.

For properly matching Linux/OS X file ownership, you need to coordinate your UIDs, and ideally also your GIDs, between the two OSes. Since OS X normally gives the first user a UID of 501, this would mean giving the same user a UID of 501 in Ubuntu (or changing the OS X UID appropriately). You can do this in Ubuntu by using the usermod command, but you've got to change the permissions on the user's files, too. It helps to have two administrative accounts, or to have activated the root account, in order to make such changes. Alternatively, you can let ownership fall where it may and configure your umask value to set permissive permissions on all files and directories, at least in the HFS+ volume. That is, it doesn't matter who owns a file if it's got 0666 permissions -- anybody can read or write it in that case.

> Note: fsck does not work on HFS+, you have to use fsck.hfsplus for all HFS+ volumes. For journaled HFS+ you have to use the force option (fsck.hfsplus -f /dev/sdxx).

The Linux fsck program calls "helper" programs for each filesystem, normally called fsck.*fsname*, where *fsname* is the specific filesystem name, such as hfsplus. On my Ubuntu 10.10 installation, this is set up correctly for HFS+:

```
$ **sudo fsck /dev/sdb1**
fsck from util-linux-ng 2.17.2
** /dev/sdb1
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking volume bitmap.
** Checking volume information.
** The volume untitled appears to be OK.

```Of course, there could be a system-specific misconfiguration, or an error in some other version of Ubuntu, or even in a specific package version.

---

### Post by drowsyhaze on 2011-05-13
Thanks for those clarifications! Pretty neat about fsck, I hadn't tried since 9.04 where you had to issue the proper command, this'll clean up my crontab quite a bit.

Curious question: I'm the OP of the aforementioned thread and have been able to find little help with my question and no documentation - do you know how safe it is to write to journaled HFS+ in Linux? What are the dangers, why do we have to use the force option, is there any known/observable effect on data integrity?

---

### Post by srs5694 on 2011-05-13
I'm afraid I don't know how safe the "force" option is when getting around the read/write restrictions on a journaled volume. The hfsplus.txt document in the kernel source tree just says "use at your own risk." I don't see any better explanation in the source code, but I haven't read it all; I just searched for the word "force" and didn't find any explanatory comments.

---

