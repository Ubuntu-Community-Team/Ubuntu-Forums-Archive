---
title: "New Clearlooks-Cairo Themes!"
date: 2005-11-19
forum: Art &amp; Design
---

### Post by Gnobody on 2005-11-19
**UPDATED:** Updated to 0.6
Here are some new Clearlooks-cairo themes! They all support animation, and have coloured scrollbars.  This is only the first release of this pack, so please feel free to add themes to it, or modify the existing ones.  I am also working on some more unique themes based off this new engine.

************************************************************************
**HOW TO INSTALL:**
Make sure you have build-essential, automake, and the gtk2-dev files and any other dependancies, if you haven't already, retrieve them via Synaptic.

The first thing you want to do is grab the latest CVS build of Cairo:

Open a gnome-terminal by hitting: alt+F2 and type in: gnome-terminal

```
Type: [I]cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo co cairo
Then: cd cairo 
Then: ./autogen.sh --prefix=/usr
Then: make
Then: make install[/I]
#(enter in your user password)

Now you need to install the clearlooks-cairo engine from gnome.org cvs:
[i] cvs -z3 -q -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co gtk-engines
Then: cd gtk-engines
Then: ./autogen.sh --prefix=/usr
Then: make
Then: sudo make install 
#(enter in your user password)
[/i]

You will need to unzip the themes to a new directory, then *cd* to that directory in gnome-terminal and type: *sudo cp -rf * /usr/share/themes/*

```
Now you'll want to kill your xserver (ctrl+alt+backspace), then log back in and enjoy the new Clearlooks-cairo themes!!
************************************************************************

