---
title: "Maddening permission problem"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by quickk on 2006-12-07
Hi everyone, 

   I've been having major problems with my file permissions, and this is driving me completely mad.  First, a quick question: how do I go about resetting all the file permissions in my home directory to their "normal" state (ie, the state they would be in after a fresh install).  

Here's my more complicated problem.  I have vmware server installed.  I want to have a guest windows 2003 server operating system (the host is ubuntu edgy).  The guest needs to have read/write access to a partition on the host operating system so that I can easily transfer files back and forth between the guest/host.  

Here's the problem: if I try to "share" an ext3 partition, the virtual windows doesn't know what to do with it.  If I try to share an NTFS partition, then it's the ubuntu host that can't have write access to it.  I've tried installing this on the guest windows [http://www.fs-driver.org/]("http://www.fs-driver.org/") to get access to the ext3 partition, but it doesn't work (it wants to format my drive!).  I tried installing something similar on the host to get R/W access to NTFS, but failed, and I don't like the idea of using these unproven methods (this is a production machine, and I don't want to chance messing up the filesystem).  

Long story short: I figured that a fat32 partition would best suit my needs.  I changed the appropriate entries in fstab, and have a 20GB partition that mounts correctly.  I called it "work"; the mount point is /home/<my user name>/work .  I can read/write to this partition without any problems using either root, or normal user name.  

Next step, I created a virtual machine, edited the properties of this machine so that it has access to this partition, and then when I try to start the virtual machine, vmware keeps complaining that: ```
Cannot open the disk '/home/amorris/.vmware/Windows Server 2003 Enterprise Edition/Windows Server 2003 Enterprise Edition-1.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file
```.  This message is directly related to my inclusion of the fat32 "work" partition.  When I remove this drive in the virtual machine settings, I get no problems.

Because of this message, I then tried starting vmare with the sudo command: "sudo vmware".  I still get the error.  What's up with that??? If root doesn't have sufficient rights then who does?  This is really driving me crazy.  I've literally spent most of the night trying to get this problem solved, and just keep going in circles.  

