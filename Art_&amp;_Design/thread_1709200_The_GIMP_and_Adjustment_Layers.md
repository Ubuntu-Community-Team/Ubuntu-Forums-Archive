---
title: "The GIMP and Adjustment Layers"
date: 2011-03-17
forum: Art &amp; Design
---

### Post by Lucradia on 2011-03-17
It's been a while since we've seen any updates to the issue of GIMP having no adjustment layers. A bug I've been tracking for a while recently got an update:

[https://bugzilla.gnome.org/show_bug.cgi?id=79025](https://bugzilla.gnome.org/show_bug.cgi?id=79025)

Seems GIMP Team will be aiming to have it in version 3.2.

---

### Post by 23dornot23d on 2011-03-18
Looking forward to these .... adjustment layers ..... when is Gimp 3.2 scheduled to be released ?

---

### Post by prokoudine on 2011-03-18
> **23dornot23d said:**
> when is Gimp 3.2 scheduled to be released ?

Scheduled? With 0.5-3 developers?

---

### Post by 23dornot23d on 2011-03-18
How much of a the difference is there between copying the layer and creating the adjustment layers manually 
other than sliders for tone ranges ...... is there ..... ?

Looking at the way basic [Adjustment layers are used in Photoshop]("http://www.basicphotoshop.com/tutz/pstutz53.htm") - we can do this any how ..... just copy the layer and adjust to
suit then overlay and blend it (masks are no problem) ......... maybe more complicated steps to newbies but it can be done .....

Not sure if Gimp could go Qt based but from what I saw of what they did with ( Qcad )
Libre Cad ..... I am quite impressed ..... :o

I look forward to any improvements .... and realise there are only a handful of designers working on this ...... 
wish I could do more to help in some way ....... and am sure there are many others feel the same way too
did have a quick play with Qt once ...... but not sure how it could be integrated into Gimp ....

Called a QT menu I made once from blender ..... and it seemed to work ok ..... was just a test ......

Can Gimp do the same sort of thing ..... and how would we do the first steps ..... call it from a console menu
similar to in Blender ..... 

( To keep things in some form of order - [I need to know more]("https://sites.google.com/site/blenderlearn/assignments/project087") - will see if I can progress at some point with this)

If anybody knows how to integrate python into Gimp easily and has a good link to a good video tutorial ..... please post
it ......  ty

---

### Post by Lucradia on 2011-03-18
Photoshop makes it easier is all. Which is what I love about it. I don't like having to make an extra mask layer just for it.

---

### Post by prokoudine on 2011-03-19
> **23dornot23d said:**
> How much of a the difference is there between copying the layer and creating the adjustment layers manually 
other than sliders for tone ranges ...... is there ..... ?

Looking at the way basic [Adjustment layers are used in Photoshop]("http://www.basicphotoshop.com/tutz/pstutz53.htm") - we can do this any how ..... just copy the layer and adjust to
suit then overlay and blend it (masks are no problem) ......... maybe more complicated steps to newbies but it can be done .....

You are missing one huge thing that's the size of Texas. In Photoshop you can reopen the adjustment dialog and tweak changes you did before. In GIMP you have to remove the copied channel, create a new copy and do everything **once again**, **from scratch**, **by heart**. **Big** difference.

> **23dornot23d said:**
> If anybody knows how to integrate python into Gimp easily and has a good link to a good video tutorial ..... please post
it ......  ty

Python has already been integrated into GIMP. There's a dozen of Python scripts shipped with GIMP, and. I dare say, a couple of dozen of Python scripts at registry.gimp.org.

Not entirely up to date documentation is here: [http://www.gimp.org/docs/python/index.html]("http://www.gimp.org/docs/python/index.html")

---

### Post by 23dornot23d on 2011-03-19
> You are missing one huge thing that's the size of Texas. In Photoshop  you can reopen the adjustment dialog and tweak changes you did before.  In GIMP you have to remove the copied channel, create a new copy and do  everything **once again**, **from scratch**, **by heart**. **Big** difference.
Would like to see what you mean by this ...... in gimp I can copy all what I see and paste as a new layer ..... ( no redoing things )
Therefore there is no backtracking ....... you just keep moving forward with your edit.
( I hate doing things twice ..... my procedure is possibly different in Gimp to Photoshop )

If you have an example of what you are doing that you think I cannot do.

Post the original and the finished ..... and I will try to show how I would achieve the same
I am always willing to learn .......



I found a few things including the link you posted for Python ..... thank you for that though ...... [here is where I got to]("https://sites.google.com/site/blenderlearn/assignments/project087?pli=1")

---

### Post by prokoudine on 2011-03-19
> **23dornot23d said:**
> Would like to see what you mean by this ...... in gimp I can copy all what I see and paste as a new layer ..... ( no redoing things )
Therefore there is no backtracking ....... you just keep moving forward with your edit.
( I hate doing things twice ..... my procedure is possibly different in Gimp to Photoshop )

If you have an example of what you are doing that you think I cannot do.

I already gave you that example: being able to tweak changes at any time later. The description was quite clear. **Not** applying changes on top of the copy of original layer, **not** removing that copy and starting all over again, but **doubleclicking** and seeing the values you defined the previous time and tweaking them from where you left them. This is no rocket science really.

---

### Post by 23dornot23d on 2011-03-19
> 
This is no rocket science really.


I never said it was  - I asked for an example ....

If I cannot reproduce it easily using my methods ..... 

I may then understand why you believe its the size of Texas ,,,,,, I just do not see problems as big as the size of Texas yet ........ like you do ...... maybe it is rocket science for you.

---

### Post by prokoudine on 2011-03-20
> **23dornot23d said:**
> I never said it was  - I asked for an example ....

If I cannot reproduce it easily using my methods ..... 

I may then understand why you believe its the size of Texas ,,,,,, I just do not see problems as big as the size of Texas yet ........ like you do ...... maybe it is rocket science for you.

I find it extremely difficult to understand what you say.

Adjustment layers are a huge productivity booster. Anybody who ever used them can tell that being able to tweak changes immediately is much better than redoing it all with copies of layers. If explanations don't work for you, fetch a trial copy of Photoshop and have a look yourself :) Or use a copy of native Pixel build for Linux that has adj. layers as well.

---

### Post by 23dornot23d on 2011-03-20
> 
I find it extremely difficult to understand what you say.

**I asked for an example ....**






I will try to put it more clearly ..... post an example a photo .... a picture .....

Then post the modifications ...... that you think that I cannot achieve .....

Simple as ...........

____________________________________________________________________

or post a link to a XCF file with all the layers in it .......

or even a PSD file if all you use is Photoshop ...........

____________________________________________________________________

If this is too confusing or you have difficulty posting links or photos - I will help you do that.

as I do it on a regular basis , everyday [HERE]("http://www.photoforum.com/index.php?showtopic=66688&st=0&start=0")

---

### Post by prokoudine on 2011-03-20
> **23dornot23d said:**
> **I asked for an example ....**
I will try to put it more clearly ..... post an example a photo .... a picture .....
Then post the modifications ...... that you think that I cannot achieve .....

What? Ever? For?

You have a project with several layers. You want you tweak curves for all of them. So you group them in one layer group and add an adjustment layer with curves. You tweak curves, export to JPEG or TIFF and give it to someone. If that someone tells you that you should have gone easier on highlights, you just reopen that PSD, double-click on the adjustment layer and tweak just one node. That's all.

To adjust changes done in GIMP before, right now you would have to

1) Use "Create from visible' all the time
2) After reopening — delete or make invisible the layer with changes
3) Create a new layer from visible
4) Reconstruct the curve you were editing from scratch or, in case of 2.7, try to figure out which one in the automatically saved one is the one you need.

