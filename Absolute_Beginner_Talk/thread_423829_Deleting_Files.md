---
title: "Deleting Files"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by adsf on 2007-04-26
Hey Guys, been using Ubuntu for a while, loving it but i have come across some thing that seems to have stumped me.

I have thee hard drives in the machine.  the two extra drives are from my old machine are in NTFS.  I have mounted them both so I can read and write on them.  

To day i deleted a whole heap of stuff from the second disc mounted as hdc1.  I right cliked on them and sent to trash and they disappeared from the screen.  i then went in to the trash folder in the bottom right of the screen and they are not in there.  

I have deleted around 30 gig of stuff but am only showing 2.4 gig free space like the never deleted.  I a have had a look around in the disc and cant seem to find them.

Can any one help?

---

### Post by Kobalt on 2007-04-26
Go to your NTFS drive with Nautilus and press Ctrl+H to see hidden files. You should see a folder names .Trash-<your user name> in there with everything you have deleted. Empty or delete that folder to completely remove those files.

---

### Post by docshawnc on 2007-04-26
go to the drive you deleted the files on and show hidden files - look for a folder called .Trash-yourusername  

Bet the deleted files are hiding in there.  You need to delete them

---

### Post by adsf on 2007-04-26
Thanks Guys,  that was the problem

---