[[IMG]http://ubuntuforums.org/gallery/files/3/9/3/7/intro.jpg[/IMG]]("http://www.ubuntuforums.org/gallery/showimage.php?i=1627&original=1&c=4")

---

### Post by GoA on 2005-11-19
Thanks. I found out that because I had installed the clearlooks cairo theme before with guide on breezy guides (just a simple debian package), I didn't have to do the cvs part but I just extracted the new themes into theme folder and they work out straight. And the green one is nice and calming. :)

---

### Post by varunus on 2005-11-19
Gnobody,

You can also patch the gtk-engines CVS source with SchAmane's patch to add more animation to clearlooks!  His newest patch has radio buttons, checkboxes, and progress bars animated...I think the one in CVS just does checkboxes fade in and progress bars.

Instructions on how to patch are here:
[http://real.wilbury.sk/~drom/patch/](http://real.wilbury.sk/~drom/patch/)

To sum it up, just get the patch 0.8.2 from here and patch: [http://files.myeburg.net/work/progressbar_anim/](http://files.myeburg.net/work/progressbar_anim/)

Then compile and install as normal.  (Patch from the gtk-engines/engines/ folder.)

I also like the new focus ring that just got added a couple days back...

I really like the way Dropline Neu brown looks with the new patch after you add scrollbar color...the first brown theme i've actually liked.  The color scheme isn't very far off of human, though, so I don't know why...(And I can upload the gtkrc here if you want.)

---

### Post by Gnobody on 2005-11-19
Thanks Varunus, SchAmane's patches are slowly making their way into the cvs version.  I believe Richard Stellingwerff is hacking on Clearlooks straight-time this week.  :razz:  

I hope Dapper has a new theme, the redish-brown human is pretty ugly.  Brown can look really good though, and I hope the artwork team sticks with something like I posted above. :KS

---

### Post by Stormy Eyes on 2005-11-19
**gnobody**, you missed a step. You're supposed to do
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo login
```
and press "Enter" at the password prompt for anonymous login first, and *then* do
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo co cairo
```

---

### Post by Stormy Eyes on 2005-11-19
Also, for the gtk-engines, the required steps are as follows:
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo login
```
and then
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo co cairo-gtk-engine
```

---

### Post by bvc on 2005-11-19
Is the new;
animation = TRUE
part of cvs clearlooks? Guess so. Well I had made these before that addition.
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-Cairo-gperfect.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-Cairo-gperfect.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-red_cairo.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-red_cairo.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/ubuntu/Human/gtk/cairo/Human-Cairo.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/ubuntu/Human/gtk/cairo/Human-Cairo.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/ubuntu/gtk/cairo/Human-Hedgehog.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/ubuntu/gtk/cairo/Human-Hedgehog.tar.gz)

---

### Post by varunus on 2005-11-19
[QUOTE=Stormy Eyes]Also, for the gtk-engines, the required steps are as follows:
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo login
```
and then
```
cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo co cairo-gtk-engine
```[/QUOTE]

Actually, Stormy Eyes, the theme at cairographics.org is outdated.  The newest CVS clearlooks cairo is now in official GNOME cvs as gnobody stated above.  SchAmane's patches are slowly being added as well (I think his 0.6 version has already been added).  He is up to 0.8 on patches, though.

bvc, if you apply SchAmane's patch, I think you need the animation=TRUE option.  I don't think you do with straight CVS from gnome, only after the patch, but the patched one is so much nicer...

---

### Post by Gnobody on 2005-11-19
[QUOTE=varunus]Actually, Stormy Eyes, the theme at cairographics.org is outdated.  The newest CVS clearlooks cairo is now in official GNOME cvs as gnobody stated above.  SchAmane's patches are slowly being added as well (I think his 0.6 version has already been added).  He is up to 0.8 on patches, though.

bvc, if you apply SchAmane's patch, I think you need the animation=TRUE option.  I don't think you do with straight CVS from gnome, only after the patch, but the patched one is so much nicer...[/QUOTE]

I can confirm that, with the GnomeCVS version you do not need to give it any special options.

---

### Post by bvc on 2005-11-19
[QUOTE=varunus]Actually, Stormy Eyes, the theme at cairographics.org is outdated.  The newest CVS clearlooks cairo is now in official GNOME cvs as gnobody stated above.  SchAmane's patches are slowly being added as well (I think his 0.6 version has already been added).  He is up to 0.8 on patches, though.

bvc, if you apply SchAmane's patch, I think you need the animation=TRUE option.  I don't think you do with straight CVS from gnome, only after the patch, but the patched one is so much nicer...[/QUOTE]thx! Thought it was weird. What is nicer about the patched? I thought it just enabled animation.

---

### Post by super on 2005-11-19
@bvc
i see you have 'ish-red' for cairo available. any chance of doing 'ish-aqua' also?
i am currently using it with the clearlooks-cairo engine but the contrast is a little low on certain things.

---

### Post by bvc on 2005-11-19
[QUOTE=super]@bvc
i see you have 'ish-red' for cairo available. any chance of doing 'ish-aqua' also?
i am currently using it with the clearlooks-cairo engine but the contrast is a little low on certain things.[/QUOTE]

-copy the theme dir to somewhere and rename it to whatever (ish-aqua_cairo?)
-open the gtkrc in gedit
-replace all
#ea4444
with
#93c1ff
-put the new theme in ~/.themes

---

### Post by bvc on 2005-11-19
oops...posted in the wrong thread!
what happen to the delete button?
I meant to post in the Opus3 thread. Sorry!

---

### Post by varunus on 2005-11-20
> thx! Thought it was weird. What is nicer about the patched? I thought it just enabled animation.

bvc,

In the current GNOME cvs version, checkboxes fade in, and progress bars are animated.  That's it.  There is no option to disable these animations either.

If you patch with SchAmane's newest patch, checkboxes fade in and out, radio buttons fade in and out, and progress bars are animated.  (Also, the code is much cleaner/faster/nicer, and uses a HashTable instead of a List, allowing a lot more animation to be done on this framework.)  The newest patch also allows for animation to be disabled by adding or removing "animation=TRUE" from the gtkrc.  Some people just don't like the animation, it seems...

And very nice with the Opus 3 theme!

---

### Post by lizardking on 2005-11-21
Where I can find the original Clearlooks color for cairo 's gtkrc?

---

### Post by darkmatter on 2005-11-21
[QUOTE=lizardking]Where I can find the original Clearlooks color for cairo 's gtkrc?[/QUOTE]

If you installed the Cairo enabled Clearlooks engine, it's located under /usr/share/themes/Clearlooks...same as before you updated the engine.

---

### Post by bvc on 2005-11-22
[QUOTE=lizardking]Where I can find the original Clearlooks color for cairo 's gtkrc?[/QUOTE]
```
  fg[NORMAL]        = "#000000" # black
  fg[PRELIGHT]      = "#000000" # black
  fg[SELECTED]      = "#ffffff" # white 
  fg[ACTIVE]        = "#000000" # black
  fg[INSENSITIVE]   = "#b5b3ac" # dark beige

  bg[NORMAL]	    = "#e8e5de" # light beige
  bg[PRELIGHT]      = "#f9f7f3" # very light beige
  bg[SELECTED]	    = "#5598d7" # deepsky
  bg[INSENSITIVE]   = "#e8e5de" # beige
  bg[ACTIVE]        = "#c9c3b4" #"#d7d3ca" # dark beige

  base[NORMAL]      = "#ffffff" # white 
  base[PRELIGHT]    = "#5f8ec4" # dark beige
  base[ACTIVE]      = "#a69f91" # darker deepsky
  base[SELECTED]    = "#5598d7" # deepsky
  base[INSENSITIVE] = "#e8e5de" # beige

  text[NORMAL]      = "#000000" # black
  text[PRELIGHT]    = "#000000" # black
  text[ACTIVE]      = "#ffffff" # white
  text[SELECTED]    = "#ffffff" # white
  text[INSENSITIVE] = "#b5b3ac" # dark beige
```

---

### Post by dude2425 on 2005-11-22
Could somebody please fix-up Clearlooks-GNOME so that it looks correct with Clearlooks w/ Cairo? It's from the BigPack IIRC, and I've tried to make it work like all the other Clearlooks w/ Cairo are supposed to look ([post #96]("http://ubuntuforums.org/showthread.php?t=89056&page=3")) but I can't seem to get a few things working like the focus ring thingy, or the colored trail thing on the sliders. I've uploaded two images showing the difference between what I've fixed so far in Clearlooks-GNOME with Clearlooks-Humanitarian. The orriginal Clearlooks-GNOME by bvc can be found here:
[http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz](http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz)
which includes Clearlooks-GNOME.

---

### Post by benplaut on 2005-11-22
What is the name of that theme preview app?! i've been looking all over for it!
[QUOTE=dude2425]Could somebody please fix-up Clearlooks-GNOME so that it looks correct with Clearlooks w/ Cairo? It's from the BigPack IIRC, and I've tried to make it work like all the other Clearlooks w/ Cairo are supposed to look ([post #96]("http://ubuntuforums.org/showthread.php?t=89056&page=3")) but I can't seem to get a few things working like the focus ring thingy, or the colored trail thing on the sliders. I've uploaded two images showing the difference between what I've fixed so far in Clearlooks-GNOME with Clearlooks-Humanitarian. The orriginal Clearlooks-GNOME by bvc can be found here:
[http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz](http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz)
which includes Clearlooks-GNOME.[/QUOTE]

---

### Post by dude2425 on 2005-11-22
It's called "The Widget Factory" by Richard Stellingwerff:
[http://www.stellingwerff.com/?p=9](http://www.stellingwerff.com/?p=9)
[http://www.stellingwerff.com/?p=10](http://www.stellingwerff.com/?p=10)

Have fun with it.

---

### Post by super on 2005-11-22
[QUOTE=bvc]-copy the theme dir to somewhere and rename it to whatever (ish-aqua_cairo?)
-open the gtkrc in gedit
-replace all
#ea4444
with
#93c1ff
-put the new theme in ~/.themes[/QUOTE]

forgot to say thank-you.
it works perfectly. :D 
i also had to change the menu-highlight to black.

---

### Post by bvc on 2005-11-23
[QUOTE=dude2425]Could somebody please fix-up Clearlooks-GNOME so that it looks correct with Clearlooks w/ Cairo? It's from the BigPack IIRC, and I've tried to make it work like all the other Clearlooks w/ Cairo are supposed to look ([post #96]("http://ubuntuforums.org/showthread.php?t=89056&page=3")) but I can't seem to get a few things working like the focus ring thingy, or the colored trail thing on the sliders. I've uploaded two images showing the difference between what I've fixed so far in Clearlooks-GNOME with Clearlooks-Humanitarian. The orriginal Clearlooks-GNOME by bvc can be found here:
[http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz](http://kernow-hosting.com/~bvc/theme/gtk/clearlooks/Clearlooks-Big_Pack-0.6.x.tar.gz)
which includes Clearlooks-GNOME.[/QUOTE]

make the bg[SELECTED] darker
```
  fg[NORMAL]			= "#000000"
  fg[PRELIGHT]			= "#000000"
  fg[ACTIVE]			= "#4A463C"
  fg[SELECTED]			= "#ffffff"
  fg[INSENSITIVE]		= "#BAB5AB"
  
  bg[NORMAL]			= "#EAE8E3"
  bg[PRELIGHT]			= "#F3F1EC" #F0EEE9
  bg[ACTIVE]			= "#CBC7BD"
  bg[SELECTED]			= "#90917e"
  bg[INSENSITIVE]		= "#F3F1EC"

  base[NORMAL]			= "#ffffff"	
  base[PRELIGHT]		= "#ADAE9B"
  base[ACTIVE]			= "#CBC7BD"
  base[SELECTED]		= "#ADAE9B"
  base[INSENSITIVE]		= "#EAE8E3"	

  text[NORMAL]			= "#000000"
  text[PRELIGHT]			= "#000000"
  text[ACTIVE]			= "#4A463C"
  text[SELECTED]			= "#ffffff"
  text[INSENSITIVE]		= "#BAB5AB"
```

---

### Post by dude2425 on 2005-11-23
GREATY GOOGLY OOGLY THAT WORKED!
I am so glad there are people out there who know more than me lol.

* Weeee! Click click!

---

### Post by bvc on 2005-11-25
you'll have to add the animated option to the gtkrc
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-aqua_cairo.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-aqua_cairo.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-purple_cairo.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-purple_cairo.tar.gz)

I see the check/option are light but since this is in devel, I don't have the patched animation, and I do not know where this is going til it is included in clearlooks, I didn't bother trying to improve visibility.

---

### Post by chadwick359 on 2005-11-29
Sweet, this looks really good. But I do have one problem. When I click on a radio button, it doesnt animate/fade actually, it doesn't change at all, instead, it just stays the same till I mouse over it again, and it snaps to the opposite status.

---

### Post by bvc on 2005-11-29
Anyone running the gnome cvs version of clearlooks having problems? I was about to upgrade to get the latest animations and someone said it wasn't working well.

---

### Post by varunus on 2005-11-29
I'm running the newest GNOME CVS version.  It has all the patches, and runs great for me...the evolution bug is fixed, and I haven't had any crashes.

---

### Post by j_baer on 2005-11-30
Somewhere along the way I missed something.

I compiled as directed by the how-to, installed the themes as directed, and rebooted to re-start X but when I click on one of the themes I get something much simplier than expected. In fact it looks much like a plain X theme.

Here is the error I believe is causing the trouble ...

the following font backends:
  FreeType: no
  Win32: no
  ATSUI: no

and the following features:
  PNG functions: no
configure: error: Cairo requires at least one font backend.
                  Please install freetype and fontconfig, then try again:
                  [http://freetype.org/](http://freetype.org/)  [http://fontconfig.org/](http://fontconfig.org/)


:(

---

### Post by Gnobody on 2005-12-04
BUMP!  I added a few more themes.

---

### Post by bvc on 2005-12-04
couldn't stand the blue in Hedgehog, eh? :p 
Took a little getting used to for me, but I like it now. :D

---

### Post by Gnobody on 2005-12-04
[QUOTE=bvc]couldn't stand the blue in Hedgehog, eh? :p 
Took a little getting used to for me, but I like it now. :D[/QUOTE]

lol, you noticed that!  Yeah it just doesn't look right IMO, so I modded it.

---

### Post by muchmusic on 2005-12-05
Hello,

Thank you for the instructions.

How do I know I have installed properly? No new themes in .themes that I can tell - advice?

Thanks!

---

### Post by raublekick on 2005-12-05
[QUOTE=GoA]Thanks. I found out that because I had installed the clearlooks cairo theme before with guide on breezy guides (just a simple debian package), I didn't have to do the cvs part but I just extracted the new themes into theme folder and they work out straight. And the green one is nice and calming. :)[/QUOTE]


I followed this method as well, and it works pretty well. The only problem I am having is that any program that requires sudo (or a password) such as Gnomad2 or Synaptic reverts back to nasty GTK1 style buttons. Can anyone explain why this is happening now? 

Great work guys, these are looking nice.

---

### Post by GazaM on 2005-12-05
Which theme folder is it in? I have noticed that themes which are in /home/'myusername'/.themes/ only work for non-sudo apps, whereas themes in /usr/share/themes/ work in sudo apps as well. This is because when an app is run with sudo, it is run as the 'root' user account, which cant use themes from your home folder, only from system wide locations or it's own home folder.

---

### Post by raublekick on 2005-12-05
that would probably explain it. i'll move them into usr/share/themes when i get home. 

thanks!

---

### Post by muchmusic on 2005-12-05
[QUOTE=muchmusic]Hello,

Thank you for the instructions.

How do I know I have installed properly? No new themes in .themes that I can tell - advice?

Thanks![/QUOTE]

I figured it out.

btw the animated scroll is definitely in CVS now. I love the checkboxes especially, very nice touch.

---

### Post by Rotarychainsaw on 2005-12-05
Can someone help me or point me in a direction? I couldn't find cairo in the gnome cvs, so I used the cairographics.org cvs. got the gtk-engines cvs fine. then those patches wouldn't work. It said 13 of 13 hunks failed. then I tried to compile it anyway and it failed. Im gonna re download the gtk-engines cvs and just compile that with no patches right now.

edit: So, recomplied the plain clearlooks from gnome cvs. it compiled, but it doesn't really work. Firefox freezes X, alot of stuff is odd. so whats up?

more edit: Hello???? Is there something obvious Im missing, like renderaccel should be turned off for this to work right? I can look at the themes in twf and click checkboxes (very nice) but not much more. Are these themes THAT unstable or is it me?

---

### Post by Gnobody on 2005-12-09
I have renderaccel turned off, but you should follow the instructions from the first page.  Remember you must restart X to get it to work correctly.

---

### Post by Rotarychainsaw on 2005-12-09
AH, a reply! ;) yeah I've restarted X many many times switching between cairo and non-cairo themes. I'm still gonna poke around and see what I can do, but I'm still kind of lost.

edit: looks like switching off renderaccel in the xorg.conf fixed the horrible instability!! I like the gnome cvs clealooks the best so far. Oneodd thing is that my round corner clearlooks window borders have gone. Im forced to use the sharp corner human style. I don'tknow why...

---

### Post by Iandefor on 2005-12-13
I must say, I got these cairo themes working, and the majority of them work faster than my old GTK+ themes. Thank you so much!

---

### Post by Kevin on 2005-12-13
If you feel like installing them, the new nVidia drivers, 1.0-8174 enabled me to turn RenderAccel back on while using cairo themes.

---

### Post by tanari on 2005-12-14
Help please!
After installing clearlooks-cairo text in all apps starts to disappear sometimes :(

How can I completely uninstall clearlooks-cairo?

---

### Post by Gnobody on 2005-12-14
sudo apt-get remove gtk-engines-clearlooks && sudo apt-get install gtk-engines-clearlooks

---

### Post by angrykeyboarder on 2005-12-16
[QUOTE=Gnobody]**UPDATED:**

```
Type: [I]cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo co cairo

```[/QUOTE]

humm. OK. here we go..

```
$ cvs -d :pserver:anoncvs@cvs.cairographics.org:/cvs/cairo
Usage: cvs [cvs-options] command [command-options-and-arguments]
  where cvs-options are -q, -n, etc.
    (specify --help-options for a list of options)
  where command is add, admin, etc.
    (specify --help-commands for a list of commands
     or --help-synonyms for a list of command synonyms)
  where command-options-and-arguments depend on the specific command
    (specify -H followed by a command name for command-specific help)
  Specify --help to receive this message

The Concurrent Versions System (CVS) is a tool for version control.
For CVS updates and additional information, see
    the CVS home page at http://www.cvshome.org/ or
    Pascal Molli's CVS site at http://www.loria.fr/~molli/cvs-index.html
``` Uhh.. It ain't workin...

---

### Post by tanari on 2005-12-16
[QUOTE=Gnobody]sudo apt-get remove gtk-engines-clearlooks && sudo apt-get install gtk-engines-clearlooks[/QUOTE]

thanks!

But why with new cairo themes text disappears sometimes?

---

### Post by angrykeyboarder on 2005-12-23
[quote=GoA]Thanks. I found out that because I had installed the clearlooks cairo theme before with guide on breezy guides (just a simple debian package), I didn't have to do the cvs part but I just extracted the new themes into theme folder and they work out straight. And the green one is nice and calming. :)[/quote] 
Where do I find *breezy guides*?


[Edit: Deisregard my question. I have since figured out [what you mean]("http://doc.gwos.org")t.]

---

### Post by Gnobody on 2005-12-24
Can somebody please tell me why in all the clearlooks-cairo themes that there is a difference in colour between gnome-panel and the gnome-panel menu?

I posted a screenshot below to show what I mean ->

---

### Post by bvc on 2005-12-24
It's not anything in the gtkrc's because if you use a 0.6.x cl theme it still does it. So it would have to be in the engine.

---

### Post by Gnobody on 2005-12-27
[QUOTE=bvc]It's not anything in the gtkrc's because if you use a 0.6.x cl theme it still does it. So it would have to be in the engine.[/QUOTE]


The latest update of Clearlooks-cairo seems to fix this issue now!

---

### Post by Gnobody on 2005-12-28
*UPDATED* :p

---

### Post by dude2425 on 2005-12-28
I think there should be new color schemes added. I've yet to find a pink or purple theme for Clearlooks-Cairo. It'd be interesting to see what y'all can come up with. Pink has always been a very powerful, and influential color when combined with other colors, or when simply taking advantage of all the different shades of pink.

---

### Post by bvc on 2005-12-29
I will start on the Big_Pack for CL-Cairo. You will find them, as I add them here;
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/)

You can get them individually or you can get them ALL in one pkg;
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ALL-CL-Big_Pack-Cairo.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ALL-CL-Big_Pack-Cairo.tar.gz)
as I add them

dude2425, ish-purple and pink is there. I will not update 'ish' specifically but the ish color schemes I decide to add will be there as well.

---

### Post by dude2425 on 2005-12-29
[quote=bvc]dude2425, ish-purple and pink is there. I will not update 'ish' specifically but the ish color schemes I decide to add will be there as well.[/quote]
I kind of like it, but I was never really fond of the whole 'ish' set. I was kind of hoping for whole themes based off different schemes of pink and purple, not just a mod for an existing series of themes. I like how all the colors of some themes go together for a more whole effect, like the default clearlooks them, or gPerfect, or Humanitarian.
Also, are there any resourses I can use to start hacking up my own themes for clearlooks? A guide, or knowledge base or tips and tricks for beginers? I like to have themes that match my wallpapers. It'd be great to be able to hack up a nice theme instead of searching for a different wallpaper when the theme I want doesn't exist.

---

### Post by bvc on 2005-12-30
Yes, the gray gets old fast and only looks good with the ish metacity theme.

I don't know how many from the Big_Pack I will be updating. See, many of them look good because of the extra stuff I put in there. Some may or may not work with the new engine...I haven't tried, and probably won't. It's too time consuming. This is really why I've been debating releasing anything. Until an official release of clearlooks-cairo is made, we don't know what we can and can not do, or what we will have to change, if anything.

So, I wouldn't get crazy with a lot of colors like in Sunset, just copy the default theme>rename> and change the colors.

The default color parameters are found at the top of the gtkrc```
  fg[NORMAL]        = "#000000" # black
  fg[PRELIGHT]      = "#000000" # black
  fg[SELECTED]      = "#ffffff" # white 
  fg[ACTIVE]        = "#000000" # black
  fg[INSENSITIVE]   = "#b5b3ac" # dark beige

  bg[NORMAL]	    = "#e8e5de" # light beige
  bg[PRELIGHT]      = "#f9f7f3" # very light beige
  bg[SELECTED]	    = "#5598d7" # deepsky
  bg[INSENSITIVE]   = "#e8e5de" # beige
  bg[ACTIVE]        = "#c9c3b4" #"#d7d3ca" # dark beige

  base[NORMAL]      = "#ffffff" # white 
  base[PRELIGHT]    = "#5f8ec4" # dark beige
  base[ACTIVE]      = "#a69f91" # darker deepsky
  base[SELECTED]    = "#5598d7" # deepsky
  base[INSENSITIVE] = "#e8e5de" # beige

  text[NORMAL]      = "#000000" # black
  text[PRELIGHT]    = "#000000" # black
  text[ACTIVE]      = "#ffffff" # white
  text[SELECTED]    = "#ffffff" # white
  text[INSENSITIVE] = "#b5b3ac" # dark beige
```

anything below that over_rides the default. For example```
style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = "#f1efeb"
  bg[INSENSITIVE]   = "#eceae4"
  bg[PRELIGHT] = "#f7f6f4"
}
```
sets diff colors than the default at the top of the gtkrc, for the buttons.

Run an app like [twf]("http://www.stellingwerff.com/?p=9") and make sure all your colors are correct.

---

### Post by dude2425 on 2005-12-30
Hmm, that's pretty much how I thought it went. I just went screwing around with it, and think I've got something of quality now. Please judge it, change things that you think will need changing, etc.
[Here's a screenshot]("http://screenshots.haque.net/screenshots/view/30475/screenshot-30475.png") of The Widget Factory showing off.
I was just changing values of the default clearlooks theme to obtain this, so if you find something you don't like, and you know how to fix it, go right ahead, fix it, and then tell me what it was you fixed, and how.

UPDATE: I tweaked a whole lot more, and now it looks even better, and I also added a nice looking purple theme to it too.
UPDATE AGAIN: OK, I am pretty sure I can call this final. It's a pink theme, and a purple theme. Screenshot's of the final version attached too.

---

### Post by bvc on 2005-12-31
nice job!
what I would change?

_Pink_
I changed;
bg[INSENSITIVE]   = "#F1ECED"
base[INSENSITIVE] = "#F1ECED"

base[PRELIGHT]    = "#F9EDED"

fg[INSENSITIVE]   = "#B88990"
text[INSENSITIVE] = "#B88990"

```
style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = "#F6D1D8"
  bg[INSENSITIVE]   = "#E0BBC2"
  bg[PRELIGHT]      = "#FFDCE3"
}
```


_Purple_
changed;
bg[SELECTED]	    = "#EE82EE"
base[ACTIVE]      = "#DDA0DD"
base[SELECTED]    = "#EE82EE"

bg[INSENSITIVE]   = "#EEE9EE"
base[INSENSITIVE] = "#EEE9EE"

fg[INSENSITIVE]   = "#B48BBB"
text[INSENSITIVE] = "#B48BBB"

```
style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = "#F3D4FA"
  bg[INSENSITIVE]   = "#DCBDE3"
  bg[PRELIGHT]      = "#FBDCFF"
}
```

---

### Post by bvc on 2005-12-31
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/)
I have added Executive, Etiquette, and Breathe. Made a few changes to GNOME, Hedgehog, and gPerfect.

I've always liked [Executive]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/CL_Cairo-Executive.jpg")

---

### Post by dude2425 on 2005-12-31
I've been tweaking it a bit more, played with your color suggestions, and even figured out how to get the focus ring to be thicker and more noticable. Now, I need an actual name (something that'll make people look at it). I think I'm gonna wait till Clearlooks with Cairo is final before I upload it to gnome-look, which would give me time to fix things in it if something major were to happen in CVS that would either break this theme, or allow it to look even better with a few changes. I'm also gonna see if I can come up with any other ideas for a nice theme or style. This is quite fun ^^

EDIT: I also updated my previous post to include the updated version with the better looking focus ring thingy and bvc's color suggestions.

---

### Post by bvc on 2006-01-04
added
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-Darjeeling.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-Darjeeling.tar.gz)

updated
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-6x.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-6x.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-GNOME.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks_Cairo-GNOME.tar.gz)

---

### Post by rjwood on 2006-01-05
Why do I get "command cvs no found"?

---

### Post by Rob2687 on 2006-01-06
apt-get install cvs ?

---

### Post by seasponge on 2006-01-06
i installed this on arch linux 0.7.1 (noodle) following your instructions without a hitch. looks wonderful. thanks

---

### Post by bvc on 2006-01-07
added Serenity and Curve (Bluecurve)
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/)

---

### Post by bvc on 2006-01-07
added ish-lite (bright) aqua, pink, purple, and red
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/)

[screenie]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/CL_Cairo-ish_lite-purple.jpg")

---

### Post by bvc on 2006-01-07
I've finished ish
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish/)
and ish-lite
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-lite/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/ish-lite/)

I'm waiting to see if darking of the checks and options are built into the engine before I make them darker in the gtkrc. Same goes for anything missing from all the others in the Big_Pack_Cairo.
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/)

---

### Post by bvc on 2006-01-08
might as well share
[http://gnome-look.org/content/show.php?content=33574](http://gnome-look.org/content/show.php?content=33574)
[http://gnome-look.org/content/show.php?content=33572](http://gnome-look.org/content/show.php?content=33572)
[http://gnome-look.org/content/show.php?content=33573](http://gnome-look.org/content/show.php?content=33573)

---

### Post by mgchan on 2006-01-09
[QUOTE=j_baer]Somewhere along the way I missed something.

I compiled as directed by the how-to, installed the themes as directed, and rebooted to re-start X but when I click on one of the themes I get something much simplier than expected. In fact it looks much like a plain X theme.

Here is the error I believe is causing the trouble ...

the following font backends:
  FreeType: no
  Win32: no
  ATSUI: no

and the following features:
  PNG functions: no
configure: error: Cairo requires at least one font backend.
                  Please install freetype and fontconfig, then try again:
                  [http://freetype.org/](http://freetype.org/)  [http://fontconfig.org/](http://fontconfig.org/)


:([/QUOTE]


I've got the same problem - tried installing freetype, freetype2, and libttf from the package manager but it still complains.

---

### Post by bvc on 2006-01-09
install their dev packages

---

### Post by rjwood on 2006-01-14
sorry-just learning! I did the gtk engine and the how-to say's unzip the themes into a new directory, but I don't see any zipped folders. I am obviously mis-understanding something. Can someone help??

Thanks in advance

---

### Post by jsmidt on 2006-01-18
The themes look great!

---

### Post by ModusOperandi on 2006-02-09
When following you directions, everything works fine up until "./autogen.sh --prefix=/usr"
I get the following error:
> 
libtoolize: command not found

./autogen.sh: ERROR: You must have `libtoolize' installed to compile cairo.
           (version 1.4 or newer is required)


