---
title: "Can't Change Ownership From root"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by roystreet on 2007-10-12
Hello,
    I've recently installed a brand new HD & have several partitions on it.  I was hoping to utilize SAMBA for the windows machines on the network.  Well, I find that I can't really do it the way I want to because I'm trying to change ownership of folders to another user.  I have opened terminal up & switched to root.  I have been able to delete folders by being root, but I can't "chown" to change it to the user name jkr.  jkr is the main admin type of account I would like to use.
    I am using the following command:
chown jkr:jkr /BINSystem

   Error I'm getting:
chown: changing ownership of '/BINSystem' : Operation not permitted

OK, so maybe the "Root" of BINSystem is locked into only the root can have ownership - Because BINSystem is the name of the partition.  So I create a folder in there via Nautilus named: "fred"

    So, I'm creating it with the username of "jkr" because I'm not using the terminal.  I check properties & as I suspected, I do not own it, now root does.

I now use the same command as above, but adding "fred" at the end hoping it would allow a subfolder to change??  I get the same error.

I've searched on this site trying to find out how to overcome this, but to no avail.  Any ideas out there?

Thanks,
  ---roystreet

---

### Post by lgcabarcas on 2007-10-12
have tried with   chgrp ?

---

### Post by roystreet on 2007-10-12
Hi - No I haven't tried that...How exactly would I do that?

Thanks.

---

### Post by roystreet on 2007-10-12
Wait -- I just tried:

chgrp jkr /BINSystem/fred

I get the same error.  I'm still using terminal as root.

But just in case, I tried it one time as "sudo" & then the rest of the command - Same error msg.

---

### Post by dfreer on 2007-10-12
Kinda important: What filesystem did you format your hard drive with?

---

### Post by roystreet on 2007-10-12
Fat32

---

### Post by roystreet on 2007-10-12
I did that in hopes that it would allow me to open it with Win SERVER 2003.  I wanted to have this test machine a dual boot.  I'm sure 2003 will want NTFS, but I don't know how to work with NTFS via linux

---

### Post by dfreer on 2007-10-12
NTFS read/writing works pretty good with NTFS3G, included by default I do believe in Gutsy. So it wouldn't be a bad choice as your filesystem, seeing as you want to share it with a windows machine.

As for the FAT32, it needs to be mounted in a certain way in order to have write support. I do not believe you can change permissions the same way as with a native Linux filesystem, you need to specify it in your /etc/fstab.
This should help you out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Specifically note the umask setting.


EDIT: hmmm, so you want to share files via Samba, and control access using user permissions? I'm working from my head here, so don't take the following as literal truth. I'm thinking FAT32 can handle write permissions (like making files read-only, read/write, read/write/execute), but not ownership (all files are pseudo-owned by one account, depending on how you mount it). I'm thinking you might run into problems with this when setting up Samba. Is there no way to use your native linux filesystem for sharing these files, perhaps just using linux w/NTFS3G support to transfer files between the two OS?

---

### Post by roystreet on 2007-10-12
I have feisty & I do not see anything that eludes to NTFS.  I would rather as you have mentioned stick with NTFS.

---

### Post by roystreet on 2007-10-12
OK, OK...I added NTFS configuration to my system & I'm now trying to figure out how to find it & use it.

---

### Post by bodhi.zazen on 2007-10-12
Neither FAT or NTFS support Linux ownership or permissions.

Either way, you set ownership and permissions at the time of mount or in fstab

sudo mount /dev/xxx /mount_point -o uid=1000,gid=100,umask=007

Or 

/dev/xxx /mount_point (ntfs-3g or vfat) uid=1000,gid=100,umask=007 0 0

See this link :  [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Also, if you can use ntfs-config , a gui tool to mount both fat and ntfs as rw

```
sudo apt-get install ntfs-config
```

Then :

```
gksu ntfs-config
```

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by dfreer on 2007-10-12
eh, you guys post too fast ;) Just finished editing the last post to see three new ones. Rather than going back to read it, basically I just wanted to know whether you could use your native linux filesystem to share the files instead?

---

### Post by roystreet on 2007-10-13
I apologize for the slow response time here...I've been trying to get a friends PC to work - Headache finding old video card drivers. 

**dfreer -** Anyway, after a quick test - On my home directory which I believe is in ext format, the sharing seems to be working pretty good.  Although I haven't tested it with further persmissions limitations.  Like, only certain users can read/write, etc.  But at least the Windows users can open/modify/delete/etc.  So you are definetely 100% right - It has to do with the formatting.

**bodhi.zazen ** - Are you saying that I'm going to run into the same problem with NTFS as I am with the FAT partitions?  If yes, does anyone have any ideas that will be helpful in resolving my ambitions?  I'm trying to use a test machine (for now) to have server 2003 & ubuntu (Which I like a whole bunch!) I want to make it a file server, but eventually be able to also access it from the web.  I would like to be able to share the same files rather the server is running server 2003 or ubuntu instead of having duplicates.  I have a 320 gb hard drive, so I guess I can afford to have duplicates, but rather now.  Any ideas here guy's?

Thanks,
   ---roystreet

---

### Post by louieb on 2007-10-13
I'll confuse you some more. 
The hard drive is on a PC running Linux correct? 
Your windows machines are going to access the drive over the network correct?

If both statements above are correct  then format the drive ext3 or some other Linux file system type. I don't know about you but I want my hard drives using a file system native to its operating system (ext3 - Linux,  NTFS - windows).

The windows machines are never going to know or care what file  system you use on the drive. To them its just another network drive. The host machine does all the reading and writing to drive.

---

### Post by mysurface on 2007-10-13
> **roystreet said:**
> Fat32

You can't do chown on fat32 filesystem

---

### Post by roystreet on 2007-10-14
I am testing both 2003 server & ubuntu server on the same system.  I am using it (The machine no matter what OS is running at the time) as a file server & etc.  That is why I would like those files available in a format the both the OS's can "Work" with.
.
Thank you for your responses to my question, it is helping me greatly understand the issue more.

---

