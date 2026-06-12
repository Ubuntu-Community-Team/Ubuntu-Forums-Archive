---
title: "[SOLVED] Question about Group Management  in Feisty"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by StewartM on 2007-09-11
Hello,

I'm a newbie with Feisty and I have created two users and the following directories:

/home/user1/   ("Administer the System" checked)

/home/user2/   (my regular working user account; "Administer the System" not checked)

I've also created a "common" folder for for files I might need to share between the two (which was created by user2, who owns it):

/home/common/

And I tried to create a group for both user1 and user2 under "Users and Groups" menu in GNOME.
Then I set everything in the common folder to be read/writeable to both (using the group owner user2 or by su- )

chmod -R 775 /home/common/

When I checked the permissions using ls -l, everything seemed to be set correctly.

However, it didn't seem to work in either the GUI or the command line. Every time I was user1 and tried to write to things in /home/common/  that user1 didn't own, I got denied permission. I would have to go in as su- and do it by the terminal to write or copy files as user1.

When I look at the directories (ls -l in the command line) and the "Users and Groups" menu, I see that I have (among many other system groups) the following groups:

root
user1
user2

Despite my having including both my users in all three groups, my granting or privileges to /home/common/ didn't seem to be working right. As I said, I would have to (temporarily) change ownership (the chown command) or do it as su in the terminal to get things copied or deleted.

SOOOOO....I went in and deleted under the "Users and Management" menu groups user1 and user2 and put everyone under group "root". That had no effect, I got the warning I could be orphaning files, and when I would check back the system would have recreated groups user1 and user2.

THEN...I went in in the terminal and saw that all the files/folders under -user1 were under group user1, and those under user2 were under group user2. So I went in as su and set the group  of all files in /home/user1 and /home/user2 to the "root" group. I also changed the membership to all the files and folders in /home/common/ to "root".

What happened? Well, I now found out that, at last, either user1 or user2 could read/write/delete files in the directory /home/common/  which is what I wanted all along.

However, when I checked by going into the GNOME menu of "Users and Groups" the menu hangs. I can kill the window and force it to close, but it hangs. So I must have done something wrong.

What I think I should do is to, under the command line:

a) see what groups exist

b) addgroup user1; include user1 and user2 as members;

c) remove user1 and user2 from group root

d) set all files in /home/user1 and /home/user1 to be listed under group "user1" and to likewise change the group listing under /home/common/ to group "user1".

Any ideas or suggestions? The system is not givng me any errors than the "Users and Groups" GUI hanging up.

Stewart

---

### Post by raijinsetsu on 2007-09-11
You have to logout of your Gnome session, and then log back in. Groups are set when you login :)
You also need to "chgrp CommonGroup /home/common" where CommonGroup is whatever the shared group is.
AND OMG!!! NEVER EVER EVER EVER put users in the root group... It gives them access to everything in the system... BAD!

---

### Post by StewartM on 2007-09-11
> **raijinsetsu said:**
> You have to logout of your Gnome session, and then log back in. Groups are set when you login :)
You also need to "chgrp CommonGroup /home/common" where CommonGroup is whatever the shared group is.
AND OMG!!! NEVER EVER EVER EVER put users in the root group... It gives them access to everything in the system... BAD!

I figured that putting both into group 'root' was not the best solution after I thought about it more.  :) That's why I was  wanting to remove both my users from it yet access /home/common/.

I'm away from that computer now, but I'll try your suggestiong after I get home.  (Create group "common", then include both user1 and user2 in it). That sounds logical.

Stewart

---

### Post by raijinsetsu on 2007-09-11
I use a similar tactic on my server. I have a "/usr/local/media" directory which belongs to group "Media". Anyone I want to allow to access these files gets added to the Media group.
I've also done some silly things like setting the group sticky bit :)
I also run a script nightly to fix any permissions/groups that get out of whack. (my torrent downloader likes to save files to the "www-data" group... grrr!)

---

### Post by StewartM on 2007-09-11
> **raijinsetsu said:**
> I use a similar tactic on my server. I have a "/usr/local/media" directory which belongs to group "Media". Anyone I want to allow to access these files gets added to the Media group.
I've also done some silly things like setting the group sticky bit :)
I also run a script nightly to fix any permissions/groups that get out of whack. (my torrent downloader likes to save files to the "www-data" group... grrr!)


