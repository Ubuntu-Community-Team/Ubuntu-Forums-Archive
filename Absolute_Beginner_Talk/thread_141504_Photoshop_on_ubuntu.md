---
title: "Photoshop on ubuntu ?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-03-08
There are only 2 things that make me dual boot
- counter-strike 1.6
- Photoshop CS2

I found something to run cs on ubuntu with wine but I', to noob to follow that tuto ^^ I'll try again in a week or something
But I really need photoshop, i know gimp is fine but I', used to photoshop so I Prefer photshop ...

Is there a way to make photoshop work on ubuntu ??

Grtz PingunZ

---

### Post by e2k on 2006-03-08
Have you tried GimpShop?
> GIMPShop is a free Open Source image editor that is similar to the popular Adobe Photoshop. Specifically GIMPShop is a version of the GIMP that has been edited to be more user-friendly for Photoshop users
I would definitely give it a shot before trying to emulate photoshop :cool:

---

### Post by Klaidas on 2006-03-08
Maybe wine/cedega would do it, I don't really know. But try out GIMP (of course, alternatives can't beat originals) but give it a try :)

---

### Post by PingunZ on 2006-03-08
I will try GimpShop, No more gimp for me ^^ I had it before photshop and its really hard to work with IMO ... GimpShop For Teh Win ^^

Edit : I can only find the source codes for gimpshop, I am using Ubuntu for a few days so i can't do anything with it ...
Is there no way to download it with synaptic or something ?

Grtz PingunZ

---

### Post by Zeroangel on 2006-03-08
Have you tried getting CStrike to work with Wine? I managed to get an older, more obscure, game working with Wine simply by writing a script that cd's to that folder then runs wine game.exe

---

### Post by Perfect Storm on 2006-03-08
You could also try with Pixel32: [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)

---

### Post by wrtrdood on 2006-03-08
Photoshop works just fine with Wine --  (...ohh that was bad...:-#  )

I was impressed that it installed so easily and then ran just as easily.  Granted, chasing down where the executable is can be a pain (look under .wine) but all I did was create a desktop link with the same command and now she kicks it off with a simple double-click.

---

### Post by PingunZ on 2006-03-08
I know what wine is :p
But could you write like a tuto or something ??? or explain in noobish how to get photoshop working with wine
I don't think I'm the only one who can't work with gimp and has to reboot for photoshop ? :-k 

If I can help with the tuto or with something else, just tell me :p

Grtz PingunZ

---

### Post by Perfect Storm on 2006-03-08
I find gimp very handy, it's about habits. I also used PS and PSP, but I got familiar with gimp. Though I have Photoshop 7 installed via xover office I don't use it anymore, since gimp and pixel 32 fulfill my needs.

---

### Post by Zeroangel on 2006-03-08
Does Pixel support 'Layer Effects' (like bevel, inner glow) like Photoshop does? Man, thats the only thing that's keeping me missing Photoshop.

(EDIT: Nevermind, it does. Even though its not as polished as PS)

---

### Post by jasplund on 2006-03-08
[QUOTE=Zeroangel]Does Pixel support 'Layer Effects' (like bevel, inner glow) like Photoshop does? Man, thats the only thing that's keeping me missing Photoshop.[/QUOTE]

yep they are called "live effects"

---

### Post by PingunZ on 2006-03-08
Idd PS stays the best photoediting program ( IMO )
so wrtrdood tell us what you got :)

Grtz PingunZ

---

### Post by eltaito on 2006-03-08
I switched over to Ubuntu back in October and I was a HEAVY photoshop user...it was really irritating to not have it, but after using The Gimp for a while....I have to say, it is a wonderful program.  It takes some adjusting, but once you familiarize yourself with it (they have some great forums and wiki's/how-to's on their site) you'll love it.  I would say just using the Gimp will probably meet most of your needs, but I'll admit, it was really hard to break my photoshop habits.

---

### Post by Brunellus on 2006-03-08
[QUOTE=eltaito]I switched over to Ubuntu back in October and I was a HEAVY photoshop user...it was really irritating to not have it, but after using The Gimp for a while....I have to say, it is a wonderful program.  It takes some adjusting, but once you familiarize yourself with it (they have some great forums and wiki's/how-to's on their site) you'll love it.  I would say just using the Gimp will probably meet most of your needs, but I'll admit, it was really hard to break my photoshop habits.[/QUOTE]
Most of the anti-GIMP FUD is from people who are trained on Photoshop and don't have the time/energy to learn a new program/interface.   there are some missing features, but in practice, I think a lot of the problem is a refusal or inability to carry over skills learned in the other platform.

I, on the other hand, have pretty much just used the GIMP.  So I wouldn't know a damn thing about PS.

---

### Post by Perfect Storm on 2006-03-08
[QUOTE=Zeroangel]Does Pixel support 'Layer Effects' (like bevel, inner glow) like Photoshop does? Man, thats the only thing that's keeping me missing Photoshop.

(EDIT: Nevermind, it does. Even though its not as polished as PS)[/QUOTE]

Still beta, but in the future it might turn into a very good program.

---

