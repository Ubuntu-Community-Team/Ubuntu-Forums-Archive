---
title: "[SOLVED] HELP! I keep digging the hole deeper!"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by RamR on 2008-04-06
I am a fairly recent convert to Ubuntu and find myself in a hole that seems to keep getting bigger.

Initially, I wanted to change my drive partition using Gparted and was relatively successful following the guide at this link [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) .  Near the end of the process I made an unfortunate error that has lead to a series of problems.  When near the end of the guide the istruction gets us "to specify to use the new home partition as /home" I forgot to change the partition in this command "/dev/hda7 /home ext3 nodev,nosuid 0 2" to the one that is specific to my setup.

After a bit of tinkering in recovery I fixed that but Ubuntu would still not boot correctly and I got the error "user's $HOME/.dmrc file is being ignored..." and was told that "Files should be owned by user and have 644 permissions".

Then with a bit more searching I found this series of Terminal commands; 

touch .dmrc
sudo chmod 644 .dmrc
sudo chown <username> .dmrc
sudo chmod 755 /home/<username>
sudo chown <username> /home/<username>

which allowed me back into the OS.  Unfortunately, once back in I found a few things that were indicating more problems.  First of all, Firefox won't start as it thinks it is already running but not responding.  Secondly, I have lost permission to many files and directories in /home.  I can't even empty the trash because I don't have enough permission.

Any help would be greatly appreciated.  If there is any info I can provide that will make the problem clearer to understand just direct me to it and how I can post it.

Thanks

---

### Post by seshomaru samma on 2008-04-06
I hope someone more profficent then me can help you edit your fstab 

but if for some reason the problem is not solved it would probably be wise to revert back to the original state
in the link you provided you are told to make a backup of the fstab file (fstab_backup)
providing you followed the link without missing any steps you should be able to revert by booting from a live CD and issuing the following commands:
```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
```

---

### Post by RamR on 2008-04-06
I'm reluctant to give up so soon.  Digging these holes is one of the frustrations I have found with Ubuntu but one of the rewards is eventually getting out of the hole.

In case the /etc/fstab needs to be edited here it is.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8b109e2d-8f40-42dc-aaef-156932350663 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ecd2b372-ae8c-4c2e-8603-5b014f535937 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda4 /home ext3 nodev,nosuid 0 2
```

---

### Post by RamR on 2008-04-06
I've been able to change some of the permission to files through nautilus.  Still don't have permission to delete trash.  Not sure if this approach is even going to solve my problem.

I still can't get Firefox to work.

How do I make sure that the home partition is set to where I think it is... that is the new partition that I created?

---

### Post by RamR on 2008-04-06
Fixed the problem with Firefox... still not sure if these fixes are helpful or not.  The problem with Firefox was that I didn't have permission for /home/.mozilla .  I did a chown to fix that but the bigger question is why I didn't have the permission for /home/.mozilla .  

Any thoughts?  Anyone?

---

### Post by Moop on 2008-04-06
When you have a separate home partition it's easy to just reinstall and save your /home. All your data and configuration will be saved and you will just need to reinstall applications. 

It's not the most elegant solution but it will work.

---

### Post by RamR on 2008-04-06
How do I know if the partition I have set up as the /home partition actual is working as that?  I suspect it is as when I go to place and home folder it brings up the files on the partition I created.  At least I think it does, how can I be sure about this?  Also, is this a sure way to make sure that the /home is where I think it is?

---

### Post by bodhi.zazen on 2008-04-06
you need to change ownership of all files in home :

```
sudo chown -R name.name /home/name
```

where name = is your user name.

---

### Post by RamR on 2008-04-06
Just did ctrl+alt+backspace to see if I would get back on and I did.  However, when I went to the Home Folder through "Places" I got the following error.  I suspect it might be helpful but I can't make sense of it.

```
GConf error: Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/nautilus/preferences/navigation_window_saved_maximized' set in a read-only source at the front of your configuration path
```

Also, I have been deleting files and they don't appear in the Trash bin that I am having troubles with.  Might this be a Trash bin connected to the backup Home that I made?  If so how do I get the active one?  If not where are the files going that I am deleting?

---

### Post by RamR on 2008-04-06
> **bodhi.zazen said:**
> you need to change ownership of all files in home :

```
sudo chown -R name.name /home/name
```

where name = is your user name.

That gave me access to everything that comes up when I type the command *ls -la* .  Is that what I want?  If so, thanks a bunch.  Do you think this is the solution to my problems?  Will the OS run as it should now?

Thanks to everyone for help so far.

---

### Post by bodhi.zazen on 2008-04-06
> **RamR said:**
> That gave me access to everything that comes up when I type the command *ls -la* .  Is that what I want?  If so, thanks a bunch.  Do you think this is the solution to my problems?  Will the OS run as it should now?

Thanks to everyone for help so far.

That should be all it takes. It looks like it was a permissions problem.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by The Cog on 2008-04-06
The command **mount** will display what is mounted and where. Then you can check that /home has a separate partition mounted on it. Actually, **df -h** is probably easier to read.

---

### Post by RamR on 2008-04-06
Looks to be working properly... just hoping I don't have permission to something that I shouldn't.  

Next step will be to shrink the original ubuntu partition down to the smallest size advisable and then use the leftover portion to join with the new /home partition... if that all is possible.  Spent all day trying to fix this problem so I think I will be leaving this next bit until tomorrow.  Feel free to make suggestions while I'm gone however... hahaha.

After I get the partitions all sorted it's back to trying to get my s-video connection to hook up to my TV as a dual monitor.

Things are looking up and I think if things are fine when I get up in the morning I will have to change the Title of this thread and open up another for my next problem.

This community is truly the greatest advantage of Ubuntu. :)

---

### Post by RamR on 2008-04-06
System seems to have made it through the night.  I'm calling it solved.

---

### Post by AndrewEsther on 2008-04-06
I am having the same problem, but mine is stemming from the fact that I changed my user's home directory to / because I was tired of not having control of a certain folder, and in my fit or rage, decided that I would try to give myself ownership of the entire drive. Turns out it didn't work well.........

any help?

---

### Post by bodhi.zazen on 2008-04-06
> **AndrewEsther said:**
> I am having the same problem, but mine is stemming from the fact that I changed my user's home directory to / because I was tired of not having control of a certain folder, and in my fit or rage, decided that I would try to give myself ownership of the entire drive. Turns out it didn't work well.........

any help?

The best solution is to re-install. It is possible to restore ownership and permissions to system files, but you need to know what you are doing and it takes hours and even in experienced hands may be problematic or incomplete. Backing up your data and reinstalling is much easier and less time intensive.

---

