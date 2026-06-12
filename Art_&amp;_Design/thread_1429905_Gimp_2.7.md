---
title: "Gimp 2.7"
date: 2010-03-14
forum: Art &amp; Design
---

### Post by alex4c on 2010-03-14
I was wondering if anyone uses this unstable version?
If you do what do you think about it? 
Single window mode?
Layer groups?
Paint dynamic editor? I didn't quite get that one yet. Can't change anything in mapping matrix.

---

### Post by VeeDubb on 2010-03-14
I seriously considered it, but every time I've used a development version of the gimp, I regretted it.  There always ends up being annoying compatibility issues with my favorite plugins, and weird partially implemented new features.

If every release was like that, it would be no big deal.  But, it's only the dev releases.  The GIMP team is really fantastic, and always seems to put out really solid releases when they're ready. So basically, I've found that it's just better to wait.

---

### Post by Minipalmer on 2010-03-15
I have not tried it yet, but I'm excited for it.

---

### Post by Merk42 on 2010-03-15
> **Minipalmer said:**
> I have not tried it yet, but I'm excited for it.

Don't get too excited, it's not due out for over a year from now

---

### Post by Minipalmer on 2010-03-15
> **Merk42 said:**
> Don't get too excited, it's not due out for over a year from nowStill. :D

I've been standing by Gimp for a long time overlooking its flaws. And now they're finally being addressed. Yeeesssssss.

---

### Post by temenex on 2010-03-15
Gimp 2.7 is very good. :D

sudo add-apt-repository  ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update
sudo apt-get install gimp

---

### Post by alex4c on 2010-03-15
Some people don't like new save and export options.
You can't save file as .jpg, .png or other non gimp file formats. You can only save as .xcf, .xcfbz2, .xcfgz. But you can export file as .jpg, .png .tif etc. There is option if you open (for example) .jpg retouch it and want to save also in .jpg format to overwrite that file instead of exporting it. 
I don't mind this new option, actually I find it helpful.

---

### Post by VeeDubb on 2010-03-15
> **temenex said:**
> Gimp 2.7 is very good. :D

sudo add-apt-repository  ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update
sudo apt-get install gimp

That's excellent.  I've only ever used testing versions of gimp by installing manually from their site.  Using that PPA seems to have avoided all of the problems with gimp testing versions I've had in the past.

Thank you.

---

### Post by cubeist on 2010-03-15
I am using a version from git (haven't pulled in a few weeks though) and use it everyday.  It is fairly stable, but remember to save early and save often!

The single-window mode is great and now that I am familiar with it, I can't go back to 2.6.  It is especially useful when you have a dozen images open, each one has its own tab instead of sifting through 12 open windows.  This is a nice clean workflow change.

I also like the save/export change. For a quick edit I open an image then overwrite and I'm done, for a larger edit or project I save the xcf until I am done, then I export in the format I want.  I think this workflow is enhanced, but your mileage may vary.

Also, if you use many 2.6 plugins, 2.7 from git probably isn't the best idea.

---

### Post by alex4c on 2010-03-16
Yes, it is fairly stable. I had only one crash which I think wasn't caused by Gimp. But I save constantly. 
I use Gimp mostly for painting so I don't need lots of plugins. Actually the only think I use is GIMP Paint Studio and it works fine with 2.7. New paint dynamic editor is interesting.

---

### Post by philiboy on 2010-03-16
if you want to test the features of  GIMP 2.7, you can try to install it from a developement repository, just  follow the steps bellow if you want to install it on Ubuntu 9.04 and  ubuntu 9.10 :

1- First open the source list file :
 **sudo gedit /etc/apt/sources.list** 
Add the following repository to /  etc / apt / sources.list if used

For ubuntu 9.04 Jaunty  Jackalope add the following line :

 **[http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) jaunty main deb** 
For ubuntu 9.10  karmic koala add  this line :
 **[http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) karmic main deb** 
2- Now add the public key:
 **sudo apt-key adv - recv-keys - keyserver keyserver.ubuntu.com 405A15CB** 
3- Update the repos and packages:

 **sudo apt-get update & & sudo apt-get upgrade** 
4- If the GIMP open gives an  error then do this
 [B]sudo apt-get install libgegl-0.0-0

[/B] I  tested this on ubuntu 9.10 karmic  koala and is working fine.

---

### Post by cubeist on 2010-03-17
Or install directly from Git yourself using these instructions.
[http://www.gimpusers.com/news/2009-10-14/compiling-gimp-27-git-ubuntu-904-910.html]("http://www.gimpusers.com/news/2009-10-14/compiling-gimp-27-git-ubuntu-904-910.html")

I would advise caution to adding an untrusted PPA to your system.  Sorry, philiboy, but with only one post here...

---

### Post by JoZ3 on 2010-03-19
How can I leave the single window mode for default?. Whenever I open the Gimp the single window mode disappear.

I have the Gimp 2.7 installed from the repository.

tnx :D

---

### Post by cubeist on 2010-03-19
> **JoZ3 said:**
> How can I leave the single window mode for default?. Whenever I open the Gimp the single window mode disappear.

I have the Gimp 2.7 installed from the repository.

tnx :D

This is a quirk of the development build.  I think the developers know about it...no resolution available though.

Keep an eye on the git log and you can see when it is fixed
[http://git.gnome.org/browse/gimp](http://git.gnome.org/browse/gimp)

---

### Post by Fzang on 2010-03-20
Is there a pre-release available for Windows as well?

---

### Post by Minipalmer on 2010-03-26
Ah this is *excellent*! It's what I've always wanted!

Anyone know if there's a way to get rid of the permanent scrollbars? I don't use them with my tablet anyway.

[IMG]http://i42.tinypic.com/zvo6s7.png[/IMG]

---

### Post by thekanuk on 2010-03-27
I was going to wait but it looks tempting. ;) I think I'll give it a try.

---

### Post by cubeist on 2010-03-28
> **Minipalmer said:**
> Ah this is *excellent*! It's what I've always wanted!

Anyone know if there's a way to get rid of the permanent scrollbars? I don't use them with my tablet anyway.

[IMG]http://i42.tinypic.com/zvo6s7.png[/IMG]

View > Show scrollbars (temporary change)
or in preferences window, uncheck show scrollbars.

---

### Post by cubeist on 2010-03-28
I am back to 2.6.7.  2.7 works fine unless you want to use Gimp Paint Studio brushes.  Somehow every time I select a preset it forgets the dynamics.  I think the dynamics system in 2.7 is a regression.  I liked being able to quickly set them from the tool-options menu.

If anyone has a work-around, please share!

---

### Post by alex4c on 2010-03-29
> **cubeist said:**
> I am back to 2.6.7.  2.7 works fine unless you want to use Gimp Paint Studio brushes.  Somehow every time I select a preset it forgets the dynamics.  I think the dynamics system in 2.7 is a regression.  I liked being able to quickly set them from the tool-options menu.

If anyone has a work-around, please share!

You can make your own dynamics in Paint dynamic editor. Then you can select it in Paint dynamic menu.

---

### Post by cubeist on 2010-03-30
> **alex4c said:**
> You can make your own dynamics in Paint dynamic editor. Then you can select it in Paint dynamic menu.

True, and the dynamic editor is cool, lots of choice and flexibility.  The problems is you cannot link a dynamic with a particular brush preset.  But, I am sure this is on the developer's todo list.

---

### Post by bvraghav on 2010-07-08
> **alex4c said:**
> Some people don't like new save and export options.
You can't save file as .jpg, .png or other non gimp file formats. You can only save as .xcf, .xcfbz2, .xcfgz. But you can export file as .jpg, .png .tif etc. There is option if you open (for example) .jpg retouch it and want to save also in .jpg format to overwrite that file instead of exporting it. 
I don't mind this new option, actually I find it helpful.


of course... and sounds logical too... great going :)

---

### Post by bvraghav on 2010-07-08
> **temenex said:**
> Gimp 2.7 is very good. :D

sudo add-apt-repository  ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update
sudo apt-get install gimp
haha... i have spent about 20 hrs idle - figuring out how to build from source code and fill in the gaps for dependencies!!! 

this piece of information comes like a saviour... :)

