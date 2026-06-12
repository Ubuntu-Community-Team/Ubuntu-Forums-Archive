---
title: "Take a scan of something and color it only black and white"
date: 2011-11-12
forum: Art &amp; Design
---

### Post by sdowney717 on 2011-11-12
For example here are 2 scans, one reversed.
The white paint came off the wheel, so I was thinking scan it and recolor it and perhaps could print it and glue it on.

But of course I have no idea how to recolor. I gimped it and it looks like you would have to painstakingly go thru this.

Is there a way to tell gimp or some other program to color threshold a range of colors to white or black only?

---

### Post by ofnuts on 2011-11-12
> **sdowney717 said:**
> For example here are 2 scans, one reversed.
The white paint came off the wheel, so I was thinking scan it and recolor it and perhaps could print it and glue it on.

But of course I have no idea how to recolor. I gimped it and it looks like you would have to painstakingly go thru this.

Is there a way to tell gimp or some other program to color threshold a range of colors to white or black only?That won't work because there are grey areas in your background that are darker than your scale marks. Furthermore, the border of the scale and letters contain grey pixels to make smooth lines (anti-aliasing). Going to two colors will make them disappear and these borders will have pixel-sized steps (and at the current size, you haven't got many pixels on the tick marks). Use the Threshold tool for this and convince yourself.

All is not lost, but:

[LIST=1]
[*]take a very clean shot of the dial:
[LIST]
[*]from far away with zoom (reduces perspective distortion)
[*]on a background that contrasts with the dial (dark if white dial and vice versa)
[*]have the dial as big as possible (almost edge to edge)
[/LIST]
[*]once in Gimp, play with contrast/brightness, this can be enough for most of the dial. But don't overdo it. The steps I warned you about above should be a lot smaller if the photo is big enough.
[*]repaint the rest by hand
[/LIST]
For a perfect result, I would do it completely differently, namely, redraw the whole thing from scratch using "paths". Letters are easy once you have the right font, and the tick marks can be generated in a spreadsheet program, so it's not so labor intensive.

---

### Post by sdowney717 on 2011-11-13
I rescanned in line art with another dial where the white has not faded. However the image is too small compared to the original item????

original dial is 3 and 1/8 inch
What prints out in GIMP is 2 13/16 inch.

why is the size not right when I try to print this?

So then I opened up the transform scale to enlarge, it appears to enlarge, but did not print any larger.
I saved the improved version in a tz file. So you can open and see it looks much better now.

> namely, redraw the whole thing from scratch using "paths".?
Please elaborate a little

---

### Post by sdowney717 on 2011-11-13
ok, why is the printer shrinking the image??

paper is 8.5 by 11 and the printer wants to scale it down?

---

### Post by ofnuts on 2011-11-13
> **sdowney717 said:**
> ok, why is the printer shrinking the image??

paper is 8.5 by 11 and the printer wants to scale it down?See Image/Image properties. Your image is 8.533 × 11.772 inches so it won't fit on the page. Actually even at 8.5x11 it wouldn't fit because your printer won't likely be able to do border to border printing vertically so the printable area on the page is more like 8.5*10.5. On the other hand, the really useful part of your page is 3.2 inches in diameter so you can crop your image so that it fits and won't be resized  (this will lead to smaller files, too...).

