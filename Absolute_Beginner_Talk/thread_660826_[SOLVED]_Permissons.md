---
title: "[SOLVED] Permissons"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-01-07
Why do I not have permission to access this folder?

/usr/share/pixmaps/

I have a firefox icon that's .png that I want to load into that folder so I can create a desktop launcher

---

### Post by hyper_ch on 2008-01-07
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dwhitney67 on 2008-01-07
The permissions on that folder are probably similar to the following:

```
drwxr-xr-x  18 root root 12288 2007-12-13 22:31 pixmaps/
```

This would prevent a regular-user from writing to the directory, however reading from it is possible.  This is a directory shared by all users on the system, thus the reason for this permission level is to prevent a regular-user from deleting or replacing files that another user may depend upon.

If you are the only user on your system, then use your system administration privileges to write to the directory.  For example:

```
$ sudo mv myImage.png /usr/share/pixmap
```

---

### Post by cartisdm on 2008-01-07
well, I'm not the only user.  I just set up a second account for my roommate (we're both administrators though), but I don't see why this particular file should interfer with him at all so I'll give it a shot.

---

### Post by DJ_Peng on 2008-01-07
You can also put the icon in any folder (even your /home folder) and just tell the launcher to use it from there.

---

### Post by cartisdm on 2008-01-07
I'm still trying to get the hang of navigating files within a terminal.  Do i need to be in the directory of the original file in order to move (mv) it to the directory I want in it?

How do I navigate to a directory that has a "space" in the directory name?

/home/dan/Documents/This Folder Has A Space

---

### Post by hyper_ch on 2008-01-07
copying is simple

```

copy FROM TO

```

You can use absolute or relative paths.

If you're in the directory /media/music and you want to copy something to /media/music/rnb you could do that:
```

cp FILE.ogg rnb/

```

If you're unsure about the directories, use absolut paths:
```

cp /media/music/FILE.ogg /media/music/rnb/

```

And if you have spaces in your path, you can encapsule with single quotation marks:
```

cp /media/music/FILE.ogg '/media/music/Alicia Keys/'

```

And what is also nice you can use the TAB key to complete paths and filenames. That's very handy. If there are more than one option for what you have started (normally type the first 2-3 characters), then press twice TAB and it will show you all of the options of available files/folders that beginn with those chars.

---

### Post by cartisdm on 2008-01-07
I'm obviously an idiot at this terminal stuff, frustrating because I want to learn this terminal stuff argh....

this is my printout

> dan@ol-red:~/Documents/Mozilla Firefox Icons/png$ mv firefox_icon.png /usr/share/pixmaps
mv: cannot move `firefox_icon.png' to `/usr/share/pixmaps/firefox_icon.png': Permission denied
dan@ol-red:~/Documents/Mozilla Firefox Icons/png$ mv firefox_icon.png /usr/share/pixmaps
mv: cannot move `firefox_icon.png' to `/usr/share/pixmaps/firefox_icon.png': Permission denied
dan@ol-red:~/Documents/Mozilla Firefox Icons/png$ 


edit: nevermind I forgot the sudo.....

---

### Post by DJ_Peng on 2008-01-07
At the risk of being more confusing, you can also but a backslash ("\") before each space. I didn't know about enclosing the path in quotes and saw that the backslash does the trick.

---

### Post by hyper_ch on 2008-01-07
This means

```

mv firefox_icon.png /usr/share/pixmaps

```
"rename firefox_icon.png to /user/share/pixmaps."

However "pixmaps" is a folder and you can't rename the file to that.

You would need to do this:
```

mv firefox_icon.png /usr/share/pixmaps/

```
That would move the icon into the pixmaps folder.

Only problem is: You are not "root" but "dan". The user "dan" does not have write permissions to that folder. So you need to do it as "sudo".

---

### Post by cartisdm on 2008-01-07
Got in finally.  Using a combination of everyone's posts (I'm sure I could have just one but some said it easier than others:)) so I finally have a nice firefox icon.  thanks all

---

