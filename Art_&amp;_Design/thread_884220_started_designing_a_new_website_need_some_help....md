---
title: "started designing a new website need some help..."
date: 2008-08-08
forum: Art &amp; Design
---

### Post by hockey97 on 2008-08-08
Hi I am working on a website. I am trying to make a layout to make a frosty looking layout of the website. Do you have any tips or tricks I could use to create good looking snow and realistic ice.

I am using gimp for the artwork. Any ideas please feel free to tell.. I got designers block lol.

---

### Post by lyceum on 2008-08-08
There is a script-fu that will do it for you. But...I re-installed Ubuntu last month and have not re-installed my script fu so I cannot tell you which one. Check out this site:

[http://registry.gimp.org/](http://registry.gimp.org/)

[http://registry.gimp.org/taxonomy/term/20](http://registry.gimp.org/taxonomy/term/20)

---

### Post by hockey97 on 2008-08-08
What would that script-fu do exactly???? Would it create the frosty effect?? or ice effect? Or make a website layout??

I want to use gimp to make a website layout.

I seen many tutorials which would create a layout using layers but then they would slice it up with some type of script-fu.

I want to make all the art on gimp and then just save each layer as an image. I done so but the problem was after finishing the look I notice that each layer was the same size as the origonal so if there were button images it would be a button with a 800x600 space around it. 

The trouble I have mostly is making the art look good while making the correct sizes that I want.

---

### Post by lyceum on 2008-08-09
> **hockey97 said:**
> What would that script-fu do exactly???? Would it create the frosty effect?? or ice effect? Or make a website layout??

I want to use gimp to make a website layout.

I seen many tutorials which would create a layout using layers but then they would slice it up with some type of script-fu.

I want to make all the art on gimp and then just save each layer as an image. I done so but the problem was after finishing the look I notice that each layer was the same size as the origonal so if there were button images it would be a button with a 800x600 space around it.

The trouble I have mostly is making the art look good while making the correct sizes that I want.


Yes, yes and yes, well... no. There are effects that will make things look frosty (covered in snow) make it look like it is snowing (not hard to do yourself) or icy. You can make buttons in GIMP, covered in snow or just icy. You can make other images and do the same. Then, you add them to your web design. 

EX:

Web design - one image
buttons - another image (or group of images)
background image - another image
other images - another image (or group of images)

As you make the buttons, background, etc.. you add them as layers to your web design. You do this by pasting them, then on the layers panel right click and change it to a layer rather than anchoring it to a new layer that takes up the whole image. This way the layer will be the size of the new picture, not the whole image (hope I am saying that right). Now you can make changes and move things around easier. Save as an .xfc (GIMP) file to save the layers. If you want a jpg or png file, flatten the image and save as such, keeping your xfc file safe, in case you want to make more changes later. 

As far as what script-fu to use when, you will have to weed through them and take what you want or need. 

;)

-edit-
YOu may also want to check out Inkscape, I like creating images in it better. You can still export the images to png, any size you want, then mess with them in the GIMP.

---

### Post by V for Vincent on 2008-08-09
Google "gimp brushes". You'll find some nice frost flakes and such pretty quickly.

---

### Post by lyceum on 2008-08-09
> **V for Vincent said:**
> Google "gimp brushes". You'll find some nice frost flakes and such pretty quickly.

I think I remember something about this release of GIMP allowing users to use PhotoShop brushes in GIMP too.

---

### Post by Hyperkill on 2008-08-10
Slicing in GIMP is pretty easy.  I do it without any script-fu pretty easily.  Here's how...

The first step is to get out your Rectangle Select Tool.  Now make your first slice by selecting the area you want, such as your header.  Now go to Image > Guides > New Guide from Selection.  This will create guide marks around your selected area.  Continue repeating this process until your whole image is sliced up.

Now it's time to save the images.  Get out the Rectangle Select Tool and select inside of your first slice.  It should snap into place along the sides of your guides.  If not go to View and check "Snap to Guides".  Now go to Edit > Copy Visible.  Then go to Edit > Paste As > New Image.  You can then save your image as slice1.png or whatever suits you.

---

