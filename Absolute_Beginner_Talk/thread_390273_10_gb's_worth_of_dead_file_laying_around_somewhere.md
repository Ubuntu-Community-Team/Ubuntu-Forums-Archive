---
title: "10 gb's worth of dead file laying around somewhere"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by sveard on 2007-03-21
Hi all,

Earlier today I was creating a .tar.gz file with the Archive Manager, I was adding nearly 10 gigabytes of data to the archive, and just before it completed my laptop shut down (it didn't suspend or hibernate or anything) because the battery was running low.

Now that I've restarted I've got an unfinished archive somewhere on my computer that's nearly 10 gigabytes large. So my problem isn't that I've lost data or anything, but that I got a dead unused file somewhere in my filesystem.

So my question is, where does the Archive Manager temporarily store it's archives when it's compressing? I want to delete this cluncker. :)

Thanks!

---

### Post by steve.horsley on 2007-03-21
Probably in /tmp

You can go go
**du / | sort -n**
which should find it after a minute or two

---

### Post by zorkerz on 2007-03-21
applications->accessories->Disk Usage Analyzer
id imagine 10 gig file would not be to hard to find with this
I think this was installed by default othrewise ga applications->add/remove... and search for disk usage analyzer

---

### Post by fakie_flip on 2007-03-21
You can find all files bigger than 5 gigabytes.

sudo find / -size +5G

You can also find files between 5 gigabytes and 15 gigabytes.

find / -size +5G -and -15G

For more on the find command, look at this good tutorial at another good forum.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Find_command_0](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Find_command_0)

You can also find all tar archives compressed with gzip ending in ".tar.gz".

sudo find / -iname '*.tar.gz'

Let me know if this helps.

---

### Post by aktiwers on 2007-03-21
I found that going as sudo into my trash, I found A LOT of files. So sudo doesnt share the same trash as normal user. Maybe if you deleted the big file as root (sudo), its still in the root trash?

Try 
```
gksudo nautilus
```And then check the trash.

EDIT:
I just read your post again, and you clearly state that the pc crashed and you didnt delete it.
Sorry about that.

---

### Post by sveard on 2007-03-21
sudo find / -size +5G did the trick!

File wasn't in /tmp or anything, it was in the directory the original, uncompressed files were. I missed it because it was hidden,

Thanks,

And on a side note, thanks Ubuntu for setting me free from the chains called Windows :)

---