thanks

---

### Post by libertypo on 2010-07-08
Using 2.7.3

Other then the ridiculously large amount of time to start and that it sucks almost all my ram and swap (have a lot of resources also), seems alright so far. I would like badly some sort of dynamically loading of the resources instead of loading everything at every start.

---

### Post by Half-Left on 2010-07-08
> **libertypo said:**
> Using 2.7.3

Other then the ridiculously large amount of time to start and that it sucks almost all my ram and swap (have a lot of resources also), seems alright so far. I would like badly some sort of dynamically loading of the resources instead of loading everything at every start.

The dev version will be slow and it is. Adobe Photoshop doesn't start fast either and as I remember, like The GIMP, it loads up brushes on start-up. Though five seconds is hardly slow.

---

### Post by psoulocybe on 2010-07-08
Been using 2.7 for about a month.
Have had a couple crashes, but nothing terrible.
I've stuck with it for development as it's been stable enough and I'm loving the dynamic brush settings.

---

### Post by libertypo on 2010-07-08
> **Half-Left said:**
>  Adobe Photoshop doesn't start fast either and as I remember, like The GIMP, it loads up brushes on start-up. 
 
That's why I said that **I would like some sort** of dynamically loading of the resources

---

### Post by curuxz on 2010-12-08
Just to add my 2 cents to this...

Single window mode sucks, terrible idea for graphic professionals using multiple monitors and I question why they are spending time on interface changes when...

Selection is mind numbing unusably slow. If I am working on a big file in the dev version then my machine (which is very good) grinds to an unusable halt. It seems to be something with the new selection tool that makes the program seize up, it is certainly nothing I have seen in previous gimp versions and despite a few new releases of the dev version it remains unfixed.

Worst part about the new version is this save/export/overwrite nonsense which I understand is for people too stupid to realise that they are saving in flat jpg etv rather than layered XCF. What a complete waste of time and effort that makes work-flow for web designers and photographic editors (which dip in and out of lots of little files, or work on single flat large images) really irritating. 

Word to the wise for gimp devs, if your going to add something so irritating...make it optional. You don't see the people making open office putting all the microsoft formats in export only then every time you press save going back to ODT. They dont do it because it would be stupid, and waste time. Gimp developers clearly only want to increase XCF users which is not really playing fair on those people that have used Gimp for the last 5-6 years like my self and want to chose my self when to use XCF and when to work in JPG or PNG.

---

### Post by prokoudine on 2010-12-08
> **libertypo said:**
> That's why I said that **I would like some sort** of dynamically loading of the resources

The best you can get right now is -d argument that disables loading of all assets. They start loading whenever you try to use any. This option has been around for quite a while.

