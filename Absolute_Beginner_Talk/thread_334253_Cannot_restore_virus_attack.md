---
title: "Cannot restore: virus attack?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by pnh on 2007-01-08
We had a virus attack on our network recently. Afterward,
I have been having problems with my Ubuntu install. The
gui does not appear, but I can get into the system.
I used both the tar and partimage methods to backup before
the attack, but I cannot restore with either method now...

1. When I try to copy my tar file to root, or use tar on
the file to restore, I get the following message:
"/bin/cp: cannot execute binary file"
The same occurs with any other command.

2. When I boot from the rescue CD and run partimage,
I get stuck on the part where it says "Action to be done:"
That is, the menu will not let me select the option to:
"( ) Restore partition from an image file".
All instructions I've read say to "select" this option,
but I cannot get it to place a star on the correct line!!!
Therefore, I cannot _simply_ "select" that option.
If I press F5 to move on, it says it will create the backup
image that I've named on the previous page....now this
will probably over-write the backup image - which is what
I do not want to do.

Help. How do I restore my computer to be workable???
I have no gui as before the breakin/attack and everything
seems to be disabled to prevent me from fixing this.

---

### Post by hal10000 on 2007-01-08
Run partimage from the directory where you have stored the image file.
You have to type in the name (except the .000 or .001 part) with the complete path to restore it (e.g. /media/hda3/name_of_your_image). And you have to tell partimage where the image should be restored (e.g. /dev/hda2).

---

### Post by pnh on 2007-01-16
A few more simple questions:

Using partimage,

I typed in the backup_file.000 (my backup with .000 extension) and
partimage ran through the motions of restoring my HD from the image.
I only have a single file named backup_file.000. Is this wrong? During
the restoration, I get the message that partimage is looking for the
next file => backup_file.001, which does not exist, and then it gets
hung up at that point. I can get out with CNTL-C and re-boot, but I'm
uneasy about it. Will omitting the extention (.000) within partimage
solve this problem?

This How-To posting says you have to keep the extention (*.000)!
[http://ubuntuforums.org/showthread.php?t=226402&highlight=partimage](http://ubuntuforums.org/showthread.php?t=226402&highlight=partimage)
Which is correct?

I did not select the option to fill in zeros in the rest of the HD space.
My image is quite small with respect to the size of the HD space. I
didn't think this is necessary. Is it important to do every time? 

BTW, for newbies (like me), partimage is not easy to use. It is not
intuitive, and every step along the way is tricky. Each has a "gotcha".
For example, to navigate the menu in partimage, you must use tab
or arrows to move around and <spacebar> to select each option,
NOT <enter>, then press F5 to save and move on in the wizard-like
menus. Also, if you don't write down the path of the image file to
restore and have that in front of you BEFORE you start partimage.
you will get stuck there, after selecting all the options etc., and have to
start all over. There is no way to "browse" for the file like you can do in
most windows wizard applications. If I can get this to restore my
Ubuntu Linux machine, I will post a detailed description of EXACTLY
what you have to do to restore a downed machine due to a virus attack
(rootkit) using a system rescue CD, a backup image file, and partimage.
Clear instructions are lacking.

---

### Post by hal10000 on 2007-01-16
You're partly right, for unexperienced users it's may be a little tricky.
But i use it for a long time and i will never miss it. You just need two steps to restore an image (Name of the backup file and name of the partition to restore).
It's very fast (about 10 min. to restore a 20G partition)

> 
Also, if you don't write down the path of the image file to
restore and have that in front of you BEFORE you start partimage.
you will get stuck there, after selecting all the options etc., and have to
start all over. There is no way to "browse" for the file like you can do in
most windows wizard applications.

There is a simple solution to this problem if you mouse is working:
prior to start partimage type [COLOR="Red"]ls -1 my.backup.file.*[/COLOR]
then mark the file you want to restore with the mouse, then start partimage and just paste the filename with the middle mouse button.

You usually don't need to fill the  rest of your HD with zeros.

> I only have a single file named backup_file.000. Is this wrong? During
the restoration, I get the message that partimage is looking for the
next file => backup_file.001, which does not exist, and then it gets
hung up at that point.

When creating a backup file, you have to select an option wether to split the backup into more than one pieces or not (you usually just need one file).

I don't know what happened when you created your backup, but it seems as if partimage is looking for a second part which you say it does'nt exist. Something went wrong. I fear that if this part doesnt exist, your backup will be lost.

---

