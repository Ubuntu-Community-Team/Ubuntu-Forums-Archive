---
title: "SMB Share Mount and FSTab Problems -- What am I doing Wrong?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by chowanec on 2007-12-22
Hey all,

Sorry to dominate the forums with newbie questions... :)

I'm trying to get this samba share to mount on boot... I can get the share to mount from the command line, and I'm trying to repurpose the mount command in the fstab file to work... here's what does work:

**From command line**
```
 sudo mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3 
```

And here's what doesn't: 
** Fstab entry **
```
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
//mp3/Music	/mnt/mp3	smbfs	fmask=444,dmask=555,guest	0	0

```

Anything obvious I am doing wrong here?

Please help. :)

-Chow

---

### Post by blueridgedog on 2007-12-22
The syntax I found on google for fstab is:

//server/share /mountpoint smbfs userid=foo,passwd=bar,rw 0 0

Also, can you run dmesg ? and see if it gives you a more specific error when you try and mount the samba share?

---

### Post by blueridgedog on 2007-12-22
Sorry, I ommitted this, I would try:

```
//mp3/Music	/mnt/mp3	smbfs	userid=guest,passwd=,rw 0	0
```

---

### Post by chowanec on 2007-12-22
Thanks for the help -- still doesn't work for some reason... In terms of dmesg, I couldn't find anything in there that seemed samba related... in fact, I did this:

```

dmesg > boot.log
grep SMB boot.log
grep smb boot.log (just to be safe)
grep samba boot.log

```

Most of the syntax I find on google is for password controlled shares... I noticed that your syntax obviously left that out, which I was hoping was going to do the trick, but, alas, nada. :P

Thanks for trying though.

---

### Post by blueridgedog on 2007-12-22
As a cheat, you chould just edit /etc/rc.local and put this line in at the bottom:

mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3

If your user account owns /mnt/mp3, then you shouldn't need to sudo it.

---

### Post by tgilber1 on 2007-12-22
Use the device rather than the windows mount point.  Something like the following should work

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#//mp3/Music	/mnt/mp3	smbfs	fmask=444,dmask=555,guest	0	0

#windows xp
/dev/hda1 /media/hda1 ntfs defaults 0 0

---

### Post by chowanec on 2007-12-22
I feel like an idiot now -- nothing seems to work...

Here's my rc.local now:
```

#!/bin/sh -e
#
# rc.local
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3

exit 0

```

Now, my user account does not own the mp3 directory -- should I put a sudo before "mount"?

Thanks for all your help... 

-Chow

---

### Post by chowanec on 2007-12-22
> **tgilber1 said:**
> Use the device rather than the windows mount point.  Something like the following should work

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#//mp3/Music	/mnt/mp3	smbfs	fmask=444,dmask=555,guest	0	0

#windows xp
/dev/hda1 /media/hda1 ntfs defaults 0 0

But it's a network drive on a different machine...?

-Chow

---

### Post by blueridgedog on 2007-12-22
Well, unmount the samba share with sudo umount /mnt/mp3 then give yourself the mount point with sudo chown YOURACCT:YOURACCT /mnt/mp3 where YOURACCT is replaced with your user name, them mount the share again.

We will get there.

---

### Post by chowanec on 2007-12-22
Ok -- so I changed the ownership, that part worked. :)

But the actual mount doesn't show up when I boot... at this point I can:
```

sudo /etc/rc.local

```

And it will then mount...  I've tried putting "sudo" in front of the mount command in rc.local and still no luck...

Now I'm learning about rc.local at this point, so, here goes nothing:

1. When does rc.local actually run?  I see it run on shutdown, but not on startup?
2. Do I need to sudo the mount command in rc.local or is rc.local executed as root?
3. When your PC boots and you get all those [OK] boxes as its starting up, where does that log live?

Thanks for your help.

-Chow

---

### Post by maybeway36 on 2007-12-22
Try replacing smbfs with cifs. It worked for me once.

---

### Post by tgilber1 on 2007-12-22
Apologize, did not realize that samba drive was on different machine.


See if "mount -a" works after boot up.  If not, then it seems to point to the fstab file.  If mount -a works, then try looking at the naming issue with samba or dns.  Possibly the fstab is being mounted before samba or dns is ready, whichever way you're handling the naming on your system WINS or DNS.

Assuming the samba server is mp3 and the drive is not mounting a boot time, try the following:

you could add auto to ensure that it automatically mounts at boot time when system does mount -a
Hence rc.local is not required

#<file system> <mount point> <type> <options> <dump> <pass>
//mp3/Music /mnt/mp3 smbfs auto,fmask=444,dmask=555,guest 0 0

However, I believe your problem is root cannot mount the samba drive because it is not a legit user.  Try adding the following to the fourth field

uid=username or make sure guest is enabled on samba share.  Here's a URL that may help you out.

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

---

### Post by tgilber1 on 2007-12-22
Apologize, did not realize that samba drive was on different machine.