> **curuxz said:**
> Single window mode sucks, terrible idea for graphic professionals using multiple monitors and I question why they are spending time on interface changes when...

Because not everybody thinks that SW mode sucks?

> **curuxz said:**
> Selection is mind numbing unusably slow. If I am working on a big file in the dev version then my machine (which is very good) grinds to an unusable halt. It seems to be something with the new selection tool

There are no new selection tools in 2.7. Which tool do you refer to?

> **curuxz said:**
> Worst part about the new version is this save/export/overwrite nonsense which I understand is for people too stupid to realise that they are saving in flat jpg etv rather than layered XCF.

And I thought *I* was agressive... Go get a bit of fresh air, mate.

Making things up is not a sin as long as you don't try to speak for people who did not grant you the right to do so.

[http://gui.gimp.org/index.php/Save_%2B_export_specification](http://gui.gimp.org/index.php/Save_%2B_export_specification)

> **curuxz said:**
> Word to the wise for gimp devs, if your going to add something so irritating...make it optional.

Things like this cannot possibly be optional. They are part of workflow.

> **curuxz said:**
> Gimp developers clearly only want to increase XCF users

I wish you could put your rich imagination to a better use.

---

### Post by curuxz on 2010-12-08
It really does seem boring that no one can even discuss this without being labelled as some kind of mad group of malcontents. Nothing is impossible in programming regardless of it being part of 'workflow' it was a choice they made, which they could have made an option along the lines of a checkbox in the config saying "do you want to lock save to XCF only?" or "do you wish to combine save and export", that would have been the easy sensible way forward.

Single window mode does not add anything, only take away from the ability to mix easily between gimp windows and other programs, thank god they made that optional.

The selection tool is the standard select box, it has some serious performance issues that spike system usage when run on big files (esp when video files are also playing at the same time).

I don't understand what you mean by speaking for people I am not entitled to speak for? I am entitled to speak my views on this and never claimed to be doing anything otherwise. To date no one has given any justification for the save/export thing except for saying that it is to stop people 'accidently' saving in a compressed or flat format. That in my book is pandering to the stupid and breaking work flow. Any program...and I mean any program....you expect when you open a file, then press save it saves the file. Like I have said before you dont see open office forcing save to only do ODT.

What annoys me is that gimp with 2.7 has some really great features but at the same time they have actively and deliberately broken the workflow and every-time this has come up on forums, blogs, dev sites etc people like me (who use gimp for at least 2-3 hours per day for work) are shouted down and given no option but to use the new clunky workflow and that costs me time and time costs me money. People get aggressive when they lose their money and yes I know I could fork etc etc but it is so much hassle for the sake of the devs just putting in check box like they did with single window mode.

While I am out having my breath of fresh air, why don't you explain to the rest of us how breaking the save workflow that has been in use for over 10 years adds any improvement whatsoever to GIMP.

I am really not trying to rant, but this kinda thing really gets to me, it is such a waste of good efforts and while you guys running it as a test may love the new 'feature' of having to manually click export every time you want to save something I assure you that once this becomes the default for all gimp users there are going to be a lot of new people who quite rightly ask why gimp does this and what have we gained from this other than more people using XCF.

> **prokoudine said:**
> The best you can get right now is -d argument that disables loading of all assets. They start loading whenever you try to use any. This option has been around for quite a while.



Because not everybody thinks that SW mode sucks?



There are no new selection tools in 2.7. Which tool do you refer to?



And I thought *I* was agressive... Go get a bit of fresh air, mate.

Making things up is not a sin as long as you don't try to speak for people who did not grant you the right to do so.

[http://gui.gimp.org/index.php/Save_%2B_export_specification](http://gui.gimp.org/index.php/Save_%2B_export_specification)



Things like this cannot possibly be optional. They are part of workflow.



I wish you could put your rich imagination to a better use.

---

### Post by idealflame on 2010-12-09
I have to agree, for the most-part, with curuxz here.

Whilst theoretically a good idea for people who don't know their PNG from their HTTP, the save/export functionality disambiguation is quite jarring for those of us power-users who have to work on large numbers of non-XCF files. It's curious; I see that the majority of posts say this is a good idea because "the spec says" or "it makes sense", but I have yet to hear anyone say they actually /like/ the separate export 'feature'.

The single-window mode I don't personally like because it's not a paradigm that works in the multi-monitor world, but I can see why others would - especially with multiple desktops: it's a lot easier to move a single window across desktops than many windows (which I've had to do a couple of times)

However, I don't actually notice any performance degradation with the selection tool (At least, not on 2000x2000px images @300dpi on 2.7.1), so I don't know if there's a universal problem there (I doubt that that I run Debian makes a difference here...). My only problem is when they introduced the whole "You have to press enter to close a freehand selection loop" thing, my request to at least be optioned of which was shot down quickly :\


Anywho, those're my two pennies worth. For all its faults, I do love the GIMP; I was only here 'cause I'm trying to find the oft-quoted 2.7.3 source that apparently fixes the "export to gif" error in 2.7.1 :S

---

### Post by prokoudine on 2010-12-09
> **curuxz said:**
> It really does seem boring that no one can even discuss this without being labelled as some kind of mad group of malcontents.

Oh, it surely isn't boring. The way you make things up as you go makes it actually quite fun. If you ever tried to properly analyze things and not jump at conclusions — now *that* would be boring. Correct, proper, but boring :)

> **curuxz said:**
> Nothing is impossible in programming regardless of it being part of 'workflow' it was a choice they made, which they could have made an option along the lines of a checkbox in the config saying "do you want to lock save to XCF only?" or "do you wish to combine save and export", that would have been the easy sensible way forward.

Nobody's talking about "impossible". The question is what is a good thing to do in the long run.

> **curuxz said:**
> Single window mode does not add anything, only take away from the ability to mix easily between gimp windows and other programs, thank god they made that optional.

Of course it adds. It adds lack of clutter :) Especially for our mates on Windows who happen to dominate GIMP's userbase.

