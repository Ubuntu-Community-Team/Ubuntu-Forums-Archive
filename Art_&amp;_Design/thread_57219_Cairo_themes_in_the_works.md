---
title: "Cairo themes in the works"
date: 2005-08-15
forum: Art &amp; Design
---

### Post by NoTiG on 2005-08-15
Heres an example of one:

[IMG]http://213.133.111.182/Temp/Screenshot-Calculator5.png[/IMG]

---

### Post by the_purulent on 2005-08-15
Dang. Looking puuurty.
Is the support for themes of this style going to be in breezy?

---

### Post by kaaredyret on 2005-08-15
Hardly. Choice is good but I dont think tht this particular theme is good enough. [-X

---

### Post by NoTiG on 2005-08-16
its just the beginning >;p there are so many possibilities now... Gnome is going to look awesome. Just hope that glitz  / xgl work someday.

*dances and celebrates his lowest rated thread ever*

---

### Post by drizek on 2005-08-16
i dont get it. whats so great about this?

---

### Post by bvc on 2005-08-16
anyone know where binary's or tarballs that'll build on hoary are? cvs and the debs from the download page have too many deps for us dialup'ers :| 

Anyway, since I can't get it, if anyone is involved in devel or mailing list or something please mention allowing themers the freedom of specifying diff font colors for as many diff widgets as possible. If we can't move around in these themes, we'll still have plain, grey based, 2 color themes....so another engine is pointless. We don't need a repeat of the pixmap/svg engines.

---

### Post by kamstrup on 2005-08-16
Fancy cairo-themes will prolly not be available in breezy, but it will be *possible*. If somebody writes up a decent cairo theme engine we will be able to install it on top of a breezy system.

---

### Post by bvc on 2005-08-16
[QUOTE=kamstrup]Fancy cairo-themes will prolly not be available in breezy, but it will be *possible*. If somebody writes up a decent cairo theme engine we will be able to install it on top of a breezy system.[/QUOTE]
I hope that wasn't directed towards my question on pkgs. It's a bit confusing really.....
Are you saying the current cairo-gtk-engine stinks? If so why? ...and why do people think themes are somehow going to be fancy now? Yes, I've seen the screenies (not the one above), but who would incorporate such silly, unuseable, nonesense, into an actual theme? They're just examples.
...and.. what is 'fancy'? I really am curious what people are thinking this means, because  it seems people have the wrong idea, but of course 'fancy' means many things to many people.

---

### Post by NoTiG on 2005-08-16
My understanding, is that cairo incorporates vector based images, and therefore looks better in different resolutions. FOr example... say you have two note books.. one is 1200 X 800 and the other is 1400 X 1000 . THey are both on 15.4 inch screens... the 14X one has more pixels, and therefore they are smaller and more dense. However... the widges will look small.. compared to the 1200 one because the widgets are raster images and have a fixed amount of pixels. Now you could stretch them if you wanted them to look bigger, but then they would look jagged because they are raster, and will look like crap. In the future with better DPI monitors and higher resolutions..cairo will allow widgets to scale properly and still maintained a crisp anti aliased look (and will look even better than lower DPI monitors since the pixels are more dense)

Im not exactly sure what else cairo allows.. thats different or better than GTK. I know that it sets the stage for future hardware acceleeration.. which we don't have yet but will be important. 

But the question is.. do you have more control over themes? Here is a quote from the gtk mailing list:

>  GTK+ now uses and depends on the cairo vector graphics
 library ([http://www.cairographics.org)](http://www.cairographics.org)), bringing such new
 graphics capabilities as antialiased shapes, alpha blending,
 and gradients. Most of the rendering of GTK+ widgets is
 now done with cairo.

Here is an example of the in development new clearlooks cairo theme:

[IMG]http://www.stellingwerff.com/cl-cairo/clearlooks-cairo1.png[/IMG] 

Is that even possible with the regular gtk without cairo themes, to get the progress bar like that ? 

> Dude, obviously complex Cairo themes are slower than current themes, because every widget is rendered by sophisticated vector drawing functions. This can't be compared to current pixmap-based themes or the primitive Gdk drawing functions we are using in current engines.

This approach is infinitely more powerful, but it also comes at a cost. There will always be simplistic themes for those on slower hardware or who are extremely pedantic about reaction times. Vector graphics are the future and this will allow us to have extremely nice looking widgets (for example the look of Aqua widgets could easily be recreated by just using Cairo drawing functions) which are totally _scalable_. And if your computer is fast enough to render the items at acceptable speeds (which will become more and more likely as Cairo gets optimized and accelerated), it won't have any significant impact on your system resources.


---

### Post by bvc on 2005-08-17
In the end...down the road, I have no doubt it'll be better. Of course it will and I look forward to it. BUT, the amount of difference we'll get from better looking images will not be worth the extra load on the sys IF we are still stuck with the current font color limitations. Your example of notebooks is good because it is on notebook borders that this loss of image quality is most noticable. Not a big deal really and can currently be resolved with bigger notebook images...but then...more resources are needed.

> But the question is.. do you have more control over themes? Here is a quote from the gtk mailing list:

Quote:
GTK+ now uses and depends on the cairo vector graphics
library ([http://www.cairographics.org)](http://www.cairographics.org)), bringing such new
graphics capabilities as antialiased shapes, alpha blending,
and gradients. Most of the rendering of GTK+ widgets is
now done with cairo.That is not at all true! If it is, why are icon artist still releasing their highly detailed svg icon themes that have angled gradients in png format? Because gnome can not and does not render svg as the svg manipulating apps do. It can't handle the detail or angled gradients. It is the reason Edge Icons were release in png and why most, or some, of the Scutum gtk theme is png.

That also has nothing to do with the biggest control we need. Which is on font color. We can be given that in the pixmap/svg engines if people would properly code. People don't seem to understand that even on mac and win the themes that are most popular are using apps that cost $ and enable the themers to change just about anything, anywhere. So if Linux wants to look good, it better get to writting good code and give themers lots of options or we'll just keep on with the gray base stuff like yours above.

> Is that even possible with the regular gtk without cairo themes, to get the progress bar like that ? Sure it is. I simply saved the screenie, cropped in gimp, put the images is Milk2.1 and told the progressbar not to stretch
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/progressbar-test.png[/IMG]
and if the short one doesn't convince you
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/progressbar-test1.png[/IMG]

BUT, cairo may come in handy on 'this style' progressbar IF we can specify which direction to stretch or not to strecth. Think they'll add that ability on their own without someone explaining that it is needed? Very doubtful. Is it possible? I don't know but I would think so. For that matter, if it is possible, why not put that into the pixmap and svg engines?
'This style' meaning one that is not stretched horizontally. Yet, that is rarely used and this is why. Not all apps display the progressbar the same height, for some silly reason. So your progressbar being told to not stretch begins to tile vertically...and looks bad.

So far, every usuable mockup I've seen can be done in a current gtk/pixmap/svg limited environment. The only advantage, concerning themes, is aa and no loss of quality when stretched. Will it be worth a performance hit for what most do not even notice? Guess that depends on the performance hit and what one considers worth it. I know I don't like using svg icon themes. I know that is one of the reasons you do not see the Human icon theme when you first login to a new install of ubuntu. Got a long way to go. Are we putting the cart before the horse? You know, win and mac can do this stuff without scalable vector graphics. Why not fix what we have that is broken and uses less resources, considering they will still be the dominate formats used for a long time to come? Everyone says scalable vectors are the future and it is.....but it is so far from being the dominate in the future we still need to fix the current which are still future formats. Reality check! Ah...someday, on the other side of the rainbow, most, may... be, somewhat... satisfied.

control
control
control

---

### Post by kamstrup on 2005-08-17
bvc: My answer was mostly targeted the_purulent.

Here's just a general rant on cairo-stuff...

What cairo does: Allows you to programmatically specify ways for drawing widgets - this makes it possible to come up with new stuff that would be entirely impossible in pure gtk/gdk. - for *example* imposing a small randomness on each button widget making them look slightly different. Furthermore glitz allows cairo to 3d-accelerate vector operations.

What cairo doesn't (theoretically :-D): Slow things down. Carl Worth recently said on lug-radio that they made a great effort to make sure that normal rendering would follow the same code-path as gdk rendering. Ie. with proper opimizations, no speed loss. 

[http://www.gnome.org/~seth/blog//xshots](http://www.gnome.org/~seth/blog//xshots) is a **great** resource on all this. Scroll down to the cairo section.

---

### Post by drizek on 2005-08-17
You dont need cairo and svg for this kind of stuff. With qt(which isnt vecotr based), the baghira theme can do animated progressbars like the one you posted, it can do brushed metal, it can create buttons that look like the ones in the first post etc. 

i agree with bvc, the only real improvement i see is being able to scale windows. but if windows are all vectors, then resizing them would be slow and jumpy(like in OSX, although for different reasons).

as for the svg icons, i dont know about gnome, but KDE's svg rendering engine is just unfinished, which is why svg icons are not rendered correctly. However, the svg engine in kde 4 will be improved, and it will use an animated svg iconset(oxygen) by default.

---

### Post by kamstrup on 2005-08-17
There are at least a 100 good reasons to switch to Cairo... Have you tried working with it? It is really easy to use and fun to work with - quite contraray to gdk! It's not only "fancy svg and scalability" (but also that) - it is also "print (exactly) what you see - as pdf, ps, png or svg" plus 3d-accelerated vector operations (with glitz).

-- If you are not hyped about Cairo, it's because you simply don't understand what it is :-D - You may quote me on that!

QT4 has the Athur drawing engine. Also magnificent work, much in the same spirit as Cairo. It will be very exiting to see the "clash of the giants" :-D Cairo vs Arthur...

---

### Post by bvc on 2005-08-17
[QUOTE=kamstrup][http://www.gnome.org/~seth/blog//xshots](http://www.gnome.org/~seth/blog//xshots) is a **great** resource on all this. Scroll down to the cairo section.[/QUOTE]Like I said I've seen that...and I'm sure most have.

[QUOTE=kamstrup]It's not only "fancy svg and scalability" (but also that) - it is also "print (exactly) what you see - as pdf, ps, png or svg" plus 3d-accelerated vector operations (with glitz).[/QUOTE]Well, I don't know about everyone else, but since this is about a gtk theme (cairo-gtk-engine), that is all I have specifically addressed, in an attempt to stay on toppic. There are other threads just about cairo but I'm posting in this one which is about a gtk theme.

[QUOTE=kamstrup]-- If you are not hyped about Cairo, it's because you simply don't understand what it is  - You may quote me on that![/QUOTE]K, I will...if hyped means we are pleased that other important things are still broken (still after years), that are still needed and desired, and cairo is somehow the one stop solution for tommorow, while we still play in the mud. No, I'm not hyped. Unfinished code is all we've seen for 4 years...is cairo going to be left undone for themers too? Based on bad history, it's hard to be hyped. The quality bar drastically needs to be raised. That is all I am saying. Can anyone deny that? If you think you can, you haven't themed. You can quote me on that :grin:
..and yes, I'm trying to upgrade this dialup machine to stay current with cairo cvs so that I can test it, join the list, and contribute to the gtk-engine, for us themers, so we do not end up dead in the water again.

---

### Post by NoTiG on 2005-08-17
[QUOTE=bvc]Like I said I've seen that...and I'm sure most have.

Well, I don't know about everyone else, but since this is about a gtk theme (cairo-gtk-engine), that is all I have specifically addressed, in an attempt to stay on toppic. There are other threads just about cairo but I'm posting in this one which is about a gtk theme.

K, I will...if hyped means we are pleased that other important things are still broken (still after years), that are still needed and desired, and cairo is somehow the one stop solution for tommorow, while we still play in the mud. No, I'm not hyped. Unfinished code is all we've seen for 4 years...is cairo going to be left undone for themers too? Based on bad history, it's hard to be hyped. The quality bar drastically needs to be raised. That is all I am saying. Can anyone deny that? If you think you can, you haven't themed. You can quote me on that :grin:
..and yes, I'm trying to upgrade this dialup machine to stay current with cairo cvs so that I can test it, join the list, and contribute to the gtk-engine, for us themers, so we do not end up dead in the water again.[/QUOTE]


What exactly is the problem? Ive seen you contribute alot...  you probably know what needs to be fixed more than some. what exactly is wrong?

---

### Post by kamstrup on 2005-08-17
Sorry bvc, I got a bit carried away... People have been picking a lot on Cairo lately, and it upsets me...

[quote=bvc]You can quote me on that[/quote] -- I quote you back.

I really feel with the frustrated themers out there, but I am also very hopeful about the future. Cairo is nearing a 1.0 release - if you are following the mailing lists... This means that we'll have a stable API, and I do believe people will step up (as they are already doing) and do some descent work on a theme engine. Bear in mind that Cairo is far easier to work with than plain gdk - there is a better foundation to build upon than before.

---

### Post by bvc on 2005-08-17
[QUOTE=NoTiG]What exactly is the problem? Ive seen you contribute alot...  you probably know what needs to be fixed more than some. what exactly is wrong?[/QUOTE]Thanks for asking, but haven't I specified enough?[QUOTE=bvc]Anyway, since I can't get it, if anyone is involved in devel or mailing list or something please mention allowing themers the freedom of specifying diff font colors for as many diff widgets as possible. If we can't move around in these themes, we'll still have plain, grey based, 2 color themes....so another engine is pointless. We don't need a repeat of the pixmap/svg engines.[/QUOTE][QUOTE=bvc]That also has nothing to do with the biggest control we need. Which is on font color. We can be given that in the pixmap/svg engines if people would properly code. People don't seem to understand that even on mac and win the themes that are most popular are using apps that cost $ and enable the themers to change just about anything, anywhere. So if Linux wants to look good, it better get to writting good code and give themers lots of options or we'll just keep on with the gray base stuff like yours above.[/QUOTE][QUOTE=bvc]BUT, cairo may come in handy on 'this style' progressbar IF we can specify which direction to stretch or not to strecth. Think they'll add that ability on their own without someone explaining that it is needed? Very doubtful. Is it possible? I don't know but I would think so. For that matter, if it is possible, why not put that into the pixmap and svg engines?
'This style' meaning one that is not stretched horizontally. Yet, that is rarely used and this is why. Not all apps display the progressbar the same height, for some silly reason. So your progressbar being told to not stretch begins to tile vertically...and looks bad.[/QUOTE][QUOTE=bvc]That is not at all true! If it is, why are icon artist still releasing their highly detailed svg icon themes that have angled gradients in png format? Because gnome can not and does not render svg as the svg manipulating apps do. It can't handle the detail or angled gradients. It is the reason Edge Icons were release in png and why most, or some, of the Scutum gtk theme is png.[/QUOTE][QUOTE=bvc]You know, win and mac can do this stuff without scalable vector graphics. Why not fix what we have that is broken and uses less resources, considering they will still be the dominate formats used for a long time to come? Everyone says scalable vectors are the future and it is.....but it is so far from being the dominate in the future we still need to fix the current which are still future formats. Reality check![/QUOTE]

See this theme? Looks good...not useable. The creator chose looks over usability. Read the 'fonts' coments.
[http://gnome-look.org/content/show.php?content=27668](http://gnome-look.org/content/show.php?content=27668)
Here's a little thread on text color
[http://gnomesupport.org/forums/viewtopic.php?t=8589&highlight=](http://gnomesupport.org/forums/viewtopic.php?t=8589&highlight=)

I emailed two good gnome themers I respect about this and both replied. One couldn't find any more hacks than I, or didn't try, and the other said he would look into it and hasn't replied yet.

What's the biggest complaint we hear?
"another gray/white theme?...oh no! don't you know any other colors?"
I have tried and tried to tell people themers are limited in their creativity because of the font limitations forced on us. It gets really old really quick to spend a lot of time just to make something work and be usable, to have people complain as if you just threw it together without trying to make it nice.

Could all of this have been avoided? Well, based on this
[http://gnomesupport.org/forums/viewtopic.php?t=8589&highlight=](http://gnomesupport.org/forums/viewtopic.php?t=8589&highlight=)
maybe so. How? Why doesn't any pixmap themes come with the engine? Why doesn't any svg themes come with the engine? You get themes with all the other engines, but not these 2. Well, there should be even if they are intentionally bad color choices. They should display everything the engine can and can not do, and should be very well documented. If the developers would have done this, we would have known about *GtkLabel long ago. We are not coders, just themers. What are the other options that we don't know about? We need 'example themes' for they are the best documentation! This is what the gtk-engine-cairo needs to do after enabling every possible option in the engine.

How devel can spend so much time on these engines and then not empower themers to show it off is beyond me. Are we expected to learn the code? If I was interested in code, I wouldn't be a themer would I? IS it a team effort or not? Coders code, themers theme. Team.

---

### Post by bvc on 2005-08-17
[QUOTE=kamstrup]Sorry bvc, I got a bit carried away... People have been picking a lot on Cairo lately, and it upsets me...

 -- I quote you back.

I really feel with the frustrated themers out there, but I am also very hopeful about the future.[/QUOTE]It's cool, and I'm sorry to! I easily get upset about this subject because I am constantly picked at as well.

---

### Post by NoTiG on 2005-08-17
oh ive run into that problem myself. I was using a dark theme and i couldnt see the writing on tabs and stuff so i had to abandon it.

There is a thread in that discussion that you posted.. one of the lasts posts was:

> The bug is fixed in gtk 2.8.1. 

Im pretty sure breezy will be shipping with 2.8 though since gnome 2.12 does. SO we will probably wait some more...

And i agree that its not entirely simple to make  a theme :P i tried to modify one... and a higher level language / toolkit is probably needed. I was trying to modify the blended theme so that the buttons wouldn't disappear when they werent focused.

---

### Post by bvc on 2005-08-18
I can assure you that what I'm talking about has not even been touched. The bug fix has nothing to do with what I'm talking about. That fix may or may not help depending on the theme. Again. Control. Sometimes the buttons will need relief sometimes they won't, and sometimes they'll need there own fg and text color. We have to be able to control that or we'll still be limited in what we can do.

---

### Post by drizek on 2005-08-20
for anyone interested, heres a screenshot comparing hte cairo AA color picker for the panel and the color picker for the gimp.

[[IMG]http://img388.imageshack.us/img388/3949/screenshot15fc.th.png[/IMG]](http://img388.imageshack.us/my.php?image=screenshot15fc.png)

---

### Post by doclivingston on 2005-08-20
[QUOTE=NoTiG]Im pretty sure breezy will be shipping with 2.8 though since gnome 2.12 does. SO we will probably wait some more...[/QUOTE]

Gnome 2.12 and hence Ubuntu breezy will use GTK 2.8. However this doesn't mean they have to use GTK 2.8.0, they can use other versions such as 2.8.1, etc - and breezy will have newer versions if it fixes bugs.

---

### Post by kamstrup on 2005-08-30
Picking up on this old thread, I just discovered that the new clearlooks-cairo engine indeed supports colored text (looking at the supplied gtkrc file).

Resources:
Mockup: [http://stellingwerff.com/mockups/buttons3.png](http://stellingwerff.com/mockups/buttons3.png)
CVS: [http://sourceforge.net/projects/clearlooks](http://sourceforge.net/projects/clearlooks) check out clearlooks-cairo module
Screenshot: [http://www.stellingwerff.com/?p=9](http://www.stellingwerff.com/?p=9)

---

### Post by bvc on 2005-08-30
[QUOTE=kamstrup]Picking up on this old thread, I just discovered that the new clearlooks-cairo engine indeed supports colored text (looking at the supplied gtkrc file).
[/QUOTE]According to the gtkrc, its level of support is the same as clearlooks. Clearlooks-devel has always done a good job of including options. As far as that goes, most 'engine-only' do....its the pixmap and svg that do not, and the pixmap is the most downloaded. [http://gnome-look.org/index.php?xsortmode=down&page=0](http://gnome-look.org/index.php?xsortmode=down&page=0)
Of the top 15, only one is 'engine only'. The docs available on cairo tell me absolutely nothing. How do you learn it? What does your gtkrc look like? If it looks like the gtkrc's that come with the cairo gtk engine, very few people will be making cairo themes until it is a lot easier.

---

### Post by kamstrup on 2005-08-30
[QUOTE=bvc]According to the gtkrc, its level of support is the same as clearlooks.[/QUOTE] Oh, yes. I just realised that right after posting :D

[QUOTE=bvc]The docs available on cairo tell me absolutely nothing. How do you learn it? [/QUOTE] The examples included in the various modules is a good start. There's also a cairo-doc package in the repos which you can browse with devhelp.

EDIT: Richard Stellingwerff (creater of clearlooks) just replied to a similar question I asked him in his blog. Look here: [http://www.stellingwerff.com/?p=9#comment-51](http://www.stellingwerff.com/?p=9#comment-51)

EDIT_OF_EDIT: Oh, you've noticed!

---

### Post by bvc on 2005-09-01
thx, but those are the docs I've looked at that say nothing......
If I wanted to write an engine I would have done so, but I just wanna make a theme...were is that doc?

---

### Post by kamstrup on 2005-09-01
Found it! Try ```
less -f /dev/null
``` to see all available documentation :-D

---

### Post by bvc on 2006-01-06
so?
it's been 5 months....
hit a wall?

---

### Post by kamstrup on 2006-01-06
Sorry; what are you refering to bvc?

---

### Post by bvc on 2006-01-07
where this theme is

---

### Post by kamstrup on 2006-01-07
Well, If we're talking clearlooks-cairo, it is default in Dapper. 

If we're talking text-coloring support I'm afraid it will have to wait for gtk 2.10 (which should be in Gnome 2.16 if I understand correct, thus Dapper+1).

---

### Post by bvc on 2006-01-07
this thread isn't about either of those :rolleyes:

---