I already explained that before. What do you need a picture with example for?

---

### Post by 23dornot23d on 2011-03-20
You have now explained it in more detail and your explanation makes more sense .... now.

Thank you for taking the time out to explain it ......

But to me the only person I am trying to please is me .... when I do an edit .... 

I rarely need to go back and re alter things to suit someone else .....

This is good if you are a professional wanting to please a client ....... and then having to go back and re-do things because they 
were not done to the other persons satisfaction.

This is no big deal for me........ and is definitely not the size of Texas ........

But I thank you for your time ....... and will look forward to seeing how they help me in the future ...... :D

---

### Post by Cranio on 2011-03-22
Dear sir,

you are underestimating the importance of adjustment layers.

It's the *way* you work with the image that becomes completely different.

- It's easier to tweak every adjustment
- You can try and compare on the fly different adjustments to see which is better without saving/loading/undoing/redoing

Most of all: 

 **You can stack different adjustment types** (ex. "Levels" underneath a color adjustment), and **you can tweak any adjustment at any level of the stack**, and when you come to many levels of adjustment with selection mask, the difference in workflow is HUGE,

Let's say I have an image: i correct the Curves (1) and then Colors (2) and then select a part and make it Grayscale (3). 

**Without** adjustment layers, you have to rebuild the whole chain: UNDO Grayscale, storing the selection mark in some way, UNDO Colors, TRY to remember settings or write them, UNDO Curvers, REAPPLY Curves, REAPPLY Colors, RESELECT mask, REAPPLY Grayscale

