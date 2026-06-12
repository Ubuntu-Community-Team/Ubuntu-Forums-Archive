---
title: "One Inch Buttons In Gimp"
date: 2007-08-22
forum: Art &amp; Design
---

### Post by WarholsGhost on 2007-08-22
I Tried Googling this for days and have found nothing so i come here for answers.

When i used windows, i used photoshop cs2 to set up templates to make one inch buttons (For wearing) But now that i am using the GIMP in Linux, i can't seem to make things work. 

I have 2 PSD files and a ATN file that would help me create the templates, is there anyway i can set this up in the GIMP so it can be simple and quick. I would love to be able to translate the ATN file to script-fu or get it working with the GIMP

Who ever can help me get this working, i will mail you 10 ubuntu buttons. 
I can email you the files i am working with.

thanks,
Gregg

---

### Post by bakermiller on 2007-08-22
I would make a template in scribus,  import the individual images (vectors if possible) in the layout, and print....

---

### Post by WarholsGhost on 2007-08-23
i have no idea how to do that, do you know of any tutorials?

---

### Post by tobbilla on 2007-08-23
mail me that psd

---

### Post by WarholsGhost on 2007-08-25
pm me your email

---

### Post by WarholsGhost on 2007-08-27
i still need help

i'm talking about this kind of software:
[http://www.badgeaminit.com/sofandcomac.html](http://www.badgeaminit.com/sofandcomac.html)

and the original files i was working with in Photoshop came from here. i was using the 1inch design.

[http://buttonmakers.net/button_design_help.htm](http://buttonmakers.net/button_design_help.htm)


i need to get something like these files and the action file working in the GIMP

---

### Post by WarholsGhost on 2007-09-06
bump

---

### Post by bakermiller on 2007-09-07
if i understand, you are trying to automate popping images in a layout, using that .atn file. right?

---

### Post by WarholsGhost on 2007-09-08
i don't know what you mean by popping, but i'm trying to get them to automaticly place themselves in the page multiple times.

---

### Post by bakermiller on 2007-09-09
pardon my jive, i could have said importing...

Do you want to make pins or run a pin-mill?

i have made a printable letter size .pdf with the ubuntu logo using the template you posted. If you want i will mail you it, you will just need to print, cut and press your pins.

otherwise, If you want to learn how to Do-It-Yourself, Be more specific in your questions and in what you know and don't know so we dont end up saying stuff for no reason. Like i don't know if you can use gimp or not. You mentioned script-fu earlier, yet don't seem to know what to do with the template file. 

there are sooo many ways to do what you need to be done. How many different designs of pins are you planning on making that you need to automate the process?

have you familiarized yourself with scribus, inkscape and gimp?

this is ubuntu forum, it has to be like a tree that grows.
other people can learn from this discussion, so it's good to be precise and to communicate in a way that does not leave ambiguities. Making your pins is just a basic example of making a layout with imported images. It could be applied in various. situations, not just pins...

i will be happy to help if i can,i just help me understand what it is you want to do....a process to make pins, or just make pins?

---

### Post by WarholsGhost on 2007-09-09
ok i will try to be as descriptive as possible. 

So i have a button making machine and i want to be able to design a button and then have it automatically lay it self out on a 81/2x11 sheet of paper. 

I make these buttons for clubs on my campus so i need to be able to do it with very simple templates. I don't understand the gimp very well, but i'm learning it. I downloaded scribus, but have not used it much. 

I want to make this process very automatic, so i can design a pin, have it place itself on an 81/2X11 sheet and print it. The buttons need to be 1 inch in diamater. The templates found on the website above work in the gimp for the most part, i just need the automate the process of laying out the pin designs on the larger template with some kind of script. 

Thanks

---

### Post by bakermiller on 2007-09-09
i can't help you with the automatic part of the process, but i can try to explain what i would do in your situation.

There are three steps: 1)make pin graphics 2) make a layout in scribus 3) insert pin graphics in the scribus layout.

