---
title: "Linux GIF animation"
date: 2007-05-01
forum: Art &amp; Design
---

### Post by dolphinboy on 2007-05-01
I'm a newbie low-tech geezer looking for software for linux to make animated icons (free if possible)-- is anybody out there who can help?
:confused:

---

### Post by madmetal on 2007-05-01
> **dolphinboy said:**
> I'm a newbie low-tech geezer looking for software for linux to make animated icons (free if possible)-- is anybody out there who can help?
:confused:

most linux programs are free and open source...
you can create animated icons with Gimp which you can find at applications >> graphics >> gimp
just handle each frame as layer...

UAResolved.

---

### Post by dolphinboy on 2007-05-01
:popcorn: :)thanks for the info--now to learn how!

---

### Post by FrooziE on 2007-10-31
You can use Gifsicle.
[http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/)

It should be in the Gusty repo, that's where i found it. The only thing is that it's CLI only, but even so it's very easy to use. Check the site, it has some basic commands and help etc.

I made the following image with it:
[IMG]http://i6.photobucket.com/albums/y213/FrooziE/Websites/anim.gif[/IMG]

I typed the following in a terminal opened in the folder where all the images were located.

> gifsicle --delay=200 --loop *.gif > anim.gif

It does the trick for those of us who don't have much of a clue when it comes to layers etc.

---

### Post by Crafty Kisses on 2007-11-01
Gifsicle is really good.

---

### Post by Paul820 on 2007-11-01
That looks like a really handy tool, i'll download that.

---

### Post by Crafty Kisses on 2007-11-01
> **Paul820 said:**
> That looks like a really handy tool, i'll download that.

Yeah, it actually is really handy. :KS

---

