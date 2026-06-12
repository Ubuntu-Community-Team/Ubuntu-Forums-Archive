---
title: "Nessus client doesn't have the right..."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by hlygrail on 2007-05-22
I've followed the installation instructions for Nessus, but now I've hit a stumbling block.  Whenever I try to launch the program, I receive a pop-up window with this message:
  The Nessus client doesn't have the right to read /home/cgilbert/.nessusrc

I have an OK button and that's all.

I'm sure I've missed a step somewhere along the way, but can't seem to locate where.

Any help would be appreciated. 

Thanks.

---

### Post by dstew on 2007-05-22
It means that the Nessus client is running with privleges that do not allow access to the file you need to read. This can happen if you are running the client as a user, but the directory you want to read is owned by root. Check the permissions on the /home/cgilbert directory, and on the .nessusrc file.

How did you install Nessus? Did you install the Debian package?

---

### Post by hlygrail on 2007-05-22
Wow!  Thanks for the quick reply.

I checked the permission on that folder and they were set to root.  I changed it to my User and all is well.

Thanks!  

For what it's worth...I'm pretty green to Ubuntu, and this forum has been an amazing asset.  Excellent work to everyone who contributes!:D

---

