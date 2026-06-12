---
title: "USB mount problem."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Dimicus on 2007-04-27
Hi.

Could not find any post about same error as i have so here i go.. 

System: Ubuntu - fiesty fawn

When i put in my USB harddrive a samsung 2,5" disk in to one of my USB port i get error 
( see screen shoot "error")

The USB disk was working until i messed it up by changing mount point.

here is what i did. i simulated the process on a internal harddrive.

When i inserted the USB harddrive i got a icon on my desk. i right clicked on the
icon and chosed properties and went to  "tab" "volyme" and clicked on settings and got some choices (see screen shoot "where").

on the mount point field i filled in some information, what, i cant exacly remember but think it was like "/usr/media" or so (please dont ask why :) i just did) and clicked on ok. After that i get error message (Screen shoot "error") all the time.

What have i done and how can i reverse it ? did i change the USB module somehow ? 

Suppose since i posted here i don't need to say that im not so good in linux. 

The harddrive have ntfs filesystem but that should not have anything to do with it since it worked before.

The harddrives name is "hej" so no strange characters

best regards
Dimicus

---

### Post by mac.ryan on 2007-04-27
Just guessing (so I might be wrong)... but the mounting point you defined might a) not exist b) being writable only by root c) a+b

Have a look to your /etc/fstab and /etc/mtab files. Maybe (but I am not sure, as i am not superexpert either) you could find there the line where the customised mounting point of a removable device has been written. If you find it there, simply change it to a workable mounting point (normally /media/<something>).

EDIT: another cause of your problem could be that only root is allowed to mount that disk (regardless to the mounting directory), in that case you should remove the "nouser" parameter from the line mentioned above, if you find it! :)

---

### Post by Dimicus on 2007-04-28
hi i solved the problem here is the solution. was a bit easy :(


I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.


thanx for all replyes.

---

### Post by vanadium on 2007-04-28
Glad you found the error yourself. I just had the same issue a couple of hours ago. The error we made is that we entered a path in the "mount point" field. Instead, you should fill in just one label, the name you want to give to the drive. Otherwise, indeed, you might leave it empty, and then the system uses a default name.

---