### Post by argraff on 2007-11-03
When you do them in GIMP, make sure that you state the time needed between frames in parenthesis - (it's in milliseconds).

So, for example, you might name a layer "dog" and want it for 1 second. You layer name should be

[FONT="Courier New"]dog (1000ms)[/FONT]

Check this page out for more: [http://www.gimp.org/tutorials/Simple_Animations/]("http://www.gimp.org/tutorials/Simple_Animations/")

Hope that helps!

---

### Post by Bruce M. on 2007-11-06
> **argraff said:**
> 

Check this page out for more: [http://www.gimp.org/tutorials/Simple_Animations/]("http://www.gimp.org/tutorials/Simple_Animations/")

Hope that helps!

Oh you have no idea!!  I stripped out /Simple_Animations/ and have the complete tutorial.  So, let me shout this:

  ***[COLOR="Blue"]THANK YOU![/COLOR]***

I'm having a heck of a time with GIMP, I'm trying to figure out how to make a transparent background in an existing .PNG file. (it's a red leaf on a white background - one layer)

So now I have the tutorials on-line.  Tried the "Help" and can't find it.  It's probably there; staring me in the face. 

Maybe I'll start a thread on how to do that. (it'll be a short one).

I'm trying to make my own animated avatar, and I'm like Shultz:  "I know nothing!"  (Hogan's Heros)

---

### Post by argraff on 2007-12-02
Do you have the newest version of GIMP? There is the new foreground select tool which is pretty easy to use - just draw a loose outline of the red leaf, the color the red to indicate it's part of the foreground. Otherwise, you could always make the PNG a layer in a transparent background PNG, select the white area and ctrl-x it!

Good luck!

---

### Post by whiteraven on 2007-12-03
The easiest way I know of to create transparency in GIMP for images that support transparency is to create your graphic using layers above the default Background layer. When you are ready to export to GIF or PNG, right click on the Background layer in the layers dialog and select Add Alpha Channel. With the Background layer active, CTL+A to select all, then CTL+K to delete. Save the image as GIF or PNG and voila! A transparent image!

You can use any color for the Background layer, keeping in mind that the color used will also be transparent in the image, thus white is not always the best choice. For example, if your image is themed with greens, you might want to try magenta (#FF00FF) as the background color. This is not a comprehensive explanation, so experiment a bit...

GIF transparency is "binary". That basically means that a pixel in a GIF graphic is either on (colored), or off (transparent). This is different from the multiple layers of transparency in graphics programs such as GIMP, or even the 254 levels of transparency possible with PNG files.

What this means is that when you have a transparent GIF, one of the critical things to watch out for are the edges. A well prepared transparent GIF blends in as seamlessly as possible with the background color or picture.

Certain effects are not suited for transparent GIFs. One good example of this is a text headline with a drop shadow. The edges of shadows are fuzzy and have subtly changing levels of transparency; therefore, when you are creating a drop-shadow element, it is rather meaningless to save it with transparency.

---

### Post by buzz2rp on 2008-03-27
I have just tried gisicle out and it found that does the job beautifully and fast. Thanks!

---

### Post by onyxbits on 2008-07-05
If you want something with a GUI instead of a CLI, you could use GiftedMotion:

[GiftedMotion - GIF Animator]("http://www.onyxbits.de/giftedmotion")

---

### Post by smartboyathome on 2008-07-06
Currently, only a few select icons are able to be animated, unless you use E17 (which, as of right now, is in constant development).

---

### Post by the_hardy_kid on 2008-07-07
how do you work gifsicle?

---

### Post by kung fu buntu on 2009-01-06
I've tried it all... major fail

Can anyone open this image and export a random frame?
And I mean frame, not layer.

I could almost pull it of with GiftedMotion, but the UI is a pain to delete frame (eg, try deleting frames 50-100 :p)



Yelp me! :)

Thanks


oops... faulty image: [http://i135.photobucket.com/albums/q141/FoamySoupp/funny/computerBAM.gif](http://i135.photobucket.com/albums/q141/FoamySoupp/funny/computerBAM.gif)

---

### Post by whiteraven on 2009-01-06
Here ya go, frame 9 (layer) - to get a complete frame you would need to make only the layers needed for that particular frame visible, then export the image. Surely you can try that and if you need more help, just shout back here...

---

### Post by whiteraven on 2009-01-06
...and here's an example of an exported frame...

---

### Post by kung fu buntu on 2009-01-07
whiteraven,

My problem is that I have no multiple selection (for example, by using the ctrl and shift keys) in the layers window, in GIMP.

How am I supposed to make all 240 frames invisible apart from just 3 or 4?
Clicking 236 times on the visible icon?

What was your shortcut? :p

For example how do you export frame 50 without having to deselect 190 frames?

Thanks.

---

### Post by whiteraven on 2009-01-07
> *For example how do you export frame 50 without having to deselect 190 frames?*

Just hold the SHIFT key down and click on the eye next to the layer name - in your case, that will leave just frame 50 visible and toggle ALL the other layers visibility to OFF.

---

### Post by kung fu buntu on 2009-01-07
Maybe I wasn't clear about it. But that doesn't solve it (at least in an elegant way).

I want to export frame 50, not layer 50.

I can make all layers (not frames!) invisible with 1 click like you said (except that you said frame instead of layer). But then I will have to make the previous 49 layers visible by clicking in each one :(
(in order to have a proper export of that frame)
Note that clicking on a random layer + the background layer, doesn't produce a valid frame.

Ok... 50 layers... not much... someone can say. That is if you don't make a mistake and have to start all over again... and what about frame 120? (in a 240 frames gif... clicking 120 layers is a lot of clicking :p)

gif image: [http://i135.photobucket.com/albums/q141/FoamySoupp/funny/computerBAM.gif](http://i135.photobucket.com/albums/q141/FoamySoupp/funny/computerBAM.gif)

What did GIMP devs removed multiple selection from a list box? :(


Thanks for your help whiteraven!

---

### Post by whiteraven on 2009-01-07
Yeah, I see what you mean now. The way that animation is constructed is a bit different. I can't think of any other tricks at the moment - guess you'll have to roll up your sleeves and do it manually. :(

---

### Post by The-ITu on 2009-05-07
i installed gifsicle from synaptic and i can't seam to find a short cut any wear. its not in the menue :(

---

### Post by ubuntu27 on 2009-05-07
> **The-ITu said:**
> i installed gifsicle from synaptic and i can't seam to find a short cut any wear. its not in the menue :(

Open the terminal [Application menu---->Accesories--->Terminal]

and type 
```

gifsicle
```

and press enter.



**EDIT** Ignore me. I don't know how to use that one. 
I just know that you have to use the terminal :D Since it is a CLI/Terminal utility.

This post can give you a clue

> **FrooziE said:**
> You can use Gifsicle.
[http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/)

It should be in the Gusty repo, that's where i found it. The only thing is that it's CLI only, but even so it's very easy to use. Check the site, it has some basic commands and help etc.

I made the following image with it:
[IMG]http://i6.photobucket.com/albums/y213/FrooziE/Websites/anim.gif[/IMG]

I typed the following in a terminal opened in the folder where all the images were located.

```
gifsicle --delay=200 --loop *.gif > anim.gif
```

It does the trick for those of us who don't have much of a clue when it comes to layers etc.

You might find more info at the homepage [http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/)

---

### Post by wubijacq on 2009-09-22
> **FrooziE said:**
> You can use Gifsicle.
[http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/)

It should be in the Gusty repo, that's where i found it. The only thing is that it's CLI only, but even so it's very easy to use. Check the site, it has some basic commands and help etc.

I made the following image with it:
[IMG]http://i6.photobucket.com/albums/y213/FrooziE/Websites/anim.gif[/IMG]

I typed the following in a terminal opened in the folder where all the images were located.



It does the trick for those of us who don't have much of a clue when it comes to layers etc.
thank you FrooziE for this simple demo dont'forget mtPaint and nautilus-open-terminal o good with gifsicle on Ubuntu

---

### Post by Younio on 2011-03-30
> **onyxbits said:**
> If you want something with a GUI instead of a CLI, you could use GiftedMotion:

[GiftedMotion - GIF Animator]("http://www.onyxbits.de/giftedmotion")

Thank you, really good Java application. Helped me a lot :D

---

### Post by SeijiSensei on 2011-03-30
> **Younio said:**
> Thank you, really good Java application. Helped me a lot :D

I'll stick with the GIMP.  That way you can edit the images in the same application you use to create the animation.  It's also easy to add borders (Filters > Decor > Borders) around the image, crop all the layers in a single step, or resize the entire animation.  The differencing engine in the GIMP is very efficient as well.

In answer to one of the earlier questions, you can open multiple images in the GIMP as layers in just two steps.  First, open the image you wish to use as the background, then use "File > Open as Layers" and pick the images you wish to include on top of the initial background.

One problem I had with GiftedMotion was that changing the frame delay didn't change the speed of the preview.  Do you need to save in order to preserve the delay?

---

