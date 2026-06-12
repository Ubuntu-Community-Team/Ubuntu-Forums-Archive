---
title: "Program for organizing pictures."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Snipershot on 2008-02-25
I copied a folder of pictures over from my windows installation, the folder contains around 35k pictures and has a total size of about 8gb. Now I'm having problems actually entering this folder with the file browser and it tends to crash when i go into the folder. So I need a program to organize them. There are some features i want though, it must be able to handle this many pictures without problems, it should have a very simple method of categorizing the files into subfolders and preferrably have some feature to locate duplicate files. Any suggestions?

---

### Post by gimfred on 2008-02-25
Well, there is always the command line to move the files around. Fspot? I have two gigs of photos and it didn't falter... Try installing whatever you can find via synaptic I guess. There are some nifty programs around.

---

### Post by jonabyte on 2008-02-25
I love Picasa and it does run on Linux.

[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

I am not sure how it handles large folders.

Have you tried using command line to access/modify the folder/files??

---

### Post by Snipershot on 2008-02-25
well, i had planned on organizing them by what the picture display. So using command line wouldnt really be efficient at all.

---

### Post by justleen on 2008-02-25
I love picassa, but under linux i couldn't upload to picassa-web.. so i started using F-spot.. 

Love that now :)

---

### Post by ajgreeny on 2008-02-25
Can't imagine why your system crashes when you try to open the folder, but perhaps there is a corrupt file or folder somewhere in there.  I don't know of any way to sort that out, but as far as ubuntu photo managers is concerned, I use both f-spot and digikam, (I know, it's a kde app, but it's also great).  Picasa was too slow for me so I gave up on that, and top be honest, I don't think it's any better than the linux alternatives now that I'm used to them.  I have nearly 4GB of photos in a simple folder hierarchy.  I don't like to put everything in one folder and then organise them with tags, as some people seem to find acceptable, so my photo folder goes about 3 layers deep to accommodate everything.  Simple but effective with both applications.

---

### Post by ryanhaigh on 2008-02-25
you may want to look at installing a different file manager that may be better able to handle such a large number of images. I cannot say if one would be better than another but you may have more luck. Some file managers I know are listed below. To install one just click the link (must be using 7.10 Gutsy)

[apt://thunar]("apt://thunar")
[apt://konqueror]("apt://konqueror")
[apt://dolphin]("apt://dolphin")
[apt://pcmanfm]("apt://pcmanfm")
[apt://krusader]("apt://krusader")
[apt://gnome-commander]("apt://gnome-commander")

As far as finding duplicates goes you can use fdupes from the command line (you will need to install it first [apt://fdupes]("apt://fdupes") ) to find an optionally delete duplicate files, it would probably be best to do this while they are all in the same directory. I actually discussed this tonght in [this thread]("http://ubuntuforums.org/showthread.php?p=4400918")

Perhaps once you have eliminated all duplicates you could move files into temporary subfolders based on creation date, which I assume should also relate to content, so that the filemanager doesn't have to work so hard to generate 35k thumbnails. You should be able to find a script to do something like this fairly easily via google or even in these forums.

---

