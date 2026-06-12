---
title: "Network OSX with Ubuntu"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by Sipheren on 2006-07-05
Hey,
I have installed Dapper on my iBoookG3. I want to network with my PowerMacG4, I have connected them through a ADSL modem.
The Mac can connect to Dapper but cant write to it, Dapper can see the mac (there is an icon in the Networking folder) but there are no folders inside it so I can't get things of the mac.

Has anyone any ideas of what I need to do, I have been searching the internet but nothing has worked as yet.

---

### Post by ciscosurfer on 2006-07-05
Writing to HFS instead of HFS+ might be the trick.  The key here is the journaling involved--Linux doesn't play well with it.

This link might help, specifically the section titled "Writing on HFS+ Journaled file system", but read the entire page for best results:

[http://pinguin.uni-psych.gwdg.de/%7Eihrke/wiki/index.php/Installing_Ubuntu_on_iBook]("http://pinguin.uni-psych.gwdg.de/%7Eihrke/wiki/index.php/Installing_Ubuntu_on_iBook")

Hope this helps.  Please post your results. :D

---

### Post by Sipheren on 2006-07-05
I only have Journaled enabled on the main mac drive, the other 80GB drive in the mac is just standard HFS+ files system, so shouldn't I be able to mount that in Ubuntu?

---

### Post by ciscosurfer on 2006-07-05
Issues still arise with HFS+ with the native Linux drivers that support HFS.  

The way I understand it, journaling is enabled by default with versions of OS X starting with v10.3 (please read the [HFS+ wiki @ wikipedia]("http://en.wikipedia.org/wiki/HFS_Plus#History"))

Re-read  as well: [http://pinguin.uni-psych.gwdg.de/%7Eihrke/wiki/index.php/Installing_Ubuntu_on_iBook]("http://pinguin.uni-psych.gwdg.de/%7Eihrke/wiki/index.php/Installing_Ubuntu_on_iBook")

Other than that, you've got me :confused:

~ maybe post the commands you're using to mount and/or also post your fstab ```
cat /etc/fstab
```

---

### Post by onehotcutey on 2006-07-05
These are networked computers right?  I assume your using NFS to network them together, rather than SMB or CIFS.

And since the mac is having problems writing to the Linux machine it's not a matter of HFS+ journaling.

This is my guess:

1) you can't write to the Dapper machine because you haven't set up the shares with write permissions turned on.  Go back and look at that.

2) have you set up any shares on you Mac?  You need to have some sort of share set up in order for Linux to detect it.

Hope this helps.  I really doubt this has anything to so with HFS partions.

---

### Post by Sipheren on 2006-07-11
I know its not the HFS thing. I ended up just conecting the 2 macs together without my ADSL modem and it worked.
I have installed Dapper and mol on my G4 now and have it working with net and I can mount ubuntu drives. But in Ubuntu I go to network and I can see an icon of the PowerMac but when I go into it there are no folders??

I have all the sharing activated on the mac.

Any ideas?

Cheers

---

### Post by AlphaMack on 2006-07-11
Another problem to watch out for involves permissions.  Even if you use the same username, in OS X your UID is 501 and in Ubuntu 1000, assuming you are the first registered user on both.

---

### Post by babyalgebraist on 2006-08-28
K. I am having similar issues.  
I just moved in with these people and one has a new powermac (intel) and the other runs window$.  I of course, run Ununtu.  
I wanted to set up a network to share music between the three laptops.  So I install SMB for sharing with the winBox laptop.  Now on the new mac, we enabled sharing with Windows machines (should help right?) and finally get to see the mac in my networks folder.  But there are no folders and I can't write to it.  Is this indeed a problem with HFS+?  THere are issues with ntfs but samba seems able to handle that.   Any one have any idea how to solve this directly?

---