See if "mount -a" works after boot up. If not, then it seems to point to the fstab file. If mount -a works, then try looking at the naming issue with samba or dns. Possibly the fstab is being mounted before samba or dns is ready, whichever way you're handling the naming on your system WINS or DNS.

Assuming the samba server is mp3 and the drive is not mounting a boot time, try the following:

you could add auto to ensure that it automatically mounts at boot time when system does mount -a
Hence rc.local is not required

#<file system> <mount point> <type> <options> <dump> <pass>
//mp3/Music /mnt/mp3 smbfs auto,fmask=444,dmask=555,guest 0 0

However, I believe your problem is root cannot mount the samba drive because it is not a legit user. Try adding the following to the fourth field

uid=username or make sure guest is enabled on samba share. Here's a URL that may help you out.

[http://www.mattvanstone.com/2007/11/...-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/...-in-ubuntu-v3/)
__________________

---

### Post by blueridgedog on 2007-12-22
> **chowanec said:**
> Ok -- so I changed the ownership, that part worked. :)

1. When does rc.local actually run?  I see it run on shutdown, but not on startup?
2. Do I need to sudo the mount command in rc.local or is rc.local executed as root?
3. When your PC boots and you get all those [OK] boxes as its starting up, where does that log live?


It runs when you boot.  It runs as root, so no sudo is required.  Boot messages are accessed with dmesg.

I am curious as to why it is not working in rc.local.  I suggest some simple debugging.

Let us first unmount the remote share if it is mounted with

umount /mnt/mp3

This should be run as your normal user.  If you get an error about permission, sudo it, but let me know if you did get an error.

Now, as your normal user mount it with:

mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3

Did it mount fine?  Report back.

If it mounted, unmount it, then try it with a sudo. Did it mount fine?

If you own the mount point it should mount and unmount using your account.  It also mount and unmout as a sudo command, unless it is in use.

This will establish if you have problems mounting/unmounting as your normal user account or as a sudo command.

I am sorry for the hoop jumping, but I want to see why a simple mount command in rc.local fails.

Also, out of curiousity, do an ls -al /mnt and let me see what is in there, who owns it and what the permissions are.

---

### Post by chowanec on 2007-12-22
Thank you both for all the help... I'm getting closer and closer.  Albeit ever so slowly, but I'd be at a massive loss if it weren't for folks like you.

Ok -- tackling both replies at once.

> 
See if "mount -a" works after boot up. If not, then it seems to point to the fstab file. If mount -a works, then try looking at the naming issue with samba or dns. Possibly the fstab is being mounted before samba or dns is ready, whichever way you're handling the naming on your system WINS or DNS.

mount -a does in fact work *after* the boot into X.  I'm not sure what the "naming" issue could be that you refer to.  My "samba server" is, in fact, a windows XP machine.  Does it need any client/server software installed on it (i.e. Win32 software?)

> 
Let us first unmount the remote share if it is mounted with

umount /mnt/mp3

This should be run as your normal user. If you get an error about permission, sudo it, but let me know if you did get an error.


I do in fact get an error:
```

chow@mediaPC:~$ umount /mnt/mp3
umount: /mnt/mp3 is not mounted (according to mtab)

```

Now, assuming I "force" the mount at the CLI, will I still get an error?:
```

chow@mediaPC:~$ sudo mount -a

```
From here, I can ls /mnt/mp3 and see what I hope to see on the automated mount.  From here, i will start over with the umount command as my normal user:
```

chow@mediaPC:~$ umount /mnt/mp3
umount: only root can unmount //mp3/Music from /mnt/mp3

```

So, now I'll sudo the umount just to make forward progress.  After that, I'm trying to mount as my normal user:
```

chow@mediaPC:~$ sudo umount /mnt/mp3
chow@mediaPC:~$ mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3
mount: only root can do that

```
Grrr.  Using sudo now:
```

chow@mediaPC:~$ sudo mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3
chow@mediaPC:~$ 

```
Success...?

I'm fairly certain I own the mountpoint.  If I goto properties in GNOME, it says I do under the permissions tab, lists "chow" as the "owner."  I assume this is a good thing.

> 
Did it mount fine? Report back.

If it mounted, unmount it, then try it with a sudo. Did it mount fine?

Summary:  only mounts with sudo commands.  Does not mount as the user.  It is worth pointing out that I ONLY have permissions over the "mp3" directory and not the root of that directory "mnt/"

And finally, the contents of my ls -al /mnt:
```

chow@mediaPC:~$ ls -al /mnt/
total 16
drwxr-xr-x  4 root root 4096 2007-12-22 06:25 .
drwxr-xr-x 21 root root 4096 2007-12-21 21:05 ..
drwxr-xr-x  2 root root 4096 2007-12-21 20:25 cdrom
drwxr-xr-x  2 chow chow 4096 2007-12-22 06:25 mp3

```

And finally:
> 
I am sorry for the hoop jumping, but I want to see why a simple mount command in rc.local fails.

Please don't apologize to me... it is I who owes you my gratitude. :)

