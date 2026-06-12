---
title: "Photo Management For Old People?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-21
My grandfather wants a digital camera. I'm going to set up a computer for him (ubuntu) and make it so he can easily transfer files to his computer. 

What he needs to do: 
transfer files
view files

This needs to be as simple as possible. No thinking should be involved. Automounting and autotransferring. 

In fact, if he could do it all in one program and never have to close a window that would be awesome.

Any ideas?

---

### Post by Inxsible on 2007-11-21
F-Spot comes pre-installed with Ubuntu and does recognize when a camera is attached. But DigiKam is a better option.

---

### Post by skyjacker on 2007-11-21
You might give digiKam a try.

---

### Post by tdrusk on 2007-11-21
I actually need something easier.  

could I create a bash command with 
```
man rsync
```
to make it sync the files from his card to his folder, then open a nautilus window with all his pictures?

---

### Post by Incense on 2007-11-21
> **tdrusk said:**
> I actually need something easier.  

could I create a bash command with 
```
man rsync
```
to make it sync the files from his card to his folder, then open a nautilus window with all his pictures?

I think f-spot is pretty easy. You just get a pop up saying you want to import your photos? You click import and you're done. Then it takes you to the main window with all your photos. You could make a bash command,but I think you would be taking out the simplicity at that point. f-spot will take care of all the folders, transfers, and everything you are looking for. I like DigiKam as well, but I don't think it's as simple as f-spot.

---

### Post by tdrusk on 2007-11-22
> **Incense said:**
> I think f-spot is pretty easy. You just get a pop up saying you want to import your photos? You click import and you're done. Then it takes you to the main window with all your photos. You could make a bash command,but I think you would be taking out the simplicity at that point. f-spot will take care of all the folders, transfers, and everything you are looking for. I like DigiKam as well, but I don't think it's as simple as f-spot.
I was thinking a bash command that syncs to a folder in home, then opens that folder when it's done.

---

### Post by torgrot on 2007-11-22
Another choice would be Picassa from Google, they just released it for Linux.


torgrot

---

### Post by Incense on 2007-11-22
> **tdrusk said:**
> I was thinking a bash command that syncs to a folder in home, then opens that folder when it's done.

I'm sure that your idea would work just fine, though I'm not too big on bash, and couldn't tell you how to do that. I like the f-spot idea, because you could place an link to f-spot on his desktop, and they need to only click on that to access the entire photo library. Although, now that I think about it, ubuntu used to do just what you are talking about before they included f-spot. Nautilus would just import the photos to whatever photo you wanted. I think it's just a command under the removable drives and media section under system. So I guess it really wouldn't be hard to write a script to do what you want. Anyway, this reply was largely useless, so I'm going to stop now. :)

---

### Post by tdrusk on 2007-11-22
I've made the script

```
#!/bin/bash
# sync files
rsync -av /media/disk/test /home/tyler/Test
#clean up camera
rm -r /media/disk/test
#open and scan for pictures
picasa 


```

the only problem is picasa isn't starting at the end.

if I go into a terminal and do
```
picasa
```
it works. 

what's the deal?

---

### Post by torgrot on 2007-11-22
This is the command to start picasa
/opt/picasa/bin/picasa

torgrot

---

### Post by tdrusk on 2007-11-22
doesn't work either.

---

### Post by torgrot on 2007-11-22
Try this in the script
sh /opt/picasa/bin/picasa

It starts picasa for me in a test script.

torgrot

---

### Post by tdrusk on 2007-11-22
this works now 

```
#!/bin/bash
# sync files
rsync -av /media/disk/test /home/tyler/Test
#clean up camera
rm -r /media/disk/test
#open and scan for pictures
sh /opt/picasa/bin/picasa

```

thanks :)

---

### Post by torgrot on 2007-11-22
No problem.  Just killing time.

torgrot

---

### Post by tdrusk on 2007-11-22
> **torgrot said:**
> No problem.  Just killing time.

torgrot
hmm.

is there a way for rsync to scan the import direcory so it only extracts the .jpg files?

OR 

a image viewer that can show all the .jpg files in a directory?

Picasa kind of does this, but it separates the pictures into folders. That's not necessary.

---

