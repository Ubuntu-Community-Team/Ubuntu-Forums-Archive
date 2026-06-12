---
title: "searching for files in ubuntu"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-27
Hi, while i was online, I downloaded a file but instead of clicking on "save as" i clicked on "open with".  It turns out that the file is a video.  After downloading, it opened my totem movie player but I don't know where it is located in my hard drive.  How can I find out?

---

### Post by matthewv on 2005-10-27
Firefox usually downloads a file that you told it to open to a temporary location (I think). I don't know where that is though.

---

### Post by ubuntumaneh on 2005-10-27
You can use either locate or slocate on terminal:

slocate "name of file"

Now, when you ask "open with", the file is saved in a temporary directory, which is removed later. So I don't believe you are going to be able to run this file again, unless you save it from the site.

---

### Post by Kyral on 2005-10-27
Two ways. Both require some sort of "work" (depends on your definition of work ;P)

First way is to use the built in slocate command. It SHOULD be running as a cronjob everynight (to update itself), but to do it manually

```
sudo slocate -u /
```

And wait for it to finish. Then

```
sudo slocate <some characters in the filename>
```

It will match EVERYTHING with those characters so watch out.

Other way is GUI and frankly frickin' AWESOME. Its called Beagle. 

[http://www.ubuntuforums.org/showthread.php?t=78810](http://www.ubuntuforums.org/showthread.php?t=78810)

The file is prolly somewhere in /tmp BTW. And it might have already been deleted (tmp gets flushed like every logout and night I think)

---

### Post by ubuntumaneh on 2005-10-27
I don't think you need to use slocate with sudo. But anyway, the GUI solution is very good.

---

