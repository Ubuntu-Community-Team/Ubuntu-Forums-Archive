---
title: "GIMP greated GIF files looks ugly..."
date: 2007-07-29
forum: Art &amp; Design
---

### Post by spottraining on 2007-07-29
Hi 

I have one problem. All my GIF pictures, what I make with GIMP looks very ugly. The same picture in other formats looks OK.

Here is one example :
[img]http://failid.com//files/1/logo.gif[/img]

How you can see - the logo and text - both are like "furry"

What I am making wrong? The same thing with all GIF images - no matter - transparent or not.

Please don't give here answers that use other file format like PNG. 99% I am using other formats, but I want to find solution to this problem.

I have search in Google and look to many sites, but maybe my keywords are wrong (gimp gif ugly) and so I find nothing.
Gimptalk forum is also down...

EDIT: GIPM version - from Ubuntu Feisty

---

### Post by zeronet on 2007-07-29
GIFs pictures only supports one alpha chanel, so you have one level of transparency (it isn´t a Gimp problem, it happens on all graphics programs), however you can save your images on PNG format, it´s better than GIF and supports lots of levels of transparency.

---

### Post by spottraining on 2007-07-29
And how I can then make some nice GIF pictures?

Mostly I am using PNG, but in some cases I want to make animated banners also. Right now its this impossible, while they look ugly...

---

### Post by PhinnFort on 2007-07-29
Animated banners are evil. But if you do need them, try to use mng or something similar.

-PhinnFort

---

### Post by graigsmith on 2007-07-30
gif files do not support true color images.  gif files only have indexed color, 256 colors.  so, anytime there are lots of gradients.  or a multitude of colors. it has to be reduced in color to be stored in the gif format.   And when you take thousands of colors out of an image to turn it into a gif file, it's very likely going to look ugly.  there isn't much you can do... Either don't use gif files.  or think of a way to reduce the number of colors ie,remove gradients.   OR put up with the ugliness that is gif files.

---

### Post by graigsmith on 2007-07-30
the image you posted diddn't look like it should have problems by being limited by a 256 color pallete.  did you convert the image to indexed color before you saved it?  if not try converting it to indexed mode, then saving to gif.

---

### Post by Jeremy23 on 2007-07-31
Sorry mate, not possible.

You want non-ugly images, and you want GIF images. Those two are almost opposites. It's like ordering an oil-water milkshake and complaining that the oil and water aren't mixing.

---

### Post by Badjaccur on 2007-12-21
It looks like you scaled your GIF image. Never scale an image while it 's in indexed colour mode. By scaling you create new pixels. When your image is in indexed mode not all colours can be used and this will cause your image to have rough edges. This can appear liek the text you have in your image. When you make a transparent image like the Ubuntu logo, make sure you make it free against a white background if you want to put it on a white background. Your Ubuntu logo is made transparent for a black background.

So basicly it's about undrestanding what you are doing. This will come by doing and asking good questions. You are doing both so you're fine ;)

Last but not least: this is not a GIMP issue at all. You get the same thing in Photoshop. I can recommend using PNG but if you want animated banners you will have to use GIF. Some people call those evil but if you want them you want them and it's up to you.

Have fun!

A  solution: 
- Open in your favorite image editor, 
- Convert to RGB colours, 
- Scale, 
- Save as GIF, 
- Smile

---

### Post by omega_user on 2007-12-21
I think the Gimp's .gif making is fine, but if you really want to have a nice picture, just stick to .png, .gif files only really make sense to use if you're making an animation.

I apologoze for the following, it's quite pointless (but fun):
:)/-<
:)\-<
:)/-<
:)|-<
:)/-<
:){-<

vs.

:)\-<   [pretend this is a higher quality image]

---

### Post by whiteraven on 2007-12-21
Actually, though there are indeed limitations to the GIF format, the problem lies with your choice of color for transparency. A well prepared transparent GIF blends in as seamlessly as possible with the background color or picture.

I use GIF images quite a bit, and with a bit of thought, never have the jaggies that are evident in your image.

Read an earlier post exactly about this "issue". Your image is well suited for clean anti-aliased edges.
=> [[COLOR="Blue"]GIF Transparency Using GIMP[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3887758#post3887758")

EDIT: If you need some help, I can remake the image for you and send you back the XCF file for you to examine.

---

### Post by Samhain13 on 2007-12-21
I have a rather radical suggestion where the banners are concerned.

GIF isn't an open format, right? So since OP is ready to use proprietary formats for what the does anyway, why not just make Flash banners? :)

Aside: they'd be the same way annoying either way.

---

