---
title: "iRiver mp3 player free space not recognized"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by suver.17 on 2006-07-12
I just recently made some space on my iRiver mp3 player, howwever, Ubuntu is not updating and recognizing this new space.  I should have 4gb free to put music on to, but it is saying that there is only 12mb free and not letting me put music on due to "lack of space".  Anyone know what could be the problem here?

Thanks
Jared

---

### Post by Kilz on 2006-07-12
> **suver.17 said:**
> I just recently made some space on my iRiver mp3 player, howwever, Ubuntu is not updating and recognizing this new space.  I should have 4gb free to put music on to, but it is saying that there is only 12mb free and not letting me put music on due to "lack of space".  Anyone know what could be the problem here?

Thanks
Jared
Do you have libifp4 installed?

---

### Post by Brunellus on 2006-07-12
did you delete things in Nautilus (GNOME's file manager)?

If so, all those "deleted" files aren't gone--they've just been moved to a 'trash' hidden directory. sitting in a hidden directory on the device.

---

### Post by suver.17 on 2006-07-12
I do not have libifp4 installed, what is that program?

Most if the items were deleted on my windows partition.  When I have used the mp3 player, i have seen the .trash folder with the stuff I've deleted using Nautilus.  Most of the space was freed up using windows though.

---

### Post by Metacarpal on 2006-07-12
I had the same problem moving files to and from my Palm Tungsten.  When you delete files on a portable device using Nautilus, it creates a trash folder, which still takes up the space.  View Hidden Files, then delete the trash folder.  Your free space will really be free then.

**Does anyone know if there's any plan to tell Gnome NOT to create Trash folders on portable devices, USB drives, etc?  It's kind of a pain.

---

### Post by suver.17 on 2006-07-12
Ok, I see the .trash folder, but when I attempt to delete it, it goes through each file telling me that it is on a read-only disk, and it will not delete.  

Sorry to be a bother, but I'm a newbie.
Thanks
Jared

---

### Post by Kilz on 2006-07-12
> **suver.17 said:**
> I do not have libifp4 installed, what is that program?

From Synaptic libifp4
"communicate with iRiver iFP audio devices
libifp allows you to communicate with iRiver iFP audio devices. It
provides a high-level interface to upload and download files to and
from the device, as well as other functions like battery status and
firmware updating."

---

### Post by suver.17 on 2006-07-12
gotcha....my iRiver is part of the iHP series.

---

### Post by sinaen on 2006-08-29
can you access it from the console go into its directory then where the trashcan-folder is?
and do a sudo rm -r .whatevertrashcansfilenameis*

---

