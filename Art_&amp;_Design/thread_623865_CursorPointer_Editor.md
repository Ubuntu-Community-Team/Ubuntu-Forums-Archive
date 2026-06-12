---
title: "Cursor/Pointer Editor"
date: 2007-11-26
forum: Art &amp; Design
---

### Post by frbe0101 on 2007-11-26
I like the DMZ theme cursor for gnome, but I would really like it in red, is there any program were I can make my own cursors?

---

### Post by jessemichaels on 2007-11-26
Note: I dont know how much more simple i can make this tutorial. its a very simple process naturally, and im doing my best to account for every detail in the simplest way possible. 

Yeah, i found a great app with an actual interface. Its called Gursor maker. It can even import CursorXP themes, which i find rather nifty. 

 what you do is you find the directory where the original cursors are installed. i believe its ~/.icons/CURSOR DIRECTORY. Back up the directory, and move the copy to wherever its convenient. youll always want the original in case something screws up. there will be a ton of files, go ahead and open them with whatever editor you like. You dont have to edit all of them, as many are the same thing, or different parts of an animated cursor. 

NOTE: you might have to rename them to pngs. just right click>rename>add .png to the end of the file. 

now edit them in whatever way you choose, and of course save them, referrably to the backup directory. 

this next part is where gursormaker comes in. download it at [http://gursormaker.sourceforge.net/](http://gursormaker.sourceforge.net/)  Its not in the repositories i don't think. 

make sure you have all of the dependencies installed, theyre in the readme file i think. 

you load it up [i think you have to do it through a terminal, just open your preferred terminal and type:

gursormaker &

Okay now that thats done, put the cursors in where you want them, and set the hot spots. 

NOTE: hotspots are where the cursor is located in a sense. it defines where the pointer of the cursor is. if the hotspots are incorrect, then your theme will be a serious pain in the ***. i mean a serious pain in the ***. and dont get me wrong, this very well could be the hardest part of the process. i use an app like kiconedit [its in the repositories] to find the exact pixel values, although that may not be the best choice, check it out for yourself.


once youre finally done with all of that, get every cursor set with hotspots and all, you can go to File>export Xcursor theme. this will make a folder, you choose where. just move the output folder into ~/.icons/NEW CURSOR THEME DIRECTORY. its also wise to save the project in your backup directory in case you want to make quick changes.

NOTE: do not archive them and then use an automatic installer, it doesnt seem to work for me. 

Odds are there will be a few problems, a few things to fix, but overall it should work well assuming you follow those steps in that order. 

Hope this guide helps, feel free to ask questions.

---

### Post by frbe0101 on 2007-11-26
Wow thinks! let me try that and get back to you if it works.

---

### Post by frbe0101 on 2007-11-26
ok so this is what I did:
1. Had a copy of DMZ-white cursors and theme
2. Open it in gursormaker (cursors are listed all looked good)
3. Selecter cursor modifiers, made a new row, change the sat to make it all red, then selected batch apply and selected all and then I get nothing, just an error in the terminal thast says

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/GursorMaker/curmod.py", line 365, in Close
    self.pbar = ProgressDialog(parent, 'Applying filters...', len(data)+1)
TypeError: object of type 'listiterator' has no len()

---

### Post by jessemichaels on 2007-11-26
oh wow haha actually i didnt even know you could do that in gursormaker, thats a tasty little tidbit of knowledge. for now, seeing as its apparent that that section isnt working, I'd try to do it manually for all of them in gimp or something of the sort, more like my instructions, unless theres another way i still dont know about.  hopefully someone can find a solution for that, unfortunately its way over my head. i'm just learning some code, mostly css at the moment, and if i move on to python next ill work on it some and send it to the developer. 

But in the mean time, hopefully someone either knows or will be able to cook up a solution.

---

### Post by frbe0101 on 2007-11-27
I can't convert the original DMZ (X11 cursor) icons into .pngs, changin the name does nothing as gimps simply can't recognize it or open it.

---

### Post by burt_57 on 2007-11-27
this is where I see the location of all cursor..... /etc/X11/cursors
But when I go to Preferences Cursor selection, it will not change my cursor!
Why oh why ?  :confused:

---

### Post by smartboyathome on 2007-11-27
Because your cursors actually go into the /usr/share/icons folder (or ~/.icons).

---

### Post by jessemichaels on 2007-11-27
AHA okay unpack your theme from the archive, then import xcursor theme into gursormaker. from there dont change anything and export as x cursor theme. there should be a sources folder, with each file as a png and a config with the hotspots in it for you. 

im not sure for that theme, but i think the problem is that theres multiple cursors packed into one file, and that screws up the conversion, just makes a broken file. gursormaker treats them as an animation when in fact they are the different cursor sizes. [this might have been part of the problem with the first manipulation you tried within gursormaker.]  i know thats the case for the dmz vanilla aa [black] cursor set, thats what i tried it on. 

sorry it took so long i have a term paper to write. doing my best not to fail haha.

pertaining to smartboy:
heres a neat page with a nice installation section. well written and clear, although nothe the directories are wrong. they are just /usr/share/icons and usr/local/share/icons [i thnk]
[http://www.xaprb.com/blog/2006/04/24/beautiful-x11-cursors/](http://www.xaprb.com/blog/2006/04/24/beautiful-x11-cursors/)

---

### Post by frbe0101 on 2007-11-28
Ok I modified the .png, now how do I get it to gursormaker to see them and save them as a cursor theme?

---

### Post by jessemichaels on 2007-11-28
open gursormaker [gursormaker &] in the terminal, or just make a link to it to make it a launcher. dont open a theme, just a blank one.

bring up another gursormaker window with the original theme, just so you can know which cursors go where and such. also you can use those hotspots unless you edited the shape or the cursor.

okay, now that youre at that point, go to the new one, double click on a cursor field, itll bring up a new window. for example, expand left_ptr field, and it will open the options window for the main cursor. under the hotspots theres an area where you can add the image files, just double click and open your .png of coice. be sure to add hotspots for every cursor.

for animated cursors, there is a button that says add a row. this will be the next frame in the animation. to set the frame time, go the the delay and change it to whichever value you want it to be. 

export as x cursor theme and move the created folder to whichever directory you preefer. i use ~/.icons personally, but hatever is convenient for you.

---

