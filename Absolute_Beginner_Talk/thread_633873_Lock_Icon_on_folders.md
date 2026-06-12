---
title: "Lock Icon on folders?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-12-07
Ok so i downloaded some folders from a windows machine.  I can access the contents but i cannot delete the folders/content?  I tried using shift + delete. 

For some reason there is a copy of desktop.ini in each folder?  How can i delete these files?

Also what is the file path to my desktop?

---

### Post by jordanmthomas on 2007-12-07
1.  to delete it, make sure you are the owner and have write permissions.  (look in its properties when you right click)
2.  If you're not, you can delete them like this:
```
sudo rm -r ~/Desktop/foldername
```
It will delete the entire folder called foldername on your desktop, regardless of the owner.
OR
```
sudo chown -R $USER ~/Desktop/foldername
```
will make sure you own all the files (and the folder itself)  Then, you can delete desktop.ini or anything else from the folders.
Also, just so you know, desktop.ini is what Windows uses to store information about a folder (like whether to use list view or icon view, etc)

The path to your desktop is /home/username/Desktop

---

### Post by dreadh3ad on 2007-12-07
ahhh thanks!

Also how do i cd into a directory with a space in the name?  Its driving me nuts lol

---

### Post by jordanmthomas on 2007-12-07
You can do it in one of two ways.
1.  with quotation marks
```
cd "folder with spaces"
```
or 
2.  with escape characters
```
cd folder\ with\ spaces
```

The \ character tells the shell to ignore the next character.

---

### Post by kpkeerthi on 2007-12-07
You can also use the <TAB> key to auto complete commands/files/folder names.

> 
...from [http://www.linuxclues.com/articles/06.htm](http://www.linuxclues.com/articles/06.htm)
Just type a few characters that start a command and press the Tab key. The command or name of an existing directory or file will be completed.

Try this. Type the following and then press the Tab key:

$ cd /u

Now add an "s" and press Tab, type "h" and press Tab. The result should be:

$ cd /usr/share/

Now type "f" "o" "n" and press Tab, "t" press Tab, "d" Tab, and press the Enter key. That should put you in:

/usr/share/fonts/ttf/decoratives


---

