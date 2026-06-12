---
title: "Backing Up Compressed File To An External Hardrive!!"
date: 2010-04-21
forum: Apple Hardware Users
---

### Post by freesparks on 2010-04-21
Hello All,

 I am attempting to be careful in case my system crashes, and although highly unlikely my first question is if there is a way to first compress my Linux Partitions.  After running the diskutil command in OSX's Terminal,  I basically end up with this poartition scheme:


> Macintosh HD       =                130GB
disk0s3                 =                1MB
disk0s4                 =               30GB
Linux Swap           =               1.3 GBI am sure there is a way in the Terminal to first compress disk0s3, disk0s4, and Linux Swap, and then output the compressed partitions into my external Harddrive.  I have already read some of the suggestions that only /HOME, /etc/fstab/, list of installed packages, /opt, and /var/cache/apt/archives/-where all installed packages are stored, is what I should backup.  But, please correct me if I'm wrong. -----Wouldn't it take quite a while to install all those packages again in case of a system failure.  Or would it just be easier to untar all of them in their directories once Linux has been reinstalled.

The closest command I have found so far in being able to achieve this is:

> sudo tar cvf - files | (cd target_directory ; tar xpf -)The above code is very suitable for what I am looking for because it enables you to copy files into another location by using the tar command where you would create In my case the new location would be my external harddrive.  My external harddrive already has its own Linux partition which I am able to mount in Linux and that Linux sees as free space.

Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by linuxopjemac on 2010-04-21
Why don't you use Clonezilla ?

---

### Post by freesparks on 2010-04-21
Just one question, will Clonezilla play nice with my OSX backup partition that resides on that same External USB hardrive?  Or will it wipe out both in an attempt to take full advantage of it.?  Again, the harddrive has 2 partitions, one that I've made for OSX, which already has my entire OSX clone on it, and the other is reserved for Linux.  Thanks so much for the quick reply!!

Best Regards,

freesparks

---

### Post by linuxopjemac on 2010-04-21
Clonezilla can make a complete copy of a hard disk, no matter which operating systems are on it. Yuu need more than just a USB stick though, an extra USB drive will do. You can also select to only clone certain partitions. It will be saved in a compressed format.

I recently restored a complete Linux partition on a MacBook with this tool.

But I guess your script will also do a good job, if you are only interested in data in /home for example.

---

### Post by freesparks on 2010-04-21
Again, thank you for the quick reply.  Upon downloading the .iso file,I noticed there's 2 files that are bing downloaded: a clonezilla-live.iso, and a clonezilla-live.iso.part.  I am not too familiar with burning iso to CD but is it just a mattrer of launching Brasero Disc Burner and using the burn image option?  Also, am I burning both of these files to the samer disc?  

Best Regards,

freesparks

---

### Post by linuxopjemac on 2010-04-21
Just wait, the part wil disappear once your download is complete. Don't forget to md5sum it.

---

### Post by freesparks on 2010-04-21
Hello,can you expound on where I use the md5sum command.  It seemed to have burned correctly but I am afraid to go through with the instructions that I found on Clonezilla's website.  I am mobile now and the only thing I can tell you is I did not use the md5sum command on anything.  I simply launched the Brasero Cd burning software, and then I burned it to CD as an .iso image--and all the files are there even the executable.  My question is what do I do now exactly step by step because I usually install software via Synaptic Package Manager.  I have gotten 2 very detailed books on Linux and Ubuntu specifically and am reading them diligently, but just need your help to ensure that I do not wipe out my external, nor my internal harddrive at that.  And, yes, you're right the file went away. :P  I really appreciate your time and expertise, I just need some step by step help because I am in the middle of a big project now and can't afford to have any problems.
 
Best Regards,
 
freesparks

---

### Post by linuxopjemac on 2010-04-22
well, clonezilla is a livecd. You have to boot from it. Then you can clone the contents of your hard drive to some other media. 

[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)

---

