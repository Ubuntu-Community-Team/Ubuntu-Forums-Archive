---
title: "somthing.html~"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by arsenic23 on 2006-05-19
I've noticed a lot of files ending with ~ sitting around my /home .  They're obviously temp copies of things I've worked on, but why are they still sitting around?  I don't think I hardly ever see them in nautilus, even after hitting ctrl+h.  In fact I really only notice them when I'm cruising around my file system using the terminal.

Example:
[COLOR="DarkRed"]*****@Stick:~/Desktop$ ls
[COLOR="Lime"]bar-004fa0f9e2.desktop[/COLOR]  temp.htm~  text.txt~
nautilus-home.desktop   text.txt   tmp.html~[/COLOR]

Is there a simple way to kill all of these little buggers?   'Cus knowing they're lurking everywhere bothers me, and manually hunting them out and deleting them in terminal could consume my life.


I also wouldn't mind a way to turn off the trash can feature on hotplugged drives.  I do a lot of my work off a 400gig external hard drive, and going back and for between Windows, Ubuntu, and etc puts a lot of clutter on my 60gig ext3 partition. 

And, while I'm asking file related questions, what exactly is the 'lost+found' folder I see lurking about on my ext3 drives?

---

### Post by aysiu on 2006-05-19
In Gedit, there's probably a preference that creates backup files with the extension ~

Turn off that preference.

In Nautilus, there's a preference that includes a Delete command separate from Move to Trash. Enable that preference.

To find all the ~, paste these commands into the terminal: ```
sudo updatedb
locate txt~
locate html~
```

---

### Post by iball on 2006-05-20
lost+found is to do with file recovery after a crash.  In Linux, all files and directories have a parent, forming a tree.  Sometimes, after a crash, a file will "forget" who its parent is, so it becomes orphaned.  When you do a fsck, orphaned files are moved into lost+found, where the systems admin can locate them, and put them back where they belong.  There is a lost+found directory for each partition.  I wouldn't worry about it too much if I was you, as it is unlikely that anything useful is placed in here, as the files are often corrupt in this case.

One way of finding and removing the backup files that are created when you save a file using certain text editiors such as Vi or Gedit is to use find:
```
sudo find / -name *~ -print
```

You can then remove them using:
```
sudo find / -name *~ -exec rm {} \;
```

The first find is to make sure that nothing is matched that you will regret moving, because the 2nd find will remove files without asking...

I hope this helps
--Ian

---

### Post by steve.horsley on 2006-05-20
Just a quick note. I think that Breezy nautilus had a bug whereby it wouldn't show files or folders ending in ~ even if you told it to show hidden files. That's fixed in Dapper.

---

