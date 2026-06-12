---
title: "Really dumb question about file permissions"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-04-03
I'm trying to install a theme in Xubuntu (I like to experiment). I need to copy the file I downloaded into the theme directory which I would like to do by dragging and dropping, but of course I'm told I don't have permission to write to that directory. I know about the sudo command but what command would I have to give. What I'd really like to do is drag and drop, I gather I can do that by being in root but I don't know how to do that either. Yes I am an idiot:mrgreen: 

If some would be kind enough to explain all this stuff as if talking to a complete moron, I'd be grateful.

PS, I have searched the forums etc, but I'm going around in circles.

---

### Post by krusbjorn on 2006-04-03
To copy a file, use the command "sudo cp /path/to/file1 /path/to/file2" where file1 is the file you want to copy and file 2 is the new file.

Or you could just do "sudo nautilus" to get a nautilus window with root access.

---

### Post by Ptero-4 on 2006-04-03
IIRC. Your themes directory is in your home folder. You don't need root access to put Xfce themes. If it tells you that you don't have permission then you probably have a big permissions messup in your system.

---

### Post by clareb on 2006-04-03
The directory I'm trying to write to is in computer>file system>usr>share>themes. Which is where all the themes seem to hang out, is that OK, you've scared me.

---

### Post by krusbjorn on 2006-04-03
[QUOTE=clareb]The directory I'm trying to write to is in computer>file system>usr>share>themes. Which is where all the themes seem to hang out, is that OK, you've scared me.[/QUOTE]

Yes, the only place you are supposed to have write permissions to, without being root, is your /home/yourname directory.

---

### Post by Ptero-4 on 2006-04-04
clareb. The reason I talked about this is b/c most window managers/desktop environments (at least Kde and Gnome are like this) create a "themes" folder in each user's home folder to allow each user to install his/her own themes without having to get root access (good for allowing employees to add their preferred desktop themes without calling the sysadmin every time).

---

### Post by jannol on 2006-04-05
the theme folder in gnome and xfce is
/home/<username>/.themes and to check if you have it you need to open your home directory and choose view > hidden files

if you don't have it you simply create a new folder and name it .themes, then if you often install themes you could make a bookmark to it, I am not sure about how the xfce filemanager handles bookmarks or if it does at all but I think so.

---

### Post by Ptero-4 on 2006-04-05
You can create a symlink from the console and every filemanager known for linux handles them similarly.

---

### Post by clareb on 2006-04-05
Thanks for all the input, I'll work on your suggestions. I'm actually trawling the web looking for the ideal firefox theme now and how to install those.. I'll never be satisfied, 'cause when I am I'll be bored. :~)

---

