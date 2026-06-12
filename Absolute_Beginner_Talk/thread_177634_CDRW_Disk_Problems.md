---
title: "CD/RW Disk Problems"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Jim Hill on 2006-05-16
Hi: I'm just getting my feet wet with Ubuntu, and here's my latest problem.

Natulus displays the folders in CD/RW disks (blank disks, and disks with files saved while using Win XP), but I can't paste Open Office word processor files (there's no paste command), and I can't eject the disk.  The disk was formatted using Direct CD, and works ok with Nero and Roxio.

Maybe I need a media application like Nero or Roxio - any suggestions?

Jim

---

### Post by zenkoanlife on 2006-05-16
I don't know much about the CD/RWs but i'v noticed that with some things sometimes i don't have the paste command, sometimes <ctrl>+v still works. just a thought.

---

### Post by steve.horsley on 2006-05-16
You can't just drag-and-drop files into a CD. You need re-burn the CD to write to it - completely overwrite it with a new set of contents. With Nautilus, open a second window. It helps to have one window each side of the screen. 

In one window, choose menu Go->CD Creator. This window now contains what is going ot be burned to the CD. Delete anything from this window that you don't want to put on the CD.

Use the other window to navigate round the hard disk, and drag the stuff you want on the cd to the creator window.

When you have collected all the stuff in the creator window, click Write to disk. If you are using Breezy, it will probably fail unless you erase the CD first (It's in the menus somewhere - I can't remember where - I'm on Dapper which doesn't have that problem, and doesn't have an erase option either).

If you can't get the CD burned with nautilus, I suggest you try k3b which has always been rock solid for me. But hte pronciple is the same - you make up a new contents set and then completely erase and re-write the CD.

---

### Post by Jim Hill on 2006-05-16
Thanks for the tips. Yes I'm using Breezy.  Little slow in replying as I stopped for lunch.  I'm not used to the quick turnaround in responses.  Where do I find k3b?
Jim

---

### Post by Bd0g on 2006-05-16
[QUOTE=Jim Hill]Thanks for the tips. Yes I'm using Breezy.  Little slow in replying as I stopped for lunch.  I'm not used to the quick turnaround in responses.  Where do I find k3b?
Jim[/QUOTE]

Type this in a terminal:
```
sudo apt-get install k3b
```

---

### Post by Jim Hill on 2006-05-16
That's certainly easy.  I also want to install pan so I will have a newsgroup reader. It's in Ubuntu Packages.  Can I use the same approach:  sudo apt -get install pan  ?
Jim

---

### Post by Bd0g on 2006-05-16
Yupp ;-)

---

