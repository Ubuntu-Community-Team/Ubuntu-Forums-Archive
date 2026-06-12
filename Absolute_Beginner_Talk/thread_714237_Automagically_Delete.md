---
title: "Automagically Delete"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by PDG1 on 2008-03-03
hey... I've been using an app called Miro for a while... really cool...
it helped me find cool High def podcasts and stuff... 
but Miro is meant to be used to play the files as well... and I've got my Xbox connected and I just use SMB to watch the content I Download
but I find that on the computer in my room it doesn't have enough to keep it open all the time, so I can't have it downloading new stuff when it comes out.

but Rhythm Box has the podcast thing built into it... so I thought I could just find a way to automatically delete files by age and I'd get almost the same thing

is there a way to automatically Delete files by age?

---

### Post by es@urito on 2008-03-03
You can do it with a bash script using the following tools:
find
rm
A simple example could be:
```
find /home/user/video/ -type f -mtime +3 -exec rm {} \;
```

To delete all files older than 3 days in the /home/user/video directory. Be careful using it

---

### Post by es@urito on 2008-03-03
... type ```
man find
``` to have details about the find command

---

### Post by PDG1 on 2008-03-13
wow. Thanks!
 I'm not too concerned about deleting old videos... as long as I make sure to put in the right path I should be safe.
And I don't have any critical files on that drive.

I can just have it run every 24 hours or so.

I don't know if this is a good idea... but is there any ways that I can have Linux move a file after I watch it through SMB?

I'm going to set up this find and rm bash first

so if I just start with ```
find /home/user/video/ -type f -mtime +3
``` and see if that finds the files I want... I should be safe, right?

---

### Post by PDG1 on 2008-03-14
actually... Now I've got a differrent problem that I really can't explain.
I can't seem to access the folders I've downloaded through rhythmbox on my XBMC.
I'm really confused... because I don't think it's permissions...
if I move the files from the downloaded folders into a folder I already had before when i was using Miro, it works great.... sorta
I'm... just lost.
any ideas?

---

