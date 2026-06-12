---
title: "How do I change permissions for multiple files"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by HuxleyHyperion on 2006-10-08
I'm a Linux newbie (just installed it about three days ago), and want to know how to change file permissions for a bunch of files at the same time.  Not understanding the whole file ownership thing at first, I created a folder under root (/download) to store stuff in, but now I realize I should store that kind of stuff in my home folder.

I have now moved all of the files into my home folder (cut & paste in WinXP), but they still have root ownership.  I know how to change the ownership to <username> on individual files, but would like to know if there is a way to change all of them at once.  I want to be able to read and write, but do I also need execute?  They're audio and video files, if that matters.

Oh, and what exactly are the emblems for?  Thanks for your help.

---

### Post by bruenig on 2006-10-08
> I have now moved all of the files into my home folder (cut & paste in WinXP), but they still have root ownership. I know how to change the ownership to <username> on individual files, but would like to know if there is a way to change all of them at once. I want to be able to read and write, but do I also need execute? They're audio and video files, if that matters.
Say the folder all your stuff is in is called foo. You can do 
```
sudo chown -R username:username foo/
```
The -R means recursively, which means it will do that command to every file within that directory.

Also a 755 permission is probably sufficient for what you want. That means it will allow you, the owner of the file, read write and execute, and will allow others to read and execute.
```
chmod 755 -R foo/
```

---

### Post by aysiu on 2006-10-08
```
sudo chown -R huxley:huxley /home/huxley
``` should do it.

---

### Post by linuksamiko on 2006-10-08
I don't know how you changed the files so fare but I will describe it in two ways (GUI, terminal):

1st GUI --> open a terminal and type in "sudo nautilus". This will open nautilus as root and you can do what ever you want to (be VERY CAREFULL what you are doing)
Browse to the folder where you have your files and select them all. Right click on them and choos "properties" one of the Tabs lets you choos which user and group they should belong.

2nd terminal --> browse to the Folder where your files are located. You can do this by typing: cd /path/where/you/have/your/files
To change owner and groupe of a file you need the chmod command it is used like this:
sudo chmod <user>:<groupe> <filename> (the groupe is named like the user in ubuntu)
if you like to change all of them you have to type:
sudo chmod <user>:<groupd> *.*

---

### Post by aysiu on 2006-10-08
> **linuksamiko said:**
> 
1st GUI --> open a terminal and type in "sudo nautilus". This will open nautilus as root and you can do what ever you want to (be VERY CAREFULL what you are doing) Actually, you should use the command ```
gksudo nautilus
``` since it is a graphical application. More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) > Browse to the folder where you have your files and select them all. Right click on them and choos "properties" one of the Tabs lets you choos which user and group they should belong. Last time I checked, Nautilus didn't do recursive permissions/ownership changes. Is this a new feature?

**Edit**: Just tested it out. Nautilus does not (as of Dapper) support recursive permission/ownership changes. I don't know if Nautilus will get it in Edgy or not.

---

### Post by HuxleyHyperion on 2006-10-08
Thanks for your help guys!  That was fast!

What exactly is the execute flag for?  Do I need that on a video/music file?

---

