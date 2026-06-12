---
title: "Permissions for Mac Drives"
date: 2010-06-06
forum: Apple Hardware Users
---

### Post by TechnoFreddo on 2010-06-06
Hi,

I have a MacBook Pro 13 with Mac OS X 10.6.3, Windows 7 64-bit Ultimate and Ubuntu 10.04 LTS installed.

I want to use my Ubuntu partition to move files between my external mac drives, the internal mac drives and my Archos 5 IT 500GB Media player (uses Ext3).

At the moment, the home directory of my Mac OS drive is unaccessible (shows crosses on all the folders in it) except in root access mode, running 10.04 LTS.

I wish to know how to setup my fstab file in order to auto mount the Mac drive, give it read/write access to all users and obviously no dump or such.

At the moment it stands as follows,

/dev/sda2	/media/Mac	hfsplus	rw,user,auto,exec	0	0

The drive always mounts successfully, but I'm still not able to access all the files without using sudo nautilus.

Please help, 

Thanks,

Fred

---

### Post by sha.goyjo on 2010-06-06
I don't think (note the think, I'm not stellar on gpt permissions issues) that the problem you are having is due to an incorrect fstab. As far as I know, file and folder permissions in gpt are a lot like file and folder permissions in ext4 or ntfs, namely that they are tagged onto each file and folder. I'm pretty sure that installing hfsprogs give you the ability to r/w mount the drive, but for changing the permission settings of files and folders you should probably use the command line utilities chmod and chown.

Please note that I'm not sure about this, as I've NEVER tried to use chmod or chown on anything that was on an hfs+ partition. I'd suggest reading up on appropriate help first, but that's really all I can give you.

---

### Post by Frobber on 2010-06-06
I suspect your problem is UID and GID. Sometimes, after updating Linux or a fresh install of Linux, we are presented with 'Cannot mount volume &#8211; you are not privileged to mount volume' while attempting to access some partitions of the hard drive. This is caused by file ownership and possibly the /etc/fstab file.
To access OSX partitions from the Linux side, the UID and GID must match the OSX UID and GID. During OSX install, the first user and OSX administrator is assigned UID 501 and GID 20. When a Linux system is installed, the user IDs start at 1000. 
We can change our user IDs to match the IDs for the MacOS from the Linux side.
To verify our UID and GID on the Mac side, login, open a terminal and Type &#8211; id. The response will display the required information.
The UID and GID cannot be changed for a user that is logged in. With Ubuntu we need to create a 'Temp' user with administrative privileges, and perform the procedure while logged in as the 'Temp'. The 'Temp' user will use sudo -i to change to root user. 
The following procedure is written for a system that has 'Root' user capabilities, and nano is the editor.. 
Note
All we are doing is changing the ID numbers and nothing else.
1.At the login screen, Key &#8211; control+alt+F1. Observe that we have entered console mode.
2.Log in as root, or the Temp user.
Edit the file /etc/login.defs.
Type &#8211; nano /etc/login.defs
Find the value UID_MIN. Change it from 1000 to 501.
Find the value GID_MIN and change it to 501.
Save the file and exit. 
Key &#8211; control+x. Key &#8211; y. Press &#8211; return.
Edit the file /etc/group.
Type &#8211; nano /etc/group
Find the line that displays dialout:x:20:(username); change the value 20 to be 99.  
Find the line that displays (username):x:1000: and change it to (username):x:20:
Save the file and exit. 
Key &#8211; ctrl-x to exit nano. Key &#8211; y. Press &#8211; return. 

Edit the file /etc/passwd.
Type &#8211; nano /etc/passwd
Find the line that displays (username):x:1000:1000:(real name),,,,/home/(username):/bin/bash and change it to be (username):x:501:20:(real name),,,,/home/(username):/bin/bash
Save the file and exit. 
Key &#8211; control+x to exit nano. Key &#8211; y. Press &#8211; return.
Change file permissions of the home folder.
Type &#8211; cd /home
Type &#8211; chown -R 501:20 (username)
Exit console mode.
Key &#8211; control+alt+F7
Reboot. 
If this did not work and you received a message stating that one of the files could not be changed, it is likely that you are still logged in as (username) somewhere on the system. Try rebooting and logging as temp at the Login Screen. 

If this procedure was performed using Ubuntu the 'Temp&#8221; user may now be removed from the system.

We should now be able to access user files from either OS.

---

### Post by TechnoFreddo on 2010-06-06
Thanks for the reply,

Looking into the properties of the folders I am trying to access, they list user 502 as being the owner, hence why I can access with root, but no one else.

I think I have worked out the problem - admin or my user accounts are enabled as the owner of the directory.

By changing the owner to everyone, I should be fine to access however.

Thanks again, keep you posted.

---

### Post by srs5694 on 2010-06-06
You can create an account called "everyone", but it will be an ordinary account. There's no such thing as giving ownership of a file to all users. You *can,* however, give everybody read/write access to files in a directory using chmod:

```

sudo chmod -R o+rw /some/directory

```

This gives everybody read/write permissions to all the files and subdirectories in /some/directory. Note that new files may not be affected.

A better option in the long term is to synchronize the UIDs and GIDs on the two OSes. Frobber has provided directions, although I suspect they're overly complex. I don't have time to verify and debug simpler custom directions right this moment, though. Perhaps Googling will turn something up. You can also check the man page for the usermod command. This sort of thing is sometimes easier with a direct root login, but Ubuntu doesn't set the system up to permit this by default.

---

### Post by sha.goyjo on 2010-06-06
srs, your points are valid. The only other thing that I could offer for advice is that if you have to do a lot of chmodding, using

sudo su

will save you a lot of time. It's the closest thing you can get to a root login.

---

### Post by Frobber on 2010-06-06
My description to make changes seems complex. The fact is we are only changing three files, and the UID/GID for home directory.

I have OSX and two versions of linux loaded, all share the same 'home' partition. My original fix was to log in one linux change files for the other linux os. 

My descriptions for changing files, although wordy, is a condensed version from several posts gleaned from the net -'google' change uid. 

For the reason stated, in Ubuntu we need to create the temp user with admin privlidges to make the changes. 

For future installations it may be easier for the user to select his own UID/GID from the front . . . . then after the load "I wish I had done that!!

---

### Post by TechnoFreddo on 2010-06-13
I've been looking into this further.

I created a new folder within Mac OS in my home directory and called it Tester.

The same folder, when in Ubuntu 10.04 LTS, was readable.

I checked the permissions within Mac OS and it came up with a group called wheel which had read only permissions.

When I tried to add this to the other folders I want to access but can't, Mac OS doesn't show up anything in its directory of people/groups I can add and hence I can't add it to those folders/files.

Can someone suggest a way, using Terminal if it's a must, in order to add this wheel group to the other directories?

Thanks,

Fred

---

### Post by billybobby2010 on 2010-07-21
Hi all,

I'm using Ubuntu live CD (10.04) to copy some files from my Mac OS drive to an external hard drive. My Mac OS drive is indeed corrupted (it automatically shuts down when I launch it) and I want to backup some files.

Using Ubuntu, I have the same problem as TechnoFreddo: the home directory of my Mac OS drive is unaccessible (shows crosses on  all the folders in it). Gksudo nautilus gives me access to them, but I can only read, not modify, copy or save as.

The chmod command doesn't help.

I guess the only solution is Frobber's. I have two questions:

1. - will it works from Ubuntu Live CD?
2. - is there a way to verify our UID and GID on the Mac side without passing by my Mac OS drive (because I don't have access to it)?

---

