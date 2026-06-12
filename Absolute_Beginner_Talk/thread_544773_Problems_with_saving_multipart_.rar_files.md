---
title: "Problems with saving multipart .rar files"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-09-06
Hi guys,
The problem i am facing is when i save a multi-part rar file which is usually names as
xxx.part1.rar, xxx.part2.rar, xxx.part3.rar.........xxx.part8.rar, these files get saved as **xxx.part1.rar.bin**. How do i save the files as they are. also ubuntu adds the .bin extension to some avi files i download too. Re-naming them helped but why do i need to do the same every time. Also how do i extract from these multi-part rar.bin files???
in windows WINRAR does the trick...anything similar in ubuntu???

---

### Post by bodhi.zazen on 2007-09-06
I do not know about the naming of your files, sounds unusual ... How are you downloading ?

For multi-part files, see this link : [http://ubuntuforums.org/showthread.php?t=476048](http://ubuntuforums.org/showthread.php?t=476048)

---

### Post by badguyanil on 2007-09-06
Nothing special. Just right click on the link and saveas... for example say the link is 

[http://rapidshare.com/files/Underworld.part1.rar](http://rapidshare.com/files/Underworld.part1.rar)

once i save it ........
check the seq 1 2 and 3 images uploaded. Check the name has changes to .rar.bin in image 3

---

### Post by badguyanil on 2007-09-06
any idea why the above is happening!!! how do i stop the file being renamed!!!! i just want them as .rar files and not .rar.bin!!!

---

### Post by qpieus on 2007-09-06
I do not know why the files are having bin attached to the filename, I've never seen that before. In answer to your question about winrar, a program called unrar is in the repositories```
sudo apt-get install unrar
```

unrar is a command line program, but it should integrate with a gui file app like fileroller. So, for example, you should get an extract option when you right click on a rar file (at least I do, but I'm using KDE - I assume it'll work similarly in gnome). The bin on the end of the file name might mess that up though. Hopefully someone else can help you with that.

---

### Post by aidanr on 2007-09-06
ntfs partiton by any chance?

[http://forum.ntfs-3g.org/viewtopic.php?p=2114#1609](http://forum.ntfs-3g.org/viewtopic.php?p=2114#1609)

---

### Post by badguyanil on 2007-09-07
Ya well i do have ntfs partition but the file is not being saved on the ntfs partition! The partition  in which i am saving the files is FAT32. Anyways will also try saving the files on ext3 partition tomo morning and let you know if there is any sucess. Thanx for the help! I know it is kinda strange that the extension is getting atttached.

Also read about the bug with firefox! if it is a bug in firefox then i guess firefox should actually consider this very seriously!!!! there are a few problems of saving images too!!! well more on that later!

edit.........
.........well did try saving the files on the desktop and it does actually does not add the .bin extension to the files... strange where ever is the bug i guess it needs a fix.

Also guys if i want to save the file can i use some other browser other than firefox. Coz if it is a firefox problem then i can actually use some other to download the files!!!

---

