---
title: "error in configuring EMULE"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by maclif58 on 2007-12-26
hi to all helpers
i try my luck  here maybe its a more suitable forum
while configuring emule i set to folder to save my downloads to an NTFS HD .
now I can not start the program at all. tried to uninstall and reinstall with the same results.
I also tried to work according to it bug could not figure out what to do.
I've attached the error message .
thanks for your help
maccabi

---

### Post by Mister.Vash on 2007-12-27
The screen capture you included indicated it is a permission error.  Since you mention that the drive is NTFS, let's just take that out of the equation for a second.

Can you create, in your home directory, a new test directory, and configure emule to use that folder instead?  If that doesn't work, something else is going on.  If it does work it could be that the NTFS volume was mounted read only.  If it is mounted as read write, then check the permissions on that folder.  

To get the information, open up a terminal window and then type mount. This will list the mounted volumes and the options

Then navigate to the /media/hda5 folder and type in ls -l which will show the owner group and permissions for all the files underneath it.  Make sure that the emule downloaded directory is listed and shows the options

---

### Post by maclif58 on 2007-12-27
thanks for your reply.
all i want now is to uninstall Emule  completely without saving any of its setting, because otherwise  i end up without being able to access Emule altogether. 
actually  i want now to get to the basic  set up of the Emule program, in which the download data is stored in the Linux file system  for which i have permission of access.
thank in advance
maccabi

---

### Post by maclif58 on 2007-12-27
sorry, but after reading more posts i got  to this
[http://ubuntuforums.org/showthread.php?t=448835&highlight=set+read%2Fwrite%2Fexec+permission](http://ubuntuforums.org/showthread.php?t=448835&highlight=set+read%2Fwrite%2Fexec+permission)
which answered my question
thanks guys

---