Well, did I manage to hose my system?

Well, when I returned home to reboot, my (relatively new, about 1 month old computer) failed to boot. It did a fsck and manged to get to 12 % complete, then waited, fixed an inode size error (although the value was the same) then went to 12.4 % complete when it fixed another inode size error. Then a black screen.

What do you think I need to do? Do I need to do a re-install? I'm posting this using the live CD that came with the system. Or can I fix the problem without an install?

Stewart

---

### Post by raijinsetsu on 2007-09-12
Boot into "recovery" mode. Go look at your logs in "/var/logs".
Try posting anything that looks strange. It's very doubtful that this was caused by your playing with groups :).

---

### Post by StewartM on 2007-09-12
> **raijinsetsu said:**
> Boot into "recovery" mode. Go look at your logs in "/var/logs".
Try posting anything that looks strange. It's very doubtful that this was caused by your playing with groups :).

Will do.

The first error that the auto fsck returned was:

os_part_ Inode 5159002, i_size is 1724725480, should be 172475480. FIXED

Then it goes to 12.4 %, and returns another similar error (different Inode #) and tells me that it's fixed.

I'll look at the /var/logs directory in os_part_(2) when I boot to CD. I've already begun to transfer stuff off the system in case I have to re-install.  Any particular log file I should be interested in? (I'm not familiar with what I should expect to find).

Luckily, the Ubuntu CD seems to find and make everything work (video, sound, etc) on this PC (A Dell, with Ubuntu pre-installed) if I do have to re-install hopefully my very first installation will be relatively painless. The guy from Canonical who was kind enough to give me a bit of (free) advice over the phone told me that Dell ships their pre-installed Ubuntu systems with hardware that's Ubuntu-certified, so getting hardware to work shouldn't be too hard.

Stewart

---

### Post by raijinsetsu on 2007-09-12
you'll want to check the "messages" file. But, you'll need to check the one on your HDD, not on the CD. K?
Also, try running fsck from the CD on your HDD partition. See what that turns up.

---

### Post by StewartM on 2007-09-12
> **raijinsetsu said:**
> you'll want to check the "messages" file. But, you'll need to check the one on your HDD, not on the CD. K?
Also, try running fsck from the CD on your HDD partition. See what that turns up.

The Linux tech on my job (who's also a resource) and who knows how I've configured my system also suggests the following:

I have drives with data, no OS, from my old Windows setup connected via external USB-IDE interfaces. They were "on" during the boot-up. My tech friend thinks that the fsck may actually be searching these drives (in the /media/ directory on the os_part_?) and finding the errors there and that's what is hanging my system.

His first thing to try: turn off these two external drives while booting up. Let fsck only check the internal HDD and see what happens.

This sorta makes sense, as the older of the two drives has had recently this habit of mysteriously disappearing on the GNOME screen w/o warning.  I would count myself as very lucky if the fix was as simple as that.

Another possibility: the guy at Canonical who offered me the free advice over the phone was concerned about my memory. I bought the system with 1 G of RAM, and the people at Dell then duly configured the swap to be 1.3 G (as is custom). I then installed 2 x 1 G memory sticks in the machine, improperly at first, in the wrong order. Of course I got a black screen on boot-up. Then, after we put them in the right order (#1 and #3 for the 1Gs, #2 and #4 for the 512 mB) the system booted and everything ran apparently OK.

However, I have since noticed some strange behavior with very large files. On Windows, I had a whole 30 G drive partition encrypted. I finally got this decrypted and created a very large (20 G) Truecrypt container on one of the USB external HDs and successfully manage to copy it from an 80 G external drive (formatted with NTFS on Windows XP) it to the internal HD running Ubuntu.  However, last night, when I tried to copy it back in case I need to do a re-install, the copy stopped prematurely and the GNOME window collapsed. Looking at the (external) drive which should contain the copied container, I saw only a 4 G file. I mention this because this is not the first time that copy commands have failed on such large files, and the result is always a 4G file. The physical memory (3G) and the swap (1.3 G) = approximately 4G is...well is that a coincidence?  

(As an afterthought, I really shouldn't have created such a large encrypted container, as I only use a small fraction of it...I could easily get by with 4 G and have lots of space to spare. It was just because the original was a whole drive partition was why I did it. I may just re-create a smaller one of my Windows laptop).

Anyway, I thought I would toss these items your way for consideration. I'll try to copy the relevant log files to a USB stick so I can read them and post them.

Stewart

---

### Post by raijinsetsu on 2007-09-12
Unless you're running 64-bit linux, or you've reconfigured your kernel, you will only be able to use 3gb of memory. In your case, the virtual memory will be completely ignored.
Also, it could be the external drives, but only if they are listed in your fstab file. Try turning them off and booting, see if that helps.
Have you tried running Memtest86 off the CD? It'll give you a pretty accurate indication if your memory is bad.
lastly, what device/partition was fsck reading when it crashed?
As far copying files, that could be many things. NTFS isn't exactly supported on Linux, and, although the ntfs-3g drivers appear to be stable, I don't know if they handle truecrypt containers or any such thing.
What is the destination partition type for the copy of those large files?

---

### Post by StewartM on 2007-09-12
> **raijinsetsu said:**
> Unless you're running 64-bit linux, or you've reconfigured your kernel, you will only be able to use 3gb of memory. In your case, the virtual memory will be completely ignored.
Also, it could be the external drives, but only if they are listed in your fstab file. Try turning them off and booting, see if that helps.
Have you tried running Memtest86 off the CD? It'll give you a pretty accurate indication if your memory is bad.
lastly, what device/partition was fsck reading when it crashed?
As far copying files, that could be many things. NTFS isn't exactly supported on Linux, and, although the ntfs-3g drivers appear to be stable, I don't know if they handle truecrypt containers or any such thing.
What is the destination partition type for the copy of those large files?

I'm running the latest version of Ubuntu Feisty 7.04; I have no idea what the kernel memory limit is.

I also don't know what device/partition fsck was reading; the Linux tech said that Inode error could well be an error on one of the external drives, which was why he suggested what he did. It's a simple matter to boot without the drives, just don't flip the power switches on them to "on". All that I know what was on the screen: it was searching os_part_. Which of course (correct me if I'm wrong) could include the external drives it found included in the /media/ directory.

(But, if it were the older of the two drives giving the problem, the one that is mysteriously disappearing, which is 30 G, again I note that the hangup is occuring at 12.4 %  through the check. And 12.4 % x 30 G = 3.7 G. Again, that's about 4 G. As if the system is saying "Hey, I'm out of memory, I'm giving up").

The destination drive I was copying to was an 80G formatted to FAT32 (I formatted it that way to avoid the permissions issue of ext3). The file partially copied (4G). If it were NTFS (which I know I can read but not copy to) I would have gotten a "permission denied" error; I've seen that previously when I was trying to copy things back and forth doing my transfers involving my dying Windows machine.  I've also noted the problem when trying to copy it to the 30G drive (FAT32), though that drive is now suspect (see above).  I have successfully copied that 20G container from the 80 G drive to the SATA drive with the OS (250 G) without a hitch. But I've also noted that when trying to create even 5 G Truecrypt containers (using Scramdisk for Linux) I have ended up with files truncated at 4 G even on the ext3 internal SATA drive containing the OS. I've succeeded, but it's not a sure thing.

I really need to reformat and partition that external 80G (FAT32) drive to include partitions < 32 G, so I can transfer stuff from the Windows XP laptop if need be (due to the Windows 32G FAT32 limitation. In case I need to do a reinstall.
 
These issues may or may not have anything to do with my current problem.

How long does a MemTest86 take to do? I started to do one, but it seems to be something you'd want to run overnight--it was taking forever. The results that were rolling off the virtual press, so to speak, weren't clear to me, though I guess if I let it finish it might give me a clear thumbs-up or down.

Stewart

---

### Post by StewartM on 2007-09-12
[QUOTE=StewartM;3354057]The Linux tech on my job (who's also a resource) and who knows how I've configured my system also suggests the following:

I have drives with data, no OS, from my old Windows setup connected via external USB-IDE interfaces. They were "on" during the boot-up. My tech friend thinks that the fsck may actually be searching these drives (in the /media/ directory on the os_part_?) and finding the errors there and that's what is hanging my system.

His first thing to try: turn off these two external drives while booting up. Let fsck only check the internal HDD and see what happens.

This sorta makes sense, as the older of the two drives has had recently this habit of mysteriously disappearing on the GNOME screen w/o warning.  I would count myself as very lucky if the fix was as simple as that.

/QUOTE]

It worked! At least the fsck passes and I get to the login screen.

However, the problem now is that I'm locked out of all my accounts becauase they're all owned by root. (apparently). How do I get them back?

Stewart

---

### Post by StewartM on 2007-09-13
> **StewartM said:**
> [QUOTE=StewartM;3354057]The Linux tech on my job (who's also a resource) and who knows how I've configured my system also suggests the following:

I have drives with data, no OS, from my old Windows setup connected via external USB-IDE interfaces. They were "on" during the boot-up. My tech friend thinks that the fsck may actually be searching these drives (in the /media/ directory on the os_part_?) and finding the errors there and that's what is hanging my system.

His first thing to try: turn off these two external drives while booting up. Let fsck only check the internal HDD and see what happens.

This sorta makes sense, as the older of the two drives has had recently this habit of mysteriously disappearing on the GNOME screen w/o warning.  I would count myself as very lucky if the fix was as simple as that.

/QUOTE]

It worked! At least the fsck passes and I get to the login screen.

However, the problem now is that I'm locked out of all my accounts becauase they're all owned by root. (apparently). How do I get them back?

Stewart

Ahh, a little more digging into past threads in these forums did the trick. Go into GRUB at boot-up, log in as root, set all the user account folder ownerships back to their home users, and to their home groups, and voila! It's OK now. 

Then I went and did as you recommended--created group "common" and put user1 and user2 in it, and set the group ID for /home/common/ to "common". 

Now that works, except I need to remember every time user1 or user2 saves a file into /home/common/ I need to update the group ID on that file (i.e., if saved there by user1, its ownership will default to owner=user1 group=user1 and user2 won't be able to write to it unless I open the terminal, change to root, and change the group ownership to "common").  Is there any way have everything written into /home/common/ default to having its group ID be "common"? 

It's not much of a  problem, I can work around it, but it would be a nice finish. :popcorn:

Stewart

---

### Post by raijinsetsu on 2007-09-13
On Fat32, no file may be larger than 4GB. It's a filesystem limitation. Nothing can be done about that...

As for having to manually set your group ID in the common directory, try this:
"cd /home"
"sudo chmod g+s common"
This will set the group sticky bit. What this means is: every file and directory created under "/home/common" will be assigned the group of "/home/common". In your case, any new files will be assigned to your "common" group. :)

---

### Post by StewartM on 2007-09-13
> **raijinsetsu said:**
> On Fat32, no file may be larger than 4GB. It's a filesystem limitation. Nothing can be done about that...

As for having to manually set your group ID in the common directory, try this:
"cd /home"
"sudo chmod g+s common"
This will set the group sticky bit. What this means is: every file and directory created under "/home/common" will be assigned the group of "/home/common". In your case, any new files will be assigned to your "common" group. :)

I bet you *that* explains my problem copying those large containers, and the inconsistencies I observed. I bet you when I copied from NTFS to ext3, it went OK, but from ext3 to FAT32, it crapped out at 4 GB. Thank you.

(I since have created new containers on my Ubuntu box of 3 GB or less for what I want, so these should be transferable to FAT32 or to anything but NTFS. It would be nice to be able to have them as Truecrypt that would be openable on removable media by either a Windows box or my Ubuntu one).

Thank you for the help on the group sticky bit; I think that solves my problems in regards to this thread (don't worry, more will follow). Thank you, you've been very helpful. Here, have some popcorn. :popcorn:

Stewart

---

### Post by raijinsetsu on 2007-09-14
Use the thread tools to mark this thread as solved :)

---