**With** adjustment layers: Simply change curves settings :)

---

### Post by 23dornot23d on 2011-03-22
Thank you for the reply .....
[B]
As I already said I will look forward to the adjustment layers  .[/B].....

At this moment in time I am not having to re-adjust or change anything as I work
 ...... and if I undo something its only the last thing I did . 

Why would I need to undo everything to apply a curve to one layer at the bottom of the stack ........ unless of course I made a bad judgement when doing something at the start ..... In which case they may be handy ...... but I would have been failing to do my job properly if I missed something early on.

As of this moment in time I have never needed them and if it is such a HUGE problem to my workflow ........ then my workflow would be slow and awkward .

At this present time my workflow is smooth and fast ....... and I really enjoy editing photos.

**If adjustment layers adds to my enjoyment and makes my workflow so much easier - then I may well revisit this thread and then thank you for pointing out what I am missing.**

( It does feel a little like a guy pulling up next to me in a Porsche and saying look if you had a car like mine you would have all this extra luxury ...... 
But the point is - my vehicle still gets me from A to B ..... and whether or not all that extra luxury is needed is another matter .  )

I am pretty sure that you use Photoshop as you seem to know all about what adjustment layers can be used for ...... as Gimp does not have them at this present time ........ but as I said its no real problem to me.

**But I will look forward to them ........ **

---

### Post by Cranio on 2011-03-22
> **23dornot23d said:**
> Thank you for the reply .....
[B]
As I already said I will look forward to the adjustment layers  .[/B].....

At this moment in time I am not having to re-adjust or change anything as I work
 ...... and if I undo something its only the last thing I did . 

Why would I need to undo everything to apply a curve to one layer at the bottom of the stack ........ unless of course I made a bad judgement when doing something at the start ..... In which case they may be handy ...... but I would have been failing to do my job properly if I missed something early on.

Yeah, I think it's fair and I'm non stating at all that you work in a *wrong* or otherwise unuseful way. If it seemed like that I apologize, sir :)

But I still don't agree at all on what you are saying.

Sometimes, you just *have* to tweak values afterwards, it's not necessarily a sign of bad workflow or bad judgement or a bad job. Expecially in cases in which *many* layers have a sort of influence one on the other.
Or in cases (very common in basic photo-retouching) in which you have to tweak adjustments *and* masks.

Main things is, it is a sort of **philosphy**, an evolution of the way we work with things called **non-destructive editing** (f.ex., average-to-advanced audio and video recording software work *ALL* also with this kind of paradigm).

> As of this moment in time I have never needed them and if it is such a HUGE problem to my workflow ........ then my workflow would be slow and awkward .

At this present time my workflow is smooth and fast ....... and I really enjoy editing photos.

**If adjustment layers adds to my enjoyment and makes my workflow so much easier - then I may well revisit this thread and then thank you for pointing out what I am missing.**

( It does feel a little like a guy pulling up next to me in a Porsche and saying look if you had a car like mine you would have all this extra luxury ...... 
But the point is - my vehicle still gets me from A to B ..... and whether or not all that extra luxury is needed is another matter .  )

Not quite, it's more like ... geez I hate those parallellisms :) ... like when you work wood and have to sand by hand, then a guy shows up and tells "hey man, you woodwork is really nice and good, and you seem expert in what you do and I'm sure you're really good at it, but how about giving a try to this set of electric sanding machine?", and imagine a set of machines that makes you work smoother and faster and less prone to errors and with more creative possibilities that can be tried in a very fast way.

Point is, with GIMP we could have those set of sanding devices for *free* :)

Please don't misunderstand, I'm just trying to explain the enormous benefits of this technique/feature, I'm not bashing your knowledge or skills in any way or trying to convince you :)