I've tried looking in Synaptic for libtoolize, but no joy.

TIA

---

### Post by dmartin on 2006-02-09
[QUOTE=ModusOperandi]When following you directions, everything works fine up until "./autogen.sh --prefix=/usr"
I get the following error:


I've tried looking in Synaptic for libtoolize, but no joy.
[/QUOTE]

Same exact problem here.  I searched high and low on Google and here on the forums, and have come up empty on where to find libtoolize.

---

### Post by dmartin on 2006-02-09
Nevermind.  It seems obvious now (but didn't when I was searching high and low):

sudo apt-get install libtool

---

### Post by dmartin on 2006-02-10
Well, ugh.  So I got past that problem.  I actually compiled and installed Cairo successfully and restarted GDM.  But then GDM just constantly restarts as soon as it tries to load, and goes into a restart loop.

I can run KDM (no gtk widgets), but as soon as I try to log into Gnome, same thing - crash back to KDM.

Now I need advice.  How can I fix this, or how do I uninstall the Cairo that I installed so I can run Gnome again?  I tried "sudo make remove" but that didn't work.

---

### Post by bvc on 2006-02-10
sudo make uninstall

---

### Post by dmartin on 2006-02-10
[QUOTE=bvc]sudo make uninstall[/QUOTE]

I did that (bothered to read the makefile, eventually).  But that didn't fix my problem.  I finally fixed it by "sudo apt-get install nvidia-glx --reinstall".  I'm not sure what I did to hose that up, but that fixed me up and now everything is working (except Cairo).

---

### Post by dmartin on 2006-02-10
By the way, I did repeat this, because I was beginning to think I was crazy.  As soon as I did "sudo make install" and restarted X, same error.  And once again, reinstalling nvidia-glx fixed it.  Weird.

I think my problem is that I'm missing necessary dependencies.  I can't seem to add the libgtk2.0-dev packages installed, because dependencies are just a mess.  Perhaps I need to move back to a more standard sources.list.

---

### Post by bvc on 2006-02-10
make sure you do not have
```
Option 		"RenderAccel" 		"true"
```
in xorg.conf

---

### Post by dmartin on 2006-02-10
Yeah, I had that set - and it was painfully obvious when I got back into my desktop and ran xcompmgr.

---

### Post by dmartin on 2006-02-11
My system continued to have problems with cairo leftovers.  In fact, it became unuseable when I switched to a certain font...so I was forced to figure out what I had done wrong.

And the winner is: stupidity.

Somehow I skipped the second step - building the clearlooks-cairo engine.  Must've been a late night.  At any rate, everything is up and running now.  

I must say, it seems to run fine with RenderAccel on.  Is there are reason why you want people to turn this off?

---

### Post by Foucault on 2006-03-15
I have followed the guide however there seems to be something wrong. When I choose a Cairo enabled theme my desktop looks like the screenshot in my attachment. Any ideas? I know I am missing smth, but I am afraid I do not know what.

---

### Post by DigiNeT on 2006-03-16
Holas a todos

I'm new on this posting stuff, and my english suck sometimes.
i need help here, sorry for posting twice.

---

### Post by DigiNeT on 2006-03-16
I have this configure error with cairo.

```
diginet@diginetp3:~/cairo$ ./autogen.sh --prefix=/usr
./autogen.sh: running `libtoolize --copy --force'
./autogen.sh: running `aclocal'
./autogen.sh: running `autoheader'
./autogen.sh: running `automake --add-missing'
./autogen.sh: running `autoconf'
./autogen.sh: running `./configure --enable-maintainer-mode --enable-gtk-doc --prefix=/usr'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for ANSI C header files... (cached) yes
checking whether byte ordering is bigendian... no
checking for vasnprintf... no
checking for main in -lm... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XRENDER... yes
checking for XrmFinalize... no
checking for some Win32 platform... no
checking for BeOS/Zeta... no
checking for PNG... yes
checking for FONTCONFIG... yes
checking for FcFini... yes
checking for FREETYPE... yes
checking for FT_Bitmap_Size.y_ppem... yes
checking for FT_Load_Sfnt_Table... yes
checking for FT_GlyphSlot_Embolden... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for compress in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for POPPLER... configure: WARNING: PDF backend will not be tested since poppler is not available
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking sys/int_types.h usability... no
checking sys/int_types.h presence... no
checking for sys/int_types.h... no
checking for uint64_t... yes
checking for uint128_t... no
checking For MMX/SSE intrinsics in the compiler... yes
configure: error: conditional "am__fastdepCXX" was never defined.
Usually this means the macro was only invoked conditionally.

```

---

