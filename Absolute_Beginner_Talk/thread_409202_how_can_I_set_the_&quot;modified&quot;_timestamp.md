---
title: "how can I set the &quot;modified&quot; timestamp?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jjf on 2007-04-14
I'm importing pictures into F-spot, and I noticed that all the pictures were dated "12/31/1999."  I discovered the cause: F-spot looks at the "modified" timestamp on a file.  The date of my camera had been reset, so my camera tagged all the photos as being created on 12/31/1999.  

I want to be able to tell Linux to set the "modified" timestamp to some date of my choice.  I've got hundreds of pictures to fix, so I'd like a command line command that can deal with a number of files at once (*.jpg) and (better yet) do it recursively within subfolders.

set_mtime_command "04/15/2007" /home/jjf/pictures/2007/04/ -r *.jpg

Clearly I don't know what I'm doing, but I'm hoping some command functionally like what I just described exists.

Thanks.

---

### Post by tkjacobsen on 2007-04-14
You can do a

touch /home/jjf/pictures/2007/04/*.jpg

which will change the timestamps to today for  all .jpgs in the folder. Dont know how to set it to a specific day.

see man touch (there is some options to set it to specific days)..

EDIT: this is the unix timestamps, I don't know if it will change the images internal tags

---

### Post by jjf on 2007-04-14
Great, thanks!  

man touch says you can provide a -d STRING argument and use that date instead of the current one.  

So can this be done recursively?  The pictures are organized into subfolders: ./year/month/day  
In order to save lots of time crawling through "day" subfolders, I'd like to just set the date of every picture taken in May of 2005 to May 15, 2005.  In other words:

touch -d "05/15/2005" /home/jjf/pictures/2005/05/ {and every subfolder in 05} /*.jpg

---

### Post by jjf on 2007-04-14
Hot d**n!  

:guitar: 

I love Linux.  (When it does what I want, at least.)  

this worked:

```
touch -d "04/15/2007" /home/jjf/pictures/2007/04/*/*.jpg
```

---