And now for the two appendices -- my fstab file and my rc.local file:

**fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b7e5c2c8-b935-47f6-9fa1-eb9e650e1796 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d1fccb5a-9513-4cd4-ae2c-c584459c9e40 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

//mp3/Music	/mnt/mp3	smbfs	auto,userid=guest,passwd=,rw 	0	0

```

**rc.local**
```

#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3/

exit 0

```

I, good people, am stumped (and totally got the newbie fever...) :)  Thanks again.

---

### Post by blueridgedog on 2007-12-22
Thanks for jumping through the hoops.  I have been brainstorming on the problem and it appears to me that the only way to get a mount that a user account and mount/unmount is to accomplish it in FSTAB, but that thus far has failed.  We tried mounting it manually in rc.local on system start, but that requires root, given that there is not entry in fstab.

Lets try an modify fstab so that a user can mount/unmount the file system:

You currently have:

```
//mp3/Music	/mnt/mp3	smbfs	auto,userid=guest,passwd=,rw 	0	0
```

Let us try:

```
//mp3/Music  /mnt/mp3  smbfs   auto,defaults,user,rw  0  0
```

Note we are eliminating the userid and password, as your remote system is not looking for one and we are stating that the user can mount it.  

You can also comment out the line in rc.local with a "#".  

Take a look here for more information:

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by eternicode on 2007-12-22
> I'm fairly certain I own the mountpoint. If I goto properties in GNOME, it says I do under the permissions tab, lists "chow" as the "owner." I assume this is a good thing.

Only root can mount.  The only time a user can mount is when fstab says they can.  Unfortunately, last I checked, the SMBFS drivers don't have this capability yet.  Can't seem to find a reference, though...

---

### Post by chowanec on 2007-12-22
*sigh* no dice... again. :(

Is there anything special I need to know about the window share?  Is it possible that Samba isn't initialized when fstab is being called/run/polled/whatever?

I'm certain I've got the case correct on the name of the PC I want to share from.

---

### Post by blueridgedog on 2007-12-22
Well, at least you can mount it manually, and you could put an icon on the desktop that mounts it:

Right click desktop -> creat launcher -> 
Name: MP3s
Command: gksudo mount -t smbfs -o fmask=444,dmask=555,guest //mp3/Music /mnt/mp3

I will have to dig into it a bit more.  I too mount various shares via smbfs, but I do them on the fly based on need.

---

### Post by chowanec on 2007-12-22
Feeling ever so stupid.  But here's the near-perfect solution... I have one question after this...

So, I decided to try out CIFS over SMBFS.  However, the only way I could get it to work was to use the IP address for the mahcine vs. the machine name.  That said, it will actually work this way UNTIL the DHCP releases that IP and gives it a new one, correct?  Or the PC reboots, etc.

So, is there anyway for CIFS to use the machine name?  Everytime I try it says it cannot find the server.

I do get this error though:
```

CIFS VFS: server not responding
CIFS VFS: No response for cmd 50 mid 58

```

My new, improved FSTAB entry:
```

//192.168.1.105/Music        /mnt/mp3          cifs         defaults                 0         0

```

---

### Post by chowanec on 2007-12-22
Going to try this now:
[http://lists.samba.org/archive/linux-cifs-client/2005-January/000650.html](http://lists.samba.org/archive/linux-cifs-client/2005-January/000650.html)

Will report back...

---

### Post by spiderbatdad on 2007-12-22
does rc.local need to cd into the pwd of your script? and how about giving the complete path to rc.local?

---

### Post by chowanec on 2007-12-22
Heh, SpiderBatDad,

I don't even know what you just said... :P  That's how new I am.

My rc.local lives in:

```

/etc/rc.local

```

---

### Post by spiderbatdad on 2007-12-22
I have to admit my newness as well, but i'm wondering if the script in rc.local needs to start with a cd command into /etc/fstab/complete/path...and if //mp3/Music...etc is the complete path name. like where is the path to the shared folder in that path?

---

### Post by blueridgedog on 2007-12-22
Well Done!  I will remember that vs the smbfs.

As to the dhcp issue, since I see you are using private addresses, why not go with static addresses on your home netwok, then put the entries in /etc/hosts and then you can use machine names from now on.

(I use statics on my 3 PC lan here at home for that very reason)

---

### Post by HermanAB on 2007-12-22
Hmm, one thing which no-one seems to have picked up is that smbfs is deprecated.  You should use cifs instead.

Cheers,

Herman

---

### Post by spiderbatdad on 2007-12-22
of course an alternative to all this is to put a simple bash script to mount in your home directory and add it to Sessions graphically under Preferences-->Sessions. though the thing is quirky and seems to take several tries before it sticks, and remember to save the session under Session Options.

---

### Post by blueridgedog on 2007-12-22
> **HermanAB said:**
> Hmm, one thing which no-one seems to have picked up is that smbfs is deprecated.  You should use cifs instead.



Wow, I went from using smbmount on the cmd line to smbfs being deprecated.  I feel old and out of touch.

---

