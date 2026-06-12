---
title: "Some werd BUG....."
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-01-28
see image about what im talking about...
  this trail lines happends every time a move a window/folder/firefox/ anything!! 

 can i fix this... i just notice this like today, i didnt see it before i think not sure tho!!!

---

### Post by JoshuaRL on 2008-01-28
Looks like it isn't redrawing quick enough.  Have you done anything lately to your video card?  If not, can you post your exact specs (processor, video card, ram) and the output of:

```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by Bluestick on 2008-01-28
ok im running 
AMD athlon 3400++
1.5 gigs of ram
200 gig HD
 A T I  Radeon X850 
PRO
____________________and i do have a problem with my video card.... and my "restricted driver" are not enablet...
 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R480 [Radeon X850Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

---

### Post by JoshuaRL on 2008-01-28
Okay, ATI has problems with Linux.  I've configured a Radeon Mobility 7500 and it was a bit of a bear.  What does your xorg.conf say about your video card?  What driver, vesa?

And if I was you I would search Google for:

site:ubuntuforums.org ATI R480 Radeon X850Pro X850

That might pull up some fixes for yours.  I'm almost sure that's the problem.

---

### Post by Bluestick on 2008-01-28
oh boy u have no idea ive tried everything to get them drivers to work... i dont even want to mess with it no more cause i have my "compfiz setup the cube and stuff"
  If i mess with it everything goes back to normal mode, with none visual effects :(
i guess ill just go and get a new VID card like a geforce or something!!!

---

