---
title: "The Gnome Shell themes thread... ..."
date: 2010-02-28
forum: Art &amp; Design
---

### Post by techno-mole on 2010-02-28
[COLOR="Red"]****** Updated on the 18th of March, first post now includes links to other schemes/themes by other users, and the latest css file is also attached (last attachment named "latest"), I also added a link to a post that mentions some add ons/extensions for gnome shell ******[/COLOR]


I (like a lot of people) have been trying out Gnome Shell (incase you didnt know - [http://live.gnome.org/GnomeShell]("http://live.gnome.org/GnomeShell") )

Myself and some others have been making themes for Gnome Shell, which is relatively easy if you know a bit of css (which is how the main look of gnome shell is controlled) 

It has been noted by some that the default black theme isnt to their (and others) tastes, so I decided to make some more themes for gnome shell, and other people have started making their own as well.

Now at present there isnt a way to actually install multiple themes, so you will have to overwrite some files, so the thing to do before installing any of the themes is to back up certain folders, the location of these folders will depend on how you installed gnome shell, for example if you have used the testing ppa then the theme folder is located here -  /usr/share/gnome-shell/theme

if you have built from source then it will be in your home folder - /home/<user>/gnome-shell/source/gnome-shell/data

So before installing any of the themes, which will hopefully get included here so they are all in one place, backup the folders in those locations, you can save them to your home folder or where ever you want.


next you can download the archives (i will include the ones ive done in this post) and extract them.
some of the archives will only have the css file, and some may have the icons as well (a couple of my themes have edited icons)

you need to copy the contents over to where ever the theme folders are, the way i do this (if you have installed from source then you dont need to be root to copy the files over) 

open a terminal and type ```
sudo nautilus
```

then browse to where you extracted the archive, then right click and select copy, next browse to /usr/share/gnome-shell/theme and paste the files (or the whole folder) and select replace.

once thats done press alt + f2 and type restart and then hit enter, and providing the files are in the right place the new theme should load.

A couple of things to note, firstly every time you update gnome shell it will revert to the default theme, so you will have to go through the steps above again.

I have been adding extra comments to the css to help with seeing which bits do what, in my opinion more comments are needed, and I'm still working on other themes, so I will add comments as I go.

The other thing is that at present the search feature of the over view mode is partly controlled by a javascript file, all the file does is change the colour of the cursor and the text, it probably won't need to be touched, but if for some reason the theme interferes with the colour of the text then a couple of lines in the dash.js file can be edited, this file is in - /usr/share/gnome-shell/js/ui or where ever you installed gnome shell.

Please note there might be differences between the dash.js file on compiled from source installations, so make back ups, or alternatively I can point you in the direction of the lines to edit in the dash.js
I believe that the idea is to increase the amount of control that the css has, so there may well be a lot more that can be done with the css in future releases.

Some helpful sites - [http://html-color-codes.info/]("http://html-color-codes.info/")

[http://www.drpeterjones.com/colorcalc/]("http://www.drpeterjones.com/colorcalc/") and this one if you want to get into editing css files - [http://www.w3schools.com/css/]("http://www.w3schools.com/css/")

have fun.

screen shots can be seen here - [http://twitpic.com/15mujl]("http://twitpic.com/15mujl") these are the current themes, there are some more I think in this thread - [http://ubuntuforums.org/showthread.php?t=1305154&page=125]("http://ubuntuforums.org/showthread.php?t=1305154&page=125")  you may have to scroll about.

I have added this post from augias as it was pointed out that if you have built gs from source you should be able to preserve your theme.

```
  	
Re: The Gnome Shell themes thread... ...
By the way, It just occurred to me that this might be important to mention. If the tip is useful, I recommend the OP add this info to his first post.

If you're building gnome-shell from source using jhbuild tools: You can keep the theme you're currently using (without having to re-do everything on updates) by committing your changes to your css file to git, like so.

Code:

$: cd ~/gnome-shell/source/gnome-shell
$: git commit -a

This will open a changelog file in nano (terminal's text editor) that asks you for a breif commmit message.
Code:

Commit changes to the CSS file.
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Committer: Fernando Mora <fernando@homework.(none)>
#
# On branch master
# Your branch is ahead of 'origin/master' by 1 commit.
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   data/theme/gnome-shell.css
#





                               [ Read 14 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

Just write something obvious like "CSS changes" where the cursor is (at the top where i wrote the same message) and press ctrl+o to save, enter to confirm and ctrl+x to quit.

This will let any updates from git take place without bugging you about your weird CSS file, but i doubt it's foolproof. If you're daring, use
Code:

$ git reset HEAD~X

where X = number of commits to revert. 
```



[COLOR="Red"]Update - just adding the other themes/schemes that other gnome shell users have posted, in link form, should make them easier to find.[/COLOR]

forest by keth - [http://ubuntuforums.org/showpost.php?p=8894180&postcount=3]("http://ubuntuforums.org/showpost.php?p=8894180&postcount=3")

smoke by me (techno-mole) - [http://ubuntuforums.org/showpost.php?p=8896045&postcount=12]("http://ubuntuforums.org/showpost.php?p=8896045&postcount=12")

a radiance type scheme by suboxide - [http://ubuntuforums.org/showpost.php?p=8922513&postcount=23]("http://ubuntuforums.org/showpost.php?p=8922513&postcount=23")

another scheme based on the radiance themes by suboxide - [http://ubuntuforums.org/showpost.php?p=8929403&postcount=28]("http://ubuntuforums.org/showpost.php?p=8929403&postcount=28")

ice by me - [http://ubuntuforums.org/showpost.php?p=8936466&postcount=29]("http://ubuntuforums.org/showpost.php?p=8936466&postcount=29")

ode to humanity by me - [http://ubuntuforums.org/showpost.php?p=8944018&postcount=30]("http://ubuntuforums.org/showpost.php?p=8944018&postcount=30")

light grey by augias - [http://ubuntuforums.org/showpost.php?p=8946829&postcount=35]("http://ubuntuforums.org/showpost.php?p=8946829&postcount=35")

light grey by augias - updated for latest version of gs - [http://ubuntuforums.org/showpost.php?p=9084097&postcount=83]("http://ubuntuforums.org/showpost.php?p=9084097&postcount=83")

human theme by mudrain911 - [http://ubuntuforums.org/showpost.php?p=9022452&postcount=75]("http://ubuntuforums.org/showpost.php?p=9022452&postcount=75")



also i have attached my latest css file (which is currently ode to humanity) to this as well (with the name as latest) it should be fine to run on your versions of gnome shell (works for me, with the latest gs update from the testing ppa) 

there is also [this]("http://ubuntuforums.org/showpost.php?p=8997676&postcount=69") version of the gnome shell css by agrh - it has a different layout to mine, and the comments are also different, people may find this one easier to figure out than mine, i never actually considered making it more understandable, so cheers to agrh

my advice would be to go through the css file (the newest one) and compare with yours, just to be on the safe side, or just edit the one i attached and change the colouring to suit your tastes.

augias linked to some gs extensions that people may or may not know about, heres the link to his (assuming he is male of course, erm sorry if your not by the way ;-)) post - [http://ubuntuforums.org/showpost.php?p=8987994&postcount=64]("http://ubuntuforums.org/showpost.php?p=8987994&postcount=64")

have fun ;)

---

### Post by icyzer on 2010-02-28
Good call, it's waaaay easier to find themes this way :)
I've been trying some editing myself but no luck so far. If there was a possibility to add a gnome shell background that would be great tbh :)

Anyway good thread

---

### Post by keth on 2010-02-28
Here is my forest theme, with major thanks to OP for commenting out the css:

---

### Post by 3rdalbum on 2010-02-28
Please rework this post and put it in Tutorials And Tips, it would be great to have a proper Gnome Shell theming HOWTO.

---

### Post by techno-mole on 2010-02-28
> **keth said:**
> Here is my forest theme, with major thanks to OP for commenting out the css:

I plant to add more comments to the css, there are bits I've missed, I'll get round to it soon.

PS - if the forum mods want to move this thread to tutorials then I can't see any problems with that, apart from that this may well be a work around for now, I have no idea if the gnome shell developers have plans regarding easy installation of themes etc.

---

### Post by techno-mole on 2010-02-28
> **icyzer said:**
> Good call, it's waaaay easier to find themes this way :)
I've been trying some editing myself but no luck so far. If there was a possibility to add a gnome shell background that would be great tbh :)

Anyway good thread

have you tried something like this - 

under the overview section for example add this - ```
background-image: url("scroll-hhandle.svg")
```

back the css file up first.

i would remove the gradient settings altogether and see if it works like this - ```
.overview {
background-image: url("scroll-hhandle.svg")
}
```

where it says - "scroll-hhandle.svg" replace this with the name of your image file, eg - overviewbackground.jpg and then put the image you want to use in the theme file, i would think it will display a jpeg, but if not convert it to a png and see what happens.

i have no idea to be honest if that would work at all, not sure how it would look either, so it might need some other code to align it and such like.

---

### Post by symon1980 on 2010-02-28
holey **** guys.... have you seen these awesome themes/mockups for gnome3/shell

this is so Awesome! If gnome 3 looks like this, then I'll consider coming back from kde... im impressed!


[http://gnome-look.org/content/show.php/New+GNOME+3+Shell+concept?content=105672](http://gnome-look.org/content/show.php/New+GNOME+3+Shell+concept?content=105672)

---

### Post by nilarimogard on 2010-02-28
> **symon1980 said:**
> holey **** guys.... have you seen these awesome themes/mockups for gnome3/shell

this is so Awesome! If gnome 3 looks like this, then I'll consider coming back from kde... im impressed!


[http://gnome-look.org/content/show.php/New+GNOME+3+Shell+concept?content=105672](http://gnome-look.org/content/show.php/New+GNOME+3+Shell+concept?content=105672)

Just some big bubbles, I don't like it. The only thing I like is the  "Ongoing" part - where you are able to directly control running  applications.

---

### Post by Symod on 2010-02-28
Using Gradients of Grey, looks really nice. Great job!

---

### Post by jpeddicord on 2010-02-28
Moved to Art & Design.

---

### Post by k3lt01 on 2010-02-28
> **jpeddicord said:**
> Moved to Art & Design.I must say I think thats the wrong place, I have never looked in art and design in the nearly 3 years I have been on this forum as it just doesn't interest me wading through it for things that "may" be of interest to me.

If this did need to be moved Tutorials and Tips would have been a much better option imho.

---

### Post by techno-mole on 2010-02-28
here is another theme I have been working on, I called it smoke, but its essentially a light grey theme.

I have changed various aspects of the css, and added a load more comments, I changed a lot of the colour codes, so instead of hex values they are now rgba, which means you can add an element of opacity to the themes, or go for full transparent if you feel the need, I did try full transparency, but in my opinion it didn't look that good.

I also adjusted some of the image files, new corner ripple etc.

I have also tried adding a background, which didn't go too well, but I think with some tweaking (and asking a couple of questions) it may be possible to use a background in the over view mode.

PS - Thanks to the mods for relocating the thread, but I have to agree that I would have put this thread in tutorials and tips, but thats me.

Screenshots of new theme and files attached.

PPS - I have just noticed an odd thing, I have tried to make the themes as user friendly as possible, so for example I have used colours that keep text easy to read etc (least I hope I have) the odd thing is that I used a gradient for the running applications, so when you look at the applications in overview mode the ones that are running should look different (see screenshot) how ever I have also noticed that if you mouse over the running application icons a border appears ?
This is meant to happen in so much as there is meant to be a border around running apps, but it's meant to be there as soon as the apps icon changes to running, so I may have to look at the code.

---

### Post by k3lt01 on 2010-02-28
Thanks again Techno, your comments in your themes are really helpful.

---

### Post by ronacc on 2010-02-28
yes thanks from me also . and I too think you had this in the right place , after all when it come to gnome-shell we are ALL beginners .

---

### Post by robinparriath on 2010-02-28
Thanks techno-mole.  Your marine theme fits perfectly with the chromibuntu theme

---

### Post by OlyPerson on 2010-03-01
Has anyone else found that the default look of the message tray is lacking?  I think it looks unclean and prefer a nice semi-transparent look all the way through like my attached screenshot... *taking it now*

I also wish the menu that shows all the applications would take up the screen by default, or have the option to resize it yourself- I'll attach another screenshot showing how it works better imho.

---

### Post by techno-mole on 2010-03-01
> **OlyPerson said:**
> Has anyone else found that the default look of the message tray is lacking?  I think it looks unclean and prefer a nice semi-transparent look all the way through like my attached screenshot... *taking it now*

I also wish the menu that shows all the applications would take up the screen by default, or have the option to resize it yourself- I'll attach another screenshot showing how it works better imho.

that can all be controlled using the css file, although why the app menu is so small is a bit of a puzzle, but its easily changed.

i was wondering is they couldnt embed some kind of editor to allow adjusting of the css from within the shell, like the looking glass feature, which I think allows for inspecting the java script, not sure it lets you edit it though ?

---

### Post by OlyPerson on 2010-03-01
> **techno-mole said:**
> that can all be controlled using the css file, although why the app menu is so small is a bit of a puzzle, but its easily changed.

i was wondering is they couldnt embed some kind of editor to allow adjusting of the css from within the shell, like the looking glass feature, which I think allows for inspecting the java script, not sure it lets you edit it though ?

You mean being able to click on an element and edit its properties?  That sounds like a really good idea actually, it would make it way easier and just be clever.  It would be cool if it were like the looking glass with the red square around the currently  selected element.

---

### Post by techno-mole on 2010-03-02
i think an embedded editor might well be easier to implement from a theming point of view, as far as i can tell things might have to be re-written to allow multiple themes to be installed ?

---

### Post by techno-mole on 2010-03-02
UPDATE - I had to re-install ubuntu again (don't ask) anyway nearly got it back to how I want it, but after installing gnome shell I applied one of my themes to it (I wish they would change the default, it sucks, especially when it can do so much more) 
but it didn't render as it should, the only thing I tested was the alt+f2 pop up for entering commands etc (you know the one most people have to type restart into to stop the cursor being hidden by the panel) it cam up with no back ground, and also didn't display the " dialog error " icon that now resides in the gnome shell theme folder.

I just thought I would let people know that the css may need tweaking (correction, will need tweaking) and that some of it has been changed a little, so I am going to go through and try and re-comment the new bits, once I find out what they do.

cheers

---

### Post by RabbitWho on 2010-03-03
> **k3lt01 said:**
> I must say I think thats the wrong place, I have never looked in art and design in the nearly 3 years I have been on this forum as it just doesn't interest me wading through it for things that "may" be of interest to me.

If this did need to be moved Tutorials and Tips would have been a much better option imho.


You might be more likely to see it in Tutorials and Tips, but it has absolutely nothing to do with tutorials and tips, it has to do with art and design. The fact that's not of interest to you is absolutely irrelevant.

---

### Post by k3lt01 on 2010-03-03
> **RabbitWho said:**
> You might be more likely to see it in Tutorials and Tips, but it has absolutely nothing to do with tutorials and tips, it has to do with art and design. The fact that's not of interest to you is absolutely irrelevant.So someone posting how to change a theme isn't classed as a tip to your pov?

I fail to see how changing a colour scheme, and that is really all that has happened so far, is artistic. Also with "design" nothing in the underlying design of G-S is changed by changing the colour scheme so that's another area where I fail to see the relevance.

Anywhooooooooo, I'm not here to argue a point over thread placement, I am also not here to have my thoughts judged as being irrelevant especially when others have posted very similar pov yet you failed to pick them on theirs. May I respectfully say that you are just going to have to agree to disagree with me.

---

### Post by SuBoXiDe on 2010-03-05
this is just something i tried based on techno-mole his smoke theme
(i used the original icons so i'm not uploading those, don't forget to back up your css if you wanna try this theme)

---

### Post by techno-mole on 2010-03-06
i like it, i take it that you are either running lucid or you have installed the themes for it ?

either way its good, ive found that editing the css is quite versatile in making the system look how you want.

I recently requested (on the gs mailing lists) the option to change the shape of the desktop previews in over view mode, when using the mosaic mode etc i thought it might be nice to round the corners of, or be able to make them circles/oval etc
ive seen some mock ups along a similar line.

i have noticed some small changes in the css for gs of late, things like the run dialog is now controlled via the css (or at least the look of it) and also there is now shadow effect when scrolling in the application menu, it kind of gives an almost drum like look to the applications, think of a fruit machine the way they look when spinning and you should see what i mean.

hopefully this weekend i will be able to upload an almost fully commented css (including the new bits) and hopefully a new colour scheme as well (fingers crossed)

---

### Post by techno-mole on 2010-03-06
me again.

i had a quick look through the css for the scheme im using (smoke) and it was mostly commented, aside from the newer additions to it.

ive attached it so everyone can look through it, there isnt that much of a difference in the css compared to a couple of weeks ago, least i dont think there is.

hopefully it prove helpful.

---

### Post by SuBoXiDe on 2010-03-06
I'm running karmic with the themes installed fastest way to install them can be faund on [http://www.webupd8.org/](http://www.webupd8.org/) i think.
and yes the run dialog can be changed in the css now also.

I'll try to make a drak theme with some lime green today if i find time, i wanna play a bit with the panel buttons and see what kind off effects i can get, the only problem i have with it is that when you theme the panel buttons you also theme a bar where you can select what desktop you want (see screen)

---

### Post by techno-mole on 2010-03-07
funny, i was thinking about making a lime/lemony type theme.

anyway i cant think why that bar appears in the workspace indicator, i tend not to use that view, i prefer the mosaic view.

daft question, but when ive messed around with the panel  buttons i havent got that bar, you havent added the panel buttons attributes to the workspace indicator have you ? thats the only thing i can think of anyway.

or perhaps the work space indicator is some how linked to the panel buttons else where ? although i cant think why it would be ?

---

### Post by SuBoXiDe on 2010-03-07
i lost my green/black theme that i was working on last night i did an update and forgot to back up my theme so gnome-shell update overwrote it :x, and i wasn"t really happy with my gtk theme i was using for base so i just started all over and made one based on the radiance theme (the new light theme) again based on your new css :).

ps: i edited some images and added some mouse overs to the panel (i even did a test with and ubuntu logo in the activities menu)

ps: the theme posted is still a work in progress some things i'm not happy about and i will have a look at the java later (but it's much better then my last one i think)

PS!!: back up your theme folder and replace with my full theme folder

---

### Post by techno-mole on 2010-03-08
managed to get another scheme done, i havent edited the icons (still thinking about what will go with the scheme)

this scheme is inspired by ice, not the stuff you get in your freezer, but polar ice, if you have ever watched a natural world type program (blue planet type of thing) and seen the polar ice flows then you will (hopefully) get where im coming from with the colouring.

---

### Post by techno-mole on 2010-03-10
I did another colour scheme last night, I decided that being as ubuntu is dropping the brown and orange type look I would make a scheme for gnome shell as a tribute, so here it is, ode to humanity :-) it's not meant to be serious, just a bit of fun.

---

### Post by SuBoXiDe on 2010-03-10
i tried to work with a repeating background last night "background-repeat:repeat-x;" something like this but it doesn't seem to work or i did something wrong i was tired and after trying 3times i stopped and went to bed and i'm at work now so can't test it but just seeing your screen remembers me of it since some kind off wood structure repeating could maybe give it a nice feel
but like i said maybe i did something wrong i'll try again tonight

---

### Post by techno-mole on 2010-03-10
i did try a background image applied to the overview, this didnt go well either, it did display, but then for some reason it seemed to cancel out the style sheet and everything went transparent, if you rename the style sheet and restart the shell you will see what i mean.

i dont know why it seemingly crashed the theme/scheme of it though.it should be possible to show a background, it may just be an alignment issue ?

ill have another go at some point, and might ask on the gs mailing lists regarding backgrounds, i did put in a feature request that would allow people to change the workspace previews to circles/ovals etc or just round of the corners, but as yet its still an idea, im not sure if it could be implemented in the css ?

the other thing was to allow editing of the theme using an embedded editor type thing, this may be harder than first thought, but one of the gs people suggested using gconf to edit it, which may well be a better idea, we shall see.

---

### Post by SuBoXiDe on 2010-03-10
i was able to add the ubuntu logo as a beackground to the activity button in my last light theme i uploaded if you look close you will see a light ubuntu logo behind the activity button but adding a repeating background seems impossible for now (or i miss something)

---

### Post by techno-mole on 2010-03-10
yes I did see the logo, it seems to be that in order to display an image it would need to be included in a lot of places, for example you can display and image in the panel buttons, and the dash and the overview, you should also be able to display and image as a background in the recent items pop out and the app pop out, and there in lies the problem I think, it's loads of little elements, rather than one big one.

I will have to play around with some image files or varying sizes etc and see what effects can be produced, for example as you said a wooden look could be applied to aspects of the shell, I don't know how well it would work, displaying and image in the app pop out, I will have a go and post some screenshots, this I think will be easier than using a large image in the over view mode, which what I tried and failed badly with.

I have sent an email to the gnome shell mailing list to ask about displaying images as backgrounds just to see what they say.

---

### Post by augias on 2010-03-10
Updated my theme on a new post. [Click here to check it out]("http://ubuntuforums.org/showthread.php?p=9025533#post9025533").

---

### Post by techno-mole on 2010-03-10
I have been trying t get an image to display in the overview mode, and I can, but there are alignment issues and then for some reason it only displays once, and seems to cancel out the style sheet for some reason.

the transparency can be removed, eg you can decide to show no transparency and no gradients if you feel the need.

the poster has edited the style sheet to show an ubuntu logo in the panel buttons, i would look there if using blue fish to edit, just press ctrl + f and type panel or such like.

I have not heard anything back from the gs mailing lists, but i most likely will. im still working on trying to add the alignment aspects to get images of varying sizes to display properly in the app menus etc, slow going.

---

### Post by augias on 2010-03-12
By the way, It just occurred to me that this might be important to mention. If the tip is useful, I recommend the OP add this info to his first post. 

**If you're building gnome-shell from source using jhbuild tools:** You can keep the theme you're currently using (without having to re-do everything on updates) by committing your changes to your css file to git, like so.

```
$: cd ~/gnome-shell/source/gnome-shell
$: git commit -a
```

This will open a changelog file in nano (terminal's text editor) that asks you for a breif commmit message. 
```
Commit changes to the CSS file.
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Committer: Fernando Mora <fernando@homework.(none)>
#
# On branch master
# Your branch is ahead of 'origin/master' by 1 commit.
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   data/theme/gnome-shell.css
#





                               [ Read 14 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

Just write something obvious like "CSS changes" where the cursor is (at the top where i wrote the same message) and press **ctrl+o** to save, enter to confirm and **ctrl+x** to quit.

This will let any updates from git take place without bugging you about your weird CSS file, but i doubt it's foolproof. If you're daring, use 
```
$ git reset HEAD~X
```
where X = number of commits to revert.

---

### Post by techno-mole on 2010-03-12
> **augias said:**
> By the way, It just occurred to me that this might be important to mention. If the tip is useful, I recommend the OP add this info to his first post. 

**If you're building gnome-shell from source using jhbuild tools:** You can keep the theme you're currently using (without having to re-do everything on updates) by committing your changes to your css file to git, like so.

```
$: cd ~/gnome-shell/source/gnome-shell
$: git commit -a
```

This will open a changelog file in nano (terminal's text editor) that asks you for a breif commmit message. 
```
Commit changes to the CSS file.
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Committer: Fernando Mora <fernando@homework.(none)>
#
# On branch master
# Your branch is ahead of 'origin/master' by 1 commit.
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   data/theme/gnome-shell.css
#





                               [ Read 14 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

Just write something obvious like "CSS changes" where the cursor is (at the top where i wrote the same message) and press **ctrl+o** to save, enter to confirm and **ctrl+x** to quit.

This will let any updates from git take place without bugging you about your weird CSS file, but i doubt it's foolproof. If you're daring, use 
```
$ git reset HEAD~X
```
where X = number of commits to revert.

consider it done :-)

---

### Post by techno-mole on 2010-03-12
ive just updated gnome shell (from the testing ppa) and there is a change to the css that controls the search feature, basically from what i can tell (havent looked at it that closely) you need to replace the search control css with the following 

```


#searchEntry {
    padding: 4px;
    border-radius: 4px;
    color: #a8a8a8;
    border: 1px solid #565656;
    background-color: #404040;
    caret-color: #fff;
    caret-size: 1px;
    height: 16px;
}

#searchEntry:focus {
    color: #545454;
    border: 1px solid #3a3a3a;
    background-color: #e8e8e8;
    caret-color: #545454;
}

#searchEntry:hover {
    border: 1px solid #767676;
}

```

you should be okay to just straight replace all the search entry stuff with the above.

---

### Post by Minipalmer on 2010-03-13
Hey guys, the themes are looking great. I tried gnome shell the other day and have a few suggestions/questions.

1. Is there a way to make the font smaller on the top panel-ish thing?

2. Is there a way to make the top panel-thing smaller?

3. My gnome shell did not have the fading icon on top, but just the regular icon. Is there a way to enable it?

---

### Post by techno-mole on 2010-03-13
[COLOR="Red"]1. Is there a way to make the font smaller on the top panel-ish thing?[/COLOR]

you can adjust the font size in the css, under the panel section there is a font attribute - 

```
#panel {
    color: rgba(255,255,255,1.0);
    [COLOR="Red"]font-size: 16px;[/COLOR] 
    background-gradient-direction: vertical;
    background-gradient-start: rgba(42,27,10,1.0);
    background-gradient-end: rgba(255,128,0,1.0);
    border-bottom: 0px solid #000000;
    
}
```

[COLOR="Red"]2. Is there a way to make the top panel-thing smaller?[/COLOR]

as for making the panel smaller this may be controlled by the panel.js file, not sure to be honest, if i get time i will look into it.

[COLOR="Red"]3. My gnome shell did not have the fading icon on top, but just the regular icon. Is there a way to enable it? [/COLOR]

im not sure which icon you are referring to ? do you mean the corner ripple that displays when you mouse over the top left hand corner of the screen ? or the message tray, which displays when mousing over the bottom left hand corner of the screen ?
or finally do you mean the icon that one of the posters in this thread has added using the css ?

PS - it will be helpful if you can tell us how you installed gs, are you using the testing ppa ? or building from source, the reason being is that folders etc will be in different places depending on how you installed.

cheers

---

### Post by Minipalmer on 2010-03-13
Thanks for the quick response. I actually just installed from the repos. If someone could direct me towards to PPA that would be great.

For #3 I mean this: [IMG]http://i44.tinypic.com/2w2gcxz.png[/IMG]

See how that image has a gradient icon on it, fading into the name of the active program? The gnome shell I installed simply had a regular icon with the name next to it. Could this just be because I was using an older version of gnome shell?

---

### Post by augias on 2010-03-13
> 2. Is there a way to make the top panel-thing smaller?

yes, in ~/gnome-shell/source/gnome-shell/js/ui/panel.js or /usr/share/gnome-shell/js/ui/panel.js :
```
const PANEL_HEIGHT = 26;
```

---

### Post by hxcobd on 2010-03-14
Not to be a huge downer, as I appreciate the trailblazing some of you guys are doing as far as understanding the new GnomeShell and making themes or whatever, but 90% of these "themes" are appallingly hideous and are simply color changes to the extremely bad gradients others are already using...

Kinda don't see the logic of replacing one terrible screen-high gradient with another.

---

### Post by techno-mole on 2010-03-14
granted they are essentially just colour changes at present, the idea is though that where possible (at least this is the impression i get) control of the theming/colour etc will be controlled by the css.

i have put forward suggestions to the devs regarding things like being able to change the desktop previews shape, from plain squares to circles/ovals etc or just rounding off the corners, i have also been looking into how an image can be used instead of gradient-ed colouring, there is a lot of scope, and possibly more with time.

at the moment most people are in agreement that the default scheme isnt that good, being able to mess about with them is a way for people to put their own stamp on things for now.
it will be a few more months before release candidates etc so everything thats done now is just experimentation, to see what works, and what doesnt.

people may or may not like the schemes/themes etc but things are still experimental.

---

### Post by Kentakunte on 2010-03-14
> **hxcobd said:**
> Not to be a huge downer, as I appreciate the trailblazing some of you guys are doing as far as understanding the new GnomeShell and making themes or whatever, but 90% of these "themes" are appallingly hideous and are simply color changes to the extremely bad gradients others are already using...

Kinda don't see the logic of replacing one terrible screen-high gradient with another.

Fu*k off. These are much nicer than the ugly black theme you get when you install. I like the new transparent one that goes with the radiance theme. Thanks, guys.

---

### Post by d3v1150m471c on 2010-03-14
That's some really nice artwork. Gnome shell still has a long way to go to compete with kde though.

---

### Post by techno-mole on 2010-03-14
gnome shell doesnt compare to kde, mainly because its not trying to (at least in my opinion) i like kde, i go back to it every now and then, but for some reason i keep coming back to gnome, i have no idea why, my wife is using kde.

---

### Post by k3lt01 on 2010-03-14
> **d3v1150m471c said:**
> That's some really nice artwork. Gnome shell still has a long way to go to compete with kde though.Ahhhhhh. not more Buck Rogers screenshots.

---

### Post by Minipalmer on 2010-03-14
> **Kentakunte said:**
> I like the new transparent one that goes with the radiance theme. Thanks, guys.Can you post a screeny of that? Haven't seen it yet.

---

### Post by tfylling on 2010-03-16
So I've tried a number of these themes and they seem to refuse to change much at all. Pretty much the only thing I've noticed changing is the calendar, which becomes transparent with some themes. Probably this is because I'm using the version from the ubuntu repository, but I really can't be arsed to start compiling it myself.

I've had a look at the gnome-shell.css file that came with the package and it doesn't contain anywhere near the same amount of classes that are in your custom files, so I guess the javascript files are severely limiting what the stylesheet can do in this version. So, would one of you guys be so kind to post your dash.js file so I can just try crowbaring that in there to see if it helps before I throw in the towel and compile it myself?

Cheers, and thanks for making the effort to plant ideas for how gnome shell can possibly look :)

---

### Post by ibuclaw on 2010-03-16
Is the plan still to keep the rather dizzy dizzle dazzling zoom-out/zoom-in effects for switching to the shell view?

I am curious if it would be instead possible to implement a fast fade-in/fade-out effect in its place, as IMO that would be better (for me).

Regards
Iain

---

### Post by k3lt01 on 2010-03-16
> **tfylling said:**
> Probably this is because I'm using the version from the ubuntu repository, but I really can't be arsed to start compiling it myself.You don't have to compile anything. You can add the ricotz ppa and its done for you.

---

### Post by techno-mole on 2010-03-16
> **k3lt01 said:**
> You don't have to compile anything. You can add the ricotz ppa and its done for you.

i really should read things more closely, if you are using the older version it probably wont work like the version im using (and others are using)

add this to your sources list - ppa:ricotz/testing

i forget the command line way, you can just open up your software sources this way --> administration --> software sources (enter your password when asked) and then click "other software" and then click "add" and paste the above into it, click add source and close, it will ask you to reload.

then you can go into synaptic and mark it for upgrading or run sudo apt-get update && sudo apt-get dist-upgrade (i think)

---

### Post by techno-mole on 2010-03-16
> **ibuclaw said:**
> Is the plan still to keep the rather dizzy dizzle dazzling zoom-out/zoom-in effects for switching to the shell view?

I am curious if it would be instead possible to implement a fast fade-in/fade-out effect in its place, as IMO that would be better (for me).

Regards
Iain


i honesty dont know, i can always ask for it to be changed (or have the option to switch between different effects) on the mailing lists.

it might be interesting to see what things could be implemented in terms of effects.


PS - i have just updated gnome-shell, and there is another small change to the css, it seems that a new feature has been added, that being a way to open a new desktop by dragging a window, in the overview mode when using the scrolling through desktops method (not using mosaic in other words) if you drag a window to the left of the screen a big + sign should appear and if you drop the window there is will open another desktop.

anyway ive had a quick skim through the css and found some new stuff that controls this new feature, so here it is, just add it under the "info-bar-link:hover"  entry.

```
.new-workspace-area {
    border: 2px solid rgba(255, 255, 255, 0.8);
    border-radius: 10px;
    background-color: #111;
}

.new-workspace-area-internal {
    background-gradient-direction: horizontal;
    background-gradient-start: rgba(16, 16, 16, 0);
    background-gradient-end: rgba(16, 16, 16, 1.0);
    background-image: url("move-window-on-new.svg");
}

.new-workspace-area:hover {
    border: 2px solid rgba(255, 255, 255, 1.0);
    background-gradient-direction: horizontal;
    background-gradient-start: rgba(130, 130, 130, 0.9);
    background-gradient-end: rgba(16, 16, 16, 0.9);
}

.left-workspaces-shadow {
    background-gradient-direction: horizontal;
    background-gradient-start: rgba(16, 16, 16, 1.0);
    background-gradient-end: rgba(16, 16, 16, 0.0);
}

.right-workspaces-shadow {
    background-gradient-direction: horizontal;
    background-gradient-end: rgba(16, 16, 16, 1.0);
    background-gradient-start: rgba(16, 16, 16, 0);
}
```

i didnt see anything else, so if i missed something, sorry ;)

---

### Post by mooseman1618 on 2010-03-16
I think the option to change between different effects would be a great addition to gnome shell.

---

### Post by techno-mole on 2010-03-17
Before I send an e-mail to the gnome shell mailing lists I thought I would make sure I have the ideas/features people have mentioned listed.

So if you have an idea,sensible preferably ;) please post in this thread and after a day or 2 I will e-mail the gnome shell people with a feature request.

at the moment I have the following (I'm not mentioning names, mainly because I can't remember exactly who mentioned it, so sorry in advanced, and I'm not taking any credit for the ideas, I shall just post as the gnome shell users community)

[LIST]
[*]1 - the ability to change the zoom in/out effect when activating the hot corner. eg - to a fade in/out effect.
[*]2 - the ability to edit themes from within gnome shell, eg - an embedded editor,or through gconf etc etc
[*]3 - the ability to change where the hot corner is, eg - moving it from the top left to elsewhere so as not to interfere with window bar buttons that are aligned to the left (as is the case with lucid)
[*]4 - the ability to change the shape of the desktop previews in mosaic mode, eg - rounding of the corners, or making the previews circles etc
[*]5 - the ability to use (easily) images for the backgrounds of the various gnome shell aspects. eg - using a different image for the overview and app menus etc.
[/LIST]

anything else I've missed please feel free to add and also if you have any ideas please again feel free to add them, and I will leave it for a few days and then send an e-mail to the gnome shell mailing lists.
Hopefully some one will read it, but i can't say either way, but I will let you know of any responses I get.

cheers

---

### Post by k3lt01 on 2010-03-17
I know they are busy getting G-S working well and adding new bits to G-S but I would like to see some effort in adding some 2.x features. Things such as incorporating applets (weather specifically) into the G-S "panel".

Making a G-S specific Gnome-Preferences would also be nice. I got caught out the other day playing around only to find nothing changed because things like Main Menu doesn't work in G-S.

Last but not least, in this post anyway, I think they need to work on the disappearing mouse pointer problem. Alt-Tabbing just isn't for me even though I can do it, it is alot harder to alt-tab continuously to an app or folder than it is to mouse to it, but you can't mouse to it if the mouse indicator keeps disappearing when your not in the workspace.

Making it pretty is all well and good, and I admire your efforts and those of others to help us change it so it does look unique for us, but the little things (functionality) seem to be forgotten in all of this.

---

### Post by techno-mole on 2010-03-17
curious, i dont have a problem with the mouse disappearing, well it only happens once and then hitting " alt+f2 " and typing either "r" or "restart" and hitting enter solves it.

but i agree that even this is not a good way to go about things, i will add both your comments to the list, and eventually the e-mail i send.

I would like to get into the js and various other aspects to tweak the functionality but my js sucks big time and i wouldnt even know where to start with the clutter/muttery type stuff.

---

### Post by steveacab on 2010-03-17
Whot is the part of code for edit the color of "activies menu"?

---

### Post by techno-mole on 2010-03-17
> **steveacab said:**
> Whot is the part of code for edit the color of "activies menu"?

do you mean the activities button (top left of the screen) there is a section that controls the look of the button itself and then there is a section that controls the look of the overview (the thing that opens up when clicking on activities or mousing over the corner)

the following is for the panel buttons

```
/*controls the colour of the panel buttons, eg - the activites button on the left, and the user menu on the right*/
.panel-button:active, .panel-button:checked, .panel-button:pressed 
{
   
    background-gradient-direction: vertical;
    background-gradient-start: rgba(255,128,0,1.0);
    background-gradient-end: rgba(42,27,10,1.0);
}
```

the next section is for the overview.

```
/* Overview */
/* this section controls the main colouring of the overview mode*/
.overview {
    
    background-gradient-direction: vertical;
    background-gradient-start: rgba(42,27,10,1.0);
    background-gradient-end: rgba(255,128,0,0.7);
}

```

hope this helps.

---

### Post by augias on 2010-03-17
> **techno-mole said:**
> 
[LIST]
[*]1 - the ability to change the zoom in/out effect when activating the hot corner. eg - to a fade in/out effect.
[*]2 - the ability to edit themes from within gnome shell, eg - an embedded editor,or through gconf etc etc
[*]3 - the ability to change where the hot corner is, eg - moving it from the top left to elsewhere so as not to interfere with window bar buttons that are aligned to the left (as is the case with lucid)
[*]4 - the ability to change the shape of the desktop previews in mosaic mode, eg - rounding of the corners, or making the previews circles etc
[*]5 - the ability to use (easily) images for the backgrounds of the various gnome shell aspects. eg - using a different image for the overview and app menus etc.
[/LIST]


Don't wanna rain on your parade but I'm sure that these topics are not on the developer's radar (nor should they be). It's fun to personalize but its still too early for fun superficial things to be discussed when the general layout that will support these skin-deep changes are constantly changing. 

I can answer most of your doubts about the items on your list with one word: Extensions.  

All of those things you're wondering about are extensible. [I'm using an alt+tab extension that behaves  differently from the official g-s one, for example. (no miniature window previews. they were a little unreliable for my use)]("http://dl.dropbox.com/u/208391/shell-caps/alt-tab.jpeg") That was done by a guy who's just interested in getting things to work his way and it just so happens it works for me too. Not G-S's responsibility imo.

So if you really wanna see those changes, you're gonna have to start getting independent hackers interested in studying the extensions api while the g-s devs get busy fine tuning everything thats right/wrong/mocked-up in gnome-shell :D

---

### Post by techno-mole on 2010-03-18
Granted some of those "features" may well come under extensions, however they are still things that users want, and I thought it best to list them in one place.

A lot of what people have mentioned are on the side of customization, and there are other things which would be better dealt with before say the ability to edit the look of the shell using gconf or some other method, however the ability to move where the corner activation is, in my opinion doesnt really come under extensions or customization, I have seen comments by people wanting to know if it can be moved elsewhere because of the way they use their windows, eg - window bar buttons aligned to the left, one comment I saw mentioned that every time the user went to close/minimize/maximize he activated the corner, which was affecting his usability of the shell, and therefore something that needs looking at, in my book anyway.

Something else, from my point of view is that no matter how I start the shell I have to hit alt+f2 and type restart to get the cursor to show up on the panel and in the overview mode, again a thing that affects the usability of the shell, and again from my point of view having some kind of editor to change the look is just me being lazy, but people will want to change the way it looks, in an easy way, some people find the default look hard to deal with.

From my point of view a lot of what people have mentioned is irrelevant to me personally, I dont use alt+tab or most of the other features, I just use the mosaic view and thats about it.

I think that although some of these things are small and perhaps not that important to the main development, but users seem to want them, and if the features people want arent there, then it wont get used.

So whilst it may seem pointless to list them, at least people will be aware of how users feel about it, and maybe some one will decide to write a load of extensions for it, or maybe some of the things will get implemented into the shell.

We shall see, I see no reason not to list the things people want, regardless of how small they might be. :)

---

### Post by augias on 2010-03-18
> **techno-mole said:**
> I have seen comments by people wanting to know if it can be moved elsewhere because of the way they use their windows, eg - window bar buttons aligned to the left, one comment I saw mentioned that every time the user went to close/minimize/maximize he activated the corner, which was affecting his usability of the shell, and therefore something that needs looking at, in my book anyway.

This feature reminds me of [an extension]("http://github.com/linux4kix/gnome-shell-extensions/downloads") I know about that disables the hotspot, so you don't accidentally enter overview, just clicking "activities" or your super key. This is a good example of an extension that solves that problem (maybe not ideally for some though). However i agree this should definitely become a preference to turn on and off in G-S itself. I think in the end what's going to happen is when the project is more or less done, a shell-preferences menu will have to be added to system preferences. This is probably inevitable. 

BTW tech-mole, I'm updating the theme I uploaded here to match the new css configurations that are getting pushed in the master branch. I thnk it's a good idea you do that too so anyone curious about the themes doesnt get any unexpected results. 

PS: What about making the first post include an updated gallery of user's submissions?

---

### Post by techno-mole on 2010-03-18
> **augias said:**
> This feature reminds me of an extension I know about that disables the hotspot, so you don't accidentally enter overview, just clicking "activities" or your super key. This is a good example of an extension that solves that problem (maybe not ideally for some though)

whilst this solves the problem of accidentally activating the hot spot, turning it off may not be want some want, so i agree that having the option to switch it off, or align it to the top right or bottom left etc etc is a better approach, simply disabling it seems a touch drastic to my mind.

> However i agree this should definitely become a preference to turn on and off in G-S itself. I think in the end what's going to happen is when the project is more or less done, a shell-preferences menu will have to be added to system preferences. This is probably inevitable. 


and required to my mind, a menu in the system preferences that allows the user to enable/disable features and adjust aspects of the shells behavior is a good idea, people may want to bind keys to various functions, eg - activate the overview by using the meta key/super key for example.
an easy way to do this makes it more usable, and would be a feature to be requested, or at least discussed, to see if its viable.

if you put yourself in the shoes of a new user to ubuntu (or distro running gnome) are they going to be able to use gnome shell ? its probably going to be fairly difficult for the new user to adjust their thinking from a windows mind set to an ubuntu/or other distro way of thinking, complicated configurations will be something they may want to mess with in time, but not right away, so a settings menu for gnome shell will be helpful, especially if it becomes the default setup,which i still think is a bad idea, users need to be able to choose, imposing things like this on a user seems familiar for some reason ;)

---

### Post by pabc on 2010-03-19
I've installed smoke and everything works except what I think is the overview background. It stays black despite the css of the section being;

.overview {
    
    background-gradient-direction: vertical;
    background-gradient-start: rgba(42,27,10,1.0);
    background-gradient-end: rgba(255,128,0,0.7);
}

i've copied the contents of the archive to /usr/sharegnome-shell after backing up the existing theme folder.

i'm on gnome-shell 2.28.1 / 10.04 b1. 

Sadly I only tried this theme swap after switching to 10.04 so don't know if that's the issue I'm seeing.

Any suggestions?

---

### Post by augias on 2010-03-20
> **pabc said:**
> I've installed smoke and everything works except what I think is the overview background. 
i've copied the contents of the archive to /usr/sharegnome-shell after backing up the existing theme folder.

[...]

Any suggestions?

Really important for us to know where you installed it from, as gnome shell from ubuntu's repos / Rico Tzschichholz's ppa / jhbuild from git.gnome.org are all at different intervals of up-to-date. 

I can rule our jhbuild because your install directory is in /usr/ and jhbuild installs in /home/username/

In any case, on the newest version, .overview is the correct class on the stylesheet. Can't see why it wont change. However a few months back, I also could not alter the area behind the workspaces, so I assume your version of gnome-shell is the older ubuntu-repository package. If so, i recommend [getting the ricotz ppa]("https://launchpad.net/~ricotz/+archive/testing") or installing from [source]("http://dl.dropbox.com/u/208391/Gnome-Shell.txt"). 

Good luck.

---

### Post by pabc on 2010-03-20
I just did a "update-manager -d" to get 10.04B1 and noticed gnome-shell had been upgraded during the process so I guess I got it from the ubuntu repos.

---

### Post by agrh on 2010-03-20
Just thought I'd contribute my notes on gnome-shell.css. I've re-organized a bit so it makes more sense to me and put lots of comments in, but it's just not something I'm going to finish. Nevertheless, here it is.

---

### Post by techno-mole on 2010-03-20
> **pabc said:**
> I just did a "update-manager -d" to get 10.04B1 and noticed gnome-shell had been upgraded during the process so I guess I got it from the ubuntu repos.

you should either build from source, or use the testing ppa.

i will have a look at the css, im using lucid beta 1, but im using the ppa so i shall change the default look and see what happens.

****** Update ******

just tested the smoke css on lucid beta 1 using the testing ppa, all aspects of it work, apart from the search filed and the ability to add another workspace by dragging the windows of applications to the right in overview, so i dont know why the smoke css isnt working.
my advice would be to add this - ppa:ricotz/testing to your sources list, go to --> system --> software sources and add it from there, reload and then update, it should be version 2.29 of gnome shell, and the css should work.

however the most up to date version of the gnome shell css i have is attached to the first post of this thread - [here]("http://ubuntuforums.org/showpost.php?p=8894068&postcount=1") 

there is also [this]("http://ubuntuforums.org/showpost.php?p=8997676&postcount=69") post which also has an up to date css, with a different layout to mine, so people may find it easier to understand than mine.

its the last attachment named "latest" you can edit the colouring from there, i will try and update the css for all the schemes today, or over the weekend, but please bare with me, my son is currently in the hospital (should be out today) after having an operation on both his feet, he will be in casts for 3 weeks.

i will do my best to get round to it.

cheers

---

### Post by mudrain911 on 2010-03-21
just letting you guys know i am working on a Human theme at the moment for those who want the Shell to match the old Ubuntu theme. Sorry im a bit late on the parade here... I just found this thread yesterday and im really interested because ive finally found something in ubuntu that i can help with (im a website designer so i know the code for Shell :) )

i'll post it in the next day or so.

[COLOR="Red"]* 

[3/22]: files uploaded, let me know what you think and if i need to make any changes that i may have missed.

[3/24]: Files updated...

 *[/COLOR]

---

### Post by augias on 2010-03-23
It looks really good but I'd personally have the gradient-end value for panel buttons match the overview background. It's supposed to look like a tab on a folder. ;)

---

### Post by mudrain911 on 2010-03-23
thats how i had it at first with the same thought process, but then i realized it is the only tab, so i decided to treat it as a button... i would have definitely done it that way if there was more than one tab though.

---

### Post by augias on 2010-03-24
[SIZE="5"][COLOR="Red"]~[/COLOR][COLOR="DarkOrange"]n[/COLOR][COLOR="Yellow"]/[/COLOR][COLOR="Green"]M[/COLOR][COLOR="Lime"] F[/COLOR][COLOR="Cyan"]I[/COLOR][COLOR="DarkOrchid"]X[/COLOR][COLOR="Blue"]E[/COLOR][COLOR="Indigo"]D[/COLOR][COLOR="DarkOliveGreen"]![/COLOR][COLOR="DarkRed"]![/COLOR][COLOR="Magenta"]~[/COLOR][/SIZE]

---

### Post by mudrain911 on 2010-03-24
I just fixed a few things i missed, here is the corrected version of my theme.... anyone have a theme request or a mod idea (that can be done with css of course)

---

### Post by josefcub on 2010-03-24
I just wanted to say thank you to everyone, especially techno-mole, for this thread, and all of the commentary and work done on custom G-S themes.  Thanks to you all, I have what is (for me) the perfect theme set up in G-S, (at least until they get around to making the recent documents obey some of the same CSS as the rest. ;)

You all are awesome.

Viva la transparency! :D

---

### Post by augias on 2010-03-25
I've added a transparency gradient to the overview's background and changes the hue of the app-well-active/hover buttons and decided to make a new post for it. Old post now refers to this one. 

To recap, this is a light grey theme that imo matches nicely with such themes as dust, egtk (elementary), clearlooks, mist and other themes with a grey / celeste pallet.

Themes up-todate with the git branch tip _as of March 29th._

---

### Post by mudrain911 on 2010-03-25
both of those look really good, im thinking about incorperating a background into my overview too, but im not sure if that fits the old human theme too well :) i think ill make a new theme here in a few days and try and come up with some good stuff like that!

---

### Post by augias on 2010-03-29
Hmm, some tweaking and obsessive restarting of gnome-shell has proven to me that making that overview layer transparent makes your overview experience lag. Heads up to whoever wants to play with rgba on the overview class: don't. It's snappier as a simple hex code.

---

### Post by mudrain911 on 2010-03-29
ive been having trouble with the calendar and notifications lately... they are causing my whole screen to go black or flicker, then everything goes back to normal like it never happened hah... i dont know, hopefully they will fix.

ive been messing around with alot of the javascript lately... (not anything to cause the above problem lol) and there is some interesting things in there to play with... so far the only useful things ive done is put what icons i wanted into the user menu on the right.

---

### Post by k3lt01 on 2010-03-29
> **mudrain911 said:**
> ive been having trouble with the calendar and notifications lately... they are causing my whole screen to go black or flicker, then everything goes back to normal like it never happened hah... i dont know, hopefully they will fix.The icons on my panel have been playing up for a couple of weeks now, when I start up they are ok but they "change" after a couple of minutes and the machine slowly becomes unusable (this is on my desktop). If I try to go into the user list to restart or anything in that, like change my start up programs, I have approx 5 seconds to click on the correct spot because after that the menu changes into minuscule program icons.

My gut feeling is the code isn't working very well and that it probably needs tidying up. While everything was just basic code it was fine but each new update just makes it worse for me.

---

### Post by mudrain911 on 2010-03-30
> **k3lt01 said:**
> The icons on my panel have been playing up for a couple of weeks now, when I start up they are ok but they "change" after a couple of minutes and the machine slowly becomes unusable (this is on my desktop). If I try to go into the user list to restart or anything in that, like change my start up programs, I have approx 5 seconds to click on the correct spot because after that the menu changes into minuscule program icons.

My gut feeling is the code isn't working very well and that it probably needs tidying up. While everything was just basic code it was fine but each new update just makes it worse for me.

I havent had any slowing down problems, its just when i click the clock at the top expecting the dropdown, my screen turns black. if i move my mouse or click again it goes back to normal, no problems other than that... its weird. and notifications animate fast and all, but like every 4th or 5th one the screen with flicker, and then it jus goes back to its business lol. idk, it seems like badly organized code to me, but i cant say much because i cant fix any of it :P

---

### Post by augias on 2010-04-06
Big changes in gnome shell. They principally come from the implementation of chat in notifications. It is not working perfectly, but it is working if you use empathy. The theming of it was a little strange but not difficult. Appended then are some screenshots of what's new, what's not, and the css file. njoy.

---

### Post by techno-mole on 2010-04-13
Morning people.

Funny that some have mentioned issues with the icons on gnome shell, I am planning a redesign of the icons to fit better with some of the colour schemes, that's once I get my graphics tablet working on lucid, which has been the main focus of my attention as I need it for other graphical work.

I have updated the first page of the thread and included a couple of links to various posts with new/updated themes.

I'm currently running gs from the testing ppa on lucid beta 2, it seems pretty stable, I haven't had any issues with icons, or the calender pop out, currently with the default theme until I have more time to make some new variations, again once my graphics tablet is working on lucid.

Cheers.

---

### Post by k3lt01 on 2010-04-13
> **techno-mole said:**
> Morning people.

Funny that some have mentioned issues with the icons on gnome shell, I am planning a redesign of the icons to fit better with some of the colour schemes, that's once I get my graphics tablet working on lucid, which has been the main focus of my attention as I need it for other graphical work.

I have updated the first page of the thread and included a couple of links to various posts with new/updated themes.

I'm currently running gs from the testing ppa on lucid beta 2, it seems pretty stable, I haven't had any issues with icons, or the calender pop out, currently with the default theme until I have more time to make some new variations, again once my graphics tablet is working on lucid.

Cheers.Hey Techno-Mole.

My intent when I can get the time to spend with my desktop is to do a minimal install and try G-S again. I just haven't done it yet because I am using my desktop for sorting my video and music collection and it's taking alot of time. As for my laptop while G-S will work with Lucid I find the laptops specs just aren't good enough to do G-S any justice.

---

### Post by techno-mole on 2010-04-14
I still see that as a stumbling block for gnome shell, the fact the a good few systems just won't run it, or run it well, the main reason I hope they don't make it a default option.

Anyway my tablet is working again, running nice and smooth on lucid beta 2 (fully updated) 
It's a trust tb-6300 slimline tablet, I wrote a how to for installing the driver on karmic and lucid, although the lucid section needs adjusting to allow for the new way of doing things, so as soon as i have a bit of spare time I shall set about trying to design some new icons for the various aspects of the shell.

Cheers.

---

### Post by techno-mole on 2010-04-23
I have noticed something strange this morning, whilst trying to run virtualbox while gnome shell is running.

For some reason if gnome shell is running and I run virtualbox it doesn't show the guest operating system window ? even clicking on " show " in virtualbox doesn't bring up the window.

Anyone noticed this ? or know of anyone that has ?

Cheers.

---

### Post by Merk42 on 2010-04-24
> **techno-mole said:**
> I have noticed something strange this morning, whilst trying to run virtualbox while gnome shell is running.

For some reason if gnome shell is running and I run virtualbox it doesn't show the guest operating system window ? even clicking on " show " in virtualbox doesn't bring up the window.

Anyone noticed this ? or know of anyone that has ?

Cheers.

I just tried it with both a Linux host and Windows host and was fine.
This is running the latest GNOME Shell via source and Virtualbox 3.1.6 PUEL in Karmic

---

### Post by WinterWeaver on 2010-04-27
Hi guys!

This thread has inspired me to write a little script to help manage gnome-shell themes.

Please note that it's still considered BETA, so please use at own risk.
You can get the code on github: [http://github.com/andrewebdev/gsthemer](http://github.com/andrewebdev/gsthemer)

I also wrote a short blog about it: [http://andre.engelbrechtonline.net/blog/2010/04/27/switching-themes-gnome-shell/](http://andre.engelbrechtonline.net/blog/2010/04/27/switching-themes-gnome-shell/)

I welcome any critique and tips.

PS: Disclaimer - At the time of writing the application, blog entry, and this forum post, I dont have gnome-shell installed cause my main laptop is in for repairs. The application should work in theory, as I created "dummy" gnome-shell folders to test theme switching etc.

Enjoy

---

### Post by petejk on 2010-05-03
2 things that made gnome shell usable for me as my main environment:

[http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome+shell&page=168](http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome+shell&page=168)
my post on installing gnome3 session (debian package) - scroll down to petejk

and moving the close/min/max buttons to the left,
sudo gconf-editor
click to desktop/gnome/shell/windows

change value to :minimize,maximize,close

This means I can log on into gnome3
plus, the button layout is the same as lucid

---

### Post by JustinBenner on 2010-05-10
I spent a few hours figuring out what to edit last night, and I thought I'd post what I learned for the other noobs like me, that way they can customize it easily and in less time.

**1. Open gnome-shell.css with gedit**

Open a terminal and type: sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css

**2. Get comfortable reloading GNOME Shell to test your work.**

To do this, just type this in terminal: gnome-shell --replace

You will need to do this before you can see any of the changes you've made to the Shell.

**3. Edit the top panel.**

The top panel can be edited to look however you want. You can use a gradient or a background image, although the background image has to be scaled to the appropriate size or it won't display properly.

Simply look for panel { in gnome-shell.css, and underneath it, there are a number of options. The first is the direction of the gradient, if any. Default is vertical, but it can be done horizontally as well. The other options are background-gradient-start and background-gradient-end. Simply alter these colors to reflect how you want the gradient to look. Go [here]("http://www.computerhope.com/htmcolor.htm") for some basic HTML color codes.

The other option, as mentioned, is a background image. To set this up, erase all the code dealing with the gradient, and call a background-image up. It should now look like this:

#panel {
    color: #ffffff;
    font-size: 12px;
    background-image: url("topbackground.xpm");
}

I am using a X Pixmap, but you can also use JPEGs. Keep in mind that the image has to be a particular size, otherwise it will be scaled automatically and won't fit the panel. I suggest starting GIMP, and starting with an image that is around 30 x 900 or so, inserting the image, reloading gnome-shell (gnome-shell --replace in terminal), adjusting the image size and so on, until it fits. Like I said, I'm not an expert, so there may be a better way - I just don't know it!

[EDIT] CSS3 seems to address this issue by letting you set the background-image-size, either as a percentage or an absolute value. This would have been useful here.

**4. Change the font used on the panel**

To change the font used on the panel, look for .panel-button {

Underneath it is your options. I left the padding and border-radius alone, but I did change the font. Now the function looks like this:

.panel-button {
    padding: 4px 12px 3px;
    border-radius: 5px;
    font: 12px trebuchet ms;
}

Since I found the font on the default theme to be a little too large in general, I took a look through the rest of the panel functions, and changed text sizes down to 12 or 10 px, when they were 14 or 16 px before.

**5. Edit the appearance of the Application, Recent Document and Places buttons in Overview**

To edit the appearance of these buttons, look for: .section-header {

You can set the gradient that appears on the buttons in this function. Mine looks like this:

.section-header {
    border: 1px solid #AAABBA;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(29,40,59,0.98);
    background-gradient-end: #000000;
    font-weight: bold;
    font-size: 12px;
}

**6. Change the background of the menu area (behind Places, Recent Documents, etc.)**

Find #dash {

You can either change the gradient around, or make your own custom image (just like you did for the top panel). Mine looks like this:

#dash {
    color: #FFFFFF;
    background-image: url("background.jpg");
    padding: 0px 14px;
}

**7. Change the appearance of the Applications and Recent Documents menu...**

Find .dash-pane {

Alter the background-color, or put in your own image. I personally use a nice dark color, then give it transparency for that sexy look. Here is what mine looks like:

.dash-pane {
    background-color: rgba(52,56,106,0.45);
    border: 1px solid #FFFFFF;
    padding: 4px;
    spacing: 4px;
}

[B]8. Comments/Suggestions

[/B] I realize this is a very basic guide, so feel free to correct me if I'm wrong or throw out any suggestions. Just thought this would make it a bit easier.

---

### Post by JustinBenner on 2010-05-10
I have noticed that many of the themes here have a different look to their Applications Menu. Mine currently displays an application icon, with the name beside it, and a description underneath. Many of the themes here just show thumbnails, with the name below. I would much prefer that setup.

Can anyone explain to me how that is done?

---

### Post by augias on 2010-05-11
> **JustinBenner said:**
> I have noticed that many of the themes here have a different look to their Applications Menu. Mine currently displays an application icon, with the name beside it, and a description underneath. Many of the themes here just show thumbnails, with the name below. I would much prefer that setup.

Can anyone explain to me how that is done?

Yes. You're most likely using the gnome-shell hosted on ubuntu 9.10's unkempt repositories while everyone else here is either using an up to date PPA repository or building gnome-shell from the source.

---

### Post by JustinBenner on 2010-05-11
> **augias said:**
> Yes. You're most likely using the gnome-shell hosted on ubuntu 9.10's unkempt repositories while everyone else here is either using an up to date PPA repository or building gnome-shell from the source.

Thank you :)

---

### Post by Ultra_Man on 2010-05-30
How do I use Lucida Grande Bold as my font for .panel-button?

---

### Post by amato on 2010-06-02
[This]("http://4.bp.blogspot.com/_-fQgYJwrvDA/S-rZD-AgbhI/AAAAAAAAAlg/0unA9HpPd84/s1600/gnome-shell-oberon-calen.png") is my new gnome shell theme, for download and more information [here]("http://www.pcfaidate.com/2010/05/il-mio-primo-tema-per-gnome-shell-e.html") :)

---

### Post by Ultra_Man on 2010-06-02
Hey guys, I made my own theme kinda like smoke, but with lots more blue, up to date, and with the elementary themes in mind(kinda).

The theme is almost done, just need to fix the new arrow menus, make the chat nicer, fix the app and recent document menus. But I'll show you what I've done for now.

PS: REMEMBER TO RENAME TO gnome-shell.css.

EDIT: Finished my theme. Updated the file.

PSS: REMEMBER TO RENAME TO gnome-shell.css

---

### Post by deadlockedgamer on 2010-07-18
This was only tested on the gnome shell in the default Ubuntu 10.04 repo so be warned! also please read the extra notes before installing as it has additional instruction to make it look right.

---

### Post by deadlockedgamer on 2010-07-18
ok here they are

---

### Post by deadlockedgamer on 2010-07-18
use alt f2 and run gnome-shell --replace then when you need to test updates save alt f2 type r and hit enter this resets gnome shell and I found it quicker, you can also type restart I think it is but I only used r .

---

### Post by Xilantra on 2010-08-01
Hello everyone, Im new here, so sorry if there's anything wrong.
Ive made my theme last night..the theme use glowing purple as the main color. Feel free to critique before I upload them.Thanks!

:popcorn:

p/s: Does anyone know how to change the workspace white border color?

---

### Post by Half-Left on 2010-08-09
I've made 3 GNOME Shell themes. Ambiance, Sonar and Elementary.

you can download them from my page. [http://half-left.deviantart.com/](http://half-left.deviantart.com/)

---

### Post by Turtle.net on 2010-10-14
I am shocked ! Nobody anmswered your post ?!
Anyway, your theme is really nice. Dark and purple glowing.
I love

---

### Post by ibuclaw on 2010-10-16
Wow, Gnome-shell has grown up a bit since I last looked... I am in :shock:

---

### Post by Half-Left on 2010-10-17
GNOME Shell is really nice in regard to making themes for it. CSS3 makes it easy.

---

### Post by justiceandfreedom on 2010-10-17
Half-Left, your themes are nice but they are very slow on my computer. I just installed gnome-shell from git.gnome.org and it is fast with the default theme, so how can another theme slow it down?

---

### Post by Half-Left on 2010-10-17
> **justiceandfreedom said:**
> Half-Left, your themes are nice but they are very slow on my computer. I just installed gnome-shell from git.gnome.org and it is fast with the default theme, so how can another theme slow it down?

GNOME Shell Git is slow anyway, 2.31.5(comes with Maverick) is much smoother. It's down to GNOME Shell not optimising shadows and such with their new changes.

---

