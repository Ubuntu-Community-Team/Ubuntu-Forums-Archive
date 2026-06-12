---
title: "connect to share?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by gruss on 2007-12-30
Ok, I hope this is an easy one and I just got the search terms wrong...
I have Ubuntu loaded, sharing files with my xp pc's to my satisfaction but I can not figure out how to connect to the fileserver with xubuntu 6.06?  Any help is appreciated.  I can "connect to server" with my vmware load of ubuntu gutsy to the same server and all is well but just cant seem to figure it out in xubuntu.

thanks

---

### Post by Paqman on 2007-12-30
So you've got a fileserver running Ubuntu, and you'd like to connect to it with your Xubuntu machine? Is the fileserver running Samba? If so check out this [guide to mounting Samba shares](http://ubuntuforums.org/showthread.php?t=288534).

---

### Post by gruss on 2007-12-31
Thanks this looks like it should work but I get the following error after a mount -a

mount: wrong fs type, bad option, bad superblock on //server/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

from dmesg|tail, well the relevant parts anyway I think

[17188678.380000]  CIFS VFS: No username specified
[17188678.380000]  CIFS VFS: cifs_mount failed w/return code = -22

I checked all my typing and I cant find the error, I'll try the manual way and see if it mounts, nope same message.  I'm not sure what all the CIFS stuff is, I did create the files in that tutorial so I'm stumped for now.


Gahhh so close ;)

---

### Post by graabein on 2007-12-31
Try exchanging **//server/share** with **//ip-address/share**.

---

### Post by gruss on 2007-12-31
I tried using the IP and got the same error, smbtree looks like it resolves the hostnames fine and the share shows up.  Should cifs be replaced with smb or somthing since I have samba running on the fileserver?  Or is there a way to install the gnome "connect to server" prog and do it that way OR I just thought does the connect to server prog write to the fstab?  IF so I could copy the settings out of my vmware load ubuntu??
Just thinking out loud let em know if I'm on the right track

---

### Post by blueridgedog on 2007-12-31
What is the full command you are using to attempt to mount the share?

---

### Post by gruss on 2007-12-31
I went a different direction with the mount, and used this and it seems to work fine, I was using the commands from the thread Paqman posted.

//fileserver/sharename /media/emptyfolder smbfs username=XXXX,password=YYYY,umask=022 0 0

I dont know if this is the "best" way or not, but I'm just going for function for now.  Thanks for pointing me in the right direction fellas, issue resolved for now, I'll look into alternate methods down the road if performance is and issue

---

