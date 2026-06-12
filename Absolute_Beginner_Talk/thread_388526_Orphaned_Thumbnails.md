---
title: "Orphaned Thumbnails"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-03-19
I'd sure like to get clear how thumbnail maintenance is handled.

Currently I'm looking at Nautilus, GQview, and Thunar. I note that my /.thumbnails directory has several subdirectories.

/fail/gnome-thumbnail-factory
/fail/gqview-1.0
/fail/thunar-vfs
/large
/normal

1) 'Fail'? What does that mean?

2) I note that only GQview seems to give me a method to root out old thumbs. Is that right?

3) Why does GQview's 'Thumbnail maintenance' panel have two sections?

/.gqview/thumbnails
/.thumbnails

4) Also, the action is "Remove orphaned or outdated thumbnails" - how does it decide what is "outdated"?

5) When I select that action for /.thumbnails, does it take care of all orphaned thumbs or just GQview's?

6) The GQview panel has a 'Create thumbnails' action. Does this only create thumbs for GQview, or thumbs shared with any other programs? And which thumb directory does it store them in?

If it only creates thumbs for itself, is there a way to generate thumbs for the other programs?

7) And how are thumbnails sourced anyway? It seems to be absolute paths - if I move things around, I have to generate thumbs again.

The GQview 'create thumbnails' action has a option to 'Store thumbnails local to source images'. Will this get rid of the problem of re-generating thumbs with every move? How is this handled anyway? Like, is it directory dependant, so if I move several images to new directories, they'll be in another area and thumbs will have to be re-generated? I figure there must be a reason or two that this isn't the default method.

---

### Post by CJay554 on 2007-04-12
i wouldnt know a thing on this subject.. thumbnails... im just gna post so that this goes to the top of the thread list and see if anyone out there has a clue?

---

### Post by diafygi on 2007-07-08
> **CJay554 said:**
> i wouldnt know a thing on this subject.. thumbnails... im just gna post so that this goes to the top of the thread list and see if anyone out there has a clue?
that, my friend, is called a bump, which is what I am doing

I would like to add a questions as well:
-Why do only some of the pictures in my gallery have thumbnails, and some do not? 

All they get is some Africa/dead tree icon. Is nautilus finding something wrong with these pictures? How do I find out what is wrong? GQview creates thumbnails just fine. I've attached a picture of an example folder.

Is anyone else getting this problem?

---

### Post by ~~Tito~~ on 2007-07-08
Yea that happens to me on some of them. I think its because the Pic is to big or o small, im not sure.

---

### Post by diafygi on 2007-07-15
I found out why only some pictures are previewed. In nautilus there is an option to set a size limit on files to be be thumbnailed/previewed. The default is 5 megabytes (5Mb). If you go to Edit > Preferences, then go to the Preview tab, then change the "Only for files smaller than" option to the size you want, you can control what gets thumbnailed. My problem = solved.

---

### Post by ofb on 2007-08-24
Months later, I've only found the answer to one of my questions:

You can store GQview thumbs within the image directory, but they are not portable - if you move the directory, you will have to generate all over again.

EDIT: actually, I'm wrong. The thumbs /are/ portable when the target is ext3, but not when the target is vfat. It doesn't matter if the source is ext3 or vfat.

---

