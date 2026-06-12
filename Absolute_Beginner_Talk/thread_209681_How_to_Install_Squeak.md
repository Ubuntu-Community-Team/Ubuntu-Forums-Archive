---
title: "How to Install Squeak"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Muun on 2006-07-05
I got the Squeak package in the normal way: sudo aptitude install squeak

It installed OK, but then it wouldn't run. Entering "squeak" in the terminal gave some info, but it wasn't entirely useful. I finally figured it out and wanted to post my solution here -- this is for Ubuntu Dapper Drake, btw .. I don't know what issues other releases may have:

1. The .image and .changes files are archived. Find these in .gz files in the /usr/lib/squeak directory. Unarchive them somewhere in your home directory. I put mine in ~/Squeak

2. The .sources file has to be moved from the /usr/lib/squeak directory to the /usr/lib/squeak/3.7-7 directory.

3. Copy /etc/bash.bashrc to a backup, then sudo gedit /etc/bash.bashrc to insert the following line at the end: 

    export SQUEAK_IMAGE=~/Squeak/Squeak3.8-6665.image

assuming you put the .image and .changes files in ~/Squeak .. otherwise, change the export statement to match your location.

4. Reboot, and you should be able to run squeak from the terminal.

---

### Post by smackenzie on 2008-05-16
Worked great for me, thanks for posting!

---

