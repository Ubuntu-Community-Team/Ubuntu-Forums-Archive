---
title: "RSYNC over smbfs or cifs or nfs"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Squish42 on 2008-03-02
I want to use rsync to copy my /home folder to a NAS device (MGB Raid Pro [http://www.galaxymetalgear.com/Products/3500MGBR_pro.html](http://www.galaxymetalgear.com/Products/3500MGBR_pro.html)) it supports Samba (cifs & smbfs) and well as NFS.  

I'm sure my problem is I've mounted the device into /media/Backup with the wrong options.  Here's everything I've tried:
```
sudo mount -t cifs //192.168.0.10/backup /media/Backup -o credentials=.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //192.168.0.10/backup /media/Backup -o credentials=.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //192.168.0.10/backup /media/Backup -o credentials=.smbcredentials,lfs
sudo mount -t cifs //192.168.0.10/backup /media/Backup -o credentials=.smbcredentials,uid=my.uid,gid=my.gid,file_mode=0777,dir_mode=0777,iocharset=utf8
sudo mount.nfs 192.168.0.10:/mnt/ide2/nfs /media/Backup
```
(Yes, the is the tried and true, poke-and-hope method of finding answers has come up dry.)  All these mount without error and everything appears fine until I try to run rsync...

```
sudo rsync --delete -azvv /home /media/Backup/
```

My /home folder (obviously) contains files and folders with many different UIDs & GIDs.  So, when rsync tries to run chown on the destination files I get an error like this:
> rsync: chown "/media/Backup/Documents/Application_Install_Instructions" failed: Permission denied (13)

How do I mount the NAS share so that rsync can do  complete copy, including the chown???

Thanks for reading this!

---

### Post by scohar70 on 2008-03-04
Have you tried running this as root?

---

### Post by herbster on 2008-03-04
Run

```
ls -la /media/Backup
```

Paste output.

---

### Post by Squish42 on 2008-03-04
> **scohar70 said:**
> Have you tried running this as root?

Sorry, I'm new at this.  What's the difference between running as root and sudo?

---

### Post by glennric on 2008-03-04
> **Squish42 said:**
> Sorry, I'm new at this.  What's the difference between running as root and sudo?

I don't think he looked at your line closely.  When you run a command using sudo you are running as root.

---

### Post by Squish42 on 2008-03-04
After using 
```
$ sudo mount -t cifs //192.168.0.10/backup /media/Backup -o credentials=/root/.smbcredentials,uid=*my.uid*,gid=*my.gid*,file_mode=0777,dir_mode=0777,iocharset=utf8
$ sudo rsync --delete -azvv /home/FTP-shared/ /media/Backup/FTP-Shared/
$ sudo rsync --delete -azvv /home/*my.home*/Documents/ /media/Backup/*my.home*/

```

```
[FONT=Courier New]$ ls -la /media/Backup
total 4
drwxr-xr-x 5 my.uid my.gid    0 2008-03-04 20:37 .
drwxr-xr-x 7 root   root    4096 2008-03-03 07:17 ..
drwxr-xr-x 3 my.uid my.gid    0 2008-03-04 20:37 my.home
drwxr-xr-x 4 my.uid my.gid    0 2008-03-04 20:37 FTP-Shared[/FONT]
```



I cleaned up the test with
```
$ sudo rm -rf /media/Backup/
$ sudo umount //192.168.0.10/backup
```


After using 
```
$ sudo mount.nfs 192.168.0.10:/mnt/ide2/nfs /media/Backup
$ sudo rsync --delete -azvv /home/*my.home*/Documents/ /media/Backup/*my.home*/
$ sudo rsync --delete -azvv /home/FTP-shared/ /media/Backup/FTP-Shared/

```

```
[FONT=Courier New]$ ls -la /media/Backup
total 16
drwxrwxrwx 4 root   root    4096 2008-03-04 21:10 .
drwxr-xr-x 7 root   root    4096 2008-03-03 07:17 ..
drwxr-xr-x 3 nobody nogroup 4096 2008-02-26 22:56 my.home
drwxr-xr-x 4 nobody nogroup 4096 2008-03-04 21:10 FTP-Shared[/FONT]
```

I cleaned up the test with
```
$ sudo rm -rf /media/Backup/
$ sudo umount 192.168.0.10:/mnt/ide2/nfs
```

---

### Post by tact on 2008-03-04
Probably no help but....  I use rsync to back up work stuff to a windows based server share in the office and personal stuff to a shared drive at home.

I use :
```
sudo rsync -r -n -t -p -o -g -v --progress --delete --ignore-existing /source/ /destination/
```

and that preserves ownership and permissions etc...

---

### Post by Squish42 on 2008-03-04
> **tact said:**
> 
I use :
```
sudo rsync -r -n -t -p -o -g -v --progress --delete --ignore-existing /source/ /destination/
```

thanks for the tip, I'll try it tomorrow.

BTW, how is your destination mounted?

---

### Post by tact on 2008-03-05
> **Squish42 said:**
> thanks for the tip, I'll try it tomorrow.

BTW, how is your destination mounted?

Both (home and office destinations) are ntfs formatted SMB shares.    I use CIFS to mount, set up in fstab

Just adding to the above - All the files go over with the right permissions AND owner but for some reason directories/folders all have the right owner, but permissions are read/write for all (0777).  (Perhaps ntfs does not support permissions on folders??)

---

### Post by Squish42 on 2008-03-05
Thanks again.  I removed the -n and --ignore-existing options.  Here's the results:

```
$ sudo mount -t cifs //192.168.0.10/backup /media/Backup -o credentials=/root/.smbcredentials,uid=my.uid,gid=my.gid,file_mode=0777,dir_mode=0777,iocharset=utf8
$ sudo rsync -r -t -p -o -g -v --progress --delete /home/ /media/Backup/
building file list ... 

$ls -la /media/Backup
total 4
drwxr-xr-x 5 my.uid my.gid    0 2008-03-05 04:31 .
drwxr-xr-x 7 root root 4096 2008-03-05 04:24 ..
drwxr-xr-x 3 my.uid my.gid    0 2008-03-05 04:31 my.home
drwxr-xr-x 4 my.uid my.gid    0 2008-03-05 04:31 FTP-Shared

```
compared to:

```
$ ls -al /home
total 48
drwxrwxrwx  9 root root     4096 2008-02-25 08:05 .
drwxr-xr-x 22 root root     4096 2008-02-24 17:15 ..
drwxr-xr-x 53 my.uid my.gid     4096 2008-03-05 22:13 my.home
drwxr-xr-x  4 root root     4096 2008-02-24 20:41 FTP-shared

```

While I liked a couple of your rsync options, it still is not able to chown on the backup folders.

---

### Post by tact on 2008-03-06
Thats really odd.   I just ran a little test duplicating what you did:
I created a directory containing 2 files.  One owned by user/user and one owned by root/root.  I also set the file owned by root to have 0700 permissions and the user owned file to have 755 permissions....

I ran the same rsync command, same options etc...

The files transferred fine and retained correct owner/grp and correct permissions.  

The only difference in our setups is how you mount the share (commandline) versus what I do (mount via fstab).   The line in my fstab is below and only the final "0 0" is different....  Sorry I am at a loss - cannot suggest anything else to try

```

//server/share$    /media/server_share  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by Squish42 on 2008-03-07
That is interesting, and promising.  The other difference I can think of is the share itself.  Is your //server/share a windows public share?  In other words, what are the settings on on the security and share tabs in Windows?  Does "Everyone" have full access or is it limited to Full access for the account in your /root/.smbcredentials?

The oter difference is my MGBNAS box is running a stripped down version of Linus/Unix/BSD and I can't get at the true share settings.

---

### Post by tact on 2008-03-07
> **Squish42 said:**
> That is interesting, and promising.  The other difference I can think of is the share itself.  Is your //server/share a windows public share?  In other words, what are the settings on on the security and share tabs in Windows?  Does "Everyone" have full access or is it limited to Full access for the account in your /root/.smbcredentials?

The oter difference is my MGBNAS box is running a stripped down version of Linus/Unix/BSD and I can't get at the true share settings.

The windows share is on a win2k3server and is only available to my userid/account on the winserver (and set up in smbcredentials of course).  Not a public share. 

Is that how your's is setup?  Pls let me know if you get this sorted.  I'd love to find out the end result.

---

### Post by Squish42 on 2008-03-10
Sorry about the delay... I had a ddclient/DynDNS problem to fix.

It appears my problem is with the MGB box.  To test that theory I just
[LIST]
[*] created a share named "NAS" on a Windows XP Pro box at 192.168.0.100.  
[*] I changed the security so that just a XP Pro account "nas" has full access on the share and security tabs.  
[*] I created a  /root/.nascredentials with the username and password
[*] I created a /home/testfolder:
> joeuser@AMD2300:/home$ sudo ls -al  /home/testfolder/*
/home/testfolder/root_files:
total 12
drwx------ 2 root root 4096 2008-03-10 16:40 .
drwxr-xr-x 4 joeuser joeuser 4096 2008-03-10 16:38 ..
-rw-r--r-- 1 root root   14 2008-03-10 16:38 test_root_file

/home/testfolder/user_files:
total 12
drwxr-xr-x 2 joeuser joeuser 4096 2008-03-10 16:38 .
drwxr-xr-x 4 joeuser joeuser 4096 2008-03-10 16:38 ..
-rw-r--r-- 1 joeuser joeuser   12 2008-03-10 16:38 test_user_file

[*] I edited my /etc/fstab file adding:
```
# test 'tact' syntax suggestion
//192.168.0.100/nas     /media/NAS   cifs  credentials=/root/.nascredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
[*] ran sudo mount -a
[*] ran the rsync command:
```
sudo rsync --delete -azvv /home/testfolder/ /media/NAS/testfolder/
```
[/LIST]

Absouletely no *rsync: chown "bla bla bla" failed: Permission denied (13)* errors.

The resulting folder looks like this:
> joeuser@AMD2300:/media/NAS/testfolder$ sudo ls -al *
root_files:
total 1
drwx------ 2 root root  0 2008-03-10 16:40 .
drwxrwxrwx 1 joeuser joeuser  0 2008-03-10 16:44 ..
-rw-r--r-- 1 root root 14 2008-03-10 16:38 test_root_file

user_files:
total 1
drwxr-xr-x 2 joeuser joeuser  0 2008-03-10 16:44 .
drwxrwxrwx 1 joeuser joeuser  0 2008-03-10 16:44 ..
-rw-r--r-- 1 joeuser joeuser 12 2008-03-10 16:38 test_user_file


I then went to my MGB box and
[LIST]
[*] reset it to factory
[*] set the IP to 192.168.0.10  <-- yes "ten" not "one hundred"
[*] created a user "nas" with the same password
[*] created a share "nas" with the nas user having "writable" (yes, its spelled wrong in the GUI interface) access
[*] ran sudo umount //192.168.0.100/nas
[*] I edited my /etc/fstab file changing 100 to 10 leaving:
```
# test 'tact' syntax suggestion
//192.168.0.10/nas     /media/NAS   cifs  credentials=/root/.nascredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
[*] ran sudo mount -a
[*] ran the rsync command:
```
sudo rsync --delete -azvv /home/testfolder/ /media/NAS/testfolder/
```
[/LIST]

And, yep, you guessed it, chown errors out the wazoo.

the resulting folder on the MGB box looks like this:
> joeuser@AMD2300:/media/NAS$ sudo ls -al /media/NAS/testfolder/*
/media/NAS/testfolder/root_files:
total 4
drwx------ 2 502 users  0 2008-03-10 16:54 .
drwxr-xr-x 4 502 users  0 2008-03-10 16:54 ..
-rwx-w---- 1 502 users 14 2008-03-10 16:38 test_root_file

/media/NAS/testfolder/user_files:
total 4
drwxr-xr-x 2 502 users  0 2008-03-10 16:54 .
drwxr-xr-x 4 502 users  0 2008-03-10 16:54 ..
-rwx-w---- 1 502 users 12 2008-03-10 16:38 test_user_file


The only thing I can figure out is the GUI interface on the MGB box only allows "writable"  access for the NAS user on the NAS share and not full access.  And I have not found a way into a command line.

It looks like I may have spent $125 on a nearly worthless box.

---

### Post by billgoldberg on 2008-03-10
<rant>

This thread obviously does not belong in the "absolute beginner talk".

This thread is used to post all the questions, while questions in the right forums don't get as much attention.

</rant>

---

### Post by tact on 2008-03-10
(this question/discussion/topic not belonging in absolute beginners)
Well......  I suppose that depends on where you stand.  I consider myself still an absolute beginner (ubuntu/linux) but in this one area had to dig deep to get my box working how I needed - thus can offer some advice to someone with a similar issue to what I had worked out a solution for.

(Even absolute beginners need to struggle with hard topics in their first days/weeks/months just to do what they have to do in a normal day)

Cannot speak for squish42 regarding his qualifications for "absolute beginner" but wouldn't it be sweet if two real beginners were helping each other out on a tough topic and in doing so using terms and concepts that make the casual observer think they are far more advanced than - beginner.

hehehe  colour me overly flattered. :)    Me!  a person who still has to google for the correct syntax every time I need to use "find" to find a file.

If you are serious about your concern perhaps u can point this to a mod and they will decide if the thread needs moving.

Ciao

---

### Post by tact on 2008-03-10
Hi squish42,

From my limited playing around with samba and windows shares - I believe samba can be configured to overrule and force any file created on a certain share to adopt preset UID and GID.

It would seem that your MGB NAS box is configured to use a create UID of "502" and GID of "users" for all files/folders created on it.

(absolute beginner disclaimer:  I may be giving wrong info here!)  :)

I guess you gotta find out how to change that config.  Does the box come with any manual that describes how you can maybe ssh into it and administer it?

---

### Post by Squish42 on 2008-03-11
billgoldberg I so agree with you.  However I could not figure out where to put this where the right people would find it.  So, given I am a n00b, I stuck it here.  If you have a better idea let me know and I'll pack it up and move.

---

### Post by Squish42 on 2008-03-12
tact,

I believe you are right about the samba UID/GID.  I guess I'm going to have to dig into the MGB box a little more.  From the manual and interface it is blatently obvious that its a Linux/Unix/BSD box.  I just have to figure out how to get past the GUI.  Maybe there's a way to flash the BIOS with something more friendly. (now that is some "over the top" wishful thinking.)

---

### Post by tact on 2008-03-12
> **Squish42 said:**
> tact,

I believe you are right about the samba UID/GID.  I guess I'm going to have to dig into the MGB box a little more.  From the manual and interface it is blatently obvious that its a Linux/Unix/BSD box.  I just have to figure out how to get past the GUI.  Maybe there's a way to flash the BIOS with something more friendly. (now that is some "over the top" wishful thinking.)

What is the exact brand and model?   Google on that .... there are sites on the web that have lists of the default username/password needed to administer all kinds of boxes.   I had to factory reset my netgear wifi router and lost the manual so didnt know the default username/password.  Google found it for me.  :)

---

### Post by Squish42 on 2008-03-12
I need to move forward on this so I've been thinking... I have two kinds of data on my /home folder - 1) the network Shared folder that everyone has access to - it s mounted with "nobody" so there is no security on the files and 2) my user folders - that contain significantly less data but security is critical.  

So, shouldn't I use two backup methods?  The rsync on to the MGB box would be ideal for the "Shared" folder.  But what other kinds of backups are there that preserve GID and UID?  TAR is the only place I can think of starting.  But I'd like a couple more opinions before I start down that path.

---

### Post by tact on 2008-03-13
For the data you want to keep secure... if you really cannot get owner/permissions sorted -  have a look at using encfs.   This encrypts the files on disk and so what you back up to the NAS will be the encrypted files.

In operation encfs mounts the encrypted files/folders and transparently decrypts for you when you are using your computer...  but what you back up will be encrypted.

---

### Post by Squish42 on 2008-03-13
That's interesting.  If Ubuntu is handling the encryption/decryption would the MGB Box's OS have any idea what was on the drive???  It should just see bits.  If that's the case, the mount command would be the only limitation on if the UID and GID were retained??? Hey, its worth a shot.  Can you point me to a source for encfs knowledge?

---

### Post by Squish42 on 2008-03-13
In a moment of clarity I called the MGB tech line and talked to "Jeff".  His advice was to reformat the drive, changing it from EXT2 to FAT32.  Since there's nothing on the drive its worth a shot.  Now I just have to wait for a 1,000,000,000,000 bytes to format. :)

---

### Post by tact on 2008-03-13
> **Squish42 said:**
> That's interesting.  If Ubuntu is handling the encryption/decryption would the MGB Box's OS have any idea what was on the drive???  It should just see bits.  If that's the case, the mount command would be the only limitation on if the UID and GID were retained??? Hey, its worth a shot.  Can you point me to a source for encfs knowledge?

if you want to give it a shot then encfs is in the repositories. A good guide is here.

[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by tact on 2008-03-13
> **Squish42 said:**
> In a moment of clarity I called the MGB tech line and talked to "Jeff".  His advice was to reformat the drive, changing it from EXT2 to FAT32.  Since there's nothing on the drive its worth a shot.  Now I just have to wait for a 1,000,000,000,000 bytes to format. :)

I don't think that fat32  supports permissions/ownership at all  - how will that help your situation?

(Sorry - I might not be as clear as needed on your requirements)

---

### Post by Squish42 on 2008-03-15
> **tact said:**
> I don't think that fat32  supports permissions/ownership at all  - how will that help your situation?
Well, I had to try something.  It didn't work (obviously) but I had to try.  

Basically it would set all GID and UID of all files to the settings in the mount.  Ex:
```
sudo mount -t cifs //192.168.0.10/admin /media/Backup -o credentials=/root/.smbcredentials,uid=joeuserevan,gid=joeuser,file_mode=0777,dir_mode=0777,iocharset=utf8 

```
would set every file and folder to belong to "joeuser".  A little cleaner but still not very useful.

So I've just started another format to EXT3 just to see what that gives me.

---

### Post by tact on 2008-03-15
Hope it works out ....  pls take the time to write back here and let us know how you fare.

I am learning from you with each strategy you try.  Filing it in my mental recesses in case I run into similar issues in future and can assist someone...

---

### Post by Squish42 on 2008-03-15
Just for kicks I did a portscan on the MGB from my XP machine.  It found:

21 80 111 139 445 889 2049 3473

Other than the obvious FTP and HTTP, do the others mean anything to any one?

And, for more fun, a telnet to port 80:
> $ telnet 192.168.0.10 80
Trying 192.168.0.10...
Connected to 192.168.0.10.
Escape character is '^]'.

UNKNOWN 400 Bad Request
Server: thttpd/2.25b 29dec2003
Content-Type: text/html; charset=iso-8859-1
Date: Sat, 15 Mar 2008 20:32:24 GMT
Last-Modified: Sat, 15 Mar 2008 20:32:24 GMT
Accept-Ranges: bytes
Connection: close
Cache-Control: no-cache,no-store

<HTML>
<HEAD><TITLE>400 Bad Request</TITLE></HEAD>
<BODY BGCOLOR="#cc9999" TEXT="#000000" LINK="#2020ff" VLINK="#4040cc">
<H2>400 Bad Request</H2>
Your request has bad syntax or is inherently impossible to satisfy.
<HR>
<ADDRESS><A HREF="http://www.acme.com/software/thttpd/">thttpd/2.25b 29dec2003</A></ADDRESS>
</BODY>
</HTML>
Connection closed by foreign host.
$ 

Not terribly informative :lol:

---

### Post by tact on 2008-03-16
> **Squish42 said:**
> Just for kicks I did a portscan on the MGB from my XP machine.  It found:

21 80 111 139 445 889 2049 3473

Other than the obvious FTP and HTTP, do the others mean anything to any one?

And, for more fun, a telnet to port 80:
 

Not terribly informative :lol:

Try to ssh into port 889 or 3473.  Use the admin username and password.  See if it gets u to a command prompt.  :)

---

### Post by Squish42 on 2008-03-18
Sorry about the delay - I had a minor system rebuild.  Nothing serious.

Anyway, I tried "ssh -p xxxx admin@192.168.0.10" for all the address except 21 and 80.  Nothing to report other than ports 111 139 445 889 & 2049 did nothing - no rejection, no response at all - I had to Ctrl+C to kill the attempt.  Port 3473, however, was "refused".  Either way, I did not find a back door.

I'll try encryption next, but not tonight its late and I have to work tomorrow.

---

### Post by mozetti on 2008-03-19
If you use the -l (that's a lowercase L) switch and supply the username then you might get it to prompt you for a password. I have a WD MyBook World Edition NAS, and that's how I ssh to it.

---

### Post by Squish42 on 2008-03-25
mozetti - thanks for the tip but still no joy.

---

### Post by Squish42 on 2008-03-25
After a lot of reading on encfs I decided I wasn't comfortable having all my backup files encrypted, alt least not yet.  So I'm back to trying to figure out the UID/GID weirdness on the MGB box.  

I think I may have found my answer though, well, at least a clue.  I discovered Scott Carpenter's Linksys NSLU2 blog entry: [http://www.movingtofreedom.org/2007/02/06/samba-and-the-nslu2-network-shares-in-gnu-linux/](http://www.movingtofreedom.org/2007/02/06/samba-and-the-nslu2-network-shares-in-gnu-linux/)

About half way down the page he's fighting the same problem I'm having.  His solution... fix the smb.conf on the NSLU2.  So it looks like all signs point to a bad SAMBA implementation on my MGB box.  At least now I have something to talk with their tech about.

Assuming, however, the tech does not have a way for me to access that file, I'll need to revert to TARing my home folder and RSYNCing my shared.  All I need for that is a good TAR thread showing me how to maintain permissions inside the TAR.  Any suggestions?

---

### Post by Squish42 on 2008-03-25
OK, here's something interesting, maybe.  I just found a "save configuration" option on the MGB.  It dumps a .TAR file on my system.  I opened it up and there's some interesting stuff in there.  I've attached a copy for everyone's inspection.  I wonder if there's something in there that I could modify and then upload the changes???  Its getting late so I'll have to  dig through the files another day.

Thanks again for everyone's help.

---

### Post by Squish42 on 2008-04-30
I thought I should come back here and let whoever is following this know what I ended up doing...

First, I did decided to go with two backup models... TAR for all the home folders so that all the GID and UID remain intact.  Secondly, RSYNC for the massive 700G+ Share folder with all the family photos and videos and MP3s etc...  I would have liked to have just done RSYNC for everything but I never could figure out how to replicate the ID values onto the [3500MGB-RAID Pro]("http://www.galaxymetalgear.com/products/3500_mgbr_pro.html").

So for the TAR here's the commands:
```
$ sudo tar cvpzf /media/nas/evan.backup-080407.tgz --exclude=/home/evan/.Trash --exclude=/home/evan/Downloads --exclude=/home/evan/.thumbnails /home/evan
$ sudo tar cvpzf /media/nas/ftp.backup-080407.tgz /home/ftp
$ sudo umount /home/Shared/Azureus/
$ sudo tar cvpzf /media/nas/FTP-shared.backup-080407.tgz /home/FTP-shared
$ sudo mount -a
```
I do the unmount/mount around the FTP-shared backup so TAR doesn't follow the mount into my torrent folder

For the RSYNC:
I started by creating a full backup
```
$ sudo rsync -vvrltDH --progress --numeric-ids --delete --delete-excluded --exclude-from=/home/Shared/Backup/.AMD2300_home_Shared.exclude /home/Shared /media/nas/Shared/080406
```
I found an interesting blog entry about hard links and backups [here]("http://www.sanitarium.net/golug/rsync_backups.html").  From Kevin's guidance, before the next backup I created a hard link copy of the original backup
```
$ sudo time cp -al 080406 080413
```
Then confirm link folder is complete but not taking up significantly more space
```
$ sudo du -shc /media/nas/Shared/*
```
Re-run rsync for the 2nd week	
```
$ sudo rsync -vvrltDH --progress --numeric-ids --delete --delete-excluded --exclude-from=/home/Shared/Backup/.AMD2300_home_Shared.exclude /home/Shared /media/nas/Shared/080413
```

This gives me some history in my backups just in case I want a document from a couple weeks ago.

When I need more space I just delete the oldest backup
```
$ sudo rm -rf 080406
```


The only thing left to do is create cron jobs for both of these.  THe only "difficulty" for this n00b is figuring out how to write a script that creates the folders based on the date.  Shouldn't be to difficult, I hope.

---

