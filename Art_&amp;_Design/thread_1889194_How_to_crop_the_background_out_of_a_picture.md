---
title: "How to crop the background out of a picture"
date: 2011-11-30
forum: Art &amp; Design
---

### Post by littleslayer15 on 2011-11-30
I want to make a picture with no background at all I tried to use GIMP's lasso tool to cut out the background for the picture and that seemed to work fine but when I saved it it put a white background back on it does anyone know how to fix this

by the way I am a huge Linux n00b so please try to make an explanation as easy as possible.

---

### Post by DMKryl on 2011-12-01
i think you saved the file in jpg, something like namefile.jpg right?, if that's the case the only thing you should do if you saved the modified file in gimp .xfc, is open it again (or modify the pic again) and export it to png, in file>export  filename.png

---

### Post by littleslayer15 on 2011-12-01
I actually did save it as a png file to start out with and the png made it have the white background.

---

### Post by DMKryl on 2011-12-01
maybe is the options in the export, this are mine, tell me if you have anything different
[http://dl.dropbox.com/u/23355517/Screenshot%20at%202011-12-01%2001%3A06%3A21.png](http://dl.dropbox.com/u/23355517/Screenshot%20at%202011-12-01%2001%3A06%3A21.png)

---

### Post by littleslayer15 on 2011-12-01
where do I find the export options sorry I am really a noob

---

### Post by ofnuts on 2011-12-01
> **littleslayer15 said:**
> I want to make a picture with no background at all I tried to use GIMP's lasso tool to cut out the background for the picture and that seemed to work fine but when I saved it it put a white background back on it does anyone know how to fix this

by the way I am a huge Linux n00b so please try to make an explanation as easy as possible.
The right technique for this depends a lot on the type of picture. To extract a "live " subject from a random background, the most efficient technique is to use a "layer mask" to selectively erase the background. But ittakes time and is a lot easier with a graphics tablet. To erase a uniform background (logos, text...), the best method is "Colors/Color to alpha".

In both cases, make sure your layer support transparency (not the case if loaded from a JPG), by adding that channel if needed (Layer/Transparency/Add alpha channel). Save as XCF at all times, and export to other formats when needed using "Save as". If you want to keep the transparency, use formats that support it (typically, PNG).

---

### Post by littleslayer15 on 2011-12-02
Well how hard is it to do since I am not very good at photo editing either is there a better program for this?

---

### Post by ofnuts on 2011-12-04
> **littleslayer15 said:**
> Well how hard is it to do since I am not very good at photo editing either is there a better program for this?The most automatic tool in Gimp is the Foreground extraction tool but I have never seen an automated way that works well in all cases, and without seeing your image or even just knowing what the image is I can't recommend a specific method.

---

### Post by sindorei9009 on 2011-12-04
Did you turn on invisibility in the layer menu?

---

### Post by dofdiamond on 2011-12-07
Thanks for Sharing useful reply here ! and i want to change only some of background in my image have 2-3 background i want to change only 1BG in .jpg Possible? How? No Replacement change in same file.

---

### Post by littleslayer15 on 2011-12-10
> **sindorei9009 said:**
> Did you turn on invisibility in the layer menu?

is that its exact name becuase I don't see that in the layers menu

---

### Post by littleslayer15 on 2011-12-10
> **ofnuts said:**
> The right technique for this depends a lot on the type of picture. To extract a "live " subject from a random background, the most efficient technique is to use a "layer mask" to selectively erase the background. But ittakes time and is a lot easier with a graphics tablet. To erase a uniform background (logos, text...), the best method is "Colors/Color to alpha".

In both cases, make sure your layer support transparency (not the case if loaded from a JPG), by adding that channel if needed (Layer/Transparency/Add alpha channel). Save as XCF at all times, and export to other formats when needed using "Save as". If you want to keep the transparency, use formats that support it (typically, PNG).

Well I need to do this for more than one picture so I can't really show you all the ones that I need to take the background out of.

---

### Post by ofnuts on 2011-12-11
> **littleslayer15 said:**
> Well I need to do this for more than one picture so I can't really show you all the ones that I need to take the background out of.Show one or two...

---

### Post by prokoudine on 2011-12-13
> **littleslayer15 said:**
> is that its exact name becuase I don't see that in the layers menu

He means the eye icon

---

### Post by ngrieb on 2011-12-14
The easiest way to turn any solid colored background transparent in GIMP is using the color to alpha tool. There is also an extremely useful tool called phatch (photo batch processor) that can do a number of nifty things on a batch of photos.

---

### Post by Neo Phoenix on 2011-12-21
if the background is one colour you can select the tool that has a hand in front of three colour cubes(sorry i dont know the right name) and then remove the background.

What i do is i create a new workspace(ctrl + n)

and then select transperancy

and then paste the current image

use the tool i mentioned above or the lasso or the selection tool and i press delete, and there you go no more background.

To maintain it as a no background image i save it as a png and deselect the "save background" checkbox.

the issue with saving as .xcf is that you cant use it with photoshop(as far as i know)

the bad thing about .png is that the layers are merged. so if you have a layer that needs continuous updation then its better to go with .xcf

Hope i didnt confuse you even more! :P

---

### Post by prokoudine on 2011-12-21
> **Neo Phoenix said:**
> if the background is one colour you can select the tool that has a hand in front of three colour cubes(sorry i dont know the right name) and then remove the background.

What i do is i create a new workspace(ctrl + n)

and then select transperancy

and then paste the current image
Instead of just adding an alpha channel to the only layer or creating a new transparent layer and placing it below the original one? Hmmmmmmmmmmmm :)

