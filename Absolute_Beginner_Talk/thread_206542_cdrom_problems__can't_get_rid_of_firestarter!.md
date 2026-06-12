---
title: "cdrom problems / can't get rid of firestarter!"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by WhoDaBear on 2006-06-30
Dear all,
 
I am a linunx newbie (dapper drake) - please speak slowly and clearly!

I have a couple of problems which remain despite forum searching, wiki searching and a go on the IRC channel.  Several forum posts have been close, but nothing has sorted my probs for me yet!  Trying to convince my girlfriend that Ubuntu is better than Windows for our desktop PC, but struggling due to these minor probs - help needed asap! ;) 

1.  My CD/DVD reader drive: I can see the directory tree after it automounts when I stick a disk in, but trying to view, say, an image on it returns a "..don't have permission" style error.

2.  My CD/DVD writer drive: I can read from it fine, having no problems in this respect.  Writing to it doesn't work though.  Any ideas?

I know the cdrom probs. are usually due to an fstab problem, but I pasted this to the ubuntu pastebin, IRC folk looked over it and could see no probs.  I include it below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,rw     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,rw     0       0
/dev/sda2	/home/creatures/windows	ntfs rw,nls=utf8,umask=0222	0	

Thanks in advance folks.

WhoDaBear.

---

### Post by Joeb on 2006-06-30
Try removing the ",rw" after the "noauto" in your cdrom lines.  In otherwords have them look like:

/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by user1397 on 2006-06-30
whats your problem with firestarter?  you can't uninstall it?

---

### Post by Apple 101 on 2006-07-01
Find the package in Synpatic, and select the "Complete Removal" option.

---

### Post by WhoDaBear on 2006-07-01
re: cdrom problem:

No luck when I applied the suggested fstab edits.

Any other ideas?

Thanks folks.

WhoDaBear

---

### Post by WhoDaBear on 2006-07-01
Hi folks.

Thanks for help so far.

Still struggling with both CD/DVD drives.

gksudo nautilus  ... allows me to copy things from my CD reader just fine.  So its  a permissions thing I guess.  Whilst logged in as root I made sure all permissions enabled for the folder to which the drive mounts.  Still no progress when logged back in as normal user again.

Does this help anyone work out what my problem could be?

Thanks.

WhoDaBear.

---

### Post by annda on 2006-07-01
Hi,

i understand you have set all permissions (read+write+execute) for all users while logged as root for both of your drives, and still the changes are ignored when you log in as an ordinary user - am i right?

i'm no expert, but i've noticed that my permissions change on automount, for example detecting whether the inserted cd is writable.

i would suggest checking the permissions before and after inserting a cd. tell us what they are and maybe someone can offer some ideas then.

also check who is the owner of both mount dirs - that might have something to do with your problems.

good luck.

---

### Post by Joeb on 2006-07-01
When you created the root user, did you maybe also remove yourself from the sudousers?  It definately sounds like a permission problem and since root is the user that is mounting the drives, then you don't have access to them.

One quick and dirty fix to the burning issue would be to edit the menus and put sudo before the command (assuming you are still a sudo user).  Then, after entering the password, things should work.

---

### Post by WhoDaBear on 2006-07-02
Hi there folks - thanks again for helping me out!

[QUOTE=annda]Hi,

i understand you have set all permissions (read+write+execute) for all users while logged as root for both of your drives, and still the changes are ignored when you log in as an ordinary user - am i right?
[/QUOTE]

Right.

> 
i would suggest checking the permissions before and after inserting a cd. tell us what they are and maybe someone can offer some ideas then.


OK did this.  I changed the owner to my user ID (was root before) and re-ticked all the permission boxes.  

Then I stuck a CD in my CD-reader drive, and now the /media/cdrom0 folder was owned by root again!  And when I tried to change this, it wouldn't let me becuase "you are not the owner and so can't you can't change the permissions"

Thanks.

WhoDaBear

---

### Post by WhoDaBear on 2006-07-02
Dear Joeb,

Thanks for your post.

[QUOTE=Joeb]When you created the root user, did you maybe also remove yourself from the sudousers?  [/QUOTE]

Ahh!  That sounds serious.  Here's the output of sudo visudo copied from the terminal:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

# Defaults      !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# creatures is my username
creatures ALL=(ALL) ALL


```

Have I done a badness?  

I do remember following some sudoers edit instructions when trying to get rid of the startup password for firestarter.

Thanks again.

WhoDaBear

---

### Post by WhoDaBear on 2006-07-02
Hi folks.

Thanks again for help so far.

Here's some bits of my mtab file once both CD/DVD ROM and CD/DVD RW driver have automounted.

```

/dev/hda /media/cdrom0 iso9660 ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8 0 0
/dev/hdb /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=creatures 0 0

```

I notice big differnces between fstab and mtab.:-? 

Why is this?  I thought from other forums that mounting was based on my fstab, and mtab was a file showing what was mounted and how.  So shouldn't the fstab and mtab entries for my CD/DVD drives match?  If not, why not?

Thanks.

WhoDaBear (back from sunny Wales on Wednesay 5th evening):cool: 

p.s. I guess I'm learning as I go along.  Should this really no longer be in the absolute beginners forum?

---

