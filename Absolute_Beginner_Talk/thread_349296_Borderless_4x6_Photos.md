---
title: "Borderless 4x6 Photos"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by hannaman on 2007-01-30
OK, after weeks of trying, I am now able to print 4x6 photos to my Epson Picturemate Deluxe from f-spot, Gimp, gThumb, etc.  The issue I have now is that the prints are not borderless in any of them.  The Gimp comes the closest to borderless, but still leaves a small white border on three sides (same with f-stop), but if I print directly from the card inserted into the printer, I get borderless.
I tried changing to different paper sizes, but the paper is definitely 4x6 and the borderless button in Gimp doesn't help.  Does any know of some settings in gutenprint that might help?

Thanks

---

### Post by john8791 on 2007-07-30
Sorry for answering your question with a question, but how did you get it to print?  I've only tried printing through Picasa but I only get about a 1" strip to print down the side.  I have seen another post with a similar problem but no one has seemed to figure it out.

---

### Post by rjs987 on 2008-04-11
I tried many different settings but I also could not find the right setting to get rid of all the border around my photo prints. I was able to print borderless photos by saving the photo to a flash memory card and then using my printer's internal photo controls to print but doing more than just a few like that is cumbersome at best and not what I felt I should have to do for every photo I wanted to print. I finally found some clues after reading many many forum threads and figured out the key is in the term FULL BLEED.

**Printing borderless (full bleed) 4x6 photos in Kubuntu**
I use digiKam and played with the settings to finally figure it out. Many of the solutions I found on Linux forums stated that my photo has to be edited to fit to a 4x6 aspect ratio. Digital cameras usually do not take photos in 4x6 aspect ratio and these solutions would have me cut down or distort the photo to get it to the aspect ratio that fit within a 4x6 size. I found that YOU DO NOT HAVE TO CUT DOWN NOR DISTORT THE PICTURE to get it to fit within the 4x6 size! That is, unless you really want to. The forums also almost unanimously stated that there is no auto crop feature in any Linux program like is found with Windows. NOT TRUE! digiKam does Windows one better with it's auto crop feature and lets YOU determine what part of the photo gets cropped. The following is how I was able to do borderless photo prints.

Step 1- fixing the photo size (OPTIONAL):
This step is only needed if I really want to save the photo in a different aspect ratio/size. I also want to do this step if I want to zoom in on a small portion of my photo and print only that.

I open digiKam and locate the photo I want to print. Then I click on the Edit tool bar icon (or use the Image>Edit...) to edit the photo. digiKam Image Editor has an Aspect Ratio Crop function (Transform>Aspect Ratio Crop...) that makes this part fairly easy. digiKam does not display photo sizes in inches or mm, only in pixels. Therefor I used a calculator to play with the pixel sizes that most closely matched the photo size and crop I wanted. In the Aspect Ratio Crop panel I set the Aspect ratio selection to None. Then in the photo sample I drew a crop box to start, and then adjusted the size to be close to what I wanted to include in the photo by grabbing the corner handles to adjust. Then I used the Width and Height counters on the right to fine tune the pixels to match the true 4x6 aspect ratio. The X and Y settings only adjust where the crop box is located on the page, not the size.

[COLOR="Red"]**NOTE: **I know there is an Aspect ratio selection equivalent to 4x6 (2:3), BUT the best I could do using that setting still leaves a very thin white line down the long edge of the photo. It is not a true 2:3 ratio but closer to 1.999:3![/COLOR]

Then I did a Save As to save the adjusted photo with a different filename, just in case I need to start over with the original.

Step 2- printing the photo:
My adjusted photo can be printed from the digiKam Image Editor or any photo (adjusted or not) can be printed using the digiKam Print Wizard (Image>Print Wizard...). I like using the Print Wizard. I start the Print Wizard and at the second panel I set the paper size to 10x15cm, set the Image Captions to Do not print..., and set the Output Settings to Output to printer (most of these are default settings).

At the third panel I make sure the photo size to print is still set to 10 x 15cm and that the photo is the right orientation in the sample.

One of the really nice details about the digiKam Print Wizard is the fourth panel. This is where digiKam blows away Windows photo print features (IMHO). There is an auto crop feature in this panel. If the photo is already adjusted to a 4x6 aspect/size the auto crop outline will only outline the entire photo. If the photo is not adjusted to this aspect/size I can move the auto crop outline box to include the part of the photo I want to print (most Windows programs I've used decide this for you!). I can also rotate the photo within the outline box.

I move on to the fifth panel and then I click Next again to get the print properties panel. I select my printer and then click on the Properties button to change or verify the printer settings. I really only need to go to the Margins and Driver Settings tabs and change or verify the settings as follows:

Margins tab...
	Select Use custom margins.
	Set all margins to 0 (zero).

Driver Settings tab...
Under General...
	I set the Media Size to Photo or 4x6 inch index card.
	I set the Media Source to Photo Tray.
Under Others...
	I set the Printout Mode to Photo (on photo paper).
	I leave the Double Sided Printing set to Off.
Under Printout Mode...
	I set the Resolution, Quality, Ink Type, Media Type to 1200 dpi, Photo, FULL BLEED, Black + Color Cartr., Photo Paper.

I then click on OK, and click on Print and out of the printer comes a very nicely done borderless photo.

I am currently running Kubuntu 7.10 with the default KDE and HPLIP 2.8.4. My printer is a HP Photosmart c6280 set up using the HP PhotoSmart C6100 Foomatic/hpijs, hpijs 2.8.4 driver.

---

### Post by taxus on 2008-04-23
Thanks for the tip. I am now able as well to print borderless 4x6 photos, under Ubuntu Gutsy using F-Spot. (I've been printing directly from my Photosmart's controls for the past 18 months!)

F-Spot does not offer me to specify printout options. So instead I duplicated (Copy in the toolbar) my printer in System > Administration > Printing, and changed the printing options as specified by rjs987 (media size, media source, printout mode etc).

I cropped a photo to have a 4/6 ratio, and printed from F-Spot using these options in the Paper tab:

Paper size: Photo or 4x6 inch index card
Page orientation: Portrait
Paper tray: Photo Tray

It worked. 

Printing is a lot slower than directly from the printer controls, though, but I can live with that.

---

### Post by rjs987 on 2008-04-25
Good idea to make one copy of your printer for just photo printing with the right settings and another copy for everything else. I haven't done that yet.

I did forget to include one very important item. When in the printer properties dialog when setting the Driver Settings, it is very important to also go to the Margins tab and set all margins to zero. I edited my post above to include that step. FullBleed printing only goes as far as the margins will allow. Zero margins PLUS fullbleed makes the photo extend all the way to the edge of the paper.

Sorry about that omission, but it's fixed now.

---

