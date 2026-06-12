---
title: "Inkscape automation?"
date: 2010-02-25
forum: Art &amp; Design
---

### Post by Bölvaður on 2010-02-25
I am making a binary clock wallpaper (see attachment) which is controlled with an xml (so the background is changed every minute)

I got each digit on a separate layer (like for the row to the right I got 2^0 , 2¹, 2², 2³ as individual layers) so all I have to do to change the numbers is to toggle layers to be visible or not.

I am using only minutes and because there needs to be 60 pictures for each hour and there are 24 of those, I would need 60×24 = 1440 pictures in total.

Isn't there any script I could build to automate this for me?

It would be really good if I realize I made a mistake and dont want to manually make those 1440 images again

---

### Post by Newfoundlander on 2010-02-25
I am aware of SVG animation but I am no expert in this area.  There are examples of this being used on the web.  Perhaps these sites may help you:

[http://www.w3.org/TR/SVG/animate.html](http://www.w3.org/TR/SVG/animate.html)
[http://www.adobe.com/svg/demos/clock.html](http://www.adobe.com/svg/demos/clock.html)
[http://www.nimblecoder.com/blog/archive/2009/12/30/animated-clocks-for-svg-and-silverlight.aspx](http://www.nimblecoder.com/blog/archive/2009/12/30/animated-clocks-for-svg-and-silverlight.aspx)
[http://en.wikipedia.org/wiki/SVG_animation](http://en.wikipedia.org/wiki/SVG_animation)

---

### Post by durand on 2010-02-25
I'm not sure that svg wallpapers in nautilus support svg animation.

I could possibly write a script for you in python. It should be pretty simple to just copy one layer into a template svg, render it, copy another, etc.

---

### Post by Bölvaður on 2010-02-25
No I dont mean animation.
Apparently I failed at reading what I wrote and missed to point out what I am doing.



You can make slide shows as desktop background by putting the paths into an xml and load the xml into the system &#8594; preferences &#8594; appearance

I got atm 720 png files ranging from 0000.png to 1159.png
and the xml looks like this:
```
	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0006.png</file>
	</static>


	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0007.png</file>
	</static>


	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0008.png</file>
	</static>

```


I made a c++ program to automate the making of the xml because it's so stupidly long (8650 lines).
[B]
So all I need to do now to _automate the making the png files_ so they name the png correctly and show the correct layer.[/B]


btw. the wallpaper looks really cool, even though there are some problems with timing.

---

### Post by durand on 2010-02-25
That is very easy. You could do it without all those layers, it would be easier to just generate the svg on the fly, and then set it as the background. Thats what I'd do. I made a wallpaper script to do just that with wallpaper clocks: [http://www.vladstudio.com/wallpaperclock/](http://www.vladstudio.com/wallpaperclock/)

It would be even simpler with svg.

---

### Post by Bölvaður on 2010-02-25
I ported what I did to the wallpaperclock and it works quite good. There are even few things that are much better. Like:
fewer images required
more flexibility

but then you get some negatives like:
be running screenlets
have to use jpg insetad of png with invisible pixels.


So perhaps it could be better to take some another approach that doesnt involve using a third party software.

> **durand said:**
> You could do it without all those layers, it would be easier to just generate the svg on the fly, and then set it as the background. Thats what I'd do.

I saw you could do some stuff with ```
$ inkscape --shell
```
but it wasnt obvious how you would make complex shapes (I might not need them) and have some blur effects on those and some things like that.


oh... wait you are talking about... because svg is pretty much just xml I can just edit the text every few seconds. That's actually quite good.
Some how I totally forgot about svgs being text files. I'll probably forget my self making L-systems now -.-

I'll look into that.
And if you have any really cool examples of what is possible to do plz post.

---

### Post by hxcobd on 2010-02-26
> **Bölvaður said:**
> No I dont mean animation.
Apparently I failed at reading what I wrote and missed to point out what I am doing.



You can make slide shows as desktop background by putting the paths into an xml and load the xml into the system &#8594; preferences &#8594; appearance

I got atm 720 png files ranging from 0000.png to 1159.png
and the xml looks like this:
```
	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0006.png</file>
	</static>


	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0007.png</file>
	</static>


	<static>
		<duration>60.0</duration>
		<file>/path/binaryWallpaperXML/0008.png</file>
	</static>

```


I made a c++ program to automate the making of the xml because it's so stupidly long (8650 lines).



Is there a particular reason why you wouldn't just use a For loop in XML for that?

---

### Post by durand on 2010-02-26
I was probably just going to use a string find and replace to make each svg. That would be the easiest way to do it. I made a wallpaper clock that works without screenlets if I want to take a look at it.

---

