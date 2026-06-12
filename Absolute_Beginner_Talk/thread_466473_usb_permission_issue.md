---
title: "usb permission issue"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-06-06
I have been using the usb port to download pictures from my camera using gtkam with no problems. I installed virtual box and put xp in it to run a couple of programs that I haven't found a sub for. (yet ;-)) I do not have usb enabled in the virtual machine, but for some reason, now, if I try to use the usb, Not sure if this is the cause, but it is about the only thing that I have done that would change any permissions. I get this error:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

If I run gtkam with gksudo, it works, but the pictures are all owned by root and it is a pain to fix them. I would fix the permissions, but I don't know what to change. Anyone know what to look for?
************Update************

I did a bunch of searches on these forums and the web and found that this is something that others have had also, but there doesn't seem to be a real concensus of a fix that works for everyone. There was a bug report that I found referencing libgphoto2-2, which is where I got the idea for what I finally did. I tried the fixes referenced in those threads, but nothing seemed to work, and I only broke the system once ;-). Finally, I totally removed libgphoto2-2 and everything else that apt-get wanted to take out in the process, rebooted the computer (mostly to make sure it still would and that I had not broken anything.) then uninstalled gtkam and digikam. 

I then reinstalled libgphoto2-2, then gtkam, and it works again. 

Not sure if this has anything to do with it, but I did have one of the backport repositories enabled, which I removed before I did any of the reinstalls. Not sure exactly what I did, but maybe this will help someone else. The bug report was at [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

---

### Post by bobbybobington on 2007-06-06
You can usually change permissions for a folder by doing the following:

   1.Select the folder that you want to change. 
             
   2.Choose File &#8594; Properties. The properties window for the item is displayed.

   3. Click on the Permissions tab.
          
   4. To change the folder's group, choose from the groups the user belongs to in the drop-down selector.
             
   5. For each of the owner, the group, and all other users, choose from these folder access permissions:

                  
      **None**
No access to the folder is possible. (You can't set this for the owner.)

     **  List files only**
The users can see the items in the folder, but not open any of them.
         
      **Access files**
Items in the folder can be opened and modified, provided their own permissions allow it.

        **Create and delete files**
The user can create new files and delete files in the folder, in addition to being able to access existing files.

Since the the usb is owned by root, you probably will have to login as root to change this.

---

### Post by dondad on 2007-06-06
Thanks, but my problem is that I don't know which folder has the wrong permissions ;-) That is what I need to know.

---

### Post by Ek0nomik on 2007-06-06
```
ls -la
```

Lists all folders and files in a given directory in a vertical fashion and shows you the user and group owner.

---

### Post by dondad on 2007-06-06
The problem is that some folder is owned by root that should not be (apparently), but I have no idea which one it is. I can check the owners, and know how to change that, but have no clue as to which one is owned by the wrong owner or which one to fix. My problem is not how to fix it, but what it is that I need to fix. Thanks for the answer though. I did learn a new command.

---

### Post by dondad on 2007-06-07
I tried plugging a usb stick into the same usb port that I tried with the camera and it works fine both read and write. It looks like the problem is mainly with the camera and/or gtkam. Any idea where to look now?

---

### Post by dondad on 2007-06-07
*bump*

---

