---
title: "Dualboot OS X/Feisty: Disk sharing and permissions"
date: 2007-04-18
forum: Apple PPC Users
---

### Post by bogoliubov on 2007-04-18
Hello. I dualboot OS X and Feisty on my iBook G4. I use the computer at work, but there I only run OS X.
The reason is that it's a hassle to keep track of filechanges if I do something in Ubuntu.

I mount the OS X drive, but I won't get write permissions to my (OS X) files without giving all users in OS X write permissions.

Is there a way to mount the OS X disk to that I appear to be the owner of my OS X files? I have the same username in both OS:es, should that make a difference....


If this worked I could really try Ubuntu for work, which I want to do!  OS X eats too much memory and is slower...

---

### Post by kidders on 2007-04-18
Hi there,

> **bogoliubov said:**
> I have the same username in both OS:es, should that make a difference.It doesn't, actually. On filesystems that support permissions/ownership, OSs pay attention to UIDs, not usernames. If your Ubuntu & OSX UIDs are the same, your shared filesystems will work as expected (assuming you're using HFS+).

---

### Post by bogoliubov on 2007-04-18
> **kidders said:**
> Hi there,

It doesn't, actually. On filesystems that support permissions/ownership, OSs pay attention to UIDs, not usernames. If your Ubuntu & OSX UIDs are the same, your shared filesystems will work as expected (assuming you're using HFS+).

Ok, so how can I check my UID? I've heard that it's dangerous to change the UID, so how should I do if I want the permissions to work in both OSes?

---

### Post by kidders on 2007-04-18
Hey again,

> **bogoliubov said:**
> Ok, so how can I check my UID?You'll find it in /etc/passwd, among other places. (**grep `whoami` /etc/passwd | cut -d: -f3**, for instance, should work on both OSs.) OSX starts numbering its users from about 500, whereas Linux tends to start around 1000 ... but for no particular reason, in either case.

> **bogoliubov said:**
> I've heard that it's dangerous to change the UIDI wouldn't exactly use the word "dangerous" ... but it's certainly not trivial. The best thing would be to have synced UIDs the moment the second of your two user accounts was created.

For simplicity, I would suggest creating entirely new accounts on each of your systems, rather than trying to change the UIDs of existing ones. In a week or so, once filesystem ownerships have had a chance to stabilise, you can remove the old accounts. Again, for simplicity, I would recommend using a new shared UID greater than about 1100.

Once you've created the new accounts, you'd be where (ideally) you ought to have been on day one ... except that you'll have lots and lots of files to move around, that both OSX and Linux will try to stop you accessing. If this isn't the sort of thing you've done before, you need to approach it slowly and carefully ... impulsive use of **sudo** can break things!

On both systems, you'd be interested in copying and reassigning ownership of things like mail, personal settings, and so on.[LIST]
[*]**Do not** manipulate the settings of any application, while its open ... that includes Finder, Gnome, KDE, etc.
[*]Always copy with **sudo cp -dpR** (ie never move stuff) ... so you can take a second stab at something that goes wrong.[/LIST]The approach I recommended against (simply because I'm not 100% sure that small issues wouldn't arise long-term) would be to boot in single user mode on both systems, alter all references to the old UIDs in /etc, and **chown** everything in ~. This way is certainly a lot quicker ... I just couldn't swear it'd be a good idea! (You seem to agree.) The choice is yours however.

In either case, the end result would be that the permissions of any files created by either OS, on any device that supports ownership, would be completely consistent. NFS shares between the two OSs would also behave sensibly ... although in a dual boot environment, that won't matter.

---

### Post by bogoliubov on 2007-04-18
Ok, thanks for the help.
I'm not sure if I'll try this road or not. It sounds like several things can go wrong which would mean to fix new users in both OSes. I'm not very keen on that since I've tweaked my OS X account quite a bit...

But would it be possible to, say, have a special partition (not /home or /Users) that both OSes can share? If needed one can work on your own home folder and sync it with this extra partition once in a while...?!

---

### Post by kidders on 2007-04-18
> **bogoliubov said:**
> Ok, thanks for the help.
I'm not sure if I'll try this road or not.Yeah, I can understand that. It may be the technically "correct" solution to your problem, but it is very much more complicated than other possible options.

One option would simply be to override filesystem permissions in one OS or the other ... something which should be done with caution. Another possibility is this ...

> **bogoliubov said:**
> But would it be possible to, say, have a special partition (not /home or /Users) that both OSes can share?

This is the sort of thing a Windoze user might do, as a messy compromise that would allow him to avoid using ntfs-3g, or ports of Ext2 drivers. You could create a FAT, HFS+, or other filesystem which either doesn't support ownership/permissions, or is explicitly configured to disregard them. Where that filesystem is would be irrelevant ... if you have no more unallocated space on your hard disk, you might want to store it as one big file on a pre-existing filesystem.