To make the pin graphics, open the .psd template in Gimp. It should import no problem, keeping all layers intact. The image is 1.313in X 1.313in at 300dpi. this is important. open or import your pin graphics on new layers and compose your pin graphics following the template guidelines.  once your pin is nice looking and well formated within the template, delete the original template layers and export as .tif or .jpg at 300dpi (which is the original template resolution). You can make many different designs...naming them all accordingly:)

iin scribus, make a new letter size page. most printers have a 1/4 margin all around, so you will be able to fit 8x10 pins on your page. place a new image frame on the page. resize it to 1.313in x 1.313in using the properties inspector. and repeat (copy + paste) it left and right to cover the page grid save the scribus document as a template. These are containers for the pin graphics that will contain the instance of the source .tif or .jpg 300dpi image.  this is the part where i guess automation using an .xml or some script to import all files within a directory into the image frames would be interesting, i'm sure there is a way to do it because you can run scripts within scribus
[there is some info here on using python]("http://docs.scribus.net/index.php?lang=en&page=scripter1"). there are probably existing scripts that will do this. look around. and tell me if you find anything. This is very interesting and i have to learn how to do it. because it's ridiculous to right-click or crtl-d 80 (10x8) individual images into the grid of image frames, but that's the only way i know how to personally...so If anyone else can help...:P.

Now you can export a print quality .pdf or print straight from scribus, and punch your pins.  

If you need more more precise help, ask...unless this helps you in no way because i'm in the same spot as you are in terms of automation....okchowbye

---

### Post by rsambuca on 2007-09-09
I know this may be a little late now, but there is a fairly easy way to do this all simply with the gimp.  

1.  Create your button design and scale it to the proper size.  In your example, this is a 1" diametre circle.

2.  Save a copy of this file in the folder /home/<yourusername>/.gimp-2.2/patterns

3.  Open up a new blank document that is the correct paper size

4.  Select "Dialogues -> Patterns" (or just press Control-P) to open the pattern selection window.

5.  Select the pattern you created, and fill the entire document with your button design.

6.  Print.

You may have to fiddle a little bit to figure out your margins and stuff, but I hope you can figure that out.  If not, post here and we can help you out.

---

### Post by rsambuca on 2007-09-09
Simple example pix. I created a simple design first, and then used it to "fill" an 8.5 x 11 size canvas with the design.

EDIT:  Do I get the 10 buttons?!

---

### Post by WarholsGhost on 2007-09-10
Yes if you both pm me your mail address i will mail you some buttons.

but my last question is how can i get gimp to have the text wrap around the edge of the circle.

---

### Post by WarholsGhost on 2007-09-10
so i tried to design the button and it's frustrating me because i can't even find how to change the font size. 

Every text box that comes up does not have an option to change the font size, what gives?

---

### Post by rsambuca on 2007-09-10
It's on the main gimp window.

---

### Post by rsambuca on 2007-09-10
> **WarholsGhost said:**
> Yes if you both pm me your mail address i will mail you some buttons.

but my last question is how can i get gimp to have the text wrap around the edge of the circle.

Don't worry about the buttons!  Just make sure you post some pictures here later so we can all admire your work.

With regards to the circular text, it can be done with gimp, but it is very difficult.  Frankly, working with text in gimp is one of its biggest downfalls.  To get circular text it can be done by first selecting the text, and the using the "dialogues -> Distorts -> Curve bend" feature, but it is painstaking at best.   For this, you are better of using something like inkscape, which I believe has this feature.

---

### Post by WarholsGhost on 2007-09-10
i found how to change the font size, but it doesn't show up right there for some reason.  i have to go to

file>dialogs>tool options. 

there doesn't seem to be a way to put it on the main bar. 

and any idea on how to type on a path?

---

### Post by WarholsGhost on 2007-09-10
i found a script that seems to do type on a path, but i don't know how to use script-fu at all, can someone walk be through making this script work?

[http://lists.xcf.berkeley.edu/lists/gimp-user/2002-December/005209.html](http://lists.xcf.berkeley.edu/lists/gimp-user/2002-December/005209.html)

---

### Post by WarholsGhost on 2007-09-10
thanks so much! they turned out great! i'm going to look more into text on a path but you helped me out A LOT


sure you don't want any buttons to show off/give to friends.

---

