---
title: "Joining Shortcuts?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by CodyJarrett on 2006-02-12
Hi,

is there a way in which I can make a "shortcut folder" which contains all the files from different folders? Let me explain: I have 3 folders containing movies on 3 different partitions. I would like to be able to access all movies at once without having to switch between the 3 folders - is there a way this could be achieved?

thanx!

---

### Post by davmac on 2006-02-12
I think symbolic links may be the answer to your questions. Open up a terminal window. Go to the directory where you want to create the link and type "ln -s /directoryofthetargget/nameofthetarget"

Type "man ln" for more info about creating links.

Hope this helps,

Dave Mac

---

### Post by CodyJarrett on 2006-02-13
thanks for your help,

with a little further reading on symbolic links it finally worked. I just had to use '*' - for instance: 

ln -s /media/stuff1/Movies/* /home/morten/Desktop/movies

this places symlinks of all the files from the first directory in the second one. Repeat those steps for all other directories containing the files you want in your directory.

---

