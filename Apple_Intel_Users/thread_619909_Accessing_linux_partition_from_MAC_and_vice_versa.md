---
title: "Accessing linux partition from MAC and vice versa"
date: 2007-11-21
forum: Apple Intel Users
---

### Post by umneydurak on 2007-11-21
Hello.
I am planning dual booting Gutsy on my MacBook2,1, second generation?, GMA 950 chipset. Anyway is it possible to access linux partition from Mac, or Mac partition from linux?

Thanks.

---

### Post by volanin on 2007-11-22
[http://ubuntuforums.org/showthread.php?p=1922676#post1922676](http://ubuntuforums.org/showthread.php?p=1922676#post1922676)
:)

---

### Post by changuito on 2007-11-23
i just went through this. I want each partition to be accessible when i'm booted in the other with both write ability and proper permissions. I posted all my details, BOTH vice and versa, here

[http://ubuntuforums.org/showthread.php?t=614948](http://ubuntuforums.org/showthread.php?t=614948)

basically, in OSX you have to disable HSF journaling and install ext2fs system extension. 
In linux/ubuntu you have to format your partition as ext2 (disables journaling) if you want it to be writable by mac. then in linux change your user id to match that in OSX. you'll have some strange KDE/GUI behavior, it dosent want to graphically deal with user 501, but it seems fine from commandline (though i didnt not probe it too much) and everything seems stable with the desired result achieved.

for anyone more knowledgeable about these things (or anyone more bold than I), there are still 2 questions in my post that are open, namely:

1.
while seeing no confirmation of this anywhere in anything i've read, i infer that (as for journaling on the mac partition) journaling (ext3) forces mac to see the ext3 partition as read-only. Is this true? Reading some other posts, people have apparently given up on writing to ext3, i've seen no accounts of making ext3 writable.

2.
the new issue in Ubuntu is that Ubuntu is confused (or something) when dealing with the user ID 501. As mentioned, the account is not listed at login in the list but you can still login. Going into system preferences -> user management also fails to show the account! WTF? Is there something in the interface that needs the userid number to be greater equal to 1000? WTF? Is this behavior expected? Is this a bug? Is it safe to use this configuration?

---

### Post by bonestonne on 2007-11-23
I found a driver this morning that helped me out tons, accessing Ext3 from HFS+

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

i'm using the beta Universal binary driver and i can read Ext3, i haven't tried to write with it yet, I'm running OS X 10.4.10 Kernel 8.10.1 and there were no issues after the restart for me. in the past i've had kernel panics after installing software, so this is a plus.

Reading HFS+ from Ext3 however, i have not found a driver for that. if/when i do i'll post a link for it.

triple booting a mac pro was hard enough, cross platform compatibility is worse!

---

### Post by timcredible on 2007-11-23
> **changuito said:**
> 
the new issue in Ubuntu is that Ubuntu is confused (or something) when dealing with the user ID 501. As mentioned, the account is not listed at login in the list but you can still login. Going into system preferences -> user management also fails to show the account! WTF? Is there something in the interface that needs the userid number to be greater equal to 1000? WTF? Is this behavior expected? Is this a bug? Is it safe to use this configuration?

not a bug - by default, the user management program is configured to only look at UIDs >= 1000.  there's a config file to change that, but i don't remember what it is.

---

### Post by aletheianalex on 2007-11-26
> **bonestonne said:**
> I found a driver this morning that helped me out tons, accessing Ext3 from HFS+

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

i'm using the beta Universal binary driver and i can read Ext3, i haven't tried to write with it yet, I'm running OS X 10.4.10 Kernel 8.10.1 and there were no issues after the restart for me. in the past i've had kernel panics after installing software, so this is a plus.

Reading HFS+ from Ext3 however, i have not found a driver for that. if/when i do i'll post a link for it.

triple booting a mac pro was hard enough, cross platform compatibility is worse!

If you turn off journaling in OSX, you should be able to do it, but it won't work right (or at all) with OSX journaling on.

And be careful with that ext2fs extension... it is really the only option, but it has crashed my system.  I wish Apple would just support the format natively... there have been add-on extensions like MountX from the 90's that would mount Ext2 on Mac OS 8, but no native support... and MkLinux from Apple in the mid 90's had native support for HFS back in osf kernel version 2.0.3!!

> not a bug - by default, the user management program is configured to only look at UIDs >= 1000. there's a config file to change that, but i don't remember what it is.

Match UID's Ubuntu with osx through 'usermod' as root... that is how to do it in Debian, so i imagine it is the same.  You can check your UID's in OSX through the 'netinfo manager' in your utilities folder

---

### Post by cyberdork33 on 2007-11-26
> **changuito said:**
> while seeing no confirmation of this anywhere in anything i've read, i infer that (as for journaling on the mac partition) journaling (ext3) forces mac to see the ext3 partition as read-only. Is this true? Reading some other posts, people have apparently given up on writing to ext3, i've seen no accounts of making ext3 writable.

Read AND Write to ext3 from OSX used to work fine for me, but I have not been able to write to my ext3 partitions since I upgraded to Leopard. I do not know if the change is a result of Leopard or not, but the driver has never been all that reliable anyway... It is really the only option though.

There is no 'driver' needed to access HFS+ from linux. The capability is part of the linux kernel.
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by GeneralSunTzu on 2007-11-26
> **cyberdork33 said:**
> Read AND Write to ext3 from OSX used to work fine for me, but I have not been able to write to my ext3 partitions since I upgraded to Leopard. I do not know if the change is a result of Leopard or not, but the driver has never been all that reliable anyway... It is really the only option though.

There is no 'driver' needed to access HFS+ from linux. The capability is part of the linux kernel.
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

I can confirm. 
On a dual boot (10.4.11 Mac OS X and 7.10 Ubuntu) there is no need to do exotic manipulations whatsoever.
I am perfectly capable to copy files from any Mac OS X folder to any Ubuntu folder.
And, yes, my OS X partition is and always was journaled.

---

### Post by changuito on 2007-11-26
I'm not clear on what you are saying.

> my OS X partition is and always was journaled.

is your linux partition ext3?

copying from the osx partition to the ubuntu partition dosent mean that the osx partition is writable from within ubuntu. or were you copying this way from within osx? That is more a statment about ext3 beig writable fro within OSX. 

which ever is the case, can you give more details? I'd really prefer to have journaled filesystems. right now neither is.

---

### Post by cyberdork33 on 2007-11-26
> **changuito said:**
> which ever is the case, can you give more details? I'd really prefer to have journaled filesystems. right now neither is.

The Linux HFS+ module does not support writing to a journaled FS. This is for the security of you data.

---

### Post by aletheianalex on 2007-11-26
> **cyberdork33 said:**
> The Linux HFS+ module does not support writing to a journaled FS. This is for the security of you data.

Correct.  I think that Roman Zippel maintains the project... or at least is one of the maintainers.  if you trace the conversations, they have been gradually moving toward full support: first read only, then read/write, and eventually read/write to journaled volumes, but it is disabled for now because you can easily screw up the volume since the kernel module still at this point can't replay the journal to confirm... so it is dangerous... although you can hack the ability into it if you really want to screw up your disk that badly ;)

Same it's the same deal with Ext3 journaling under OSX.

Can it be done right now?  Yes, if you really want it and want to do the hacks yourself.

SHOULD it be done?  if you want to live dangerously, sure... but as for me, NO!! I have journaling off until support is better.  Like I said, I have had some crashes (kernel panics) ... and under Tiger... with the ext2 extension, and Leopard has been reported to wipe-out disks.

---

### Post by hardawayd on 2007-12-15
> **GeneralSunTzu said:**
> I can confirm. 
On a dual boot (10.4.11 Mac OS X and 7.10 Ubuntu) there is no need to do exotic manipulations whatsoever.
I am perfectly capable to copy files from any Mac OS X folder to any Ubuntu folder.
And, yes, my OS X partition is and always was journaled.

I would like to know how you have done this. I have a new MBP with leopard and have installed gusty. When i try to open the documents folder on the mac from gusty it says i do not have permission to read it.  I am only interested in reading not writing between systems. Any ideas?

---

### Post by cyberdork33 on 2007-12-15
> **hardawayd said:**
> I would like to know how you have done this. I have a new MBP with leopard and have installed gusty. When i try to open the documents folder on the mac from gusty it says i do not have permission to read it.  I am only interested in reading not writing between systems. Any ideas?

since your Mac 'user' owns that folder, other users cannot read it. You need to go edit the permissions on that folder in OSX. Or you can just use root (sudo) to access the files, but that could be dangerous if make a mistake.

---

### Post by Fuz2y on 2008-04-12
I have achieved a method that works great to mount ext3 partitions on OS X Startup

[http://fuz2y.blogspot.com/2008/04/how-to-mount-ext3-partition-on-os-x.html](http://fuz2y.blogspot.com/2008/04/how-to-mount-ext3-partition-on-os-x.html)

Enjoy &#12484;

---

