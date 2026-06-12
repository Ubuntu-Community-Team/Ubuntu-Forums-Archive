---
title: "Canon 5000F Scanner Driver"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by kencoburn on 2007-01-11
After years of using Windows I thought it would be a good idea to get to know Linux.  I installed the Ubuntu distro and then tried to use my Canon 5000F scanner.  I opened Xsane Image Scanner but got a message stating that no device could be detected.  However, it is attached to my computer via USB port and works okay under Windows.  The Canon site does not list a Linux driver.  Does anyone know how to fix this?

Incidently, I can't access my NTFS drive either and can't find an easy solution on this forum (but that's another story)

Hence my first experience of Linux is disappointing and I may have to return to Windows.

---

### Post by jvc26 on 2007-01-11
Linux isnt a free windows - its important to remember that. I use it completely now with no Windows on my PC any more, however, that has been with a lot of tweaking and messing about with things.

Some things will work straight out of the box, others won't - the forums are good for this sort of thing to help you. For instance - what is the problem with the ntfs drives - can you read them/access them or can you see them at all. We can have a go at sorting that one out for you, and presuming your scanner has some method of working with linux (which it may/may not I've heard bad things about Canon support for linux, which isnt Linux's fault its Canon being unwilling to support a competitor to microsoft I fear) it may just be a matter of waiting for someone with the know-how to come and look at your post.

Anyway, my advice would be dont give up yet, it can be very frustrating at times I know, but if you're willing to stick around and give it a shot and adapt to a new way of doing things rather than the windows way then it may be worth hanging in there a bit.
:)
Il

---

### Post by rocknrolf77 on 2007-01-11
About mounting your ntfs drive, you can find here : [www.ubuntuguide.org](www.ubuntuguide.org) (just search for "ntfs" with your browser.) Remember to choose dapper starter guide.

And check out [www.getautomatix.com](www.getautomatix.com)



Linux isn't windows. Things are built in another/better/safer way. You have to learn how to use it.  The thing about the scanner is that canon has lousy support for linux and has nothing to do with linux. Blame canon for that. (I never buy a canon product because of this.)

---

### Post by kencoburn on 2007-01-11
Thanks for the quick response.  I'm happy to give Linux (Ubunto - Dapper) a try and hopefully with the communities help I can get this working.

Let's start with accessing my (Windows) hard drive - my Linux is on a separate hard drive connect as IDE slave.  I have two partitions, c: for windows and d: for data, both NTFS.  It is this second partition that I am trying to access.  When I try to mount this partition I get the message:

Unable to mount the volume

error: device /dev/hda5 is not removable
error: could not execute pmount

I searched the forum and found dozens of contibutions relating to such a problem.  One advised me to download **ntfs-3g ** from a repository that was not included in the Ubuntu 'add/remove' programs list.  Hence I set up access to the relevant respository using:

sudo gedit /etc/apt/sources.list

and added the line:

deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main main-all

I then loaded this program(s) thinking that this would allow me to mount my Windows NTFS data partition - it did not, so back to the forum.

I then found instructions to configure the NTFS partition to be mounted by ntfs-3g which I followed.  This gave the following results:

kencoburn@Mesh:~$ sudo fdisk -l | grep NTFS
/dev/hda2   *         911        7454    52564680    7  HPFS/NTFS
/dev/hda5            7455       30401   184321746    7  HPFS/NTFS
kencoburn@Mesh:~$ sudo cp /etc/fstab /etc/stab.bak
kencoburn@Mesh:~$ sudo gedit /etc/fstab

My fstab file is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0      

As you can see, my /dev/hda (windows) drives are not listed.

The instructions I found on the forum then said that if my driver was not listed I should create one where I would like to mount the NTFS drive. I don't understand how creating a directory will help.

Where do I go from here?

---

### Post by kencoburn on 2007-01-11
Having just posted a message, I continued trying to set up my Ubuntu (Dapper) installation to access my Windows NTFS drive and succeeded.  I set up the directory where I wanted to mount it as follows:

sudo mkdir /media/windows

I chose windows but it could have been any other name

I then added the highlighted line to the fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/hda5       /media/windows  ntfs-3g defaults,local=en_GB.utf8 0 0**

And bingo, when I rebooted my computer my windows DATA directory was there on my desktop.

Now back to the Canon 5000F scanner problem.  Does anyone have any ideas?

---