For paths, see a pretty good tutorial: [http://limn.0fees.net/2008/06/15/gimp-path-tool-aka-pentool-tutorial/](http://limn.0fees.net/2008/06/15/gimp-path-tool-aka-pentool-tutorial/)

The idea is to define a path that creates a selection that is bucked-filled to generate the tick marks. This is often a much cleaner way to reconstruct a damaged geometric drawing (I've used it on old logos). It's less complicated than it seems once you figure out  that you can obtain most tick marks by duplication and rotation. Another solution is to generate them mathematically (a path is just a set of points). 

However, you seem to have obtained a pretty good image of the dial, so there should be no need for this.

---

### Post by SeijiSensei on 2011-11-13
It can be a bit painstaking, but you can also use the select by color tool and pick individual pixels.  You'd need to zoom the image probably to at least 4x or 8x.  If the zoom is high enough, you can click on a pixel you want to change, then use Select by Color.  You can then use the fill with foreground or background color option to switch the selected pixels to color you want.  If you add an alpha channel to the image, you can simply "Clear" the selected pixels and make them transparent.

---

### Post by sdowney717 on 2011-11-13
not easy for me to figure out cropping although I understand the idea.
Anyone want to tell me how to crop this thing?

[http://docs.gimp.org/en/gimp-tutorial-quickie-crop.html](http://docs.gimp.org/en/gimp-tutorial-quickie-crop.html)
following this I somehow managed to crop. But I dont see this dialog box with aspect ratio.

Well, I just printed the cropped image and it still comes out too small. it prints the same thing as before.
So what should i do?

here is a screen shot showing the cropped image

OK, I think I got it, yes that worked doing the crop. But I did not see any dialog aspect ratio box.

---

### Post by sdowney717 on 2011-11-13
hey thanks, the crop size made it print the exact dimensions.

Now I tried printing with my HP laser jet, but my black is not really solid black. It looks good but could be better. I tried the enhanced settings etc... which made a small improvement.

Could a copy machine take my print out and enhance to full solid black?

Or how could I print this and get a real good quality black AND could it even be printed on something other than paper?
This goes in a tachometer which gets sunlight falling on the tach.
I was planning on cutting out the paper image and gluing it onto the face plate.

---

### Post by robert shearer on 2011-11-13
tintii might be worth a try....

[http://www.indii.org/software/tintii](http://www.indii.org/software/tintii)

There is a linux version.

and another ppa here
[https://launchpad.net/%7Edhor/+archive/myway/+index?batch=75&memo=75&start=75](https://launchpad.net/%7Edhor/+archive/myway/+index?batch=75&memo=75&start=75)

---

### Post by ofnuts on 2011-11-13
> **sdowney717 said:**
> hey thanks, the crop size made it print the exact dimensions.

Now I tried printing with my HP laser jet, but my black is not really solid black. It looks good but could be better. I tried the enhanced settings etc... which made a small improvement.

Could a copy machine take my print out and enhance to full solid black?

Or how could I print this and get a real good quality black AND could it even be printed on something other than paper?
This goes in a tachometer which gets sunlight falling on the tach.
I was planning on cutting out the paper image and gluing it onto the face plate.
The best thing (contrast- & longevity-wise) would be real photo paper. Try your usual photo print shop. But you may need a couple of calibration trials, I don't know how well they stick to dimensions/definition. Or figure out the rectangle which is 6"x4" in your image and crop to that around the dial. They usually scale, but don't change the aspect ratio.

---

### Post by sdowney717 on 2011-11-17
I am almost there with this.

I put the image into a 4 by 6 inch format to print out at the store.
The store machine makes the image about 1/8 inch across too big. I can live with that but nice to be exact.

So how would I scale it down 1/8 inch in diameter?

The image prints perfect size on my printer.
Would I manipulate the border size of the 4 by 6 framework ?

OR

is the image going to have to shrink and how would you do that?

---

### Post by sdowney717 on 2011-11-17
I scaled the image down 1/16 inch across and 1/8 inch across and will take these in and see what it does.

I hope their machine does not auto scale the image bigger to fit their paper

---

### Post by desktorp on 2011-11-17
I don't mean to cause eye-rolling, but as a paper nerd, I advise against using photo paper for this, if you have sunlight hitting it.  You may want to look at something that does not have such a high gloss.  A satin / semigloss photo paper would be the glossiest thing I would use for something that needs to be readable in strong sunlight.. ideally you might even want something more of a matte finish. The nicest way it will turn out will be on a vinyl (weather/UV resistant) decal, but obviously that'd probably cost a couple/few bucks (more).

Sorry for being a paper nerd, but I have a sordid history of misusing regular ol' photo paper where I should have been using vinyl or at least better paper.
Cool project, either way.:guitar:

---

### Post by sdowney717 on 2011-11-17
A vinyl print would be nice, where do you go for that?
Would that be self sticky?

I do have a spray can of automotive clear coat. I could overcoat the paper, think that would hold up? 

I was told by the photo paper people to use matte versus gloss as it holds up better to sunlight.

This is my final working copy an unshrunk version.
I scanned this one at 1200 by 1200

Sun Electric tachometer face plate

---

### Post by ofnuts on 2011-11-17
> **sdowney717 said:**
> A vinyl print would be nice, where do you go for that?
Would that be self sticky?

I do have a spray can of automotive clear coat. I could overcoat the paper, think that would hold up? 

I was told by the photo paper people to use matte versus gloss as it holds up better to sunlight.

This is my final working copy an unshrunk version.
I scanned this one at 1200 by 1200

Sun Electric tachometer face plate


Glad you got it working. But it got me thinking so I now have an OpenOffice spreadsheet to generate dials, and a Gimp python script to import CSV as paths, so I could generate: 

[IMG]http://i.imgur.com/SXVMS.png[/IMG]

---

### Post by desktorp on 2011-11-17
ofnuts, that is so kewl.  I need to learn me some of that.

I have mixed luck with clear coats.. but I think it's just me messing it up sometimes.  Generally it sure seems like clear coat is always recommended when you're doing something at all "crafty" .. ink is like paint, right?  may as well spray it with some clear coat.  :D

Is that scan the final product or am I misunderstanding?  Looks good if it is.

edit: I was trying to find a particular site but I can't remember the name.
Onlinelabels.com looks nice though.  I ordered from them once with no trouble.
[http://www.onlinelabels.com/material_weatherproof_matte_inkjet_labels.htm](http://www.onlinelabels.com/material_weatherproof_matte_inkjet_labels.htm)

---

### Post by sdowney717 on 2011-11-17
yeah I think so. I dont see how I can improve it much. Maybe someone else. I notice that scans at high zoom show a lot of pixelation dot squares not smooth curves. Is this true of all images?

This little project started when the tachs stopped working. the tach meter connection inside the magnet frame where the clock spring grounds got high resistance, so the needle could not respond to the signals. So I soldered a small wire to the spring attachment back to the the internal circuit board and it works.

The face plate however, after 40 years, the white painted lettering oxidized and my hand brushed it off. So had to do something.

The needle I repainted with red orange flourescent paint.

The tach face you made looks good, it would just need numbers and some lettering.

---

### Post by desktorp on 2011-11-17
Yeah, my printer buddy always rages to me about using vector rather than raster for printing projects and he's right most of the time; clearly, you  just get a much cleaner print with a well-made vector design.

If you want to go super overboard, get some textured/patterned vinyl that appeals to you and have the dial (and numbers, etc) printed up on CLEAR vinyl.  Pro.

---

### Post by sdowney717 on 2011-11-17
here are the real compresed images. I noticed when I downloaded the picture I posted, it was changed. 
So if anyone ever wanted them, they can have these originals.
There are 3, 2 are scaled smaller to see if the store can print a perfect size.

---

### Post by ofnuts on 2011-11-17
> **sdowney717 said:**
> 
The tach face you made looks good, it would just need numbers and some lettering.That one isn't calibrated like yours (4.5°/unit instead of 4.2) but you get the idea. The whole thing is available there: [http://gimp-path-tools.sourceforge.net/](http://gimp-path-tools.sourceforge.net/) (see path-csv) and the OO spreadsheet for dials is in the samples section.

---

### Post by sdowney717 on 2011-11-19
some of the repair pictures.
I clear coated both sides with Duplicolor clear and that worked great
Used a red hot small nail to burn an exact screw hole and lined up the 3000 mark at the top and the 2 screw to get it perfectly centered.
Glued it on with some black silicone.

The photo machine, I had to shrink it. I found you cant just shrink the image and print on a photo machine because it will enlarge the entire image back to 4 by 6. So you have to shrink it and then copy paste the image into a new blank 4 by 6 image.

This tar file is a perfect fit for a Sun electric tach, when printed on a wal-mart photo machine.

Pic showing the meters, the brass housing and glass and the new faces
 [IMG]https://lh4.googleusercontent.com/-MXpb6H8dFEg/Tsg5NDDH3wI/AAAAAAAAAl8/8VOiUiDORmw/s640/image%252520%25252819%252529.jpg[/IMG]

showing the backside of the plate. the red mark is the perfect center of the 3000 rpm mark to align the photo.
[IMG]https://lh3.googleusercontent.com/-AMmVRg_64SM/Tsg5NK0GhxI/AAAAAAAAAl4/DgSXXdgVlfU/s800/1119111653a.jpg[/IMG]

FYI, to remove the stainless bezel rim, I ground off the crimp at an angle using the table saw and a metal cutting blade. Then carefully separated the parts. the inner metal pinch ring that held the glass was wasted away, (the only steel [part on it). so I glued the rubber seal ring to the satinless bezel and then glued the glass to the bezel using SealAll adhesive.

There is still a tiny lip to center the bezel back to the housing. And I will use a light sticky gummy glue (Henry 430) to join these pieces.

---

### Post by sdowney717 on 2011-11-21
picture of finished tachs. Phone pictures are not great but you can get the idea.
[IMG]https://lh4.googleusercontent.com/-NXCia_n_5_4/TspbKeuYKaI/AAAAAAAAAmc/k-1JoedHu2U/s640/image%252520%25252820%252529.jpg[/IMG]

some items I used to do this. 
Glued new face to old with silicone gasket maker. The clearcoat on both sides of the paper sealed it, and made it easy to wipe off the silicone sealer if a small amount gets on the face.
And that silicone gasket maker is easy to remove the photo if years later it needs redoing. 
I found I could not easily cut with a razor. So scissors used after gluing paper to face and heated up the screwdriver probe tip red hot to burn holes for screws and burn out the central space. Black marker then ran around edges to color it black. Made the circular template to paint the central black dot on the face with black spray paint. The edges of the face look real good and you cant see them anyway once it is together.

[IMG]https://lh4.googleusercontent.com/-Ed6ZRnbai_A/TspbKQ90uTI/AAAAAAAAAmY/yqR6XX7oOic/s320/image_2%252520%2525282%252529.jpg[/IMG]

detail of where SS bezel ring meets brass housing. 
Simply ground off the pinch and left a small lip useful to align ring back to housing.
Then glued on with Henry 430 adhesive
[IMG]https://lh6.googleusercontent.com/-N-pJkKxZdWs/TspbKjwN5hI/AAAAAAAAAmo/_VZtIRIVaXE/s800/1121110842b.jpg[/IMG]

---

