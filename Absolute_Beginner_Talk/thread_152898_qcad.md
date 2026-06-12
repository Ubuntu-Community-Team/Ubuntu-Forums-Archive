---
title: "qcad"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-03-30
I'm looking for a decent tutorial in qcad.  I've used other architectural programs back when I was running M$ (only a week ago, but now seems like a lifetime)...

I mainly do floor-planning and facility layouts, and it looks as though this package will work quite well.

Any input is greatly appreciated. I need this package to get productive again.

---

### Post by arnieboy on 2006-03-30
[http://www.ribbonsoft.com/qcad_doc.html](http://www.ribbonsoft.com/qcad_doc.html). look for the pdf manual.

---

### Post by gymsmoke on 2006-03-30
Nada - there is no tutorial in that pdf.  And, the pdf is the html user manual exported to pdf.  I have the html manual, and it contains no tutorial either.

---

### Post by hatstand on 2007-01-28
Wikipedia gives this [http://www.linuxfocus.org/English/January2002/article132.shtml](http://www.linuxfocus.org/English/January2002/article132.shtml) as a "good tutorial".

I couldn't make head nor tail of it: the language is strange and it seems to be about a previous version. See what you think.

Isn't there some sort of "now click this button" beginner's guide?

---

### Post by gymsmoke on 2007-01-28
I was in touch with the author of qcad (via channels) some time ago, and he promised that he would have a book on qcad out "very soon"... that was some time ago, and I haven't seen it yet.  I'd really like to get my arms around how to use this package.  As mujch as I feel very confident in being able to tear into most software I spend time on, cad is one of those areas where I feel like a complete dunce.  I was finally able to succesfully draw a box in the interface after about 2 weeks of experimentation, but the learning curve is so steep that I've had to put it down for a while, since I also need to work, go to school, and have time to sleep...

---

### Post by ridgeland on 2007-02-25
Gymsmoke

I also found it almost impossible to use QCad so I created a Tutorial as I cleared each hurdle.
The tutorial is here
[http://www.david.dentlinger.net/qcad/index.html](http://www.david.dentlinger.net/qcad/index.html)
I think it can get you started.
Please give me get some feedback though.  I want to improve it.

---

### Post by nanotube on 2007-09-03
> **ridgeland said:**
> Gymsmoke

I also found it almost impossible to use QCad so I created a Tutorial as I cleared each hurdle.
The tutorial is here
[http://www.david.dentlinger.net/qcad/index.html](http://www.david.dentlinger.net/qcad/index.html)
I think it can get you started.
Please give me get some feedback though.  I want to improve it.

i eventually made sense of the linuxfocus tutorial... but yours is very nice too. :)

i have a problem though... when making dimensions, the dimension lines show up, but there's no labels! anyone run into this problem, and if so, what's the fix?

using 7.04 (feisty), with qcad from the official repos. any help would be appreciated.

---

### Post by ridgeland on 2007-09-03
> i have a problem though... when making dimensions, the dimension lines show up, but there's no labels! anyone run into this problem, and if so, what's the fix?
Most likely the labels are there, so are the arrows at the end of the dimension lines.  The most likely problem is the size of the label, i.e. it may be 1/10,000 the size of the drawing.  
The size of the text is in Edit -> Current Drawing Preferences -> tab "Dimensions".  The size depends on the scale of the drawing.  I  saw a default of about .2 and changed it to 4 for a layout of a room  we were laying tile in.  One other note is that each time I pop on a dimension line, I change snap-to to endpoint then pick the points to dimension, then change snap-to to grid then set where the dimension line is placed.

---

### Post by nanotube on 2007-09-03
> **ridgeland said:**
> Most likely the labels are there, so are the arrows at the end of the dimension lines.  The most likely problem is the size of the label, i.e. it may be 1/10,000 the size of the drawing.  
The size of the text is in Edit -> Current Drawing Preferences -> tab "Dimensions".  The size depends on the scale of the drawing.  I  saw a default of about .2 and changed it to 4 for a layout of a room  we were laying tile in.  One other note is that each time I pop on a dimension line, I change snap-to to endpoint then pick the points to dimension, then change snap-to to grid then set where the dimension line is placed.

man, you're right, i zoomed WAY in and i saw the text and the arrows. :) changed the settings, and now everything shows up. cool. thanks for the help! :)

and by the way - in an amazing coincidence, i'm using qcad for a room that we're planning to lay tile in, too! fancy that! hehe.

---

### Post by ridgeland on 2007-09-04
What I liked about using qcad for laying out the tile was the tile was 12 inches by 12 inches (US is sooo way behind the world with metric :( ).  I used a square hatch to show where each tile would lay.  That way I could reselect 0,0 to avoid 2 inches strips at the door or the whole length of one side of the room.  I used a quick OpenOffice Calc to help me determine points each time I wanted to try a new place for 0,0.
The hatch on my grid was a 0.24 I guess it depends on the scales selected for the grids.  With dimensions I confirmed the 12x12 and it worked great.

---

### Post by nanotube on 2007-09-04
> **ridgeland said:**
> What I liked about using qcad for laying out the tile was the tile was 12 inches by 12 inches (US is sooo way behind the world with metric :( ).  I used a square hatch to show where each tile would lay.  That way I could reselect 0,0 to avoid 2 inches strips at the door or the whole length of one side of the room.  I used a quick OpenOffice Calc to help me determine points each time I wanted to try a new place for 0,0.
The hatch on my grid was a 0.24 I guess it depends on the scales selected for the grids.  With dimensions I confirmed the 12x12 and it worked great.

That's a cool use for the hatch! :) I used parallel lines with 12unit distance to achieve a similar effect - because I knew that i wanted whole tile along both the long sides of the pool, that meant having a line of cut tile in the middle - so i couldn't just use a square grid for the whole thing. 

but yea, generally, i'm glad i decided to qcad this before jumping in - it really helped me plan things out, the patterns i want, what cuts i'll need to make, etc. 

thanks for your help. :)

out of curiosity... i don't suppose you have a picture of your completed tilework? :)

---

### Post by ridgeland on 2007-09-05
For a picture instead I put the qcad drawing on the web.
[http://david.dentlinger.net/qcad/index.html](http://david.dentlinger.net/qcad/index.html)
now has a link in the last paragraph "Sewing Room".  Right click and save to file.  If you just click on it you'll get a stream of numbers and letters.  From the 0,0 red cross you can see how I could shift the start around to pick how the hatch layed the tiles. 

p.s. Tomorrow I'm off on vacation for two weeks so I won't get to the forums much and not from my PC.

---

### Post by DebianFanatic on 2007-10-01
> **ridgeland said:**
> Gymsmoke

I also found it almost impossible to use QCad so I created a Tutorial as I cleared each hurdle.
The tutorial is here
[http://www.david.dentlinger.net/qcad/index.html](http://www.david.dentlinger.net/qcad/index.html)
I think it can get you started.
Please give me get some feedback though.  I want to improve it.

Solid! I learned more in 30 minutes following your tutorial than I have in a year of on-again-off-again trying with other resources. Thanks for publishing it!

I have trouble with the hatching, however.

I have the stop-signish circle drawn and print-previewable, as up to your step 15. But when I do step 16 as written, I get the error "Invalid hatch area. Please check that the entities chosen form one or more closed contours", and the selection indicators (red and blue) go away.

I'm using Debian (Sid) on a 2.6.21 kernel, QCad version 2.0.5.0 (Community Edition), August 22 2006.

---

### Post by ridgeland on 2007-10-02
I don't see a reason why the hatch doesn't work.  The error says the selection is not a closed area.  I can generate the error by selecting only 3 sides of a square and requesting hatching.

Possible errors I ruled out:
Layer error - drawing the hatching on a layer that is not visible.
Parts not joined corectly - looks fine
Incomplete selection - selecting most but not all the points of the assembly.
Debian vs Ubuntu - the problem file (qcad drawing) is a problem on both systems.

My only suggestions is to backtrack to earlier files like ExampleStep6.dxf and see if hatching works there on just the rectangle and just the trapezoid.  This might show one as the problem piece.

---

### Post by Old Jimma on 2007-10-27
David:

In Step 9 of your tutorial, I tried to turn of the dimension layer by selecting Layer 0.... nothing happened... the dimensional arrows and dimensions where still there.

Also, when I procede to Step 10, although I follow your instructions, nothing gets dragged or connected.

Your advice would be greatly appreciated!

Thanks,
Phil Smith
Duluth, GA

---

### Post by ridgeland on 2007-10-27
Think of the layers as layers of transparent paper that can be stacked up.  The "eye-ball" icon determines which layers can be seen.  To get the dimension layer to go away you click on the "eye-ball" icon for that layer and it vanishes.  Grey-ed out and it cannot be seen, black and it can be seen.

The active layer, the one selected (blue), is the one you are working on.  With the dimension layer turned off and the "0" layer the active one it should be possible to select and move parts.

---

