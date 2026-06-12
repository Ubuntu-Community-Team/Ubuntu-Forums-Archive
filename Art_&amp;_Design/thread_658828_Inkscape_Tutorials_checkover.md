---
title: "Inkscape Tutorials checkover"
date: 2008-01-05
forum: Art &amp; Design
---

### Post by sloggerkhan on 2008-01-05
I'm in the process of making a set of inkscape tutorials and I'm just looking for feedback, typo corrections, etc.

Basically, I need to give some fellow college students some training in computer graphics for making signs and logos and such that'll use to make signs, news letters, and logos and such for clubs. 

I'll only be using foss so they can install it on their laptops. I plan to go inkscape > gimp > scribus in that order and have a couple tutorials and an overview for each, and then one project where elements from all three are put together.

In any case, I've gotten started and I was hoping to get some feedback and editing. (I'm making them into 300 dpi .pdfs, but for the forums I'm using 150 dpi .pngs)

_________________________________________________
Update: Now at 5 pages, in theory, all revised. Please download here:
[http://sloggerkhan.deviantart.com/art/BASIC-Inkscape-Part-1-74130021](http://sloggerkhan.deviantart.com/art/BASIC-Inkscape-Part-1-74130021)
~ about 4 megs in size, when complete I will make a .jpg based .pdf . 
In the meantime, if enough people request it, I will add one with lower res images.

---

### Post by Tyche on 2008-01-05
On the first page:

First, under "What Software" about halfway down, Synfig has a Linux version.  I know, I tried to play with it at one time.

Second, under "Boolean Combines", I would use parenthesis to help define the operations:
A. Union (Addition)
B. Difference (Subtraction)
C. Intersection (Exclusive And)
D. Exclusion (Exclusive Or)
E. Division (Separaation)

On the second page:

Point 4, you have CTL -+ OR. . .  This is a bit confusing to me.  Do you mean control and either minus or plus, or control plus minus and plus?

These are the only things that I can see, at 5:00 in the morning with no coffee.  Hee hee

BTW sloggerkhan, now that I've had some time to get some coffee in me and wake up, I'd like to thank you for what you are doing.  I would appreciate knowing when you get the complete tutorial done, as it looks like it might help me to understand Inkscape better.  Thanks again.

---

### Post by Samhain13 on 2008-01-05
Spotted...

in "What Software?":
*Consequently, all guides will **be** presented using Inkscape...*

in "Vector Graphics",
may I suggest a clearer differentiation between, say vector graphics and "bit maps" (instead of "regular computer graphics"). To my understanding, vectors are also regular computer graphics, they're just not bit maps.

...still reading. :)

[edit]

Wasn't able to see anything wrong it the second page. Cheers, and good luck with this project.

---

### Post by smartboyathome on 2008-01-05
I would suggest you use the Inkscape version from SVN if you are going to train them. It has quite a few  new useful features in it which are helpful.

---

### Post by Muscar on 2008-01-05
Great stuff

---

### Post by oomingmak on 2008-01-05
> **Samhain13 said:**
> may I suggest a clearer differentiation between, say vector graphics and "bit maps" (instead of "regular computer graphics"). 
I would suggest using "raster image" instead of "bitmap image". 

'Bitmap' refers to a specific type of raster image, so it's not the best term to use as a contrast to vector.

---

### Post by meho_r on 2008-01-05
The first image:

– under "Vector graphics" you have typo: "diference" > "difference"
– under "What software". Shouldn't it stand: "...a number of graphics specific vector **applications**" or "...software" (without 's')?
– same place: "...all guides will be presented using Inkscape..." (capital "i" in "inkscape")

The second image:

– maybe put capital first letters on modifier keys (Ctrl, Alt...)
– check text under point 3 and 4 ("...top and of each circle.even.")
– point 5. maybe "object's color to some more fruity..." (or something like that)
– point 6. "one for a stem, one for a leaf" > "one for a stem **and** one for a leaf"
– point 6. "...object order" > "...objects order" since you have now three objects
– under "Stroke and Fill": "...with object selected" > "...with an object selected"; check the last sentence: "...there at many more..."

Nice work :D Please post it when you finish it.

---

### Post by sloggerkhan on 2008-01-06
Thanks guys.
Since I will actually need to use these at some point, there will be updates. 
I've started the next page, but I was busy today so more updates later.
So when I'm finished, I'll post a final. (Multi page .pdf probably.)

---

### Post by sloggerkhan on 2008-01-06
Okay, I updated the first 2 pages, now there are 2 more sheets, the second half of the apple tutorial, and an aside on the star tool.

I kept the keys lower case because changing that seemed like it didn't matter that much and I'd already used the lower case keys in 3 different documents. 

I put raster in parenthesis rather then just delete 'regular graphics' as I'll be teaching people who won't be familiar with the difference between vector and raster and if I just put that it'd be meaningless to them.