---

### Post by Neo Phoenix on 2011-12-21
The transparent layer at the bottom should work though, funny how you miss these things lol

you know what they say, old habits.... :P

---

### Post by littleslayer15 on 2012-01-02
> **Neo Phoenix said:**
> if the background is one colour you can select the tool that has a hand in front of three colour cubes(sorry i dont know the right name) and then remove the background.

What i do is i create a new workspace(ctrl + n)

and then select transperancy

and then paste the current image

use the tool i mentioned above or the lasso or the selection tool and i press delete, and there you go no more background.

To maintain it as a no background image i save it as a png and deselect the "save background" checkbox.

the issue with saving as .xcf is that you cant use it with photoshop(as far as i know)

the bad thing about .png is that the layers are merged. so if you have a layer that needs continuous updation then its better to go with .xcf

Hope i didnt confuse you even more! :P
first of all I will say I am really sorry that it took me so long to reply. I used the hand in front of three colour cubes but I don't know how to remove the background I tried right clicking and the selecting cut but that didn't work so could you tell me how to remove the background after that? I know I am probably frustrating some people but I want to thank you all for you help and been so understanding of my Ubuntu ignorance.

---

### Post by ofnuts on 2012-01-02
> **littleslayer15 said:**
> first of all I will say I am really sorry that it took me so long to reply. I used the hand in front of three colour cubes but I don't know how to remove the background I tried right clicking and the selecting cut but that didn't work so could you tell me how to remove the background after that? I know I am probably frustrating some people but I want to thank you all for you help and been so understanding of my Ubuntu ignorance.

If your image is some logo/text on a uniform background:

- Make sure your layer can be transparent: "Layers/Tansparency/Add alpha channel" (if it is disabled it means it is already there, so it's OK).
- Start Magic Wand ('"U" shortcut)
- Click on the background, this should make a selection around your subject (slighly outside the subject). If you see unselected areas (likely due to JPEG compression artifacts) you can increase the threshold a little bit.
- "Select/Grow" and grow the selection two pixels (selection should now also include the borders of the subject)
- "Colors/Color to alpha" and use the color picker on the background

Save as XCF, and, if you need it on some web page, as PNG

---

### Post by littleslayer15 on 2012-01-02
> **ofnuts said:**
> If your image is some logo/text on a uniform background:

- Make sure your layer can be transparent: "Layers/Tansparency/Add alpha channel" (if it is disabled it means it is already there, so it's OK).
- Start Magic Wand ('"U" shortcut)
- Click on the background, this should make a selection around your subject (slighly outside the subject). If you see unselected areas (likely due to JPEG compression artifacts) you can increase the threshold a little bit.
- "Select/Grow" and grow the selection two pixels (selection should now also include the borders of the subject)
- "Colors/Color to alpha" and use the color picker on the background

Save as XCF, and, if you need it on some web page, as PNG

sorry that didn't work for me but I am not sure what you mean when you say
 "Select/Grow" and grow the selection two pixels (selection should now also include the borders of the subject)

I tried to do what I thought you meant but it probably wasn't right.

---

### Post by ofnuts on 2012-01-02
> **littleslayer15 said:**
> sorry that didn't work for me but I am not sure what you mean when you say
 "Select/Grow" and grow the selection two pixels (selection should now also include the borders of the subject)

I tried to do what I thought you meant but it probably wasn't right.
See [http://gimpforums.com/thread-proper-subject-extraction-and-background-painting](http://gimpforums.com/thread-proper-subject-extraction-and-background-painting) especially post #3

---

### Post by littleslayer15 on 2012-01-03
> **ofnuts said:**
> See [http://gimpforums.com/thread-proper-subject-extraction-and-background-painting](http://gimpforums.com/thread-proper-subject-extraction-and-background-painting) especially post #3

Yeah thank you so much that did it is there a thanks feature or button on this website that I could use because you really deserve it?

---

