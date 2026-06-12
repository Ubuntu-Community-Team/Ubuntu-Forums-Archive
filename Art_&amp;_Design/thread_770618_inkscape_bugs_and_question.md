---
title: "inkscape bugs and question"
date: 2008-04-27
forum: Art &amp; Design
---

### Post by proalan on 2008-04-27
New inkscape seemed kind of cool, but I've had problems

Bugs I've found

Can't resize the window to full screen (clicking on the maximise button). It just resizes the windows height.

I click on the toolbar and the window decorator disappears and i end up clicking on the toolbar buttons.

When I get into some serious detailed graphics, the application crashes the entire system.


Question

Is there a brush tool feature or plugin in inkscape similar to illustrator? The only functionality gripe I have with inkscape is I can't control how my stokes look other than dots and dashes. Though I think this may be down to the svg specs.

---

### Post by smartboyathome on 2008-04-27
> **proalan said:**
> New inkscape seemed kind of cool, but I've had problems

Bugs I've found

Can't resize the window to full screen (clicking on the maximise button). It just resizes the windows height.

What desktop are you using, and what is your screen resolution?

> **proalan said:**
> I click on the toolbar and the window decorator disappears and i end up clicking on the toolbar buttons.

I think it is because it is trying to show itself. I had this bug where if I had a big enough window border, and maximized it, it did this. Just use alt+drag.

> **proalan said:**
> When I get into some serious detailed graphics, the application crashes the entire system.

Run it with this on the end to get all the output to go to a file:
>> /home/*USERNAME*/.inkscape-errors


> **proalan said:**
> Question

Is there a brush tool feature or plugin in inkscape similar to illustrator? The only functionality gripe I have with inkscape is I can't control how my stokes look other than dots and dashes. Though I think this may be down to the svg specs.

I don't think there is. I know it is also missing a mesh tool, but it works well for most pics. :(

---

### Post by Half-Left on 2008-04-27
Inkscape is pure svg vector which means limited effects and filters.

---

### Post by proalan on 2008-04-27
> What desktop are you using, and what is your screen resolution?gnome (latest version) same regardless of compiz being on or off
resolution 1024x768
RAM 504 MB
SWAP 514 MB

I'm not running in full screen mode (via F11). However I noticed another bug that the entire application flashes whenever i click on any of the UI components when in full screen mode.

The window decoration toggles on and off when i click on either the menu bar or toolbars. I can only resolve this by not working in maximised mode. Someone has already reported this as a bug on launchpad.

The system doesn't actually crash per se, its just that the ram/swap gets eaten up and the system crawls and I end up doing a hard reset. This is also true for GIMP when I'm working with really big or complex files (i'm talking about 6MB+) as well as .eps files. 

I'm going to try running a lighter desktop like fluxbox or xfce and see if it resolves any of the issues.

thanks for the replies.

---

### Post by BLTicklemonster on 2008-04-29
> **Half-Left said:**
> Inkscape is pure svg vector which means limited effects and filters.

But seeing as how one can do effects and such, is there any likelihood that one day scripts will be made to be used such as scriptfu and such in gimp? I'd sure like to be able to do some simple effects in inkscape without having to follow poorly written tutorials (meaning vaguely written). I've yet to get a single effect in inkscape to look remotely like what they should look like, which is frustrating, because I can get the effects I want in gimp all day long, but IT HAS scriptfu.

---

### Post by Half-Left on 2008-04-29
> **BLTicklemonster said:**
> But seeing as how one can do effects and such, is there any likelihood that one day scripts will be made to be used such as scriptfu and such in gimp? I'd sure like to be able to do some simple effects in inkscape without having to follow poorly written tutorials (meaning vaguely written). I've yet to get a single effect in inkscape to look remotely like what they should look like, which is frustrating, because I can get the effects I want in gimp all day long, but IT HAS scriptfu.

Well Inkscape goes by SVG spec, Even Illustrator has limited svg filers. It's pretty much why Illustrator is why it is, it's not just that because you apply blur in inkscape and it's slow as hell. 

Illustrator has best of both, I'm not trying to push it, but it's tons more powerful and so is Xara.

---

### Post by BLTicklemonster on 2008-04-29
Oooh, I keep forgetting about Xara!!! Thanks!

---

### Post by smartboyathome on 2008-04-29
> **Half-Left said:**
> Well Inkscape goes by SVG spec, Even Illustrator has limited svg filers. It's pretty much why Illustrator is why it is, it's not just that because you apply blur in inkscape and it's slow as hell. 

Illustrator has best of both, I'm not trying to push it, but it's tons more powerful and so is Xara.

But Xara isn't really in development anymore. I don't suggest it because of that fact, and it isn't really THAT much more powerful when you look at how poorly it exports svgs. :(

---

### Post by Half-Left on 2008-04-29
> **smartboyathome said:**
> But Xara isn't really in development anymore. I don't suggest it because of that fact, and it isn't really THAT much more powerful when you look at how poorly it exports svgs. :(

True but if your doing backgrounds and icons you can use png. Vectors it's the fastest bar non, lot of production places dont use svg anyway, they use eps or other formats for print. The reality is it's far superior to Inkscape but Inkscape has a great and easy UI to do simple stuff.

---

### Post by proalan on 2008-05-02
Oh dear now that its been mentioned, the mesh tool would be nice. I've wasted too much time with work arounds rather than actually drawing. 

I might give coreldraw a go when I have time. Can't argue that illustrator is more powerful with more useful features.

---

### Post by keithwwalker on 2009-02-04
I just installed and when the window is maximized, the lower toolbar is partly hidden.  

If I clip on the window frame or anywhere inside it, the whole window shifts up and down with each click.  It is frustrating when you are trying to select an element or corner of one and the window shifts on you(!)

When the window isn't maximized, I can never pull the window higher so that the entire lower toolbar is visible(!)

Fullscreen, F11, the problem goes away

---