### Post by aysiu on 2006-03-08
Can someone who knows both Photoshop and GIMP well spell out once and for all what *exact* features Photoshop has that GIMP *lacks*, and how often graphic designers use those features?

Features only--not interface, polish, or whatnot.

---

### Post by wrtrdood on 2006-03-08
[QUOTE=PingunZ]I know what wine is :p
But could you write like a tuto or something ??? or explain in noobish how to get photoshop working with wine
I don't think I'm the only one who can't work with gimp and has to reboot for photoshop ? :-k 

If I can help with the tuto or with something else, just tell me :p

Grtz PingunZ[/QUOTE]

Sure.  I'll have to look at the machine when I get home before I can give you the details but basically it's going about using it the same way you would on Windows except that you have to do things manually at first.  For example, once you have wine installed just execute the setup.exe from the CD with something like:

wine /media/cdrom/setup.exe

This will kick off the install and after you get through all that you would run Photoshop with something like:

wine ./wine/c/Program Files/Adobe/pshop.exe

(that's off the top of my head but you get the idea)

Then simply create a new desktop link and place that same line in the spot identifying the program to run.  As I said, I'll check the specifics later but this should get you started.


*****************************************
The correct command and location would be:

wine .wine/drive_c/Program\\ Files/Adobe/Photoshop\\ 6.0/Photoshp.exe

Because creating desktop icons varies with the DM in use (KDE,Gnome, WM, E) I'll not get into that.  Regardless, each one should provide some way to create a startup icon and the program path should include what I've shown above.

---

### Post by steve.horsley on 2006-03-08
[QUOTE=aysiu]Can someone who knows both Photoshop and GIMP well spell out once and for all what *exact* features Photoshop has that GIMP *lacks*, and how often graphic designers use those features?[/QUOTE]

Don't know if you'd call it a feature, but the killer for my wife is the speed at which the preview repaints as you drag the colour dialogue slider bars around. In photoshop, she starts by slamming the slider from end to end at about one cycle per second, and slowly reduced the amplitude until she settles on a value. Then goes "Hmm", and does it again, then again.  This is absolutely impossible in the Gimp because the preview pane takes so long to repaint - I'm sure that behind the scenes, it's processing the main image and then copying it out to the preview pane, and it can take several seconds to catch up.

---

### Post by abu-fatu on 2006-03-08
how can i get gimpshop for ubuntu.

---

### Post by Zeroangel on 2006-03-08
The version from [this thread](http://ubuntuforums.org/showthread.php?t=67525) works fine for me.

---

### Post by love4stupidppl on 2007-02-05
When I try and Wine photoshop I get this error 
```

fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  41
  Current serial number in output stream:  41

```
Any idea out there?

---

### Post by TheKid965 on 2007-02-15
> Can someone who knows both Photoshop and GIMP well spell out once and for all what exact features Photoshop has that GIMP lacks, and how often graphic designers use those features?

The one "biggie" feature lacking from GIMP is the one feature that's absolutely necessary for many designers - CMYK support.  Without a true CMYK color-separation process GIMP is all but useless in a print or pre-press environment.  

There are workarounds for this, such as using GIMP for the actual work then using Krita (the KOffice photo manipulator) for the color separation (as Krita *does* do CMYK), but these solutions are inelegant at best.

I've not heard the latest as to why GIMP doesn't support CMYK, or even if such support is being added for the latest versions.  The last I heard (and I could be mistaken) is that the GIMP team doesn't want to support it out of concern for a licensing issue; think how Ubuntu and many distros don't ship with support for MP3 and other "closed" multimedia codecs.  The same principle would apply here.  Fortunately, there are some projects out there that seek to add CMYK to GIMP via a plug-in, such as [this one](http://www.blackfiveservices.co.uk/separate.shtml); it may be worth your time to keep an eye on these.

---

### Post by revertex on 2007-02-21
If you need CMYK support, then use cinepaint.

Almost all people that say, "forget photoshop, use gimp" or "gimp can do all photoshop do" don't use photoshop plugins.

GIMP CAN'T RUN LOTS OF PHOTOSHOP PLUGINS. period.

that's why we need to run photoshop under linux.

for all ppl that are trying install photoshop:

It seems that photoshop CS portable can run under wine.

[http://frankscorner.org/index.php?p=photoshopcs](http://frankscorner.org/index.php?p=photoshopcs)

Photoshop 7 runs flawlessy with crossover office.

It's also work with wine, instructions here.

[http://frankscorner.org/index.php?p=ps7](http://frankscorner.org/index.php?p=ps7)

---

### Post by Lumbee1 on 2007-08-11
> **love4stupidppl said:**
> When I try and Wine photoshop I get this error 
```

fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  41
  Current serial number in output stream:  41

```
Any idea out there?

Searched for ideas on this issue and I have the exact same problem.  Any ideas on how to fix this?

BTW, the wine Photoshop install took about 15 minutes but eventually finished.  Starting Photoshop in wine took about 3 minutes and crashed with the error above.

---

### Post by revertex on 2007-08-11
which photoshop version?
photoshop 7 runs fine here.

---

