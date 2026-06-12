---
title: "GIMP 2.6 - Burning planet"
date: 2008-10-17
forum: Art &amp; Design
---

### Post by Half-Left on 2008-10-17
I'm sure like me your playing and enjoying GIMP 2.6, so here's something I've done to show how good GIMP can be.

I was doing a alien planet but this ended up being a burning one about to die. I've lost count how many filters I used but they are all in 2.6(no extra) and quiet a few GEGL operation effects as well.

I like showing stuff like this because it shows what good effects and work you can do in GIMP. 

Enjoy :)

---

### Post by Ub1476 on 2008-10-17
Amazing as always. I can't believe how you do it.

---

### Post by Joeb454 on 2008-10-17
Nice, you should upload it as a background, I'd certainly be interested.

I'd love to learn gimp too, but I don't have the time

---

### Post by alwez_loner_TZ on 2008-10-17
This is really great i didn't know you could do so much with GIMP. I gave GIMP a try yesterday and I almost forgot to sleep.. 

Maybe you can explain a bit how you did it.

---

### Post by Perfect Storm on 2008-10-17
Nice work :guitar:

---

### Post by jedimasterk on 2008-10-17
> **Half-Left said:**
> I'm sure like me your playing and enjoying GIMP 2.6, so here's something I've done to show how good GIMP can be.

I was doing a alien planet but this ended up being a burning one about to die. I've lost count how many filters I used but they are all in 2.6(no extra) and quiet a few GEGL operation effects as well.

I like showing stuff like this because it shows what good effects and work you can do in GIMP. 

Enjoy :)

Nice!.

---

### Post by Malac on 2008-10-17
> **Half-Left said:**
> I'm sure like me your playing and enjoying GIMP 2.6, so here's something I've done to show how good GIMP can be.....
.......I like showing stuff like this because it shows what good effects and work you can do in GIMP.

Excellent Work.
Ever thought of doing some tutorials/walkthroughs for the forum ?

---

### Post by Half-Left on 2008-10-17
> **alwez_loner_TZ said:**
> This is really great i didn't know you could do so much with GIMP. I gave GIMP a try yesterday and I almost forgot to sleep.. 

Maybe you can explain a bit how you did it.

Ok, here's a few starters.

1. Make anew layer and use the Ellipse selection tool to create the planet shape. Got to Filters>Render>Sphere Designer and you can make a basic looking planet for there(Type: Texture, Texture: Noise).

2. Create a nice bumppy rocky surface by going to Filters>Light and Shadow> Lighting Effects, put the light where you like and enable Bump Mapping in the tab, make it how you like, 0.0.3-0.0.5 is good. Dont add shinny light, set it to 0 in the options under material(a real planet isn't shiny)

3. With your selection still selected around the planet, create a new layer for the glow around the planet. Got to select>Grow and glow is by about 5, then select>Feather and set to about 100. Make sure the glow layer is below the planet and then fill it with a colour with the Bucket Fill Tool. You can use Gaussian blur to make the glow around the planet more softer.

4. To make the stars, select your background and got to Filter>Noise>RGB Noise, set it like on the screenshot, apply. Now go to Colours>Threshold and move the slider down to get rid of the noise until your satified with the looks of the stars.

Thats just the basics of how to do scene like that, hope that helps.

---

### Post by Najmudin on 2008-10-17
Great work, i love your spirit in showing how gimp is good and the capabilities it has, instead of just arguing about gimp your work prove that its a great application ,especially to those who think its not as good as photoshop and refuse to use it.
Keep it up :)

---

### Post by blakjesus on 2008-10-17
Thats amazing. I have been wanting to learn to use gimp but i havent really found good tutorials and i find it hard to get use to the multi-window interface. :)

---

### Post by Gutt on 2008-10-17
I really want to get into the GIMP but never had the time.

I'm going to try to follow that small tutorial Half-Left :D .

---

### Post by Half-Left on 2008-10-17
**Part 2**

1. To make the clouds select your planet layer and right click the layer>Alpha to Selection, now make a new layer(make sure it's top layer. Go to Filters>Render>Clouds>Solid Noise and set the options in the screenshot or as you like.

Set the mode on the layer to Dodge and got to Colours>Curves and set like the screenshot. You can then colourise it to make it look hot.

2. To make the shadow just use the same method as the glow around the planet(make it black ofcourse), put it under the cloud layer. Then just move it off center of the planet and erase the over hanging part of the shadow and add a Gaussian blur to soften it out.

---

### Post by Gutt on 2008-10-17
Great :) . Managed to do it all the way :-P , thanks for the tutorial Half-Left, is there any more to do ?

---

### Post by Half-Left on 2008-10-17
> **Gutt said:**
> Great :) . Managed to do it all the way :-P , thanks for the tutorial Half-Left, is there any more to do ?

it's just remembering how I did that nice bumpy effect that gives it depth, just play around with the filters and select part of the hot clouds and apply a glow over them using the glow method using a gradient and free select tool for the hot parts.

You can use Filters>Enhance>Unsharp Mask on the planet(the GEGL operation one is better for 2.6) bumps to make them more rocky.