> **curuxz said:**
> The selection tool is the standard select box, it has some serious performance issues that spike system usage when run on big files (esp when video files are also playing at the same time).

Never seen this. But chances are that you are using ATI drivers, and there seems to be something going wrong there.

> **curuxz said:**
> To date no one has given any justification for the save/export thing except for saying that it is to stop people 'accidently' saving in a compressed or flat format.

No, what actually happens is the dialog that looks like this:

— I don't understand why you did it
— Here is a document that explains it, in details
— I don't care about no document, explain!
— It's already explained, go read up
— No, explain!

When I look at this, the word "childish" comes to mind.

> **curuxz said:**
> What annoys me is that gimp with 2.7 has some really great features but at the same time they have actively and deliberately broken the workflow and every-time this has come up on forums, blogs, dev sites etc people like me (who use gimp for at least 2-3 hours per day for work) are shouted down and given no option but to use the new clunky workflow and that costs me time and time costs me money.

You are not shouted down. But right now you are arguing against someone who happens to use GIMP on daily basis for work several hours a day and actually likes the change.

Once again. GIMP is moving towards becoming hi-end tool suited for work on complex multilayered images where you do save XCF. Every time. The introduced distinction between save and export is also the first step to streamline saving for web, exporting to CMYK and so on. The suggested workflow is: create everything in GIMP the way it looks best, then adapt it to any media (web, print, etc.) by means of exporting, keeping original data intact.

Moving to this new workflow involves a lot of internal changes and makes the old workflow very difficult to support, especially with only 2.5 developers around. Even if it was supported somehow, it would be a crude hack that nobody would like to maintain. Craftsmen hate crude hacks.

> **idealflame said:**
> I see that the majority of posts say this is a good idea because "the spec says" or "it makes sense", but I have yet to hear anyone say they actually /like/ the separate export 'feature'

Yes, I do like this separation. Even more, I'd like it to be used in Inkscape as well. We actually had a GSoC project on that this year, but it failed — the student disappeared.

> **idealflame said:**
> My only problem is when they introduced the whole "You have to press enter to close a freehand selection loop" thing, my request to at least be optioned of which was shot down quickly :\

You don't need pressing Enter. When you bring mouse pointer close enough to starting point, the selection closes itself. Try it :) Works for me on a week old build from Git master.

> **idealflame said:**
> I was only here 'cause I'm trying to find the oft-quoted 2.7.3 source that apparently fixes the "export to gif" error in 2.7.1 :S

Er.. What error?

---

### Post by robert shearer on 2010-12-09
@prokoudine> Of course it adds. It adds lack of clutter Especially for our mates on Windows who happen to dominate GIMP's userbase.

 an open source application being  developed primarily for a closed source user-base  ?? Is this your implication...?  Curious ):P

 What a strange and wondrous world we live in ..:)

---

### Post by DMKryl on 2010-12-09
> an open source application being developed primarily for a closed source use-base ??

So if i use windows i don't have the right to use an open source app?

---

### Post by robert shearer on 2010-12-09
@DMKryl> So if i use windows i don't have the right to use an open source app?

Read my post again. Never said nor implied **your** construction.

A large user-base can only be beneficial for long term growth and development.

merely looking for clarification of prokoudine's post that seemed to indicate the  development path was to accommodate  > our mates on Windows  
as I posted (I am) curious.:)

---

### Post by curuxz on 2010-12-09
> **prokoudine said:**
> Oh, it surely isn't boring. The way you make things up as you go makes it actually quite fun. If you ever tried to properly analyze things and not jump at conclusions — now that would be boring. Correct, proper, but boring


This seems a little on the immature side of dealing with criticism, I have not made anything up and while I would be the first to admit (as I did in my last post) that I may sound a little peeved this is only because I love working with GIMP and the recent changes are concerning to say the least. I have properly analyzed the situation and my opinion (again have not stated it as anything otherwise) is that these changes are not only unnecessary but actually are very counter productive and counterintuitive.

> **prokoudine said:**
> 
Nobody's talking about "impossible". The question is what is a good thing to do in the long run.


"Things like this cannot possibly be optional. They are part of workflow." to quote....you. Something that is described as 'cannot possibly' could also be said to be 'impossible' hence in response to you saying nobody is saying it is impossible, I would refer you to your own quote. I was merely stating that nothing "cannot possibly" be done in programming, within the laws of physics...

> **prokoudine said:**
> 
Of course it adds. It adds lack of clutter Especially for our mates on Windows who happen to dominate GIMP's userbase.



I am not even going to begin to comment on how bizarre it is to even suggest that you are altering a flagship linux package to suit the windows port users but I must say I accept that there is the clutter argument. But for something that is hyped quite a bit it is a rather minor addition. However like I said previously they did make it optional which I think is fantastic, would just have been nice to extend that same open minded thinking to the save/export system.


> **prokoudine said:**
> 
Never seen this. But chances are that you are using ATI drivers, and there seems to be something going wrong there.