---

### Post by 23dornot23d on 2011-03-22
Thanks ....

I can see that you were being helpful now ..... and one thing that I did pick up from what you said earlier that is quite important is being able to judge any difference between how we change something compared to the original work - or even between layers if we save as I do - every so often I take a snapshot and keep it as a layer,

( The way I have learned to work with Gimp - could be compared to always keeping something to fall back to at a earlier stage of the edit ..... if you do need to recover something ..... so I never lose the possibility of dropping back and altering things - should I need to. - this is done by creating a copy of everything visible at certain stages through the edit ... usually where you do major alterations ..... and you might want to step back and try it a different way ...... the way I work means you can still do this )


What I would like to see as well is a Split screen half and half ..... half showing the original work and half showing the modification.
( at the moment with gimp you can have two windows open and see it especially if you have a dual screen its more helpful ) 

Now that to me would be handy for most users  ..... as well as the Adjustment layers , I do look forward to seeing what they can do.

I will check for a plugin .... it always amazes me with Gimp .... what else is available.


There are lots of addons that are not initially seen by the people - who do not use Gimp on a regular basis.


When I first started using Gimp with only the basic menu - I saw no real worries about things being complex and even felt that maybe Gimp was not that powerful a tool  ..... but when you download such as [Mathmap]("http://www.complang.tuwien.ac.at/schani/mathmap/") the nodes addon - plus the [GMIC set of tools]("http://gmic.sourceforge.net/gimp.shtml") .... [FxFoundary]("http://registry.gimp.org/node/13661") ... [SriptFu]("http://registry.gimp.org/taxonomy/term/20") ....... then it becomes quite a different animal ......

I have also picked up many other scripts along the way .... adjustment layers is not one that I have seen - but there are others like difference layers .....
Also one for layer groups which I believe to be similar to photoshop in some respects ...... and PSPI for paintshop plugins like GMLmatting  so it does end up being quite a powerful tool.

If you like art like I do and have a wacom or G-pen you can also load up GPS Gimp Paint Shop .... which does alter it quite a bit ..... but this is
towards Arty things more than photoshop .....

What happened with me was I work alongside someone that uses Photoshop .... and the way it as worked is I try to reproduce anything that he can produce ..... if that means going and finding addons to do it then I have done it - but in the long process of doing this over the last few years , there is little I feel would worry me.

[B]And as I said earlier I really do enjoy working with photos and editing ..... so all in all to me its not work but fun ......
[/B] 
But thank you for the kind words and nice reply ..... as I say I will look forward to the adjustment layers , maybe it will be like a power sander when I get it .......

But I have also seen what a Power sander can do in the wrong hands ...... where a block and a piece of sandpaper has been quite adequate ...... and destroyed less of that fine finish when the user makes a slip in the wrong direction with it ........

Ok its been interesting reading your reply and hopefully I will get some enormous benefits 
from the adjustment layer feature once it has been added. 

Thank you ....

---

### Post by Cranio on 2011-03-22
> **23dornot23d said:**
> Thanks ....
Can see that you were being helpful now ..... and one thing that I did pick up from what you said earlier that is quite important is being able to judge any difference between how we change something compared to the original work - or even between layers if we save as I do - every so often I take a snapshot and keep it as a layer,


Right. Also, by undoing or taking snapshot, you often lose the perspective on very subtle changes that can make your work really outstanding.

Second things, these special layers can be grouped... very handy to toggle them on/off or create variations to compare.

> 
( The way I have learned to work with Gimp - could be compared to always keeping something to fall back to at a earlier stage of the edit ..... if you do need to recover something ..... so I never lose the possibility of dropping back and altering things - should I need to. - this is done by creating a copy of everything visible at certain stages through the edit ... usually where you do major alterations ..... and you might want to step back and try it a different way ...... the way I work means you can still do this )


And that was the way I always worked with Photoshop (and the way I work now with gimp) before discovering the whole thing.

There is also another *very important* issue: every color alteration can produce a slight reduction of the number of the colors in the image. So if your images come with 8-bit color information, **applying** every adjustment (as in GIMP) could lead to worse results than **calculating** dinamically these adjustment in a more broad color space in your RAM.

