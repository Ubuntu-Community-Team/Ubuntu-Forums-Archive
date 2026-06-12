---
title: "What's a terminal command for....."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-03-31
I backed up gigs upon gigs of music files on dvds and accidentally set the permission to read only (stupid I know) and all those pad lock orange icons annoy me. 

Now that I've put the files back onto my system whats the easiest way to change the permissions of the folders and files to read and write? Point and clicking my way through them is painstaking :mad:

Is there something I can do about this in terminal?

---

### Post by penguinpi.com on 2008-03-31
```
sudo chmod 777 -R /folder
```

---

### Post by milton1 on 2008-03-31
```
 chmod -R 755 <foldername> 
```
This should recursively set the permissions on everything inside the folder listed as <foldername>. I would check, however, to see if the -R flag is upper or lower case (man chmod)

---

### Post by h-town on 2008-03-31
harrison@machine:~$ ls
Desktop  Documents  Music  Pictures  Torrents  Videos
harrison@machine:~$ sudo chmod 777 -R /Music
[sudo] password for harrison: 
chmod: cannot access `/Music': No such file or directory
harrison@machine:~$ 

i know i'm doing something stoooopid again : )

---

### Post by ByteJuggler on 2008-03-31
> **h-town said:**
> I backed up gigs upon gigs of music files on dvds and accidentally set the permission to read only (stupid I know) and all those pad lock orange icons annoy me. 

Now that I've put the files back onto my system whats the easiest way to change the permissions of the folders and files to read and write? Point and clicking my way through them is painstaking :mad:

Is there something I can do about this in terminal?

You betcha.

Firstly, change ownership to yourself (if needed) of folder "folder":

```

sudo chown -R $(whoami).$(whoami) folder
```

Next, add read and write permissions to all files in "folder":
```
sudo chmod -R u+rw folder
```

(That is untested but should work, if you run into trouble/I've forgotten anything, post back.)

---

### Post by philinux on 2008-03-31
Just for info.

For your quick reference here are a few standard numeric codes (that's what it is called) that are often used..

```
Frequently used numeric parameters for chmod
755
	The general preferred permissions for almost all the files on your disk
700
	Extremely private data
500
	Extremely private data that you would not like to accidentally modify. So write protect it
775
	General files used when working as a Group (Others can only view/execute your files)
770
	Important files used when working as a Group (Others cannot do anything with your files)
750
	Allowing group to view your files but no write access (Others cannot do anything with your files)
777
	Something you should never want to do ;-)


```

---

### Post by penguinpi.com on 2008-03-31
l

---

### Post by ByteJuggler on 2008-03-31
> **h-town said:**
> harrison@machine:~$ ls
Desktop  Documents  Music  Pictures  Torrents  Videos
harrison@machine:~$ sudo chmod 777 -R /Music
[sudo] password for harrison: 
chmod: cannot access `/Music': No such file or directory
harrison@machine:~$ 

i know i'm doing something stoooopid again : )

/Music is not the same as ~/Music aka /home/harrison/Music (which is where you're "ls"ing.)  Remove the "/" and you'll be good to go.  (BTW, 777 is probably overdoing it a little, that will mark every folder and every file as executable by anyone on the system, which is strictly speaking not correct. 644 [rw to you, read-only to your primary group and the world] or 640 [rw to you, read-only to your group, non-readable by everyone else] for files, is probably best.)

---

### Post by yota on 2008-03-31
Hi,

the command to change permission is "chmod", and the command to change owner/group is "chown".
You can see "man chmod" or "man chmod" for details; probably you need something like:
```

sudo chmod -R u=rwX,g=rwX,o=rX *BaseDirectory*
sudo chown -R *yourUser*:users *BaseDirectory*

```
where you have to substitute *yourUser* with your user name and *BaseDirectory* with the base folder path of your data.
-R means recursively change; u=rwX means that the owner will have r ead, w rite and e X ecute permission (but only on directories and files that are already executable); g= are the group permissions and o= the other users permissions, with same logic as before.

Hope this helps!

edit: oops! many other answers bornt while I was typing...

---

### Post by h-town on 2008-03-31
Thanks for all your help and guidance guys. I used ByteJugglers code and it works like a charm! Saved me a lot of hassles. :popcorn:

---

### Post by mcduck on 2008-03-31
Also, if you are already the owner of those files & directories, you do not (and should not) use 'sudo'. It's not something that you need to add to every command you run, only to those that really need to be run with full root privileges..

---

