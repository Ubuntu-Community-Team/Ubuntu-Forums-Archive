---
title: "Thunar Terminal Folder Permissions Remove"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Ch3knraz3 on 2008-04-12
I started this thread on accident before I was able to read all the similar posts.  Then I could not figure out how to delete it.

Since I can edit it I might as well ask my question.

The delete and rename menu options are greyed out on the menu bar and when I right click on a folder.  In fact all I seem to be able to do is browse.  When I drag to trash I get a message that says I do not have permissions.

By the way my apostrophe key doesn t seem to work and makes a system beep.  I have no idea what is up with that???

Anyway, back to my problem.  I am trying to set up a folder in home to  hold my MP3s.  Currently they are on a windows box on the network in a shared folder.  I was following the directions of some tutorial and I was working in terminal and I executed this command:

> sudo mkdir /home/samba.prMusic

Instead of:

> sudo mkdir /home/samba/prMusic

Now I cannot remove the directory.  I have tried:

> wprince3@mookie:~$ sudo rm /home/samba.prMusic
[sudo] password for wprince3:
rm: cannot remove `/home/samba.prMusic': Is a directory

and

> wprince3@mookie:/home$ rm samba.prmusic
rm: cannot remove `samba.prmusic': No such file or directory

I have spend two hours looking around the documentation and searching the forums and am starting to get really kind of frustrated.  I have a real interest in learning how to Ubuntu.  I plan on installing various versions on different boxes.  I intend to have a  fairly complicated network but at the pace I am going I do not know if I will have the patience.  I started down this path three weeks ago.  I am not new to computers, OSs, CLIs, Programming Languages, etc. but every step forward is followed by a detour/roadblock that takes me hours to research and resolve before I can continue with the original task.

I really want to live in a FREE world without WINDOWS and GATES...
Sorry, I am beginning to whine.  I hate whiners.

Anyway, I would appreciate some help.  Thanks, in advance.

Ch3knraz3](*,)
There are 10 kinds of people...
2+2 = 5 for large values of 2

---

### Post by Ch3knraz3 on 2008-04-12
Bump

My apostrophe seems to work inconsistently.

Seems to always work with a double tap...

---

