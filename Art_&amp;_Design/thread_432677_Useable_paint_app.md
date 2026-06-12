---
title: "Useable paint app?"
date: 2007-05-04
forum: Art &amp; Design
---

### Post by affected on 2007-05-04
I'm trying to minimize my windows use, as I find rebooting every time I need to use Photoshop is painful. I've got Maya and Shake running in Linux, and that's great, now I just need a simple bitmap editor that has gets a few very basic painting-related things right. This is a list of what I need at minimum:
 
 -round brushes, Option to adjust brush hardness. Custom brushes a big bonus. 
 -brush size slider, easily accessible please.(say with a hotkey) 
 -Clone stamp tool or the like. 
 -layers and a few layer blend modes: multiply, screen, overlay mostly. 
 (even an app without layers would be something) 
 -16-bit colour mode. (if there's something out there without this, I'll gladly hear of it, but then I will sometimes still have to boot to windows to use photoshop)
 -WORKING wacom support 
 
That's about it. I've tried Gimp and Krita and Cinepaint and Pixel, all of which fail in one way or the other:

I'm not going to even start on Gimp's interface, but in Gimp and Cinepaint you can't adjust the brush size on the fly, only select a different size brush from your brush library. The fact that the Gimp's been in development for years and years and is still missing BASIC functionality like this doesn't get my hopes up regarding that app, even though I hear this particular feature is coming in version 2.4.

 Krita fails with brush spacing, I get very nasty spacing problems even with spacing at 0. Maybe it'll be fixed, I filed a bugreport, but development on Krita isn't exactly fast.

Pixel doesn't have wacom support at all, but it's "coming" in beta 7, which was "released" about a month ago, except it wasn't actually, and the developer hasn't been updating the site since... Apparently not the first time he's had problems like this.

Anyway... Even a bare-bones paint application would help me a great deal, as long as it puts coloured pixels on a bitmap, and fulfills the minimum requirements listed above. But I can't seem to find such an application, which I find pretty incredible. Help appreciated.

---

### Post by ComplexNumber on 2007-05-04
try mtpaint (click [here]("http://gnomefiles.org/app.php/mtPaint") for a description). thats what i use for a fast and simple bitmap editor. download the deb [here]("http://sourceforge.net/project/showfiles.php?group_id=155874&package_id=173703").

---

### Post by zeronet on 2007-05-04
Try the last Gimp Development version (2.3.16) It has a lot of features like adjust brush size on the fly :)

Here is the .deb package:
[http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k1_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k1_i386.deb)

With some options in the preferences you can use it like Photoshop´s Interface:

