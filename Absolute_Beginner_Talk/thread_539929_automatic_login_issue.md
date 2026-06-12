---
title: "automatic login issue"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Antimatter27 on 2007-08-31
i'm a fairly ignorant linux person, still learning, so go easy on me here. ;)


i was hoping to have ubuntu load and automatically login. it did so, but my desktop files disappeared, and when i go to the places menu i only see desktop listed and not home folder. i click desktop and get the error: could not open location file:///home/desktop/mycomp/Desktop

i removed the automatic login (system > preferences > login window) but my problem still remains. the files from my desktop are there if i search for them, but i cannot acess any files or folders on my computer, nor flash drives...

any help? =\

---

### Post by Antimatter27 on 2007-08-31
*bump* :)

---

### Post by alienexplorers on 2007-08-31
Your desktop icons should be in /home/Desktop.  I don't know where you got the line
> ///home/desktop/mycomp/Desktop
This is looking for a file on your computer, not the actual Desktop directory.  Whenever a file starts with /// it is looking for a text file or other type file not a directory.

---

### Post by Antimatter27 on 2007-08-31
whatever happened i am locked out of the file system on my computer, and my desktop files are hidden. im really clueless.

---

### Post by alienexplorers on 2007-09-01
In terminal try typing:
> chown -R username:username /home

---

