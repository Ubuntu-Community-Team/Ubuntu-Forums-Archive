---
title: "ubuntu equivalent of 'shortcuts'"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by droogy on 2006-08-23
What's the ubuntu/linux equivalent of windows shortcuts?  Ie. placing links on my desktop to directories on my ntfs drives...

---

### Post by Qrk on 2006-08-23
You can right click on a folder in nautilus and select "make link" then drag that link to your desktop. (won't work unless you have write permissions)

To make a launcher you can right click on the desktop and select "create launcher" and then specify the program name and icon. If you want nautilus to open to a directory (say to make a link) use "create launcher" and in the command box type 

nautilus /path/to/folder

---

### Post by droogy on 2006-08-24
> **Qrk said:**
> You can right click on a folder in nautilus and select "make link" then drag that link to your desktop. (won't work unless you have write permissions)

To make a launcher you can right click on the desktop and select "create launcher" and then specify the program name and icon. If you want nautilus to open to a directory (say to make a link) use "create launcher" and in the command box type 

nautilus /path/to/folder

thanks.  one thing I've found though is that the nautilus commandline does not like spaces.. ie. trying to open 'Documents and Settings' on the windows drive it caues problems and doesn't open.

---

### Post by mssever on 2006-08-24
If you're willing to use the command line to set it up, you can use symlinks, which are much more powerful than Windows shortcuts. Do this from a terminal:```
ln -s /path/to/target name_of_link
``` Type a \ before any spaces in filenames.

The reason this is better, is because if you symlink something, it always acts like that thing, even in open/save dialogs.

---

### Post by droogy on 2006-08-24
> **mssever said:**
> If you're willing to use the command line to set it up, you can use symlinks, which are much more powerful than Windows shortcuts. Do this from a terminal:```
ln -s /path/to/target name_of_link
``` Type a \ before any spaces in filenames.

The reason this is better, is because if you symlink something, it always acts like that thing, even in open/save dialogs.

Where does this symlink go?  on the desktop of ubuntu?

---

### Post by robins_web on 2006-08-24
*one thing I've found though is that the nautilus commandline does not like spaces*

Actually, it's Linux itself that doesn't like spaces, not just nautilus. But I generally manage to get around that by-the-way-I-name-my-files, see? :-D

---

### Post by mssever on 2006-08-24
> **droogy said:**
> Where does this symlink go?  on the desktop of ubuntu?

Wherever you put it. For example, if I wanted to place a symlink to the My Documents folder on my desktop, I'd do this (file paths are for my system):
```
[FONT=Courier New]ln -s /media/hda1/Documents\ and\ Settings/My\ User/My\ Documents Desktop[/FONT]
```

Type [FONT=Courier New][COLOR=SeaGreen]man ln[/COLOR][/FONT] for documentation

---

### Post by droogy on 2006-08-24
I tried the ln command... it made something not sure what... is it possible to symlink a directory?!  I just want a link to a folder on my ntfs drive that's a few levels deep.

---

### Post by mssever on 2006-08-24
Yes, it's possble to symlink a directory. And an icon should show up. Note, however, that by default, the terminal starts out in ~ (your home directory) and the desktop is ~/Desktop. So you need to specify the proper path--or cd to the proper directory. If you don't see an icon on the desktop, look in your home folder.

---

### Post by droogy on 2006-08-24
> **mssever said:**
> Yes, it's possble to symlink a directory. And an icon should show up. Note, however, that by default, the terminal starts out in ~ (your home directory) and the desktop is ~/Desktop. So you need to specify the proper path--or cd to the proper directory. If you don't see an icon on the desktop, look in your home folder.

I've made a few... now how do a get rid of the ones I made my mistake?  I've trien sudo rm <*Link name*>

---

### Post by mssever on 2006-08-24
> **droogy said:**
> I've made a few... now how do a get rid of the ones I made my mistake?  I've trien sudo rm <*Link name*>

That should work, though you only need the sudo if you created the link with sudo (which is unneccesary in your home area). If rm gives you errors, please post them. You should also be able to delete them from Nautilus.

> **robins_web said:**
> *one thing I've found though is that the nautilus commandline does not like spaces*

Actually, it's Linux itself that doesn't like spaces, not just nautilus. But I generally manage to get around that by-the-way-I-name-my-files, see? :-D Just noticed this post. Actually, Linux allows absolutely any character in filenames except for /. But special characters need to be escaped. You can do it several ways. One way is to put a backslash (\) in front of every special char. Or, you can usually surround the full path/filename in quotes.

---

### Post by droogy on 2006-08-24
Thanks for all your help guys... you've made me just that little bit more comfortable w/ my switch to ubuntu.  Starting to get the hang of it... so used to everything being at my fingertips but I enjoy getting 'down w/ the command line'. hehe.

---

### Post by mssever on 2006-08-24
> **droogy said:**
> Thanks for all your help guys... you've made me just that little bit more comfortable w/ my switch to ubuntu.  Starting to get the hang of it... so used to everything being at my fingertips but I enjoy getting 'down w/ the command line'. hehe.

Once you get to know the command line, you'll start to really like it. I rarely use Nautilus because it's so much faster and easier to use the command line for file management--since I've learned it.

---