Yeah I am using the official ati drivers and I am sure that has an effect on it. Very frustrating because while it does not exist in previous versions of GIMP I do not want to roll back and lose layer groups which is a life saver in my line of work. Hope this is something that ATI fixes and not a bug that will stay in the GIMP end of things. I am not experienced enough in the programing that GIMP uses to figure who out of GIMP and ATI is at fault.

> **prokoudine said:**
> 
No, what actually happens is the dialog that looks like this:

— I don't understand why you did it
— Here is a document that explains it, in details
— I don't care about no document, explain!
— It's already explained, go read up
— No, explain!

When I look at this, the word "childish" comes to mind.


Again not really sure calling me childish demonstrates the greatest maturity on your own part but aside from that I disagree strongly with how you describe my thought process. I am saying...

- I don't understand what this adds?
- Thanks for the document, read it....still cant see any benefit (certainly not one big enough to explain the workflow break)
- I wish you guys had thought this through a bit more, any chance of changing it?
- Oh ok I understand, this is the only possible way it can work and anyone who disagrees can go live in a cave
- Goes to live in cave, still trying to wonder why no one could cite a benefit/necessity of the new procedure.


> **prokoudine said:**
> 
You are not shouted down. But right now you are arguing against someone who happens to use GIMP on daily basis for work several hours a day and actually likes the change.


To be fair you have called me childish and not given a single good reason for the changes other than you 'like them' and that they help windows users. This is the same response I have received or seen others receive across the discussion and in my book the lack of discussion on this change or willingness to make it optional change is shouting down, but I guess thats just my opinion.

> **prokoudine said:**
> 
Once again. GIMP is moving towards becoming hi-end tool suited for work on complex multilayered images where you do save XCF. Every time. The introduced distinction between save and export is also the first step to streamline saving for web, exporting to CMYK and so on. The suggested workflow is: create everything in GIMP the way it looks best, then adapt it to any media (web, print, etc.) by means of exporting, keeping original data intact.


OK, I get that gimp wants to be a high end tool, to rival lets say...photoshop? Which is pretty much the defacto highend tool for complex multilayer raster images. So why....with all their customers and all their proffesionals using it are they so dimwitted that when you work on a png in photoshop and press save..the morons...unbelievably...inexplicably...save the file in png. I am amazed if given what you say is true they have managed to stay solvent after all the complaints about files being saved in the format they are being used in. Or perhaps people that wish to work in layered files work in PSD and export when they need too, and perhaps GIMP could continue to (as it has for over 10 years) save the file instead of force me to make an XCF.

As a user it is my choice how I save data, if I go into OOcalc and decide to save in CSV thats my business, if I go into firefox and screenshot a page its my choice and if I lose data or formatting or layering because of my choice then that is my choice to make. Real professionals in real workplaces often work on a multitude of files and a high-end package needs to be as good at the 2second edits as it is at the 100 hours of a single multi-layer file. I dont want to have to have one graphics program for tweaking my icons, buttons, headers and another for doing the design layout.

And this is the crux of the problem, before 2.7 you COULD do both and you COULD chose but somewhere along the lines someone has said "no, they MUST use xcf all the time". Linux isnt about MUST its about choice and if gimp wants to chose to force everyone into XCF then fine, people will just stop using it. My business does not care about the cost of photoshop, I use gimp because as a workflow I find it faster and more intuitive and if you break that workflow by forcing that 5 second extra chore of click export instead of tapping ctl-s then people will start using photoshop for the high-end stuff and your whole argument fails either way.

> **prokoudine said:**
> 
Moving to this new workflow involves a lot of internal changes and makes the old workflow very difficult to support, especially with only 2.5 developers around. Even if it was supported somehow, it would be a crude hack that nobody would like to maintain. Craftsmen hate crude hacks.



This, unless I am very much mistake in which case I am sorry, is simply a lie and whomever told you is being disingenuous. When you press save it makes a window come up and depending on which format you chose in the drop down it runs the routine or function to set it into that format. All those other save functions are still there under export so there is no extra code whatsoever, it is a conscious decision to limit one menu and move it to another. No hacks should be involved, and I as a programer can not see possibly how any program can go from doing something for 10 years..then change it...then it be impossible without screwing up the whole system to retain that functionally.

I really dont want to seem like I am arguing with people but you have to at least conceed that there are going to be people who no matter how many times you tell them its to save their data and steamline their workflow and make gimp highend and techincal spec bla bla are just going to see it as clunky.

---

### Post by prokoudine on 2010-12-09
> **robert shearer said:**
> @prokoudine
an open source application being  developed primarily for a closed source use-base  ?? Is this your implication...?  Curious ):P

Well, it isn't developed for a closed source user base. It's developed for everybody. It just so happens that most of that "everybody" is on Windows. I find it irritating myself. No active GIMP developer is on Windows, GTK+'s Windows port itself doesn't get as much love as it needs, and yet this is what we deal with.

But it's quite usual for cross-platform open source projects. E.g. Audacity didn't have many Windows developers for years, things changed only few years ago. And until fairly recently Hugin too suffered from lack of developers who use Windows by choice, because every time a new version was released somebody always started loudly complaining how Windows users were not taken care of.

> **curuxz said:**
> I am not even going to begin to comment on how bizarre it is to even suggest that you are altering a flagship linux package to suit the windows port users

