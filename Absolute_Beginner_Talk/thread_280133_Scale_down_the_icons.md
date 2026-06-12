---
title: "Scale down the icons?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Will5639 on 2006-10-19
Gnome icons .. needless to say (I hope).. are huge!

I run a 1440x900 resolution and.. with only 35 icons my desktop is nearing capacity.

Yeh I'll move some off the desktop... but im really used to Window's icon sceme, where thier set to a uniform size and spacing.  Hell.. 30-35 icons is nothing for window's.

And (I don't care either way) window's dosn't care so much about generating pretty previews of things like pictures.. its a standard image saying "hey ima jpg / gif / whatever".

Does Ubuntu/Gnome support anything like that????

---

### Post by Dr. Nick on 2006-10-19
while possible, the only way i know would be tetious, you can right click any icon and hit 'strech icon" and then make it smaller

---

### Post by Dr. Nick on 2006-10-19
look under gconf at this key

/desktop/gnome/thumbnailers/disable_all

setting that to true may take the thumbnails off pictures

Or in nautilus go to edit, prefrences , preview tab and set them to never

---

### Post by Will5639 on 2006-10-19
Changed the preview setting...  I suppose it's a start.

I'm looking something a little more "big-picture" to have a standard for ALL icons regardless of type... (without using the tetious aproach you suggested). 

But it sounds like something I'll just have to live with.. ](*,)

---

### Post by dolphinsonar on 2006-10-21
There has to be a way to set the default icon size to a size smaller than the one it is currently at.

The thing that says "Restore Icon's Original Size" (no apostrophe in Icons by the way) has to have a code base hiding somewhere.  How can you open up the source code and change the "Original Size?"

Find the answer to that question and you can just change all the "origninal sizes" to smaller, no?

A little help from someone with more experience would be good.

---

### Post by gustolove on 2006-10-21
unless you are completely in love with gnome i suggest going to xfce... 

sudo apt-get install xubuntu-desktop

---------

---

### Post by Dr. Nick on 2006-10-21
Wow, we seemed to be thinking to hard :)

Open up a file browser and go to Edit -> Prefrences -> Change Default Zoom Level on "Icon View Defaults" to a smaller percentage

Overlooked it on my way to disabling previews

---

### Post by donniep152 on 2006-11-01
Many thanks for this answer.  It was exactly what I was looking for.

---

### Post by Camden on 2006-11-20
Got it!!!  

gconf-editor

dive down to apps->nautilus->icon view

change default zoom level to "small" or "smaller" or "smallest"
whatever suits your needs (no quotes)

---

