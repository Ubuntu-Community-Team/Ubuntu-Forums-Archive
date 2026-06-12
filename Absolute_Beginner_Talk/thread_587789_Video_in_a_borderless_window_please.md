---
title: "Video in a borderless window please"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-23
I love playing videos on my computer in a window and not full screen so i can do other work.
But i think the window borders take up to much space yes i know your like what is he talking about there only like a 1/4 in at mos and most of the sides are less then an 1/8 but i usually have 5 windows open on one desktop and 2 on the others so it can get cramt quikly and this would be a nice way to save some space
so any way 
could some one tell me a way to get vlc player to have a border less window
so it looks just like the full screen video except it is in a borderless window :)
thanks

---

### Post by chuckyp on 2007-10-23
I thought this was in the options for VLC.  They may have removed it though since trackign a mouse for a DVD in a none borderless none movable window would be a PITA.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-23
well no you could move it
if i could implement it, it would have
  -  left click to move window 
  -  resize the way you normally do get near a conner or side and click ...  
  -  then for every thing else like minimize right click menu pops up and then ....

---

### Post by glantucan on 2007-11-17
Hi I found the real solution, I think.

Go to ***Options/preferences***, then choose ***video*/*Output Modules*/*Xvideo***, click on advanced options (bottom-right side of the window), and then check** *the alternate full screen method***.
It did work fo me :D

Cheers

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-03
what player was this in

---

### Post by NoVista on 2007-12-03
VLC ..

Settings, preferences,video.
Scroll down to "Window decorations", and un-check it.

You now have the video in whatever size and location you have already established, and absolutely no borders.

Ok, I use a black desktop, and didn't realize there actually is still a border around the frame.
It looks to be 1 pixel wide, and it's color is black, hence the reason I did not initially see it.
However, for all intesive purposes, it is borderless.

---

### Post by Whiffle on 2007-12-03
You mean like this?

[http://www.resnet.trinity.edu/avaselaa/konq2.png](http://www.resnet.trinity.edu/avaselaa/konq2.png)

All i did was open it up in mplayer, right click the Titlebar, Advanced > No Border.

Easy as pie.  You can move it around w/ alt+click.  At least thats how its done in KDE.

edit: I'm not using compiz though, so you may not have that option w/ compiz, i can't remember.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-10
> **NoVista said:**
> VLC ..

Settings, preferences,video.
Scroll down to "Window decorations", and un-check it.

You now have the video in whatever size and location you have already established, and absolutely no borders.

Ok, I use a black desktop, and didn't realize there actually is still a border around the frame.
It looks to be 1 pixel wide, and it's color is black, hence the reason I did not initially see it.
However, for all intesive purposes, it is borderless.

ya that dint work for me i dont know why though

---

### Post by NoVista on 2007-12-10
So, and this is important to know, you already have the window size and location set?
When you start VLC, the window already goes to the position you have already set, and it is in the size you already set?
And it displays there? With borders, still?

If you are resizing and positioning the window every time VLC starts, you don''t have all the setting set right.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-12
ok will try and play around with it more but it dosen't seem to do any thing when i uncheck stuff in the options

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-12
I  cant get this to work for the life of me 
can you run me through exactly how to do this with vlc

---

### Post by forestpixie on 2007-12-12
open vlc preferences -
 then near bottom on the right tick advanced options - then click video scroll down to window decorations

---

### Post by mozetti on 2007-12-12
If you are running Compiz, use the Compiz Config Settings Manager and get to the Window Decoration option (can't remember where it is, not at my Ubuntu PC). 

The default argument is any, so just add: ```
 & !name=<name of your video player>
```

I used this to remove the window decoration from my terminal. To do the same for videos, my settings would look like this: ```
any & !name=gnome-terminal & !name=mplayer
```

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-15
> **forestpixie said:**
> open vlc preferences -
 then near bottom on the right tick advanced options - then click video scroll down to window decorations

ya thats what i did before 
but I do have desktop effects on so i will try what mozetti said

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-15
can do in kde easy dont know in gnome yet

---

### Post by il-luzhin on 2008-05-22
In case anyone is still watching this thread

I was wondering if <<joe>> neglected to:
pref --> Interface --> Main Interface --> wxWidgets

uncheck 'embed video in interface'

This launches a seperate window for viewing which is rendered sans borders.

---

