---
title: "mouse troubles"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by arkady69 on 2006-07-07
installed dapper a while ago and still have one minor issue to resolve. i would like to get my mouse wheel to scroll slightly faster. in windows, you can set how many lines the mouse wheel can scroll through pretty easily, but i can't seem to find any info on how to do it in ubuntu?

---

### Post by Denis on 2006-07-07
A quick [search]("http://www.ubuntuforums.org/search.php?searchid=6579822") on the forum shows that adjusting the scroll speed isn't easy to do. 

truant says the following: 
> **truant said:**
> Some digging around a Gnome forum ([here](http://gnomesupport.org/forums/viewtopic.php?t=5355&highlight=mouse+wheel+scroll)) suggested that scroll speed was handled by gtk, and it was hard coded.  He also says that scroll speed was going to get more sensible in gtk 2.6.  But dapper ships with gtk 2.8, and that post was made in february 2004.
If the scroll speed is hard coded in GTK it will be very difficult to adjust. Some future version of Gnome should support this feature to change it in an easy way. 


This explains why scroll speed in KDE **can** be adjusted (KDE uses QT instead of GTK). 

But there are alternatives: 
[LIST]
[*]If you would like that, you can make the scrollwheel do a "page up and page down" (search the forum for how to do this)
[*]You can change the scroll speed in firefox. I've found [this guide]("http://www.extremetech.com/article2/0,1697,1862333,00.asp") on how to do this. (It involves changing a few parameters in about:config)
[/LIST]

---

