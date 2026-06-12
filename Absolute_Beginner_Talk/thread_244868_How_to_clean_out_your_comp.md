---
title: "How to clean out your comp?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Luthy on 2006-08-27
Stupid question i knw, but when i upload stuff in general, the list that pops up that i select whatever it is i need to upload, some of the stuff on there is old, like ive already deleted it but its showing up just on that list anyway! how do i clean up my comp? Note i am not a "newbie" im just fiwuering out where to put this stupid question. Thanks!

---

### Post by nu2this on 2006-08-27
I think this might be what you're looking for
```
sudo apt-get autoclean
```
cleared out enough that I got an extra gig & some context menu items were removed too.

---

### Post by Carbonfish on 2006-08-27
Hi Luthy,

If I understand you right, this should help, if you just want to purge packages that are obsolete, in a terminal type:

sudo apt-get autoclean

If you have obsolete packages in your archives you will see a series of messages listing the files that are now deleted. 

If you are really pressed for space and don't want a patch management repository on your computer, you can run: 

sudo apt-get clean

Just remember, this command deletes all files in what you could potentially use as a local patch management repository.

---

### Post by huwshimi on 2006-08-27
Let me see if I understand...

I'm guess you are doing something like uploading files to a webserver with something like Gftp, and when you do so, you see a whole lot of file names in the list that have a "." before the name. I'm also having stab that you have been using something like gedit to make most of these files. These files are often auto generated backups of files that you have created. In this case you can safely delete them. However in some places such as you home directory Ubuntu stores data (such as user settings) for the software that you run. In that case you should not delete them as you might have problems.

To see hidden files you can go to a window and then View > Show Hidden Files.

If you are ever sure whether to delete files or not then you best option is to leave it alone.

---

### Post by Luthy on 2006-08-27
Thanks guys i love you! ;-)

---

### Post by Luthy on 2006-08-27
um tried both but old stuff still shwoing up? hmm?

---

### Post by Carbonfish on 2006-08-28
Sorry Luthy, 

I just noticed that your problem is still there. Unfortunately, I am out of suggestions. I am sure that someone much better versed in Linux than me will show up soon.  ;) 

KC

---

### Post by huwshimi on 2006-08-28
> **Luthy said:**
> um tried both but old stuff still shwoing up? hmm?

If you give us some more specific details then that might help.

Cheers.

---

### Post by Luthy on 2006-08-30
When i go to upload stuff into like my website or whatev, i push the upload button right? Well on the list of stuff i can upload onto whatev it us i want alot of old files show up, ones i have deleted. I have cleared my cookies, cache, deleted my recent docs ect. but the old docs, still show up when i want to upload stuff!

---

### Post by huwshimi on 2006-08-30
Did you try my previous suggestion and show hidden files and delete the ones you don't want (files that start with a "." will be hidden)?

Cheers.

---

### Post by Luthy on 2006-08-31
yes. and it didnt work :-(

---

### Post by insane_alien on 2006-08-31
the only true way to clear out your computer is to copy your documents to a cd make sure you have an os install disk and then apply an electromagnet to the harddrive.

---

