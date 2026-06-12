---
title: "Success! Sharing home partition between Ubuntu/OS X"
date: 2007-06-28
forum: Apple Intel Users
---

### Post by thully on 2007-06-28
A few days ago, I posted about sharing a home partition between Ubuntu and OS X.
I finally got around to working on it, and indeed it CAN be done!  The same exact partition
is used for both, with /home/user in Linux corresponding to /Users/user in OS X.  Permissions work fine, and no symbolic links are used - the entire thing is done with mountpoints.  The only issuemay be dotfile conflicts, but that is really only a problem for those who use OS X's Terminal often. However, these is some work involved to get this working.  Once set up, though, this is quite nice for dual-booters...

First of all, there is partitioning.  To do this, one will have to create a case-sensitive, non-journaled HFS+ partition for the home partition - it's the only filesystem both OSes work with well enough to use as a home partition.  Of course, you'll also want to create journaled HFS+ and ext3 partitions for the OS X and Linux installs, respectively.  Install both OSes to their respective partitions, and then you'll be ready to start the setup.

WARNING - Try at your own risk!  If done wrongly, it could mess up your Linux/OS X installs!  Make sure your data is backed up before attempting!

Setup on the Linux side:
1. Change your User/Group ID to match Mac OS X (sudo groupmod -g 501 yourid;sudo usermod -g 501 yourid;sudo usermod -u 501 yourid)
2. Reclaim ownership of your home directory (sudo chgrp -R yourid /home/yourid/*;sudo chmod -R yourid /home/yourid/*;sudo chgrp -R yourid /home/yourid/.*;sudo chmod -R yourid /home/yourid/.*)
3. Manually mount the new home partition somewhere (sudo mnt /dev/sda<whatever> /mnt)
4. Copy everything from /home to the new partition (cp -R /home/* /mnt)
5. Edit /etc/fstab and add the new partition (<device name>   /home           hfsplus defaults        0       1)
6. Rename /home to /home-old
7. Reboot and cross your fingers - if you have problems, check the permissions and device filenames.

Setup on the OS X side:

1. Copy everything from /Users to the new home partition (sudo ditto -v -rsrcFork /Users /Volumes/<our volume here>)
2. Find out what device node our partition corresponds to (df -k)
3. Edit /etc/fstab and add the partition (<device node> /Users hfs rw 1 2)
4. Run niload (sudo niload -m fstab / < /etc/fstab)
5. Reboot in single-user mode (Command-S on boot)
6. Do /sbin/mount -uw / to mount root read-write
7. Do mv /Users /Users-old;mkdir Users;chmod 755 Users
8. Do mkdir /Users
9. Reboot (reboot at command prompt) and cross your fingers

Comments welcome - I know this may not be the most stable setup in the world, but it's nice to have *one* home directory instead of two, and it seems like it would be great for dual-booters.

---

### Post by ivesjd on 2007-06-28
Very very nice, next time I reinstall I'm gonna give this a try.

---

### Post by kzm. on 2007-06-28
> Very very nice, next time I reinstall I'm gonna give this a try.

my thoughts... would it make sense to do it afterwards too, i wonder. may be i should try it and just copy everything from my home to it and empty my home.. would that break symlinks?

---

### Post by ronocdh on 2007-06-28
Candidate for a sticky! This is fun. Maybe with an appropriate warning "for advanced users only."

---

### Post by cyberdork33 on 2007-06-28
> **ronocdh said:**
> Candidate for a sticky! This is fun. Maybe with an appropriate warning "for advanced users only."

Yea, I don't know that I will even do this. I have never had a lot of luck having a shared home partition. Just make a separate storage partition, and symlink pictures, music, etc from your home folder to the appropriate storage folder. To each his own!

---

### Post by ivesjd on 2007-06-28
@cyberdork, But how big is your harddrive? On a 60gb'er it makes a bit of sense to do.


I'm working on doing it now. Decided to reinstall. (didnt have anything planed for the weekend) I will post back when I get it working. (or dont get it working)

---

### Post by ivesjd on 2007-06-28
First try didnt go so well. When trying to reclaim my ~ I ended up with no uid 1000 in passwd file. So there was no sudo. Oh well, reinstall and try again :P

---

### Post by cyberdork33 on 2007-06-28
there is just the possibility of running into issues with config files and such in your home directory... probably not as much between OSX and Linux... I just think there is an easier solution to the problem without taking anymore space, but as I said, to each his own.

---

### Post by alloydwhitlock on 2007-06-28
I've been trying to do this for days!  After seeing the guide, it looks like how I was modifying the permissions on the Linux side was incorrect.  I found some info on changing the UID on the Mac side, but I could see that having more issues.

Great job!   :KS

---

### Post by thully on 2007-06-29
If anyone is having trouble, try opening a sudo shell with sudo su and doing all the permission-changing operations in that - that way you don't lose sudo after changing the uid.

---

### Post by Gen2ly on 2007-06-29
> **cyberdork33 said:**
> there is just the possibility of running into issues with config files and such in your home directory... probably not as much between OSX and Linux... I just think there is an easier solution to the problem without taking anymore space, but as I said, to each his own.

I'm with cyberdork.  Do this at your own risk.  Most likely this is a candidate for disaster.  You can look at OS X and Linux as forks of one another that broke apart a long time ago.  It is likely, though I haven't looked, that OSX and Linux will have the same name for a preference (those .name) files, and it is very likely they don't write to them the same way.  For instance I think there is a "bash" preference for each.  The Gentoo Linux Wiki, if you want to look it up will show you how to make a third partition a shared one, but not as a home directory.

> **alloydwhitlock said:**
> I've been trying to do this for days!  After seeing the guide, it looks like how I was modifying the permissions on the Linux side was incorrect.  I found some info on changing the UID on the Mac side, but I could see that having more issues.


If you really surely have the need to change the user ID's I would do this from the LiveCD following installing:

```
useradd -m -u 501 -G adm,audio,cdrom,cron,portage,users,usb,video,wheel -s /bin/bash USER
```

Obviously use the groups you have in Ubuntu (I'm using Gentoo.)  Use the command "id" to see what they are.

---

### Post by pxwpxw on 2007-06-29
Did I miss something? Well, maybe only in Apple Intel?  This from a G5 runnung  10.4.8 -

mac03:/Users/peterc admax$ ls /etc/f*
/etc/find.codes /etc/fstab.hd   /etc/ftpusers


mac03:/Users/peterc admax$ cat /etc/fstab.hd 
IGNORE THIS FILE.
This file does nothing, contains no useful data, and might go away in
future releases.  Do not depend on this file or its contents.
mac03:/Users/peterc admax$

---

### Post by cyberdork33 on 2007-06-29
> **Dirk.R.Gently said:**
> I'm with cyberdork.  Do this at your own risk.  Most likely this is a candidate for disaster.  You can look at OS X and Linux as forks of one another that broke apart a long time ago.  It is likely, though I haven't looked, that OSX and Linux will have the same name for a preference (those .name) files, and it is very likely they don't write to them the same way.  For instance I think there is a "bash" preference for each. 

Exactly. I am very sure some of them are the same name because they use the same applications... .nano_history, .bash*, .profile, etc. and the configuration of bash is setup differently in both. Also, Dirk, on a side note, can you post the stuff to colorize the terminal from gentoo? I came from gentoo awhile back and always liked how they colored everything. Maybe this needs to be a new thread.

Ok back on topic.

**@pxwpxw** 
I was unaware that OSX actually used the fstab, and your output supports this. Thully, what version of OSX are you using?

Also, on the sudo note... once your sudo su or whatever to get a root prompt, run 'passwd' to set the root user password, then you can just login as root at the terminal, then there is no dependence on sudo at all.

---

### Post by thully on 2007-06-29
It's /etc/fstab - which doesn't exist by default in OS X - not /etc/fstab-hd.

Also, to respond to concerns that there will be configuration conflicts - this should ONLY be an issue if you use the UNIX part of OS X heavily.  OS X programs (meaning Carbon or Cocoa apps as opposed to X11 apps)don't use dotfiles - the only thing that does is the UNIX subsystem/X11.  

So yes, if you use MacPorts/Fink, definitely avoid this.  But otherwise, I don't think this will be an issue - honestly, I'm more concerned that Linux might eventually have problems with case-sensitive hfsplus write support.  In that case, a safer alternative may be to symlink all of the subdirectories of home (Music, Movies, Documents, Desktop, etc) to a shared FAT32 partition.  You wouldn't be able to save your settings across reinstalls then, though.

---

### Post by thully on 2007-06-29
BTW, I'm using 10.4.10 - and the fstab is only used ifthe user wants to define custom mount points (hence its default nonexistance).

---

### Post by pxwpxw on 2007-06-29
So is it strictly an intel version macosx10,4 variation?

---

### Post by cyberdork33 on 2007-06-29
> **thully said:**
> It's /etc/fstab - which doesn't exist by default in OS X

Good to know.

---

### Post by cyberdork33 on 2007-06-29
> **pxwpxw said:**
> So is it strictly an intel version macosx10,4 variation?

Don't exactly know what you mean, but it should be the same on either hardware.

---

### Post by Gen2ly on 2007-06-29
Sure, I list the bash script were I believe that information.  I wont' have an oppurtunity till tomorrow though.

---

### Post by pxwpxw on 2007-06-30
I just meant, can we use this on an Applemac G5 (not intel) because its a very neat idea., wihout rocking the boat for macosx10.4.8...  and Darwin.

Edit: answered I think on re read.

---

### Post by flaggh on 2008-05-01
I was thinking about doing this on a newer macbook.  Has anybody run into any problems sharing the home directory?  Do you think there is an advantage to doing it this way as opposed to using symbolic links?

---

### Post by cyberdork33 on 2008-05-01
> **flaggh said:**
> I was thinking about doing this on a newer macbook.  Has anybody run into any problems sharing the home directory?  Do you think there is an advantage to doing it this way as opposed to using symbolic links?
I have always recommended against it, buy many have gotten it working.

There is a new Apple forum now. Please post there:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

