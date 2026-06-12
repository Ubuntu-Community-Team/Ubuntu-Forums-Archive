---
title: "Not given write permission by default for files copied from CD into /home/user"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Gimbo on 2005-12-29
This is my second day so please bear with me :???: 

I'm copying some files I backed up (eg photos in JPEG format) from CDs (normal CD-Rs) I burned before starting with Ubuntu into /home/user (my username is andrew, so it's /home/andrew/).

It seems that when I copy these files, they appear with a padlock icon by default, and their permissions are set so that "write" is unticked for all users, including the owner of the files (which I assume is me, as they're copied into my /home folder).

I've gone through and manually checked "write" in the Permissions tab of Properties, but I assume there's an easier, automated way, which I'd like to know for future reference. Is there some way to automatically give write permissions for the owner when files are copied into a home directory? Also, is there a way to make all files in a folder use the folder's permissions (eg when I add write permissions to /home/andrew/photos, can I make it so that all sub-folders and files get those permissions automatically?

Any advice/help would be greatly appreciated.

---

### Post by darth_vector on 2005-12-29
hi,

chmod is the command you want to change permissions. if you open up a terminal and cd to the required directory:

cd /home/andrew/photos
chmod u+rw *

should do it. the arguments that you give chmod (in this case) tell it to give the **u**ser **r**ead and **w**rite access to * - which is everything in the directory. have a look at the man page for chmod:

man chmod

good luck :)

---

### Post by Gimbo on 2005-12-29
I've had a look at man chmod, which will be very useful for future reference - thanks :)

[QUOTE=darth_vector]
* - which is everything in the directory
[/QUOTE]

* doesn't seem to change the permissions for absolutely everything in the directory. For example,

```

cd /home/andrew
chmod u+rw *

```

sets the permissions up how I want them for all sub-directories of /home/andrew, but the files in (for example) /home/andrew/videos are still all "locked" (ie I don't have write permission for them). For want of a proper technical description, it seems that * doesn't "drill down" more than 1 level below the directory you're in when you use it.

---

### Post by Madpilot on 2005-12-29
Look in man chmod for the -R (recursive) option, it does what you want WRT subdirectories and such

*chmod -R 755 ~/foo* will change everything in /foo to 755 perms, including all the way down any subdirectory trees in /foo.

(I still use the numerical permissions, because I know them from messing with FTP in Windows and haven't bothered sorting out the whole +/- wrx-whatever system yet...) :p

---

### Post by GreyFox503 on 2005-12-29
Use the -R flag for recursion with the chmod and chown commands.  (that is, it will affect all directories and sub-directories "below" it)

so you could do:

```
chmod -R u+rw *
``` 

chown is the command to change the owner of the files.  It works similarly.  If for some reason it says you are not the owner of the files, then something like this should fix it:

```
sudo chown -R andrew:andrew /home/andrew/photos
``` 
The above command will change the owner and group of all files in /home/andrew/photos to "andrew", recursively.  You will probably need a sudo in front, because you can't change ownership of the root's files as a normal user.

Just be careful with the wildcards (* and others).  Changing stuff inside your home directory is fine, but you don't want to run around and change the owner or permissions of most other files on your system.  Have fun!

---

### Post by Gimbo on 2005-12-29
```

chmod -R u+rw *

```
worked great.

Thanks very much for all your help guys!

---

### Post by Manny C on 2005-12-29
Incidentally, if you use the excellent k3b for future backups, you will find that there is an inbuilt "backup" option available. This results in files being burnt onto CD that are not read-only. 

It does this by preserving the status quo permissions of files copied onto the CD.

---

