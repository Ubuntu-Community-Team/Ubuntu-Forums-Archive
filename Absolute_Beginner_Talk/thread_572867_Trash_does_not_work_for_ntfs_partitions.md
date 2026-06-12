---
title: "Trash does not work for ntfs partitions ???"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by graben3 on 2007-10-10
I hava a partition in NTFS for XP... when I delete a file on it it never get to the trash... Why and what can i do ?

I'm using Ubuntu feisty 7.04 all updates made

---

### Post by cameronw on 2007-10-10
Yes I notice this as well. The thing is though when I access the NTFS partition from Windows I find a .Trash-cameronw folder with all my deleted files off that partition in it. Not sure if it's possible to direct all deleted items to a folder (.Trash in your home dir) automatically. There is a bug repot here  [https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247) . I think it may be so if you run two linux systems using the same home dir, files aren't switched between partitions when deleting, as it makes a new .Trash-<username> on every mount point.

---

### Post by graben3 on 2007-10-10
I hit ctrl+h in nautilus on my HD i deleted files from in NTFS... I have this too (.Trash-graben) ....

What can I do to make it appear and be cleared automatically in the Ubuntu Trash ?

Or at least (don't want to come to this since I plan to quit XP for Ubuntu) just set the folder created to RECYCLER instead of .Trash-graben on that HD  so I can clear the trash under XP ?

---

### Post by cameronw on 2007-10-10
Im not sure if you can set it to go into the Ubuntu trash. Reading that bug report, I found a post that said even dragging a file from a NTFS partition to the Trash icon still does not make it go into the Trash. I'll look around if there are any ways to have all files in that folder automatically move to .Trash in home dir. Because this problem annoys me to.

---

### Post by cameronw on 2007-10-10
I found this : > Solving the issue was trivial. I just had to add the appropriate file system names to the table, rebuild gnome-vfs and experience the trash icon to its full power :-) The issue is reported in [bug #336533]("https://bugs.launchpad.net/bugs/336533") and is already commited to pkgsrc. Therefore, it will be part of the forthcoming pkgsrc-2006Q1 stable branch.Now that I think of it you could have simple script accessible from scripts menu that moves the file to /sda?/home/<username>/.Trash

---

### Post by graben3 on 2007-10-11
I do not like the idea to move files across physical hd's....

Would like to be able to virtually merge trash folders together or add symlinks for each hd trash into my home folder trash....that would work too if they are permanent

Don't know if something like this is possible....

---

### Post by graben3 on 2007-10-11
> Solving the issue was trivial. I just had to add the appropriate file system names to the table, rebuild gnome-vfs and experience the trash icon to its full power  The issue is reported in bug #336533 and is already commited to pkgsrc. Therefore, it will be part of the forthcoming pkgsrc-2006Q1 stable branch.


I will try this solution to see... seems complicated for a little anoying bug ! I will give it a try however....

---

### Post by Sef on 2007-10-11
> .Trash-cameronw folder with all my deleted files off that partition in it. Not sure if it's possible to direct all deleted items to a folder (.Trash in your home dir)

To get rid of the trash in .trash, I highlighted all the folders (CTRL + A), and right clicked, then chose trash.  Then once in trash, I just emptied it.

---

### Post by graben3 on 2007-10-11
> **Sef said:**
> To get rid of the trash in .trash, I highlighted all the folders (CTRL + A), and right clicked, then chose trash.  Then once in trash, I just emptied it.

I don't understand what you mean.... you trashed all .Trash-<your username> folders on all drives you have mounted ?

This won't solve the issue...it will just delete all trashed files on all drives you have mounted once... but when I will trash new files it will recreate those directories and they will not be seen in my global trash at /home/username/.Trash folder....


I<ll have to redo this step everytime I trash files on other drives than my main drive....

---