I skipped most of your reply above that, because those things are simply not worth arguing over. Now, the quoted bit is exactly what I call jumping at conclusions: GIMP is *not* altered to suit Windows users. All the UI changes are meant for the whole user base. There are zero active GIMP developers who use Windows.

> **curuxz said:**
> Yeah I am using the official ati drivers and I am sure that has an effect on it. Very frustrating because while it does not exist in previous versions of GIMP I do not want to roll back and lose layer groups which is a life saver in my line of work. Hope this is something that ATI fixes and not a bug that will stay in the GIMP end of things.

Yes, let's hope this will be sorted out.

> **curuxz said:**
> To be fair you have called me childish

No, I haven't. But feel free to waste few more pages in the forum to argue how "childish behaviour" suddenly means "childish person". Of course, you'll have to argue all alone, but that shouldn't stop you.

> **curuxz said:**
> and in my book the lack of discussion on this change or willingness to make it optional change is shouting down, but I guess thats just my opinion.

Yes, it's just your opinion, and no, I don't think there is a lack of discussion on that.

> **curuxz said:**
> OK, I get that gimp wants to be a high end tool, to rival lets say...photoshop?

GIMP doesn't rival anything. Rivalling is not the point of creating GIMP.

> **curuxz said:**
> As a user it is my choice how I save data, if I go into OOcalc and decide to save in CSV thats my business, if I go into firefox and screenshot a page its my choice and if I lose data or formatting or layering because of my choice then that is my choice to make.

What you are saying basically boils down to "It's all right for software to let me screw my work up, because I'm used to it". I don't want to live in a world where everybody has to use crappy tools just because someone is emotionally attached to them and has means to ensure that this sorry state of affairs continues.

> **curuxz said:**
> And this is the crux of the problem, before 2.7 you COULD do both and you COULD chose but somewhere along the lines someone has said "no, they MUST use xcf all the time". Linux isnt about MUST its about choice and if gimp wants to chose to force everyone into XCF then fine, people will just stop using it.

GIMP is not Linux. Wherever you look there have always been changes that upset somebody somewhere. You can adapt your workflow, which is very simple, or you can stop using GIMP. It's entirely up to you.

> **curuxz said:**
> My business does not care about the cost of photoshop, I use gimp because as a workflow I find it faster and more intuitive and if you break that workflow by forcing that 5 second extra chore of click export instead of tapping ctl-s then people will start using photoshop for the high-end stuff and your whole argument fails either way.

If the people in question are willing to pay for Photoshop licenses instead of finding out how to setup keyboard shortcuts in GIMP, I wish all the luck in the world to them — they definitely need it more than me.

> **curuxz said:**
> This, unless I am very much mistake in which case I am sorry, is simply a lie and whomever told you is being disingenuous.

Yes, you are mistaken.

> **curuxz said:**
> When you press save it makes a window come up and depending on which format you chose in the drop down it runs the routine or function to set it into that format. All those other save functions are still there under export so there is no extra code whatsoever, it is a conscious decision to limit one menu and move it to another. No hacks should be involved, and I as a programer can not see possibly how any program can go from doing something for 10 years..then change it...then it be impossible without screwing up the whole system to retain that functionally.