---

### Post by Half-Left on 2008-10-17
Oh and remember that GIMP can use Photoshop brushes, you can get aload from here [http://www.deviantart.com/#catpath=resources/applications/psbrushes&order=9](http://www.deviantart.com/#catpath=resources/applications/psbrushes&order=9).

Just put the brush file in /Home/myusername/.gimp-(version)/brushes and refresh them from inside GIMP, they are usually .vrb or .arb.

I actually used some real fire and volcano pictures for the planet, just removed the background or blending mode to screen and angled them over the hot glowing parts of the planet.

---

### Post by smartboyathome on 2008-10-17
Half-Left: That reminds me of [the planet I made]("http://smartboyathome.deviantart.com/art/Nubius-of-Uria-87262090") in GIMP. Looks kind of like one you would see in one of those extraterrestrial FPS games.

To get the clouds to look like that, I think I did overlay (or one of those layer filters), which made it look more real.

---

### Post by Half-Left on 2008-10-17
> **smartboyathome said:**
> Half-Left: That reminds me of [the planet I made]("http://smartboyathome.deviantart.com/art/Nubius-of-Uria-87262090") in GIMP. Looks kind of like one you would see in one of those extraterrestrial FPS games.

To get the clouds to look like that, I think I did overlay (or one of those layer filters), which made it look more real.

Yer, it's not that it's the effect I did than make the planet look like it has big shadowed holes, pretty sure I used the Solid Noise to get that effect but forgot the rest. :)

Nice planet BTW, good job.

---

### Post by smartboyathome on 2008-10-17
Thanks, Half-Left. If you ever need textures, just go to NASA's site. They got tons which are public domain, and some of them are really high quality.

---

### Post by deGz0rx on 2008-10-19
this has to be the best "make a kickass picture in less than 5mins" kind of tutorial lol
please man, whenever you have time, update this topic with new details or open a new topic for new stuff. i always wanted to learn gimp but i havent had a good reason ... this one kicked my *** though ;)

nice stuff :)

edit: heres what i got in the end. i played with supernova and added another smaller planet.

[http://i188.photobucket.com/albums/z225/deGraszlo/omajgad.jpg]("http://i188.photobucket.com/albums/z225/deGraszlo/omajgad.jpg")

---

### Post by Gutt on 2008-10-19
> **deGz0rx said:**
> this has to be the best "make a kickass picture in less than 5mins" kind of tutorial lol
please man, whenever you have time, update this topic with new details or open a new topic for new stuff. i always wanted to learn gimp but i havent had a good reason ... this one kicked my *** though ;)

nice stuff :)

edit: heres what i got in the end. i played with supernova and added another smaller planet.

[http://i188.photobucket.com/albums/z225/deGraszlo/omajgad.jpg]("http://i188.photobucket.com/albums/z225/deGraszlo/omajgad.jpg")

It's good but for some reason, the big planet doesn't seem that round to me, it's kinda oval :lolflag: .

---

### Post by Perfect Storm on 2008-10-19
Perhaps it was stretch a bit wrong, but it's still nice :)

---

### Post by AJB2K3 on 2008-10-19
Nice work but time for me to show off.

[http://ajb-2k3.deviantart.com/art/gimp-splash-1974377]("http://ajb-2k3.deviantart.com/art/gimp-splash-1974377")

Been making planets since it hit windows in 98 8P

10 years using gimp, Now that a long time and alot of experience.

---

### Post by deGz0rx on 2008-10-19
about my pic .. lol it was intended to be that way!
ahah, seriously, before you guys said it was stretched i thought it was ok. i guess i was pretty hyped about making my first planet in gimp so i didnt care about the shape, as long as its a planet lol :)

heres my new one. [http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg]("http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg")
im having hard time adding "fire-ish" surface, with some fire explosions and other details like that...and adding shadows to the bottom half of the planet is .. confusing? i know theres an option in filter>light and shadows but it doesnt allow a user to pick the area he wants to drop shadow on.
any tip concerning this and improving my work is welcome. i wanna learn gimp even tho im a newbie :P


btw AJB2K3 could you upload some of your newer stuff? :D

---

### Post by Gutt on 2008-10-19
> **deGz0rx said:**
> about my pic .. lol it was intended to be that way!
ahah, seriously, before you guys said it was stretched i thought it was ok. i guess i was pretty hyped about making my first planet in gimp so i didnt care about the shape, as long as its a planet lol :)

heres my new one. [http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg]("http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg")
im having hard time adding "fire-ish" surface, with some fire explosions and other details like that...and adding shadows to the bottom half of the planet is .. confusing? i know theres an option in filter>light and shadows but it doesnt allow a user to pick the area he wants to drop shadow on.
any tip concerning this and improving my work is welcome. i wanna learn gimp even tho im a newbie :P


btw AJB2K3 could you upload some of your newer stuff? :D

That's much better :) . The colors fit in really well too :D .

---

### Post by AJB2K3 on 2008-10-20
> **deGz0rx said:**
> 