Essentially, there are lots of ways of side-stepping your problem (all of which are quick & easy), but only one way of actually solving it. Which approach you'd prefer to take is entirely up to you.

**Edit:** Incidentally, I wonder what would happen if you mounted your /Users partition in Linux, and then rebind-ed your home directory to a second mount point, with new mount options that overrode filesystem permissions. (Does that make any sense?)

---

### Post by domino on 2007-04-21
I have a heavily tweaked Tiger also and changing UID isn't really an option. I went the way of Mac-FUSE/FUSE/NTFS-3G since it's pretty stable on Mac PPC/Intel and Linux. However, I find that OS X writing to an external USB2 NTFS drive is still slower than it's Linux distro counterpart. R/W access on internal drives or partitions is very good in both OS.

There is also a application that works well for PowerPC. It's called ExtFSManager. What it does is mount EXT 2/3 filesystem under OS X which supports both read and write.

---

### Post by kidders on 2007-04-21
Hi domino,

Your post is interesting...

> **domino said:**
> changing UID isn't really an option.It's hard to imagine a situation in which simply adding a new account (or changing an existing one) wouldn't be an option. When faced with the prospect of habitually using a filesystem native to neither platform (NTFS of all things!), it certainly seems like the better choice. Given how precious many peoples' files are, don't you feel it's hard to justify voluntarily using non-native filesystems, when standard alternatives exist? NTFS doesn't even have proper support for the features of either OS the o/p is using.

I suppose it just sorta seems logical (to me) that, where a problem arises because two numbers aren't equal, the sensible thing to do is to *make* them equal, rather than circumventing the problem with non-standard hacks. Of course, everyone's different ... that's just my 2 cents hehe. :-)

---

### Post by domino on 2007-04-21
Simply put, I trust FUSE/NTFS-3G. I've tested it on a virtual environment for quite a while. Then went native and have had no problem with it the past 6 months. My original OS X account has not changed since installing 10.4. Having to get acclimated to another user environment simply just won't work "for me". I'm a creature of habit and it would take quite some time to replicate my orig UI and settings.

I trust Linux just as much as OS X, but I do not trust the hardware makers. That said, all precious materials go on a centralized file server also.

> NTFS doesn't even have proper support for the features of either OS the o/p is using.
So true.. I guess my post wasn't intended for the op. I just got a bit carried away with adding Windows in the mix since I do work on all the operating systems at our building and I need the flexibility to be able to write backed up and recovered files to an external media.

Aggguhh getting way off topic. I'm sorry for highjacking your thread bogoliubov. I must get seep. You can ignore this useless post, but i'll post it anyway since I've already spent 7 minutes writing it. :rolleyes:

---

### Post by kidders on 2007-04-21
> **domino said:**
> Aggguhh getting way off topic. I'm sorry for highjacking your thread bogoliubov. I must get seep. You can ignore this useless postEeep no! It's nice to have as many options as possible, imo. That's the Linux way! :-)

Now we wait, with baited breath, to see what bogoliubov decides hehe.

---

### Post by rccharles on 2007-04-22
> **bogoliubov said:**
> Ok, so how can I check my UID? I've heard that it's dangerous to change the UID, so how should I do if I want the permissions to work in both OSes?

You can change the permissions of files and directories in either OS.

I suggest you create a backup administrator id's on each system that you are changing!!!

Mac OS X ... harddrive -> Applications -> Utilities -> terminal
Ubuntu ... Applications > Accessories > Terminal

Your current user is:
echo $USER
Let's assume myuser

 To find out your UID and GID do:

ls -ln
ls -l

compare the output and write down what you find.


You best use the numeric value for your userid.  In this case it is 500.  To list all the files owned by a userid do:
sudo find / -user 500 -exec ls {} \;
/* adding a -x before the / limits the search to the current file system. */

Mac OS X ... harddrive -> Applications -> Utilities -> NetInfo Manager
In the middle column is the function.  Pick users then select your user.  Click on the lock at the bottom of the panel. Go into the property list and change UID and GID.

In the Ubuntu terminal, 
man 5 passwd  
   ... will give you the format of the passwd file.
sudo nano /etc/passwd

  ... the format is user-name, password, uid, gid, ...

control-o
  ... to save
control-x
  ... to quit

The groups are defined in /etc/group
cat /etc/group

Now change the UID and GID of all files:
You best use the numeric value for your userid.  In this case it is 500.

sudo find / -user 500 -exec chown 1100:211 {} \;
/* Where chown has the format of chown uid:gid */


On the Mac you get into single user mode by holding down command-s when you poweron your machine. Just in case you run into problems.

Robert

---

