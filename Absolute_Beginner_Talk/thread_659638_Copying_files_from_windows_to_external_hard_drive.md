---
title: "Copying files from windows to external hard drive"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Brakesur on 2008-01-05
Ok, I did my searching, and I couldn't find the answer I need.

My other computer suddenly died on me, and I have a lot of music that I purchased on it that I cannot lose. I put the hard drive in my other laptop which is pretty much a backup. I'm on it now, and I have the hard drive from the broken computer in it. 

As you all know, you cannot use a windows installation on another computer. I am using a live cd right now to get online. I am getting the permissions errors or something when I try to copy the files from the disk to my external hard drive. I don't want to install an OS until I can backup everything. 

How do I get around these permission restrictions to copy and save my stuff?

---

### Post by BreathEasy on 2008-01-05
Can you be more specific about the errors? 

Keep in mind, Linux cannot assign permissions on an NTFS drive because there are none - the filesystem doesn't support it. However, copying files to it will still work, it will just complain a lot, but the files will be there. Unless I'm missing something, in which case we go back to my first question.

---

### Post by chevyman962000 on 2008-01-05
I have a similar problem, in that I'm using an external HD. when I try to create a folder, I am told that I am not the owner of that folder... Is there a way to become the owner?

---

### Post by Brakesur on 2008-01-05
I get this error:

Error while copying to "media/disk/backup".

You do not have permissions to write to this folder.

I don't have any special security on my external drive, so I don't know what is making this not work,

---

### Post by SpookComix on 2008-01-05
I would suspect that this is an issue with your "regular user" not having access to that mount point.  Try preceeding your command with "sudo" if your at a command line.

If you're on an Ubuntu Live CD, run "gksudo nautilus" to run a graphical drag-and-drop environment as "root" with all the permissions you should need.

If you're on an Kubuntu Live CD, try "kdesudo konqueror" for a graphical environment as "root" under KDE.

--SpookComix

---

### Post by SpookComix on 2008-01-05
PS.  If you have access to a "Windows Ultimate Boot CD," plug in your external drive and boot from it.  Use "Fab's Autobackup" to grab the information that most people need the most, like their email and settings, favorites (from IE, Firefox *and* Opera), etc.  It grabs everything under a user's My Documents folder.  There are many options.  Restoring the files is a snap.  I use it weekly for clients.

---