btw AJB2K3 could you upload some of your newer stuff? :D
I could but all I've got is photo's and there already uploaded.:(

Been too busy to wip up anything.

---

### Post by Half-Left on 2008-10-20
> **deGz0rx said:**
> about my pic .. lol it was intended to be that way!
ahah, seriously, before you guys said it was stretched i thought it was ok. i guess i was pretty hyped about making my first planet in gimp so i didnt care about the shape, as long as its a planet lol :)

heres my new one. [http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg]("http://i188.photobucket.com/albums/z225/deGraszlo/omajgad-1.jpg")
im having hard time adding "fire-ish" surface, with some fire explosions and other details like that...and adding shadows to the bottom half of the planet is .. confusing? i know theres an option in filter>light and shadows but it doesnt allow a user to pick the area he wants to drop shadow on.
any tip concerning this and improving my work is welcome. i wanna learn gimp even tho im a newbie :P

btw AJB2K3 could you upload some of your newer stuff? :D

Looks way to shinny, in the Lighting effect option under Material, turn Shiny to 0 and play around with glowing, you shouldn't have a bright light on the planet like that.

Updated the tutorial to reflect this. :p

---

### Post by Half-Left on 2008-10-20
Some tips for making your planet look better.

1. Dont make your planet look shinny, since they are not.

2. Dont make your planet texture to bumpy, the reason being is because they are supposed to be the surface or maintains and from space they dont look very bumpy because of the distance.

3. Dont put your planet texture to near to the edge, either that or smooth, blur, fade it off, this give the planet a more rounded rather than flat look.

4, Make your planet light soft since the atmosphere gives off that type of light

5. Usually match your outside atmosphere glow colour with the planet colour and make it more softer with Gaussian blur. 

6. You can put a light shadow around the edge of the planet(Duplicate your glow, make it dark and cut the middle out with the selection tool) which helps it look more rounded at the edges.

---

### Post by GoFishy on 2008-10-20
Thats pretty cool. I been doing photoshop for awhile and just recently installed ubuntu on laptop. Will have to try it when i get home.

Thanks for the tips Half-Left!

By the way does GIMP update when you run those system updates in ubuntu?

---

### Post by smartboyathome on 2008-10-20
> **GoFishy said:**
> Thats pretty cool. I been doing photoshop for awhile and just recently installed ubuntu on laptop. Will have to try it when i get home.

Thanks for the tips Half-Left!

By the way does GIMP update when you run those system updates in ubuntu?

Not if you're on Hardy. It only updates to the latest version if you are on Ibex, due to how Ubuntu tries to keep things stable.

---

### Post by GoFishy on 2008-10-20
Yeah im on Hardy.

Easiest way to go about updating it?

---

### Post by lukjad on 2008-10-20
Thanks!

---

### Post by mrowth on 2008-10-20
> **GoFishy said:**
> Yeah im on Hardy.

Easiest way to go about updating it?

Download the .debs from [http://www.getdeb.net/release.php?id=3257](http://www.getdeb.net/release.php?id=3257)

---

### Post by AJB2K3 on 2008-10-21
I'm getting conflict messages with gnomevfs.

---

### Post by mrowth on 2008-10-21
> **AJB2K3 said:**
> I'm getting conflict messages with gnomevfs.
I see there's a typo in the control file of the GIMP deb: it "replaces" "gimp-gnoemvfs" -- yep, misspelled like that. I don't know if that's something to do with it. Can you remove "gimp-gnomevfs", then install the new GIMP packages? (Apparently you're supposed to install "gvfs-backends" for GIMP to use FTP, HTTP, etc.; don't trust me, though, on anything. I only ever use Kubuntu.)

---

### Post by GoFishy on 2008-11-03
how did you do the fire?

---

### Post by MaxIBoy on 2008-11-03
I've been using GIMP 2.6 for about 20 minutes now. The new window layout basically emulates what I had to do manually before (main GIMP window was set as "always on top" over the editor window) with fewer annoying side effects. What I've noticed is that there aren't many new features, but the output from the existing features is much more pretty. I'm getting very close to what I used to be able to accomplish with my old combination of paint.NET and Paint Shop Pro 6. 

20 minutes of work with the new GIMP is attached. The source pictures are here:
[http://www.jalna.com.au/Portals/11/grannysmith apple.JPG](http://www.jalna.com.au/Portals/11/grannysmith apple.JPG)
[http://www.ximtc.net/home/wp-content/uploads/2006/11/mushroom-cloud.jpg](http://www.ximtc.net/home/wp-content/uploads/2006/11/mushroom-cloud.jpg)

Obviously, my style of editing looks "painted" rather than "photoreal." I'm also not done: the apple's core needs seeds, the entire apple needs to ripple like a cloud, those jets need to be dealt with, the glow leaking out from behind my GIMPage needs to be dealt with.

Still missing is a way to view all layers separately and simultaneously in thumbnail form, which is one of the things I loved about paint.NET.

---

### Post by Half-Left on 2008-11-04
> **GoFishy said:**
> how did you do the fire?

Uses a brush that looks like a blast and made it glow and a real fire image.

---

