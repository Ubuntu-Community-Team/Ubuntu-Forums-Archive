---
title: "Permission prob"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-03-14
I installed apache 2 and when I try to go on the site and click a link it says permission denied. I went through them and change permissions if needed but still the same.

Take a look [http://redwind.servehttp.com:8080](http://redwind.servehttp.com:8080)

---

### Post by irwa82 on 2007-03-14
Hi,

Seems like you have some sections working now. The other sections that are still not working is probably to do with permissions on your directories.

Make sure all directories have the permissions of 755. Then you should not have any problems with the forbidden messages.

Also so you know directories must have execute permissions for you to be able to do directory listing on them and see what is in there.

Kind Regards,
Anthony Irwin

---

### Post by RED WIND on 2007-03-14
how would I change them, before I went to properties

---

### Post by irwa82 on 2007-03-15
Hi,

The easiest way to ensure that all of the directories have the correct permissions is to open up a terminal window then go into where your web site starts.

then run the following commands

find ./ -type d -exec ls -lhd {} \;

The above command will show you all the directories and the permissions that the next command will effect

Providing everything shown with the above command has to do with your web site run the command below to give the directories the permissions of 755.

find ./ -type d -exec chmod 755 {} \;

There would be a way to manually do it with a gui but I prefer the computer to do the work.

---