Since you are programmer and certainly know your way around, my recommendation for you is to read Git log since ca. May 1 2009 and up to end of July or early August same year. I will not reply any of your further comments until you properly read and understand the work behind the UI change in question, how it relates to the specification and some long-term plans like native CMYK support ([http://river-valley.tv/gimp-ui-taking-some-big-issues-by-the-horns/](http://river-valley.tv/gimp-ui-taking-some-big-issues-by-the-horns/))

If you, being experienced programmer, fail understanding things even after reading changes in the code, watching the video etc, well... at least I honestly tried.

> **curuxz said:**
> I really dont want to seem like I am arguing with people but you have to at least conceed that there are going to be people who no matter how many times you tell them its to save their data and steamline their workflow and make gimp highend and techincal spec bla bla are just going to see it as clunky.

Any graveyard is full of people who wanted to be liked by everybody. They ended up being liked by nobody. Pleasing everybody is a terrible waste of time and energy. Something dies for something else to live — sooner or later everybody learns it, easy way or hard way.

---

### Post by robert shearer on 2010-12-09
@prokoudine> No active GIMP developer is on Windows, GTK+'s Windows port itself doesn't get as much love as it needs, and yet this is what we deal with.
 Hugin too suffered from lack of developers who use Windows by choice, because every time a new version was released somebody always started loudly complaining how Windows users were not taken care of.

Ahh.., I begin to see the dilemma.

Windows is the "big" potential for exposure for these apps.
More **users** = more support (forum,development,**donations**) and that feeds back into being able to improve the app for **all** users.
 So goes the circle.

Windows versions are mostly always behind in their functionality/features often due to libraries etc outside the apps control. ??

ergo these apps are seen as 'also-rans' against the paid-for competitors in the Windows arena.
 People shell out big bucks for known apps and donations to open-source pale in comparison.
So goes the circle.

Meanwhile the Linux user-base has cutting edge features in return for a 'testing' environment.
They are used to 'free beer' so donations presumably are modest. ??

Yet,  as more involved and educated users the Linux community request features and functionality comparable to or exceeding the closed-source apps.

Sheesh, must be hard for open-source devs to work towards all those conflicting demands.

---

### Post by prokoudine on 2010-12-09
> **robert shearer said:**
> 
Ahh.., I begin to see the dilemma.

Windows is the "big" potential for exposure for these apps.
More **users** = more support (forum,development,**donations**) and that feeds back into being able to improve the app for **all** users.
 So goes the circle.

Well, I can't speak about donations re users of different platforms simply because I have no statistics on my hands and I don't think anybody has. The rest of your statement is definitelty sound.

> **robert shearer said:**
> Windows versions are mostly always behind in their functionality/features often due to libraries etc outside the apps control. ??

It's not just features. E.g. GIMP and Inkscape have UIs that don't look and feel native on either Windows or Mac, and their keyboard shortcuts on Windows work only for languages with Latin-based alphabet. Scribus project has a history of recommending its Win32 users to stick to old-style Win2K-like WinXP theme, because Qt failed using other XP themes properly quite a long time. And the list goes on.

> **robert shearer said:**
> ergo these apps are seen as 'also-rans' against the paid-for competitors in the Windows arena.

Um, no &#8212; I think this is rather a clash of cultures and general lack of understanding how different motivations can be.

Windows culture is a lot about making a clear distinction between user and developer. It is therefore difficult for people to understand that software can be seriously worked on by people who do not intend to make money on it either way (up to a point when vendors refuse to give you specs "because you are not a real company"). And it is even more difficult to understand that Windows can be not a primarily targeted platform with all consequent outcomes such as lacking features.

> **robert shearer said:**
> Meanwhile the Linux user-base has cutting edge features in return for a 'testing' environment.
They are used to 'free beer' so donations presumably are modest. ??

It varies from project to project. Ardour, being primarily a Linux tool, while having a Mac build, is developed mainly on donations, $4500 every month. GIMP has donations of several hundreds bucks a week is last thing I heard. At the same time e.g. LinuxSampler that also works on various platforms barely receives any donations at all despite of being important part of production workflow ((though development is partly supported by Lionstracs, an Italian company that produces Linux-based keyboard workstation).

> **robert shearer said:**
> Sheesh, must be hard for open-source devs to work towards all those conflicting demands.

The most difficult part is cultural dissensions. No matter how much you try to explain why and how an open source project exists in the first place, a bunch of stubborn heads will always tell you how you fail to understand what users need and that you should quit using that OS (Linux) nobody cares about anyway :)

---

### Post by curuxz on 2010-12-10
> **prokoudine said:**
> I skipped most of your reply above that, because those things are simply not worth arguing over. Now, the quoted bit is exactly what I call jumping at conclusions: GIMP is *not* altered to suit Windows users. All the UI changes are meant for the whole user base. There are zero active GIMP developers who use Windows.


No, I haven't. But feel free to waste few more pages in the forum to argue how "childish behaviour" suddenly means "childish person". Of course, you'll have to argue all alone, but that shouldn't stop you.



Yes, it's just your opinion, and no, I don't think there is a lack of discussion on that.



GIMP doesn't rival anything. Rivalling is not the point of creating GIMP.



What you are saying basically boils down to "It's all right for software to let me screw my work up, because I'm used to it". I don't want to live in a world where everybody has to use crappy tools just because someone is emotionally attached to them and has means to ensure that this sorry state of affairs continues.



GIMP is not Linux. Wherever you look there have always been changes that upset somebody somewhere. You can adapt your workflow, which is very simple, or you can stop using GIMP. It's entirely up to you.



If the people in question are willing to pay for Photoshop licenses instead of finding out how to setup keyboard shortcuts in GIMP, I wish all the luck in the world to them &#8212; they definitely need it more than me.



Yes, you are mistaken.



Since you are programmer and certainly know your way around, my recommendation for you is to read Git log since ca. May 1 2009 and up to end of July or early August same year. I will not reply any of your further comments until you properly read and understand the work behind the UI change in question, how it relates to the specification and some long-term plans like native CMYK support ([http://river-valley.tv/gimp-ui-taking-some-big-issues-by-the-horns/](http://river-valley.tv/gimp-ui-taking-some-big-issues-by-the-horns/))

If you, being experienced programmer, fail understanding things even after reading changes in the code, watching the video etc, well... at least I honestly tried.



Any graveyard is full of people who wanted to be liked by everybody. They ended up being liked by nobody. Pleasing everybody is a terrible waste of time and energy. Something dies for something else to live &#8212; sooner or later everybody learns it, easy way or hard way.


I find your response frankly laughable, you are quite happy to point out everyone is wrong then when you are asked reasonable questions you chose to ignore them, patronise by telling me to read github so I can 'understand things' or contradict your own words.

-You brought windows up as a reason for changes, not me so you are arguing against your self

- You said that something was programatically impossible then when challenged on this said it was because of " how it relates to the specification and some long-term plans like native CMYK". Well which is it? It sounds like your saying I am wrong for the sake of it (without understanding the programming your self) then making it a spec issue not a technical issue.

- To say gimp does not rival photoshop is just plain silly, of course it does. Any product or service that competes for user base in any way with another product or service rivals it, intentionally or unintentionally. Photoshop and Gimp are rivals..thats a fact my friend to argue otherwise would make your self look even more foolish it has nothing to do with intention is has to do with market reality.

- "It's all right for software to let me screw my work up, because I'm used to it" again a stupid over simplification of the point I was making. It is not the job of a tool to control its use, you buy a gun and put it in your mouth it does not warn you that pulling the trigger is a bad idea and it certainly does not prevent you from doing so. You completely proved my point 100% that it is nannying on the part of GIMP devs. We don't need you to chose weather we 'screw our work up'. Not your choice and like I said no other main stream cross platform program treats non-native formats like this.

- Accusing someone of any behaviour insinuates they are that thing. Calling someone thugish implies they are a thug. Thats how english works, simple. Sorry thats not something you can grasp.


If you wish to be rude and arrogant and say things like you can be bothered to read what other people have put (in response to your own words no less) then fine, but if you are going to read anything read what you wrote your self then you may see why your so 'misunderstood'.

Like I said this argument is boring and certainly not something I am going to waste any more of my time on, you had an opportunity to debate any of the points sensibly and instead put your hands over your ears and started shouting "i cant hear you" loudly while trying to fob me off with github. Fair enough, if you cant defend your point of view I wont bother trying to have a reasoned discussion with you, have a great day.

---

### Post by idealflame on 2010-12-10
> **prokoudine said:**
> Yes, I do like this separation. Even more, I'd like it to be used in Inkscape as well. We actually had a GSoC project on that this year, but it failed — the student disappeared.

Ahh, okay. I guess I stand corrected - I'm not personally a great fan of it, but I guess, ultimately, my biggest gripe is merely that I haven't yet assigned a shortcut to it yet. :)
However, I don't think it would be a large programming task to optionalise at all - the system can already identify if you're trying to save to a non-XCF file and tells you to instead use the Export function. Surely it couldn't be too hard to, rather than inform the user they're wrong but instead (if optioned for) merely directly invoke the Export dialogue's "save" method instead?

> **prokoudine said:**
> how it relates to the specification and some long-term plans like native CMYK support ([http://river-valley.tv/gimp-ui-takin...-by-the-horns/](http://river-valley.tv/gimp-ui-takin...-by-the-horns/))
Wow, this is pretty amazing stuff, indeed! I don't like the Export separation, but certainly can't argue the genius it's paving way for!


> **prokoudine said:**
> You don't need pressing Enter. When you bring mouse pointer close enough to starting point, the selection closes itself. Try it :) Works for me on a week old build from Git master.

Woo, so it does. That must have been introduced in a later build, because I'm certain it wasn't there at the beginning (more the fool me for not actually checking the latest!). Again, I stand corrected...



> **prokoudine said:**
> Er.. What error?
Ahh, interesting. For the third time in almost as many points, my mistake. Looks like the problem is actually in that the GIF export plugin crashes when trying to save a GIF with layers larger than the image size (can't find it mentioned in Bugzilla, though; anyone care to try to replicate this so I am justified in reporting it?).
I was originally referring to my belief that merely exporting to GIF was broken - A quick Google search "revealed" that this was a bug in 2.7.1, fixed in the mythical 2.7.3 release...(Guess I might have a go at compiling the Git tree when I have time to see if it's even still there!)

---

### Post by prokoudine on 2010-12-11
> **idealflame said:**
> Ahh, okay. I guess I stand corrected - I'm not personally a great fan of it, but I guess, ultimately, my biggest gripe is merely that I haven't yet assigned a shortcut to it yet. :)
However, I don't think it would be a large programming task to optionalise at all - the system can already identify if you're trying to save to a non-XCF file and tells you to instead use the Export function. Surely it couldn't be too hard to, rather than inform the user they're wrong but instead (if optioned for) merely directly invoke the Export dialogue's "save" method instead?

I'm not sure I understand. It sounds a bit like the old workflow where every time you saved to a lossy format a message popped up to warn you that it's going to cause cancer and bring 30 year of unluck into your family :)

> **idealflame said:**
> Looks like the problem is actually in that the GIF export plugin crashes when trying to save a GIF with layers larger than the image size (can't find it mentioned in Bugzilla, though; anyone care to try to replicate this so I am justified in reporting it?).

[https://bugzilla.gnome.org/show_bug.cgi?id=623186](https://bugzilla.gnome.org/show_bug.cgi?id=623186)

Fixed on July 26 this year.

---

### Post by idealflame on 2010-12-23
> **prokoudine said:**
> I'm not sure I understand. It sounds a bit like the old workflow where every time you saved to a lossy format a message popped up to warn you that it's going to cause cancer and bring 30 year of unluck into your family :)


Hehe; that's a pretty amazing description of the gist of it


> **prokoudine said:**
> Fixed on July 26 this year.
Ahh, so it was. Cool :)

Also, I finally managed to compile the GIT version (after taking embarrassingly long to realise I needed GIT versions of GEGL and BABL :$). All I have to say is whoever designed the new value sliders (i.e. opacity slider in the toolbox) is a genius.

---

### Post by prokoudine on 2010-12-25
> **idealflame said:**
> All I have to say is whoever designed the new value sliders (i.e. opacity slider in the toolbox) is a genius.

IIRC, it was done mostly with graphic tablets users in mind, but this kind of UI is used in other apps. Ardour has a similar widget for editing values of LADSPA audio effects, and darktable has a similar one for all the plugins in darkroom mode.

---

### Post by Merk42 on 2010-12-27
So, hey [where's my GIMP 2.8?](http://www.phoronix.com/scan.php?page=news_item&px=NzkxNw)

---

### Post by prokoudine on 2010-12-28
> **Merk42 said:**
> So, hey [where's my GIMP 2.8?](http://www.phoronix.com/scan.php?page=news_item&px=NzkxNw)

OK, I think this should have been better communicated to users.

Here comes explanation: [http://libregraphicsworld.org/news.php?readmore=667](http://libregraphicsworld.org/news.php?readmore=667)

---

