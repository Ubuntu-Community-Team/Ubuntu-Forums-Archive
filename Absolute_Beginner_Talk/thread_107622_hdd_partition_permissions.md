---
title: "hdd partition permissions"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by jerrybee on 2005-12-23
I've just installed a second hard drive and have created 3 logical partitions in an extended partition.  I'm the only user on this box, which is dual-boot of Win2000 and Ubuntu.  I need to change the permissions for the 3 partitions so that I can write to them, because the owner and group for them now is root.  I've tried, as root, "chown jerry hdb5" , e.g., and get a response of operation denied or some such.  I also need to change permissions for the Windows partitions on the first drive so that I can write to them.  I've successfully done a chown on the /media directory but can't do a chown on the directories under it.  Should I have done a recursive chown on /media  ,  or is the solution to getting full access to all partitions involve having to edit the fstab file?  An example or 2 would be most helpful.

---

### Post by bscbrit on 2005-12-23
If you are not the current owner of a directory, you cannot change its permissions.  Use sudo e.g.

sudo chown -R username:  /dev/hdb5

The 'username:' is a shorthand for username:username, which in turn means change the ownership to user 'username' and group 'username'.

If this is leaving you confused you might want to read up on 'man chown'

---

### Post by bscbrit on 2005-12-23
Neither FAT32 nor NTFS supports user permissions in a way compatible with linux.

---

### Post by bscbrit on 2005-12-23
finally, try these

[http://www.tldp.org/HOWTO/User-Group-HOWTO.html](http://www.tldp.org/HOWTO/User-Group-HOWTO.html)  *** sorry - this one is a mistake!

try this one instead: [http://rute.2038bug.com/node14.html.gz](http://rute.2038bug.com/node14.html.gz)

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

and

[http://www.tldp.org/LDP/lfs/html/chapter08/fstab.html](http://www.tldp.org/LDP/lfs/html/chapter08/fstab.html)

---

### Post by bscbrit on 2005-12-23
Finally, finally

[http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000](http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000)

OK , I'll stop now, promise.

---

### Post by jerrybee on 2005-12-23
[QUOTE=bscbrit]If you are not the current owner of a directory, you cannot change its permissions.  Use sudo e.g.

sudo chown -R username:  /dev/hdb5

The 'username:' is a shorthand for username:username, which in turn means change the ownership to user 'username' and group 'username'.

If this is leaving you confused you might want to read up on 'man chown'[/QUOTE]


      Well, I tried the sudo route and that didn't work.  Yes, I've read man chown and everything I can find in my Linux books, which make chown sound like a walk in the park, and nothing so far tells me how to change permissions on the other partitions, both Linux and Windows, that I've put together.  I'll have a read of the other references you've provided links to.
     This may be an inappropriate time to ask, but:  do I have to re-boot after I've done something like 'chown' to enable the changes?
     Anyway, thanks for the feedback -- it truly is much appreciated.

---

### Post by bscbrit on 2005-12-24
No the reboot is not necessary.

The windows disks do not have the file structure to support file permissions and ownership in a way that can be understood by linux.

But when you mount each drive, you have to specify a 'mount point' for each one e.g. /mnt/win1 and /mnt/win2.  In this case it is the mount point that might have the incorrect permissions.  Secondly, if the drives are mounted using the contents of fstab (/etc/fstab) you will have to ensure that the permissions that you want are specified in the fstab file.

That is why I gave you links to chmod and to the rute description of the file mounting procedure.  The information is probably there.  BUT, if having read the available documentation, there is something that you do not understand or it does not do what it claims then that is when someone here can help.
You couldn't change the permissions of the windows drives, so I hope I have explained why not and given you pointers to how you can achieve what you are trying to do.  

Of course, you could always bring the computer round and I could charge a standard engineer's fee....:p  :p  :p

---

### Post by bscbrit on 2005-12-24
Try this one - it is probably the clearest explanation that I can find:

[http://makuchaku.info/amnesty/#windows](http://makuchaku.info/amnesty/#windows)

But come back if it doesn't help.  Good Luck, bscbrit.

EDIT:  I've added the Breezy Guide to my sig.

---

### Post by jerrybee on 2005-12-24
OK, got it now.  Had to edit the /etc/fstab file by inserting the 'umask=000' in the options area.  Never was able to change ownership, but will continue to work on that.
     The idea of bringing the box to you sounds good, as I'm sure the weather on "the rock" is much warmer than here in NE Georgia -- 18 degrees F this morning.
     I thought there was a way for me to send a private email to you from this area, but I sure don't find it.
     Thanks again, and Merry Christmas.
                Jerry the newbie

---

### Post by bscbrit on 2005-12-24
If you click on my name bscbrit just above the avatar, one of the options it gives you is the chance to send me a private email.

I'm glad that you've made some progress - I'll give you a hand to sort out any other problems once the holidays are over.  (My wife will probably not want me to spend too much time on the computer!)

As for weather, we are a pleasant 16 degrees C at the moment (I've forgotten what that is in degrees F, but around 60 I guess!).  And I haven't been to Georgia since 1983 - but I have some happy memories of that visit.

Your thanks are acknowledged and gratefully received, but not necessary.  You're welcome.

Enjoy the holiday, Merry Christmas and happy ubuntu'ing....

---

### Post by david_e on 2005-12-29
Hi, I had the same problem, and I tried putting this line @ the end of /etc/fstab:

/dev/hda1	/media/windows  vfat    [COLOR="Red"]rw,user,noauto[/COLOR]	0          0

I have installed Ubuntu just 3 days ago and I have never used Linux before, but it seems to work (don't ask me why I have just tried :) as my HD is still empty and I have nothing to loose tring).   

Do u think this could be the right solution or I am just doing a mess? :confused:

---

