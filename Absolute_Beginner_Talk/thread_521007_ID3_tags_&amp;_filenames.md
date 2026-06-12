---
title: "ID3 tags &amp; filenames"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by clitmaster on 2007-08-08
Hey! I've dumped all of my songs into one 'Music' folder, within my home folder...none of the songs hav ID3 tags, all ID3 fields are completely blank on every track...What I want to do, ultimately, is have all of my tracks renamed to 'artist - title', within an 'album name' folder, within an 'artist' folder, within my 'Music' folder. 

So I guess what I need to do is get the tags filled out from what filenames are present, probably from an auto CDDB ID3 tag generator. Then from the ID3 tags, have the files renamed appropriately, and placed in the appropriate folders.


Which program would be best to fill the ID3 tags? Which program would be best to rename the files appropriately and placed into the appropriate folders, based on the ID3 tags? (Out of the 1000+ tracks, some filenames have the artist & title, some have just the title, etc.) Am I on the right track?

To be honest, I haven't tried much yet (except easytag which just confused me somehow ) but some guidance on what I should do exactly would be nice, so I don't head down the wrong track (these processes can take a long time). I'm using gnome, too. TIA

---

### Post by kevinlyfellow on 2007-08-08
I use audio tag tool to rename files/tag files.  It's very configurable (but still easy), I think you'll like it.  [http://pwp.netcabo.pt/paol/tagtool/](http://pwp.netcabo.pt/paol/tagtool/)

---

### Post by starcraft.man on 2007-08-08
Easytag is a good editor. I will explain how to use it. For automatic editing with the CDDB it is easy. First open up all the songs into easytag (easy way is to have it scan the top level music folder containing all your songs, browse for the folder via the left tree pane). Then the songs should sort down via folder they were ripped in. Next select a whole group of them that form one set/cd (i.e. a whole album of songs, the background color usually changes from white to blue when it's a different album and back for another new one) then push the CDDB button (shiny CD in bar). A new screen pops up, push the search button and leave it automatic. The list of options matching will display, pick the one that best fits. Note that multiple instances of same CD may display, some are remixes make sure its exactly the same. If you need more control, use the manual tab.

Now for manual batch editing (if you want to make artist/album fields uniform) it is even easier. In the middle pane select all the songs from a album/artist. Then look to the right and see the ID3 fields, type in the name you want to apply to all tracks selected. When happy, right click the field you just typed in and select "tag selected files with this field".

In both cases once all changes are made and your happy, select all files you edited (highlighted in red) and then push the save button, data will be written out.

I had my files sorted in folders already, not sure if EasyTag can sort files based on the ID3, this should make sure their tagged right I'm sure making folders is much less painful than the ID3 tags manually. Best of luck :).

---

### Post by aysiu on 2007-08-09
I would recommend TagTool. I found EasyTag's interface confusing.

---

### Post by Inxsible on 2007-08-09
> **aysiu said:**
> I would recommend TagTool. I found EasyTag's interface confusing.
I use EasyTag too. I agree the interface is not very intuitive, but it was starcraft.man who told me about EasyTag and later explained to me how to use it. :D

Now it seems like a breeze :guitar:

---

### Post by clitmaster on 2007-08-09
I'll try easyTag again, and also tagTool, when I get home from work... thanx for the advice ;)

---

