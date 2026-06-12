---
title: "For the love of god, why is this not a theme?"
date: 2006-07-17
forum: Art &amp; Design
---

### Post by tocky on 2006-07-17
I know that probably most of you have already seen this mockup, though I'm a fresh Ubuntu converter, but this looks so nice, especially the pick in the middle. I would love to have a task panel in the bottom like that, and the theme is pretty good. Does anybody know if there is a theme like this, or is it someone that could comment on how you make one.

[http://www.gnome-look.org/content/show.php?content=31128](http://www.gnome-look.org/content/show.php?content=31128)

---

### Post by smartalecks on 2006-07-17
I think they are working on it atm.

---

### Post by bvc on 2006-07-18
working on what?...the systray? That would be nice but shouldn't they fix all the other broken things in the gnome-panel first?...or redo it completely?

Other than the systray the panel is easily done.
The gtk, or, the only released versiion I know of is here
[http://gnomethemes.org/?p=19](http://gnomethemes.org/?p=19) (see the panel directory except transparency in the panel is broken so the images have to be redone...but you'll get the idea)
and
[http://gnomethemes.org/?p=4](http://gnomethemes.org/?p=4)

[http://gnomethemes.org/](http://gnomethemes.org/)
[http://gnomethemes.org/forum/index.php](http://gnomethemes.org/forum/index.php)

---

### Post by tocky on 2006-07-19
Well I hope there will be a version of this out fast, though it is the best looking theme I've ever seen on any platform.

---

### Post by tocky on 2006-07-19
Btw, what is systray? And why is that hard to develope

---

### Post by bvc on 2006-07-19
> **tocky said:**
> Well I hope there will be a version of this out fast, though it is the best looking theme I've ever seen on any platform.version of what? there's 2 things here....
1. mockup of a panel that can not be done (exactly) and who know if and when, and a file manager interface that currently doesn't exist
2. theme (which has a release)

---

### Post by bvc on 2006-07-19
> **tocky said:**
> Btw, what is systray? And why is that hard to developeLook at the second screenshot. On the right where the clock, volume, and workspaces are they are stacked in two rows. The rest of the panel is one row, though the window list is doubled, which can be done now with the right padding and height combo. So we call it a systray because it doesn't exist and acts like a 'systray', so it goes....

Hard to develop? I wouldn't know, but I know the gnome-panel is a mess and is in need of help in devel if anyone can contrib.

---

### Post by H.E. Pennypacker on 2007-06-13
Oh, man..that dock makes me drool, and is infinitely superior to any other docks out there, because this one also handles the window list.

---

### Post by weblordpepe on 2007-06-13
I'm sold! Sign me up. Where do I pay? Anyone want my wallet?? Gimme gimme gimme gimme gimme

---

### Post by drummer on 2007-06-13
Well, that is a schmexy theme... but why bump a year-old thread just to say so?

---

### Post by weblordpepe on 2007-06-13
> **drummer said:**
> Well, that is a schmexy theme... but why bump a year-old thread just to say so?

Quite simply, its because GIMME GIMME GIMME GIMME GIMME GIMME GIMME.

---

### Post by arbulus on 2007-06-13
> **bvc said:**
> Look at the second screenshot. On the right where the clock, volume, and workspaces are they are stacked in two rows. The rest of the panel is one row, though the window list is doubled, which can be done now with the right padding and height combo. So we call it a systray because it doesn't exist and acts like a 'systray', so it goes....

Hard to develop? I wouldn't know, but I know the gnome-panel is a mess and is in need of help in devel if anyone can contrib.


It actually kinda looks like KDE's panel.  That's actually what I thought it was at first until I saw the foot logo.

---

### Post by mech7 on 2007-06-13
yes i would like this too plz.. looks 100x better then default skin :)

---

### Post by H.E. Pennypacker on 2007-06-13
> **drummer said:**
> Well, that is a schmexy theme... but why bump a year-old thread just to say so?

To raise awareness.

---

### Post by oxalá on 2007-06-14
so...why isn't this available yet?

---

### Post by HeavyAl on 2007-06-14
Slick. Very slick. Someone mentioned that the dock looked like the kde panel but I'd have to disagree - kde's stuff is blocky and butt ugly! Course, that's just my opinion, hehehe. 

Couple of more productive thoughts: Seems like one might be able to modify Thunar easier than Nautilus to achieve the file manager appearance that is given, but I haven't looked at the code in it in so long it may not be that easy anymore. 

The dock bar itself with the roundish corners and such couldn't be done with gnome in it's current state. Probably have to write some kind of plugin for gDesklets which to me would ruin the whole project since that means adding another layer of memory-hogging code to the desktop. 

I hope whoever is working on this figures a way around all of the issues - the controls are a simple matter of creating another gtk+ engine but the rest of it looks like ts going to require some custom code. Anyway, if they get it done it would be sweet.

---

### Post by H.E. Pennypacker on 2007-06-14
> **oxalá said:**
> so...why isn't this available yet?

Because no one is working on it.  It was never an official project; just a mock-up.  From its appearance, it would require massive work adjusting Gnome, and that is simply not a priority at this time.  It will likely never be implemented.

---

### Post by locke.dragon on 2007-06-14
i don't really think this is a theme/mod.  to me, it looks like just a customized task bar.  i could be wrong, but i'm gonna see if i can edit one of my taskbars to look like that.  will post a tutorial if i succeed!

EDIT: sorry for being so rude before.  :(

---

### Post by HeavyAl on 2007-06-15
> **locke.dragon said:**
> ok.  well...  uh...  hate to break it to you all...  but this isn't a theme.  :P  that's just a customized dock bar thingy like you have with normal ubuntu.  you know, the applications/places/system bar?  it's just that, only customized.  takes about 10 mins to do.

Not to put too fine a point on it but no one called it a theme from the get go - notice the thread title? Especially the part where it says '.. NOT a theme'? It's a mock-up .. probably a few of which you should have done with that Leaflet web page of yours before making it live .. green, ICK!

The docking part of the mockup is of course relatively simple to implement. The issues would be with the actual integration - if it were to be a part of gnome itself then you'd have to tack on quite a bit to the bar handling code to get such nice fine lines, but if it were a plugin for a third party system that floated in gnome then that might be a little more doable - much like the cairo/leaflet thing you appear to have been working on.

I apologize for my tone throughout this message but I found it rather offensive how you swooped down out of no where to criticize in aggregate those who were otherwise having a relatively civil discussion regarding this fine piece of art and vision.

---

### Post by locke.dragon on 2007-06-15
yeah.  -stares at floor-   i was kinda rude...  i wasn't having the greatest day...  sorry everyone...  will fix it and it won't happen again...  i'm still gonna see if i can change one of the docks to look like this though.  will post a tutorial if i succeed!  :)  cheers!

p.s.  you'll be able to change the color of leaflet...  ;)

---

### Post by nine01a on 2007-06-15
Wow! This is a really cool-looking concept and it almost saddens me that it hasn't already been created =) If Gnome's overall appearance was of that mock-up, people would be sold on it like free doughnuts.

---

### Post by locke.dragon on 2007-06-15
i like free donuts!  :P

---

### Post by HeavyAl on 2007-06-15
> **locke.dragon said:**
> yeah.  -stares at floor-   i was kinda rude...  i wasn't having the greatest day...  sorry everyone...  will fix it and it won't happen again...  i'm still gonna see if i can change one of the docks to look like this though.  will post a tutorial if i succeed!  :)  cheers!

p.s.  you'll be able to change the color of leaflet...  ;)

Not to carry this on too far, but I'm impressed. It seems that these days the Net is full of people who's response to criticism is to simply start yet another 'flame war' and thus degrade the quality of the community. You show that you are a person of quality by taking this in stride in such a mild manner. You have my respect, for whatever that may be worth.

On a technical note, your leaflet application - I read a bit about it but I was wondering, is it based on existing code? Is it primarily a GTK application, or something more home brewed? My C/C++ skills are rather rusty so I probably would not be of much help in that regard, but how hard would it be to integrate some of the 'tray' ideas from the mockup in the original post with your current code base? It seems to me that other than the look of the bar that the modular tray is the only thing really missing.

---

### Post by locke.dragon on 2007-06-15
thanks HeavyAI.  :)  that actually means alot to me.  :)  by the by, i tried the dock idea...  not as simple as i first thought.  my version would look fine if i could just get rid of the annoying buttons on the side of the dock.  as for my program, it's based on cairodock by macslow.  i haven't done that much to it, but i'm gonna make a GUI that will allow easy customization of the dock.  once i get done with school (or get free time), i'm gonna do more with it, but the project's on halt right now since the guy who was gonna work on the code hasn't gotten back to me...  :(  would it be possible for you to whip up a GUI in c/c++ that would be able to edit a text file and then recompile?  the program's written in python.  i have a bit of a GUI ready, but it's nowhere near what i want.

---

### Post by locke.dragon on 2007-06-15
i don't think it would be that hard to add in the functionality since we can probably take a cairodock add on and fix it up for our needs.  but don't look for that anytime soon.  i haven't even released a public beta yet.  :P

---

### Post by JC_510 on 2007-06-15
Looks absolutely fantastic!!! Good luck with getting it working; I look forward to using it! :D

---

### Post by HeavyAl on 2007-06-15
> **locke.dragon said:**
> would it be possible for you to whip up a GUI in c/c++ that would be able to edit a text file and then recompile?  the program's written in python.  i have a bit of a GUI ready, but it's nowhere near what i want.

Like I mentioned, my C/C++ skills are rather rusty - I haven't actually used them in about ten years. These days I do more web dev (php/mysql). And I have yet to get a handle on Python, though I hear it's similar in some respects to Delphi which I'm still proficient with so I may be able to whip you up something in that if I get some time (In Python that is, not Delphi). 

I ran through the quick install of Cairo that is posted on your site but I'm not sure how to get it to actually run (compilation and installation went fine) - I'm at work right now on my T40 Laptop which doesn't handle Beryl and appears to only work with the default Compiz setup that came with Feisty so I'm not sure if I'm missing some kind of configuration tool or what.

All that said, I need some clarification - are you working on a way to EXPAND the abilities of Cairo, or a tool to just adjust the settings? Also, I can't find your current set of code for the project - Your Launchpad appears empty and I didn't see any links on your blog page .. what am I missing?

---

### Post by locke.dragon on 2007-06-15
yeah.  i haven't actually released the code yet.  all you need is the code.  i'll send it to you as long as you'll help me in getting furthering the program.  it's not ready for the general public yet.  and i'm looking to expand the capabilites AND do a GUI.  but the GUI comes first.

---

### Post by HeavyAl on 2007-06-15
Let me take stock of what my obligations are at the moment. I won't ask you for the code until I am certain I can contribute something meaningful to the project.

---

### Post by locke.dragon on 2007-06-15
sounds good, but maybe we should communicate through e-mail/private messages.  :P  we're kinda destroying this thread.

---

