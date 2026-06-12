---
title: "Why does cp command return &quot;cannot stat&quot; for some files but not others"
date: 2011-05-23
forum: Apple Hardware Users
---

### Post by TnkerTailor on 2011-05-23
THis is my first post on the forums, and I am an Ubuntu newbie, so I apologize if I break etiquette.  Let me know if I do.

Anyway, I am trying to copy files off of my wife's Macbook onto an external hard drive using an Ubuntu 11.4 Live CD.  I have been using the following command in terminal:

$ sudo cp -r /media/MacHD/Directory /media/externalHD

and it has been working for the most part.  However, it has been returning a lot of "cannot stat" messages for certain files -- all .jpeg or .avi files.  I'm hoping to find out why it is doing this so I can fix the problem and grab those files.

P.S. The reason I'm using a Live CD is that the Macbook won't boot on its own drive.  The local Genius Bar diagnosed this as a bad hard drive, but I can still access it through Ubuntu...  I don't know.  Also, I'm using sudo to copy because the files in question are within a user profile on the HD, and thus are permission-protected.

---

