---
title: "Searching for files in ubuntu?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-31
Hi,

In windows, if I wanted to search for files within a particular folder or subfolder, i could right click on the folder, then choose "search".  If I wanted to do a search for *.mp3, I would pop that in, & it would bring up all mp3 files in a directory.

Im trying to figure out an easy way to do this but I cant. 

I know thats pretty basic.

Thanks,
Rich

---

### Post by warp99 on 2008-03-31
The easiest way is to open a console in that directory and type 'find -name *.mp3'. That will search the current directory and any sub-directories for that string with the wildcard.

Edit:

It's also finds the files much faster then in Windows.

---

### Post by Oldsoldier2003 on 2008-03-31
> **warp99 said:**
> The easiest way is to open a console in that directory and type 'find -name *.mp3'. That will search the current directory and any sub-directories for that string with the wildcard.

Edit:

It's also finds the files much faster then in Windows.

here is a nice tutorial on using find. Find is a very powerful  tool.
[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by JAPrufrock on 2008-03-31
Find is great, but requires opening a terminal. A gui way to do it would be to add the utility "search for files..." to one of your panels.  Just right click on any panel and then left click  "add to panel".  Then find "Search for files", and add it.   The principal advantage using "Search for files" is that once it locates the file, you can double click it and it will open.

---

### Post by Oldsoldier2003 on 2008-03-31
> **JAPrufrock said:**
> Find is great, but requires opening a terminal. A gui way to do it would be to add the utility "search for files..." to one of your panels.  Just right click on any panel and then left click  "add to panel".  Then find "Search for files", and add it.   The principal advantage using "Search for files" is that once it locates the file, you can double click it and it will open.

It doesn't search subdirectories,hence limiting its usefulness to the OP nor does the search script you can call from nautilus.

---

### Post by JAPrufrock on 2008-03-31
> **Oldsoldier2003 said:**
> It doesn't search subdirectories,hence limiting its usefulness to the OP nor does the search script you can call from nautilus.

Sure it searches subdirectories.  What it doesn't do is search the whole computer- you have to choose the partition you want.  You can only choose one partition at a time, and it will search all the directories and subdirectories of that partition.

---

### Post by garyed on 2008-04-01
You could also use  " Places -> Search for Files " from the menu bar.

---

### Post by Oldsoldier2003 on 2008-04-01
> **JAPrufrock said:**
> Sure it searches subdirectories.  What it doesn't do is search the whole computer- you have to choose the partition you want.  You can only choose one partition at a time, and it will search all the directories and subdirectories of that partition.

thats not really what he wanted though, he wants to check a directory and its subdirectories. I really do wish the graphical serach tool had a recursive directory search...

---

### Post by JAPrufrock on 2008-04-01
One can choose the directory or sub-directory he/she wants to search in "Search for Files" by going to "Look in Folder" first.  After choosing the directory/sub-directory you can then search for a particular file/files.

---

### Post by Oldsoldier2003 on 2008-04-01
> **JAPrufrock said:**
> One can choose the directory or sub-directory he/she wants to search in "Search for Files" by going to "Look in Folder" first.  After choosing the directory/sub-directory you can then search for a particular file/files.

he wanted recursive searching... or thats what seemed to be implied, using the example of Mp3s searching the music directory is kinda useless if you have a library of ripped cds...

---

### Post by JAPrufrock on 2008-04-01
> **Oldsoldier2003 said:**
> he wanted recursive searching... or thats what seemed to be implied, using the example of Mp3s searching the music directory is kinda useless if you have a library of ripped cds...

Are we writing about two different things here?  What I'm saying is that "Search for File" _is _recursive, if I understand the meaning of the word.   In other words "Search for File" will search the selected directory and its subdirectories and the subdirectories of those subdirectories, etc.  Isn't that what you mean by recursive?

---

### Post by robertchahine on 2008-04-01
i use this method it's global and fast:
open the terminal and write 
```
 locate *[COLOR="Red"]the file name[/COLOR]*
```
then press enter , it will search the directory or the machine for your filename

---

### Post by t0p on 2008-04-01
> **JAPrufrock said:**
> Find is great, but requires opening a terminal. A gui way to do it would be to add the utility "search for files..." to one of your panels.  Just right click on any panel and then left click  "add to panel".  Then find "Search for files", and add it.   The principal advantage using "Search for files" is that once it locates the file, you can double click it and it will open.

The GUI "search for files" tool is *no good*!!!

Why do I say that?  Because the damn tool doesn't find files that I ask it to find!!

For example: I've got some files on my system that are called "cfi-en".  I ask the damn Tracker Search Tool to find cfi-en and it comes back with "Your search returned no results".

But if I use **find**... well, I give the command
```
sudo find / -name cfi-en
```
and I get the following output:
```
/media/sda1/Documents and Settings/Home/My Documents/The Library/cfi-en
/usr/share/doc/cfi-en
/usr/share/doc-base/cfi-en
```

So, how come **find** can find the files and the GUI tool can't?  Seems to me, this is yet another example of the fact that *the CLI is inherently better than the GUI*.  It's a shame there are so many Windows-damaged folk around who can't use the command line.

**EDIT:** **locate** is a good tool too.  And it's another CLI tool.  Why oh why do folk like JAPrufrock think that having to open a terminal is some kind of problem???****

---

### Post by billgoldberg on 2008-04-01
> **garyed said:**
> You could also use  " Places -> Search for Files " from the menu bar.

I use that to search for files and it's fast as hell.

I add it to the panel instead of the deskbar applet.

---

### Post by t0p on 2008-04-01
> **billgoldberg said:**
> I use that [**Places > Search for Files**] to search for files and it's fast as hell.

Yes indeed.  And it even *works* - **Places > Search for Files** is able to find my "cfi-en" files that the Tracker Search Tool has such difficulty with.

> **billgoldberg said:**
> I add it to the panel instead of the deskbar applet.

I'm also going to replace that deskbar applet with this tool.

---

### Post by dannyboy79 on 2008-04-01
find thrashes your hard drive, so the more you use it, the more your thrashing your hard drive. Use the slocate database, the command is locate. You can change which folders the slocate database will include, so I had to update my slocate database to include the /media/ folder among others. a cron job is run by default in Feisty to update the slocate database every night. otherwise, if you just put a file somewhere and forgot where, you can run
sudo updatedb

and it will update the slocate database. good luck

I have also read that this command works  for binary files also.
which vncviewer
will return the results of where vncviewer is found.

---

### Post by warp99 on 2008-04-02
> **dannyboy79 said:**
> 
sudo updatedb

and it will update the slocate database. good luck

You know I tried to use locate a long time ago, but forgot all about it until I you posted that you have to update the database. 

See you learn something new every day. Thanks!!!

---

### Post by dannyboy79 on 2008-04-03
well you only need to run sudo if say you just added a file to your computer and you want to use locate immediately. updatedb happens daily on my machine (Feisty Fawn) by default, you can see within cron.daily that find.notslocate get's called which runs updatedb.

---

### Post by jakupl on 2008-04-03
I've always just used 'locate' and then the file name. nice and easy

---

### Post by prismpirate on 2008-04-03
> **RichTJ99 said:**
> Hi,

In windows, if I wanted to search for files within a particular folder or subfolder, i could right click on the folder, then choose "search".  If I wanted to do a search for *.mp3, I would pop that in, & it would bring up all mp3 files in a directory.

Im trying to figure out an easy way to do this but I cant. 

I know thats pretty basic.

Thanks,
Rich

I assume that your running Gutsy Gibbon. If so, then type it in in Tracker. 

Applications>Accessories>Tracker Search Tool

type in *.mp3 and your done :)

---