> 
What I would like to see as well is a Split screen half and half ..... half showing the original work and half showing the modification.
Now that to me would be handy  ..... as well as the Adjustment layers , I do look forward to seeing what they can do.
I will check for a plugin .... it always amazes me with Gimp .... what else is available.
There are lots of addons that are not initially seen by the people - who do not use Gimp on a regular basis.


Yeah and I'm, still discovering the whole potential of the program as an ex PS user.
But a feature such as the adj. layers pertains to the very core of the software, so I hope to see this implemented soon to totally abandon Photoshop.
I feel really that GIMP misses that only things to be really competitive.

> 
Ok its been interesting reading your reply and hopefully I will get some enormous benefits 
from the adjustment layer feature once it has been added. 
Thank you ....

Thanks to you, you're welcome :)

---

### Post by 23dornot23d on 2011-03-22
> 
There is also another *very important* issue: every color  alteration can produce a slight reduction of the number of the colors in  the image. So if your images come with 8-bit color information, **applying** every adjustment (as in GIMP) could lead to worse results than **calculating** dinamically these adjustment in a more broad color space in your RAM.

You have hit the nail on the head here  ..... the 8 bit editing in Gimp is its main draw back.
I did not realise it degrades while adjusting from layer to layer ,,, though as this is still in memory ...... are you sure about this ?

It definately does if you go from JPG to JPG .... but we save as XCF to stop them degrading.
My final save is always as a JPG for posting on the web though .... even photoshop has to do this .... to keep the filesize low for the forum limits.

Once they change this I would feel confident to compete with anyone .... and I am sure that with time this will come .... GIMP V3.0 is when it happens ...

Here is what the Gimp menu looks like with the additional addons and  things I use .....

[IMG]http://img806.imageshack.us/img806/8955/gimpmenus800.jpg[/IMG]

Obviously its more important what options are in the drop downs for each one ......... but there are a lot of good ones now .....

I just hope that the developers retain them in the new version .......

---

### Post by Cranio on 2011-03-22
> **23dornot23d said:**
> You have hit the nail on the head here  ..... the 8 bit editing in Gimp is its main draw back.
I did not realise it degrades while adjusting from layer to layer ,,, though as this is still in memory ...... are you sure about this ?

It definately does if you go from JPG to JPG .... but we save as XCF to stop them degrading.
My final save is always as a JPG for posting on the web though .... even photoshop has to do this .... to keep the filesize low for the forum limits.

Once they change this I would feel confident to compete with anyone .... and I am sure that with time this will come .... GIMP V3.0 is when it happens ...

Yes but I was talking about a different and more subtle issue, just have a look here, when it comes about "banding", it explains well what happens:

[http://www.photoshopessentials.com/photo-editing/adjustment-layers/]("http://www.photoshopessentials.com/photo-editing/adjustment-layers/")

---

### Post by 23dornot23d on 2011-03-22
Ok thanks for posting that , I want to check what GEGL actually does , as that is what will be used in GIMP .....

[B]

The result is what matters ...... as soon as 16 bit comes we will see then how much detail we lose .......

I am obviously loosing some along the way anyhow ..... reading it in ..... it goes to 8 bit straight away .......
( editing it and blending the edit back with the original at the end possibly puts back what was lost along the way )
depending on how severe the edit was ....... if things have been removed then this will not work .... 
putting it out as a Jpeg degrades it too ........ ( only the first can be avoided as we can output png or xcf or tif )

The results still look good to me ...... be glad if they can be improved though .......

[/B]

I have just realised something here - something very useful as come from this .......

1 ...... The original image ........ 16 bit .........

2 ...... The image is pulled into GIMP .... straight away it is converted to 8 bit ...... ( lost some image information here )

3 ...... We go through the image editing process - ( possibly loses some more information along the way )

4 ...... We can then save it as a EDIT.PNG file here ...... ( no blending with the original here as I would normally do )

5 ...... We open the EDIT.PNG in Cinepaint ...

6 ..... We then open the original photo in Cinepaint and do the last stage of the blend here ....... overlay multiply - whatever
at this point we should regain a lot of the data we destroyed ........in the 2nd step .......


Will try this on the next edit I do and see if it makes a difference ...... at least its one more option till we get full 16 bit or better editing.

[COLOR=Red][B]The only reason I do not use cinepaint all the way through is that it does not have all the plugins available ...... 
if I could make them work with it, then I would use that - although the windowing system for it is a bit dated .... 
the editing still works ok.
 
[/B][/COLOR]

---