Otherwise, I'd clarified and fixed as has been suggested. For that one section where I'd accidentally duplicated the same directions, I've fixed that also.

So, once again, looking for more feedback and editing. I should have another simple tutorial along the lines of the star one up pretty quick, maybe later tonight or tomorrow.

Thanks again, especially to typo/spelling/grammar error finders!

PS: I'd been using a late November autopackage version, but since they've posted .debs of the SVN on the Inkscape site, I'm trying those out now.
PSS: Manual kerning doesn't seem to be working for me... any ideas?  (alt - arrow keys do absolutely nothing in a text box. It records 'kern left', etc. in the undo menu, but it does absolutely nothing to the text.)

---

### Post by sloggerkhan on 2008-01-07
One more page: Simple Tiles.
As always, editing and feedback welcome.
I'm planning to do one more Inkscape tutorial before going on to the gimp, but it will be much more in depth and comprehensive than those so far.

---

### Post by meho_r on 2008-01-07
> **sloggerkhan said:**
> 
PSS: Manual kerning doesn't seem to be working for me... any ideas?  (alt - arrow keys do absolutely nothing in a text box. It records 'kern left', etc. in the undo menu, but it does absolutely nothing to the text.)

It depends of how you create text. If you just click and type, kerning works. But, if you drag a text frame, then it doesn't work.

---

### Post by Samhain13 on 2008-01-07
> **oomingmak said:**
> I would suggest using "raster image" instead of "bitmap image". 

'Bitmap' refers to a specific type of raster image, so it's not the best term to use as a contrast to vector.

Raster it is then. :)

[edit]
Here's from page 3:

from item 11, "Click on the straight **vertical** edge... Drag it until **it's** curved..."

from Gradients, "A simple gradient (is?) has two stops..."
suggestion: "A simple gradient is a transition between two colors and/or levels of transparency..A complex gradient is a transition between three or more colors and/or levels of transparency."...or something to that effect?

[edit2]
page 4:

suggestion on the heading's sub-text, "Creating floral and geometric elements in X easy steps."

---

### Post by sloggerkhan on 2008-01-07
> **meho_r said:**
> It depends of how you create text. If you just click and type, kerning works. But, if you drag a text frame, then it doesn't work.

Thanks!! I guess I misinterpreted the documentation.

---

### Post by CAD-MAN on 2008-01-07
Really cool tutorials Slogger. I'd like to ask a question though: On the 'Simple Star Florals' tutorial, how did you get the very straight edged yellow, orange, red and grey star (listed under variations)? I've been able to get very similar shapes, but they always have very curved edges.

Thanks.

---

### Post by sloggerkhan on 2008-01-07
> **CAD-MAN said:**
> Really cool tutorials Slogger. I'd like to ask a question though: On the 'Simple Star Florals' tutorial, how did you get the very straight edged yellow, orange, red and grey star (listed under variations)? I've been able to get very similar shapes, but they always have very curved edges.

Thanks.

Basically, use negative roundness values and zoom in on the center a lot while using a light stroke.

See attachment for examples.

---

### Post by Madpilot on 2008-01-07
Neat tutorials, saved for future reference!

---

### Post by CAD-MAN on 2008-01-08
Excellent, thanks Slogger.

---

### Post by durand on 2008-01-08
> **sloggerkhan said:**
> One more page: Simple Tiles.
As always, editing and feedback welcome.
I'm planning to do one more Inkscape tutorial before going on to the gimp, but it will be much more in depth and comprehensive than those so far.

Paragraph 10 says "Use use the tiled clones tool"

PS: Really nice set of tutorials! Great work!

---

### Post by sloggerkhan on 2008-01-08
I set up a deviant art so I could upload and download stuff more easily.
I put all the ones so far in a .pdf [here]("http://sloggerkhan.deviantart.com/art/BASIC-Inkscape-Part-1-74130021").
Direct link here:
[http://www.deviantart.com/download/74130021/BASIC_Inkscape_Part_1_by_SloggerKhan.zip](http://www.deviantart.com/download/74130021/BASIC_Inkscape_Part_1_by_SloggerKhan.zip)

I can make a .pdf with the medium sized images instead of print sized if anyone request it, as the the 5 page .pdf with images is currently ~4 megs.

Once I'm done with the whole project, I'll see about using .jpg or something to get the whole business down to a more manageable size.

Lastly, once again, thanks for the edits, I think I got the posted errors all fixed or modified somehow.

---

### Post by durand on 2008-01-08
Once you're done, you should tell inkscape.org about them.

---

### Post by sloggerkhan on 2008-02-25
I have a little bit more to add, but probably won' get to it for a while.
I'm also thinking of making an inkscape -> website tutorial:
[http://ubuntuforums.org/showthread.php?p=4399771#post4399771](http://ubuntuforums.org/showthread.php?p=4399771#post4399771)

---

