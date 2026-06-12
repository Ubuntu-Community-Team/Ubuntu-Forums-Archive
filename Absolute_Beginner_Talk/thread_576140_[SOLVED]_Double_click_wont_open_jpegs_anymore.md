---
title: "[SOLVED] Double click wont open jpegs anymore"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Boaslad on 2007-10-14
O.k. Yesterday all was well. Double clicks opened my vast collection of jpeg images just fine. Today. I get a message about "blah blah blah indicates that this file is of type "jpg document". The contents of the file indicate that the file is of type "JPEG image". If you open this file, the file might present a security risk to your system." now I have to right click and select program to open it. I haven't downloaded any upgrades or changed any settings that i am aware of. so what gives? How do I get it back to normal?

---

### Post by wormser on 2007-10-14
Right click on the .jpg> Properties> Open With tab> select Image Viewer.  That will make .jpg files open with Image Viewer on a double click.

The security warning has me a bit concerned.  I have never seen it before in Linux.  Are these .jpg known to be ok?  It could just be a default warning.

---

### Post by Boaslad on 2007-10-14
Yeah the whole security warning thing has me surprised too. i haven't seen it before either. I haven't had this problem since I started using Ubuntu. It just startted today.. It has me a a bit confused.

---

### Post by Boaslad on 2007-10-15
Never mind. I fixed it. Sort of. I think there was a setting that was messed up some where and I couldn't figure out which one. So I just made a new administrator account under "Users and Groups" and deleted the "malfunctioning" one. This probably isn't the most graceful of fixes but it works. I only had a few settings to reconfigure. 

Here's a hint for if you should ever need to do this. If you are running Beryl  and/or Emerald, you can access the old user name's /home folder, and copy the .Beryl and .Emerald folders over to the new user's /Home folder.This will keep you from having to reconfigure all the settings. I am sure this will work with other programs, and some of the configuration files, too. I chose not to transfer those because of the jpeg issue.

---