[http://i104.photobucket.com/albums/m171/alphonse_isaac/screenshots/gimp2-3.png](http://i104.photobucket.com/albums/m171/alphonse_isaac/screenshots/gimp2-3.png)

Gimp 2.3 rocks!

---

### Post by Hairy_Palms on 2007-05-04
also photoshop 7 runs fine under wine, and CS2 works too if you download PortablePhotoshopCS2

---

### Post by affected on 2007-05-06
*sigh*


Thanks, guys.

Mtpaint was too much of a pure pixel editor, I need something with opacity controllable by wacom, soft brushes etc.

I've tried photoshop with wine, I don't even remember any more what was the problem but it was a bit of a hassle... Maybe I'll look into that again.

Tried that Gimp development version as well, and I don't know whether to be happy or to cry. They put in a size slider, yes, but HOW they did it seems to demonstrate yet again a pathological unwillingness to do things the sane way. The sane way in this case would be to have the size slider set the pixel width of the brush, so that when the slider value is 1, the brush is 1 pixel wide, and when it is 100, the brush is 100 pixels wide. Instead it is a scale multiplier, so that if I have selected a brush that is, at default, 15 pixels wide and want to scale it down to 1 pixel, I must first quickly calculate 1/15 and then input that in the scale dialog. It's better than before to be sure, but if you're going to fix something, why not fix it well? In a well-designed brush system there is no need to have more than one size brush preset of each shape, the user can just scale the brushes at will. (assuming the brush is not a bitmap, in which case different scales may warrant different  images to prevent loss of quality.)

Oh well, I'm going to go see if I can turn the cursor display off for brush tools, so it only shows the brush size outline.

edit: I found that just having the brush editor open at all times in Gimp is the best option for me, as it has sliders for radius and hardness. I'd still prefer having a dialog that comes up with, say, right-click that has the two sliders, but oh well.

---

### Post by ComplexNumber on 2007-05-06
**affected**
you could try [this]("http://gnomefiles.org/app.php/MyPaint").

---

### Post by zeronet on 2007-05-06
> 
Tried that Gimp development version as well, and I don't know whether to be happy or to cry. They put in a size slider, yes, but HOW they did it seems to demonstrate yet again a pathological unwillingness to do things the sane way. The sane way in this case would be to have the size slider set the pixel width of the brush, so that when the slider value is 1, the brush is 1 pixel wide, and when it is 100, the brush is 100 pixels wide. Instead it is a scale multiplier, so that if I have selected a brush that is, at default, 15 pixels wide and want to scale it down to 1 pixel, I must first quickly calculate 1/15 and then input that in the scale dialog. It's better than before to be sure, but if you're going to fix something, why not fix it well? In a well-designed brush system there is no need to have more than one size brush preset of each shape, the user can just scale the brushes at will. (assuming the brush is not a bitmap, in which case different scales may warrant different images to prevent loss of quality.)

Oh well, I'm going to go see if I can turn the cursor display off for brush tools, so it only shows the brush size outline.

edit: I found that just having the brush editor open at all times in Gimp is the best option for me, as it has sliders for radius and hardness. I'd still prefer having a dialog that comes up with, say, right-click that has the two sliders, but oh well.

Well, maybe for the 2.4 final release developers should correct that problem with the brushes size, you can contact with them at Gimp´s Developers mailing lists, or Bug Reports.
That´s the idea,  give more advices to improve the programs :P

>  	affected
you could try this.

No, all the ***Paint, MtPaint, MyPaint, Gpaint, KolourPaint, sucks a lot, and their options are minimal, as Graphics Designer the only programs who works for you on Gnu/Linux are only three without wine: Krita, Gimp and Pixel (Is a ****, very buggy, and isn´t Open Source, but is Photoshop-like).

---

### Post by ComplexNumber on 2007-05-06
> No, all the ***Paint, MtPaint, MyPaint, Gpaint, KolourPaint, sucks a lot, and their options are minimal, as Graphics Designer the only programs who works for you on Gnu/Linux are only three without wine: Krita, Gimp and Pixel (Is a ****, very buggy, and isn´t Open Source, but is Photoshop-like).have you used mypaint or even read the write-up, or is that just a grand sweeping generalisation?

---

### Post by zeronet on 2007-05-06
> have you used mypaint or even read the write-up, or is that just a grand sweeping generalisation?

Yes, I´ve used it, but it´s only for paintings, it wasn´t made for general use like the others >.< (Gimp, Krita and Pixel)

Sorry for the generalization with MyPaint, was an error xD

---

### Post by ComplexNumber on 2007-05-06
> **zeronet said:**
> Yes, I´ve used it, but it´s only for paintings, it wasn´t made for general use like the others >.< (Gimp, Krita and Pixel)

Sorry for the generalization with MyPaint, was an error xD
thats what i was wondering about. affected says that he wants something basic but which satisfies his criteria. mypaint is different to most of the others because it has the brush dynamic that he wants, and is also designed for use with graphic tablets. the only required aspect it doesn't have is layers.

---

### Post by mech7 on 2007-05-06
> **zeronet said:**
> Try the last Gimp Development version (2.3.16) It has a lot of features like adjust brush size on the fly :)

Here is the .deb package:
[http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k1_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k1_i386.deb)

With some options in the preferences you can use it like Photoshop´s Interface:

[http://i104.photobucket.com/albums/m171/alphonse_isaac/screenshots/gimp2-3.png](http://i104.photobucket.com/albums/m171/alphonse_isaac/screenshots/gimp2-3.png)

Gimp 2.3 rocks!

How did you get GIMP looking like that? without all the floating windows as a window and smaller panels ?

---

### Post by zeronet on 2007-05-06
> How did you get GIMP looking like that? without all the floating windows as a window and smaller panels ?

It´s very easy, just changing some options on the preferences (**File---> Preferences**)

First, change the icon theme to **small**, now the panels can be adjusted to be more small.

[http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike1.jpg](http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike1.jpg)


Second, you can change te background of the Picture Window, and remove some elements that you don´t use, like the rules in my case .
[http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike2.jpg](http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike2.jpg)

Third, put the toolbar and other panels in **Utility Window **mode, so they can´t float anymore and don´t appear on the List of Windows in your Desktop.
Check the other option, and they will minimize or maximize depending of the Active Image Window :p

[http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike3.jpg](http://i104.photobucket.com/albums/m171/alphonse_isaac/tuto2/photolike3.jpg)

Now, separate docks from the toolbar and change the size of them !

---

### Post by longfire on 2007-05-06
Gimp 2.3.16 works well for me. It enabled the [ and ] keys like in photoshop for brush size enhancement. It may not be as exact but provides the pretty much what was missing without having to manually set keys in the last releases. I really like  the utility window option and improved CMYK support.

---

### Post by thedaemon on 2007-05-06
Gimp most certainly has better brush size selection than you lead on. Just create a new brush, then open the brush editor. There is the radius and other changes you may want to twiddle with.

---

### Post by mech7 on 2007-05-07
> **thedaemon said:**
> Gimp most certainly has better brush size selection than you lead on. Just create a new brush, then open the brush editor. There is the radius and other changes you may want to twiddle with.

What i hate about changing brush sizes is that they did not make it into a slider.. instead you have to put it in numerically or press the tiny buttons :(

---