Can anyone help? :(

---

### Post by meng on 2006-12-07
I have a question about your first question? The question is, why are your file/folder permissions out of whack in the first place? Is it because you did a reinstall, perhaps entering the users in a different order than on an earlier install (hence they get assigned different user ID numbers)? Or is it because you backed up your files onto CD or a Windows filesystem, then restored files from this with the permissions scrambled?

In order to restore permissions/ownership, you'll want to use chmod and/or chown respectively. The -R switch indicates recursive feature. man chmod or man chown for more info. I'm not sure if this is the answer you're after, you can clarify the question if I'm off base here.

In order to prevent this problem from happening, it depends how the problem occurred in the first place. You may want to back up using .tar.gz in future, I think this will preserve your permissions better.

---

### Post by quickk on 2006-12-07
To answer your question about my question :), my permissions are all messed because at one point something went wrong (I'm not sure how--maybe I did something to my home folder while in sudo -s mode).  Basically, I had a bunch of files that I couldn't access from my normal account.  To try and fix it, I did just like you said and did something like "chmod -R u+rw *", but I didn't realise that this might remove some permissions for the "others", or make executable files non-executable (I thought that it would just add the read/write attributes for the current user).  The I just made things worse by trying to fix this new problem and ended up with all my files being executable.  The problems just escalated from there.

---

### Post by quickk on 2006-12-07
In case people didn't want to read my whole previous post, here's a "to the point version".  My fstab is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=9cceb0e5-76a4-41d2-84e4-24c7e4ca375c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb7
UUID=ae85130a-4d3a-4be7-8a9f-83c8ceca7936 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=10E058A7E0589536 /windows/C      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/sdb2
UUID=F4BD-1A0D  /home/amorris/work      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=B6E0B795E0B759F7 /windows/E      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=2A9CF87F9CF8473B /windows/F      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=2138bbff-d0a3-407b-b884-d3071a98398e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,unhide,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```
 (it was ugly like that by default).  I wan't to make the /home/amorris/work partition available to a vmware windows guest and to the ubuntu host.

I set everything up correctly in vmware, and always get an issuficient user rights when I try to start the virtual machine that has this shared drive available.  Starting vmware in su mode doesn't help.

How can the "root" not have sufficient rights?

---

### Post by Hendrixski on 2006-12-07
I would just ls -l to see what the current permissions are, then chmod it as needed.  Don't be afraid to use the man pages for these commands.  

I've been thinking about writing an application that would bring up a GUI where you could change permissions by right clicking on a file.  because a lot of new users don't want to have to put up with ls -l and chmod, or with the terminal in general.

---

### Post by quickk on 2006-12-07
A nice GUI would be nice!  A few more questions:

1. Are these permissions normal:

```
root@sacapus:/dev# ls -l sd*
brw-rw---- 1 root disk    8,  0 2006-12-07 07:32 sda
brw-rw---- 1 root disk    8,  1 2006-12-07 07:32 sda1
brw-rw---- 1 root disk    8,  2 2006-12-07 07:32 sda2
brw-rw---- 1 root disk    8,  5 2006-12-07 07:32 sda5
brw-rw---- 1 root disk    8, 16 2006-12-07 07:32 sdb
brw-rw---- 1 root disk    8, 17 2006-12-07 07:32 sdb1
brw-rw---- 1 root disk    8, 18 2006-12-07 07:32 sdb2
brw-rw---- 1 root disk    8, 19 2006-12-07 07:32 sdb3
brw-rw---- 1 root disk    8, 20 2006-12-07 07:32 sdb4
brw-rw---- 1 root disk    8, 21 2006-12-07 07:32 sdb5
brw-rw---- 1 root disk    8, 22 2006-12-07 14:33 sdb6
brw-rw---- 1 root disk    8, 23 2006-12-07 14:33 sdb7
brw-rw---- 1 root plugdev 8, 32 2006-12-07 14:33 sdc
brw-rw---- 1 root plugdev 8, 48 2006-12-07 14:33 sdd
brw-rw---- 1 root plugdev 8, 64 2006-12-07 14:33 sde
brw-rw---- 1 root plugdev 8, 65 2006-12-07 14:33 sde1
brw-rw---- 1 root plugdev 8, 80 2006-12-07 14:33 sdf
brw-rw---- 1 root plugdev 8, 96 2006-12-07 14:33 sdg

```

And if so, why are all the file names yellow on a black background?  It makes me think that something is desperately wrong!

---

### Post by quickk on 2006-12-07
I'm still not really sure what is going on, but I added my user name to the "disk group" like so: ```
adduser <username> disk
```, and it seems to have fixed my problem.

---

### Post by Hendrixski on 2006-12-07
That's a lot of disk groups. There's something wierd there, but then again, I have never tried the weird partition stuff you're doing so I don't know if I can help.

I hope the adduser to the disk group worked :) If I try something like this soon (I just might have to... sigh*) I'll keep the adduser trick in mind.

---

### Post by quickk on 2006-12-08
Yeah, I know that I have a lot of partitions :) . Before I started playing around with linux I allready had 4 partitions (windows, work stuff, media stuff, backup).  Add 2 optical drives, then install linux with a separate partition for virtual mem, /, and /home and you'll have lots of partitions too!

Regarding the fat32 partition, I am seeing now that this type of filesystem can be it can be quite troublesome because it does not support setting read and write permissions (hence the reason everyone could see everyone else's stuff in windows pre-2000). Consider this example which just happened to me: I had my "work" partion mounted to /home/<my user name>/work.  I could read/write to it without any problem using my default (non-superuser) credentials.  I got my virtual windows up and running (finally) through vmware, and everything worked fine.  I tried reading and writing to the "work" partition with the virtual windows, and that worked fine too.  I was very happy.  

Unfortunately, my happiness was short lived.  Once I had accessed the "work" partition from my virtual windows, all the permissions for that partition were magically (an evil magic) changed such that I can no longer write to it from ubuntu! ARGH!  

What I'm guessing is that the since I was logged onto my virtual windows as the administrator, somehow  accessing the partition changed the owner to "root".  I'm not sure how this is possible, but it happened.  I think that this is all happening because of the fat32 wich has no real support for file permissions, so the operating system (windows or linux) just makes things up as it goes along.

The moral of the story: if you plan on sharing a fat32 drive between operating systems, be prepared for some major permission related headaches...

---

### Post by quarkhirad on 2006-12-08
you can also fix the prob by doing the following 

I prefer using numbers instead of the ugo+ rw type notation for chmod 


first cd to ur home dir then 
u might need root permission for the following 

type chown -R urname /home/urname

where urname is ur username 

then type chmod -R xyz /home/urname 

 where xyz are numbers ranging from 1-7 
 x gives root the permissions 
 y gives user the permission 
 and z gives others the permission

no 1 signifies execute 
no 2 signifies write 
no 3 signifies execute + write
no 4 signifies read
no 5 signifies read + execute 
no 6 signifies read + write
no 7 signifies read +write +execute

hence for example 

chmod -R 764 /home/urname

will give the following permissions to urname dir and all dir and files under urname dir.

read +write +execute to root
read + write to user 
only read to others 

depending on what kind of permisssions u want for each of the three users u can substitute any of the 7 values for xyz.

As far as ur Vmware problem. Sorry buddy i dont use Vmware and hence i am not familliar with it.

---

### Post by Phrawm48 on 2007-08-22
VMware users will occasionally receive the message "Reason: Insufficient permission to access file" when trying to start a virtual machine.   I find this usually occurs after I've checkpointed a particular partition or used VMware's internal defragmentation tool.  

I don't know if this is the official, approved way of fixing this problem when it occurs, but what I do is:
[LIST=1]
[*]I CD to the directory containing the virtual machine for which the error was reported.  For me, this equals typically */var/lib/vmware/Virtual Machines/[virtual machine name]*.
[*]In the directory, I use *ls -l* to view the owner and group settings for the files.  Typically, when the problem occurs it's because something has reset owner:group to *root:root* and the r-w-x permissions are insufficient.
[*] I use *sudo chown owner:group ** to change the ownership of the virtual machine files to my username and group, and *chmod 775 ** to open up the r-w-x permissions.[/LIST]As I said, I don't know if this is the official way to solve this problem.

I also suspect I'm being too generous with owner:group and files permissions to suit some purists.  But I don't care -- Linux files permissions seem to cause as many problems as they solve on my single-user computer.  There's no better example of this than a program, VMware, run via sudo that can't access files belonging to the user who used sudo to run the program...

Cheers & hope this helps,
Ric
SFO

---

### Post by gregoryo on 2008-03-11
I had a similar problem, but only for a physical partition I was trying to mount as a local disk within the VM. I fixed it by adding my user account to the group "disk", then ensuring /var/local/vmware-server/lib/vm/* and ~/.vmware/preferences were owned by me, not root. All works well.

---

### Post by Shazaam on 2008-03-11
I NEVER give ANY  Windows O/S write permissions for ANY linux partitions because of some of the same problems already stated in this thread and others and my own personal experience. Windows has a BAD habit of adding files/changing files enough to make me pull what little hair out that I have left. Why would I need a "Recycle Bin" in my /swap file? Insane. I wish I had kept the error message that I got with that one.

---

### Post by hyper_ch on 2008-03-11
Ubuntu Host and Windows Guest are two totally independant systems

--> This means no local partition read/write but networking through SMB, SSH/SCP/SFTP

---

