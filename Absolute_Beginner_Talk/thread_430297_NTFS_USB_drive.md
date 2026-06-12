---
title: "NTFS USB drive"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-05-02
OK.  I have an external USB drive that I've been using to move files from my old windows box.  It's the drive I use to back things up to.  The problem is that I can't create files on the drive from Ubuntu. It keeps telling me that I (nor root) own this resource so I get read only.  So what's the secret so that I can write to it?  On Windows there's the concept of "take ownership", is there something similar in Linux?

Dave

---

### Post by hyperair on 2007-05-02
The reason you cannot write to the NTFS partition is because the traditional NTFS drivers that come out of the box with Feisty do not have stable write support (i.e. they can destroy your NTFS partition). So the solution is to install ntfs-3g and set it up to use the ntfs-3g drivers on your external USB drive. 

Try this code:

```
sudo apt-get install -y ntfs-3g ntfs-config && sudo ntfs-config
```

---

### Post by jiminycricket on 2007-05-02
Since it's an external drive, you must  be VERY CAREFUL to unmount it before you power it down or remove the USB cable.  Otherwise you'll more than likely lose your partition.

---

### Post by alexjhill on 2007-05-02
Doesn't work for me :( it errors and says i need to edit my fstab file to say

dev/sda1/ blah.....  defaults, Force 0 0 

but the stiuck wont mount. If i disable the "allow to write" option the disk is detected and loaded fine (but i cant write to it)

Help!  (i did make a post but no one's replied)

---

### Post by hyperair on 2007-05-02
I've never seen such a thing. Could you post the *exact* error message or take a screenshot?

---

### Post by alexjhill on 2007-05-02
Sure unfortuanly i'm at work but i'll post just after 6pm (UK time) :)

I've tried completely removing the NTFS-3G, Pmount and NTFS-Config and followed a bunch of online guides and get the same message.

one used something called FUSE? any way - i removed all and tried again this morning but no luck! 

apt-get install ntfs-3g
apt-get install pmount

hit the Y  option i get prompted with ..... and nothing! 

will post my screen shot!

Thanks! 


ps any syntax error is because i'm newbie so still trying to remember what i type :)

---

### Post by alexjhill on 2007-05-02
this is the error i get :)

---

### Post by LaRoza on 2007-05-02
I would recommend formating your flash drive to FAT32. This forum discussion brings up some interesting things:

[http://portableapps.com/node/5975](http://portableapps.com/node/5975)

---

### Post by alexjhill on 2007-05-02
ok question... i'm admittedly a dumb ***.

i changed the mount point in the properties for my USB stick under the advanced option when looking at the tabs for the stick. and it's now no longer registering on the machine (well it won't mount) and i cant seem to access it.

how do i "delete" the manual settings? there is no entry in fstab or mtab so they must be else where?

thanks!

---

### Post by alexjhill on 2007-05-02
Best thing - reformat the disk as Fat32 = no more issues :)

---

