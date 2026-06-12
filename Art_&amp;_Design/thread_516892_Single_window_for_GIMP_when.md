---
title: "Single window for GIMP when?"
date: 2007-08-03
forum: Art &amp; Design
---

### Post by u.b.u.n.t.u on 2007-08-03
I just downloaded 2.2.17 and it is the same awful setup. 

I have read about a single window. So when will such be released - GIMP as a single window program?

I know modifications exist but such do not interest me.

Thanks.

---

### Post by yabbadabbadont on 2007-08-03
From the GIMP FAQ:
> When will an MDI/nested windows be implemented?

This is often requested by MS Windows users who lack some of the window management features common in other operating systems. An MDI interface is largely considered a step backwards by interface designers. The core Gimp developers share this sentiment, so don't expect them to implement the feature any time soon. However, there are no objections to the feature itself. So far only the [WWW] Deweirifyer plugin attempts any sort of a fix. It seems to be good enough for some, but not for others. If you are interested in implementing MDI support [WWW] bug 7379 is the place to start.

See also:

[http://bugzilla.gnome.org/show_bug.cgi?id=7379](http://bugzilla.gnome.org/show_bug.cgi?id=7379)
[http://bugzilla.gnome.org/show_bug.cgi?id=121087](http://bugzilla.gnome.org/show_bug.cgi?id=121087)

Edit: After reading through those bugs, it appears that the GIMP devs don't really care what the "average" user wants.  They specifically state that GIMP is intended for professional graphic artists....  :roll:  You might want to check out paint.net, pixel, krita, inkscape, ...  to see if one of them meets your needs.

---

### Post by u.b.u.n.t.u on 2007-08-03
I am proficient with Paint Shop Pro which I use regularly. I also use Photoshop.

I want however to use GIMP as a single window.

I think a single window version is on the horizon. Just wondering when.

---

### Post by henriquemaia on 2007-08-03
> **u.b.u.n.t.u said:**
> I am proficient with Paint Shop Pro which I use regularly. I also use Photoshop.

I want however to use GIMP as a single window.

I think a single window version is on the horizon. Just wondering when.

In Gimp’s new version (2.3.x), the window management is much clever. Give it a try installing the development version (future 2.4) to see if it fits your needs.

---

### Post by CarpKing on 2007-08-03
The only real problem (annoyance) that I can see from the current setup is that it puts a bunch of stuff in the window list and the fact that there are two menus labeled "file."  The rest is all just a matter of rearranging things to your liking and getting used to it.  The developers are, however looking into a redesign ([http://gui.gimp.org/index.php/GIMP_UI_Redesign](http://gui.gimp.org/index.php/GIMP_UI_Redesign)).

---

### Post by Half-Left on 2007-08-04
Photoshop on OS X uses the same muti window layout, professionals dont complain, infact it;s what they liked about GIMP. 

2.3.x does have a option to fit all windows into one just to please the Windows users that have been used to the same old layout.

---

### Post by evissecx on 2007-08-04
I like the windows gimp uses.
I have the image i'm working on on monitor 1 and all the 
docks on monitor 2. It's easy to reach everything. And to not get
all the gimp icons in the taskbar, I use a kde-setting to hide gimp docks icons in the taskbar. 
so I got just the image icon and the main dock icon in the taskbar. It's really great. 
So by just minimize the image i'm working on, all the docks automaticly hides as well.

---

### Post by AJB2K3 on 2007-08-04
On multi head setup gimp default setup is a good send because it means all the tools can be thrown into a seperate screen leaving just the image on one screen.
However on the laptop im forever looking for tools.
Another plus is that you can put a screen under a drawing tablet, put the controls to that screen then have every thing to hand.

---

### Post by u.b.u.n.t.u on 2007-08-04
> **henriquemaia said:**
> In Gimp’s new version (2.3.x), the window management is much clever. Give it a try installing the development version (future 2.4) to see if it fits your needs.

Unfortunately not available for XP at the moment, only linux.  I am using XP, waiting for Gutsy to solves some bugs so I can try it.

At least Gimp is moving in the right direction - choice.

---

### Post by berniefranks on 2007-08-04
> **Half-Left said:**
> Photoshop on OS X uses the same muti window layout, professionals dont complain, infact it;s what they liked about GIMP.
Well, as a professional designer, I really don't like it when a program has all those open windows like in OS X or the GIMP - which is one of the reasons I prefer using Windows to Mac for design. ;)

For Mac, though, it makes sense because OS X doesn't use a taskbar (unlike Windows or Gnome). You can't maximize a window to fill the whole screen in OS X, you need to be able to click behind to switch between windows (or nowadays with the Expose feature). But when you maximize Photoshop in Windows, for example, you just navigate with the taskbar, no need to actually click on the windows behind. Same applies for the GIMP.

Essentially, it's completely unnecessary to have the OS X-style layout for GIMP in an OS that uses a taskbar. It may not be a step forward to convert the GIMP to a single nested screen, but it sure as hell ain't a step backward.

---

### Post by CarpKing on 2007-08-05
Another link of interest: [http://www.mmiworks.net/eng/publications/labels/GIMP.html](http://www.mmiworks.net/eng/publications/labels/GIMP.html)

---

### Post by vexorian on 2007-08-05
> When will an MDI/nested windows be implemented?

This is often requested by MS Windows users who lack some of the window management features common in other operating systems. An MDI interface is largely considered a step backwards by interface designers.

This shows shortsight on the gimp developers, most requested features is something you should take more consideration into instead of minimizing into something only MS Windows users want, I think the gimp's stubborness on using that terrible interface is what makes it a bad piece of software.

Let me ellaborate about the current interface: It is hard to use, it complicates me, it makes me lose time, it is the only piece of software that does this.

- hard to use: In order to effectively use the current interface, you need to consistently make the gimp use its whole own workspace all the time, you need to make the main windows but the documents to be always on top, and many other tweaks, it is painful.

- It complicates me: Seriously, after I make the main gimp window on top then I get issues when exporting to other document formats, because the save as... dialog will be on top of the convert dialog , yeah, blame the window manager, it is still too much complication to me.

- It makes me lose time,  see previous paragraphs.

- It is the only piece of software that does it. Gnome comes with plenty of software that got decent interfaces, things like tabs (For god's sake) abound, you should also take a look at inkscape which is a lot more confortable than the gimp to use, and unlike photoshop+illustrator they are totally incosistent interface-wise.


It really does not make much sense to keep the current gimp interface, if the developers really like it then they should have it as an option, but not as the default, I think that the image of linux for the desktop is at peryl because of crazy interface choices like this one.

--
one thing we could do is voting for initiatives like this one: [http://gnome-look.org/content/show.php/GIMP+3?content=49951&PHPSESSID=71ab1124275669f465187c874df60ee3](http://gnome-look.org/content/show.php/GIMP+3?content=49951&PHPSESSID=71ab1124275669f465187c874df60ee3)

---

### Post by henriquemaia on 2007-08-05
> **vexorian said:**
> This shows shortsight on the gimp developers, most requested features is something you should take more consideration into instead of minimizing into something only MS Windows users want, I think the gimp's stubborness on using that terrible interface is what makes it a bad piece of software.

Let me ellaborate about the current interface: It is hard to use, it complicates me, it makes me lose time, it is the only piece of software that does this.

- hard to use: In order to effectively use the current interface, you need to consistently make the gimp use its whole own workspace all the time, you need to make the main windows but the documents to be always on top, and many other tweaks, it is painful.

- It complicates me: Seriously, after I make the main gimp window on top then I get issues when exporting to other document formats, because the save as... dialog will be on top of the convert dialog , yeah, blame the window manager, it is still too much complication to me.

- It makes me lose time,  see previous paragraphs.

- It is the only piece of software that does it. Gnome comes with plenty of software that got decent interfaces, things like tabs (For god's sake) abound, you should also take a look at inkscape which is a lot more confortable than the gimp to use, and unlike photoshop+illustrator they are totally incosistent interface-wise.


It really does not make much sense to keep the current gimp interface, if the developers really like it then they should have it as an option, but not as the default, I think that the image of linux for the desktop is at peryl because of crazy interface choices like this one.

--
one thing we could do is voting for initiatives like this one: [http://gnome-look.org/content/show.php/GIMP+3?content=49951&PHPSESSID=71ab1124275669f465187c874df60ee3](http://gnome-look.org/content/show.php/GIMP+3?content=49951&PHPSESSID=71ab1124275669f465187c874df60ee3)


Have you tried the latest version with the new window management feature?

---

### Post by u.b.u.n.t.u on 2007-08-05
> **CarpKing said:**
> Another link of interest: [http://www.mmiworks.net/eng/publications/labels/GIMP.html](http://www.mmiworks.net/eng/publications/labels/GIMP.html)

That site talks about Gimp technicalities and I haven't even gotten to the stage of actually using Gimp yet. I decline to until such time as they implement a single window.

---

### Post by u.b.u.n.t.u on 2007-08-05
> **vexorian said:**
> 
It really does not make much sense to keep the current gimp interface, if the developers really like it then they should have it as an option, but not as the default, I think that the image of linux for the desktop is at peryl because of crazy interface choices like this one.


Well said. We are reading from the same page. I fully concur. Now if only the Gimp developers would condescend to providing such.

---

### Post by leo_rockway on 2007-08-05
i was sure someone was gonna mention this project: [http://www.gimpshop.com](http://www.gimpshop.com)

i havent tried it myself, so if someone did please leave comments.

---

### Post by Half-Left on 2007-08-05
> **u.b.u.n.t.u said:**
> That site talks about Gimp technicalities and I haven't even gotten to the stage of actually using Gimp yet. I decline to until such time as they implement a single window.

A bad workman always blames his tools and you can setup GIMP like that.

Why can you people not take a minute to set it up how you want it instead of complaining.

---

### Post by vexorian on 2007-08-05
> A bad workman always blames his tools and you can setup GIMP like that.
Hmm, could you please enlighten us? I tried looking for that option, and although not everything is bad since I found a way to use Tango for the toolbar ... I couldn't find a way to change the window behavior.

Edit: or do we need a new version? I am using the latest one available for Feisty.

Edit: It seems I have failed for not reading the whole thread.

---

### Post by vexorian on 2007-08-05
> **leo_rockway said:**
> i was sure someone was gonna mention this project: [http://www.gimpshop.com](http://www.gimpshop.com)

i havent tried it myself, so if someone did please leave comments.
got to say it is terribly hard to install, after downloading the file it complaints about a gimpprint1 library that is missing, but that library is not even in synaptic, got to be the first time...

edit: I also  found out it will replace thegimp so that kind of brings some package issues.

---

### Post by henriquemaia on 2007-08-05
> **vexorian said:**
> Hmm, could you please enlighten us? I tried looking for that option, and although not everything is bad since I found a way to use Tango for the toolbar ... I couldn't find a way to change the window behavior.

Edit: or do we need a new version? I am using the latest one available for Feisty.

Edit: It seems I have failed for not reading the whole thread.

You can try following redforce&#8217;s instructions on the following page (in the comments section) to run the latest version. Gimp is way more better now (as in the 2.3.19 version).

[http://www.gimpusers.com/news/2007-07-27/new-gimp-2319.html#kommentare](http://www.gimpusers.com/news/2007-07-27/new-gimp-2319.html#kommentare)

---

### Post by u.b.u.n.t.u on 2007-08-05
> **Half-Left said:**
> A bad workman always blames his tools and you can setup GIMP like that.

Why can you people not take a minute to set it up how you want it instead of complaining.

I want a single window in Gimp. If you can't understand and respect that then simply go away because your banal comments aren't needed!

---

### Post by Milos_SD on 2007-08-05
> **Half-Left said:**
> Dont cry like a baby,  set GIMP up so that the toolbars are above the canvas on each side, maximize the canvas your done. Or just get 2.3.x or just dont use it, it's that simple.

2.3.x has a single window option, why waste time bitching about it?

How can I set single window option in 2.3.18?

---

### Post by qamelian on 2007-08-05
> **u.b.u.n.t.u said:**
> I am proficient with Paint Shop Pro which I use regularly. I also use Photoshop.

I want however to use GIMP as a single window.

I think a single window version is on the horizon. Just wondering when.

If GIMP ever move to a single window interface, I'll basically have to avoid upgrading it...ever. The multi-window interface is one of the great strengths of GIMP and is far more useable than the single window interface of Photoshop. The flexibility of the GIMP interface is one of the main reasons why I dumped Photoshop for GIMP in the first place. A single window interface would be a major step backward in my opinion.

---

### Post by Half-Left on 2007-08-05
> **Milos_SD said:**
> How can I set single window option in 2.3.18?

Actually it's not a single windows as such but more allowing the flexibility of both.

Edit/Preferences/Window Management/Toolbox and other docks are translative to the active image window.

---

### Post by smartboyathome on 2007-08-05
That doesn't work for me... :(
I am running gutsy with the latest gimp installed. I tried that, and all I get is the panels staying above the window.

---

### Post by u.b.u.n.t.u on 2007-08-05
> **qamelian said:**
> A single window interface would be a major step backward in my opinion.

Just to state the obvious - the single window can be a toggle feature, on and off.

---

### Post by Milos_SD on 2007-08-05
> **Half-Left said:**
> Actually it's not a single windows as such but more allowing the flexibility of both.

Edit/Preferences/Window Management/Toolbox and other docks are translative to the active image window.

Thanks. I was looking for this. I don't need the photoshop single window. I needed this. :)

---

### Post by longfire on 2007-08-05
I skimmed through this thread and I'm not sure if someone already mentioned this but, the gimp is getting a redesign. 

Its been on digg for a couple days now and has gotten some good attention.

screenshot:

[http://www.venturecake.com/gimps-major-ui-revamp/](http://www.venturecake.com/gimps-major-ui-revamp/)

sites with info on the  redesign:

[http://gui.gimp.org/index.php/GIMP_UI_Redesign](http://gui.gimp.org/index.php/GIMP_UI_Redesign)

[http://www.mmiworks.net/eng/index.html](http://www.mmiworks.net/eng/index.html)

---

### Post by henriquemaia on 2007-08-06
> **Milos_SD said:**
> Thanks. I was looking for this. I don't need the photoshop single window. I needed this. :)

This new window management feature is very nice and powerful. Pressing the tab key hides the toolbox window, great when working in fullscreen mode.

---

### Post by CAD-MAN on 2007-08-06
Thanks for those links longfire; it looks interesting.

At first I didn't like the multi window interface of the GIMP, but having used it now for about a year, I've grown quite fond of it. For me, its a flexible way of displaying the program and its utilities.

Undoubtedly, some will not like it, and will not take to it like I did, so thats why I think the GIMP team would do well to offer a choice. My reason for saying this is that it will reduce the amount of time it takes for new users to become acquainted with the program (a time that was, for me, quite long - maybe a month of fairly frequent use). Now, when I go back and use photoshop at times - It takes me a little while to remember where everything is and how to use it!!

Its just about personal preference, and the more options there are, the more people will enjoy using the program.

---

### Post by Half-Left on 2007-08-06
People go on like Photoshop is easy to use, it's not, it's way harder and deeper. You learn a application and it's interface, dont expect to use something different and imply that applications should be the same because it's what your used to.

Photoshop is not your usual everyday joe's photo editor, people forgot that.

---

### Post by Merk42 on 2007-08-06
I think the reason that the single/multi window GUI is debated may be through miscommunication. Right now the multi-window of GIMP is similar to PS in that there's separate, and customizable, windows, for layers, brushes, etc.  The one place where the multi-windows of GIMP and PS different is at the bottom.  In Windows/OSX PS takes up one window down on the bottom taskbar/dock.  The GIMP on Windows/Linux (haven't tried OSX) on the other hand, takes up a space for every tool window open.

All I'd personally want is for The GIMP to only take up one space down below.

---

### Post by picpak on 2007-08-06
For now there's this:

[http://xubuntu.wordpress.com/2006/09/05/howto-run-gimp-in-one-window/](http://xubuntu.wordpress.com/2006/09/05/howto-run-gimp-in-one-window/)

Xubuntu-related, for Gnome just change xfwm4 to metacity:

```
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp --display :1
```

---

### Post by vexorian on 2007-08-06
> People go on like Photoshop is easy to use, it's not, it's way harder and deeperI have actually been using thegimp lately and there are things that are a little annoying, one is the multiwindows thing that is (yay) getting solved, but also there are things like how to get a big brush? In photoshop you only need to move an scrolling bar thing to increase the size of the brush to very big values, in the gimp you have to navigate through the hole list of brushes, and they don't have a lot of sizes, you need to add a size manually so then you can find it...

---

### Post by evissecx on 2007-08-06
You are able to choose one of those brushes and then scale it up or down. scale starts at 1 and goes down to 0.01 or up to 10.0.
Using gimp 2.3.16

---

### Post by hikaricore on 2007-08-06
Try and cut back on insulting each other folks.

Lets stay on topic.  :p

---

### Post by henriquemaia on 2007-08-06
> **vexorian said:**
> I have actually been using thegimp lately and there are things that are a little annoying, one is the multiwindows thing that is (yay) getting solved, but also there are things like how to get a big brush? In photoshop you only need to move an scrolling bar thing to increase the size of the brush to very big values, in the gimp you have to navigate through the hole list of brushes, and they don't have a lot of sizes, you need to add a size manually so then you can find it...

You can see here what you can expect in the new version:

[http://www.gimpusers.com/tutorials/gimp-2-4-new-features.html](http://www.gimpusers.com/tutorials/gimp-2-4-new-features.html)

Most of those things are solved.

---

### Post by Merk42 on 2007-08-06
I'm confused about the numbering

The latest stable is 2.2.x
The GIMP's site mentions 2.3.x development
The big changes are in 2.4.x

So there will be a slew of 2.3.x stable releases before the big changes of 2.4.x?

---

### Post by Half-Left on 2007-08-06
> **Merk42 said:**
> I'm confused about the numbering

The latest stable is 2.2.x
The GIMP's site mentions 2.3.x development
The big changes are in 2.4.x

So there will be a slew of 2.3.x stable releases before the big changes of 2.4.x?

2.2 is stable branch, 2.3 is dev branch(unstable), odd numbers development, even numbers stabel just like the linux kernel and all other software.

---

### Post by graigsmith on 2007-08-07
personally i LIKE the gimp user interface. and it's not terrible. if you take about 5 minutes to configure it.  i usually have 1 window for the gimp tools, and a window for my drawing or photo.  2 windows that's it.  I would MUCH rather be able to switch between a few drawings via the taskbar than by having to use some convoluted photoshop like way.  where you have to minimize a window inside a window, and then try to find the icon of the other minimized thing underneath the other photo. photoshop's interface is just flat out horrible for working on multiple images. where as gimps makes it much easier to switch back and forth.

---

### Post by graigsmith on 2007-08-07
ooh 18, foreground extraction, this was one thing i missed from photoshop. it's much harder to do this by hand.   

faster gaussian blur :)

healing brush. :)

2.4 is gonna be completely awesome.

---

### Post by smartboyathome on 2007-08-07
What is planned for multiple images in the single-window gimp is to use tabs to switch between images. I like that idea, actually.

btw, I would like it if the GIMP had at least a way to use the GIMP tools as 1 window (instead of multiple. Right now (as of 2.3.18), the WM is good, but it shows a window space when you have the task panel up, and doesn't show one when you don't. I would like it to be constant.

---

### Post by vexorian on 2007-08-07
> What is planned for multiple images in the single-window gimp is to use tabs to switch between images. I like that idea, actually.
That would be like moving from a weakness to an strength , I'd love tabs on thegimp.

---

### Post by leo_rockway on 2007-08-07
it would be cool if you could drag and drop the tabs into single windows, for those that like the style used now.

i personally like the tab thing.

---

### Post by RJQ on 2007-08-07
Reading the first posts I realize that they may be few people who actually do not use the right button in their mouse (if they are using a mouse) I have all my tools right there no need to replace windows except for further actions other than changing and setting tools, you can always use two windows if the quantity annoys, I think when we want to learn a program we should have the previous knowledge of how to use a computer as a whole. Right click is another world just besides your finger.:popcorn:

---

### Post by berniefranks on 2007-08-08
> **graigsmith said:**
> personally i LIKE the gimp user interface. and it's not terrible. if you take about 5 minutes to configure it.  i usually have 1 window for the gimp tools, and a window for my drawing or photo.  2 windows that's it.  I would MUCH rather be able to switch between a few drawings via the taskbar than by having to use some convoluted photoshop like way.  where you have to minimize a window inside a window, and then try to find the icon of the other minimized thing underneath the other photo. photoshop's interface is just flat out horrible for working on multiple images. where as gimps makes it much easier to switch back and forth.
I think it'd be neat to have a single window like Photoshop, but instead of the windows inside the program minimizing to a titlebar down at the bottom, they go to something like a "preview" window, and you can just switch between your images through that instead of using the taskbar or the minimizing/maximizing technique in Photoshop.

---

### Post by smartboyathome on 2007-08-08
Or, like said above, tabs!

---

### Post by Railsbuntu on 2008-07-17
> **Half-Left said:**
> Photoshop on OS X uses the same muti window layout, professionals dont complain, infact it;s what they liked about GIMP. 

2.3.x does have a option to fit all windows into one just to please the Windows users that have been used to the same old layout.

1) Photoshop on OSX uses the same multi window layout -> This is incorrect.

2) professionals dont complain -> This is correct.

3) infact it;s what they liked about GIMP -> This is incorrect.


1) Wrong, because when you click on one window of PS, all the other windows come back to the front as if they were the same window. Not having a background doesn't mean the windows are not part of the same "group".

2) True, see 1. And on OSX when you hit alt+tab, PS only appears as 1 window. On Linux or Win, you would have 3 windows for Gimp.

3) Pros rarely use Gimp anyway, so I don't know what you are talking about


As long as there is not a better alt+tab for Gimp and its multi window mode, Gimp will be hated like hell.

---

### Post by leo_rockway on 2008-07-17
> **Railsbuntu said:**
> As long as there is not a better alt+tab for Gimp and its multi window mode, Gimp will be hated like hell.

GIMP's alt-tabbing is consistent: if I alt-tab to the image, I just want to see the image, if I alt-tab to the layers I just want to see the layers. Photoshop forces me to see all the windows when that's not what I asked for.

After you alt-tab to the image in GIMP you can push tab and that will show you the tools, layers, etc. That's a better approach, IMO.

---

### Post by Merk42 on 2008-07-17
> **leo_rockway said:**
> GIMP's alt-tabbing is consistent: if I alt-tab to the image, I just want to see the image, if I alt-tab to the layers I just want to see the layers. Photoshop forces me to see all the windows when that's not what I asked for.

After you alt-tab to the image in GIMP you can push tab and that will show you the tools, layers, etc. That's a better approach, IMO.

Next time you're using Photoshop try hitting TAB or F...

---

### Post by leo_rockway on 2008-07-17
> **Merk42 said:**
> Next time you're using Photoshop try hitting TAB or F...

There won't be a next time for me an Photoshop because I don't use privative software.

The F or TAB in Photoshop doesn't change the fact that if I alt+tab to the layers window I __just__ want to see the layers window and not all the rest.

---

### Post by Merk42 on 2008-07-17
> **leo_rockway said:**
> There won't be a next time for me an Photoshop because I don't use privative software.

The F or TAB in Photoshop doesn't change the fact that if I alt+tab to the layers window I __just__ want to see the layers window and not all the rest.

I want F to have the same function in GIMP, but it doesn't so I guess that makes it inferior?

Or, I want alt-tab to cycle through tabs in Firefox, but it doesn't so I guess that makes it inferior?

If you want to use GIMP over Photoshop, fine, but don't get all high and mighty when a solution is provided to you, but you refuse to aknowledge it.

---

### Post by acelin on 2008-07-18
Haha that is why if you buy it currently its a one window program.... lol

---

### Post by leo_rockway on 2008-07-18
> **Merk42 said:**
> I want F to have the same function in GIMP, but it doesn't so I guess that makes it inferior?

Or, I want alt-tab to cycle through tabs in Firefox, but it doesn't so I guess that makes it inferior?

If you want to use GIMP over Photoshop, fine, but don't get all high and mighty when a solution is provided to you, but you refuse to aknowledge it.

You can't change Photoshop's behaviour, but you can take GIMP's code and change it. So, yes, Photoshop is inferior and that's not my opinion but a fact. If that makes you think I'm high and mighty then too bad. You can go install some Adobe crap to make you happy. Don't forget to click "Accept" on the EULA!

And for your information, you can cycle through tabs in Firefox with ctrl+tab as if you were using alt+tab with an extension (or whatever they are called, I don't use Firefox).

---

### Post by V for Vincent on 2008-07-18
Bit of an odd reasoning, you have to admit. I love large open projects like GIMP, but you cannot go preaching what isn't even there. Might as well claim that the absence of a program is superior to photoshop because you can write your own.

Free software is great, but if people want to charge for functionality no one else is offering, let them. Or write a new program with the same or better functionality.

---

### Post by AJB2K3 on 2008-07-18
> **V for Vincent said:**
> Bit of an odd reasoning, you have to admit. I love large open projects like GIMP, but you cannot go preaching what isn't even there. Might as well claim that the absence of a program is superior to photoshop because you can write your own.

Free software is great, but if people want to charge for functionality no one else is offering, let them. Or write a new program with the same or better functionality.
Ah but for photoshop you have to write a whole new app where as with gimp you just fork the code and mod it slightly.

Your not allow to know how photoshop works or does its buisness whereas gimp you are incouraged to look through the code, learn ho it works and mod it.

BTW **leo_rockway**You forgot to mention **PAY over the odd** then click accept.

---

### Post by V for Vincent on 2008-07-18
I'm quite aware of that. I'm just saying that as long as the possibility is there without it actually being taken advantage of, there's no reason to go touting your program's superiority. For your interest, I've never even used photoshop. In order to succeed, open source should maintain high standards and an unbiased view.

---

### Post by Kimmik on 2008-07-18
I think a single window gimp would really suck. They shouldn't change the gui, it's already very nice (and super flexible).
I'm a fan. ;)

---

### Post by AJB2K3 on 2008-07-19
Ok IMHO there should be the single windows option because

On systems with a single screen/monitor multiple pannels are down right annoying.
On Muli/Duel screens multiple panels are sweet because you can banish them to the second window and arrange them to better suit your work flow leaving one screen purely work the work piece.
So there are pro's and cons of having the normal gimp layout over a single window setup.

---

### Post by pixelnate on 2008-07-20
> **AJB2K3 said:**
> Ok IMHO there should be the single windows option because

On systems with a single screen/monitor multiple pannels are down right annoying.
On Muli/Duel screens multiple panels are sweet because you can banish them to the second window and arrange them to better suit your work flow leaving one screen purely work the work piece.
So there are pro's and cons of having the normal gimp layout over a single window setup.

It just bothers me that the palettes can be covered with image windows. The palettes should always be visible, and adding the TAB function to hide all palettes is a GOOD idea. IMHO, everything in the Gimp interface takes far too many clicks, and there aren't enough key+click combos to avoid all the clicking.

For example, in PS you can Cmd-click (Ctrl-click in Windows), to activate a selection based on the layer's alpha. To do that in Gimp you have to right-click on the layer then click on "Alpha to selection". It sounds like nitpicking, but my left hand is already on the keyboard for other keyboard shortcuts, why do I need to click twice on the mouse to do something that could only take one click? I am not bagging on Gimp, I think that for a FOSS app it's great, but the UI needs to be sped up a bit.

Another example, when I click on the add layer icon at the bottom of the layers palette, I am confronted with three options before I can continue: layer name, size, background. WHY? I just want a new layer, presumable transparent because I have layers behind it, at the document size. Why on Earth would I want a layer size smaller (bigger?!) than my document? If there really is a need for so many options e-v-e-r-y single time I try and doing something, please provide me with the option of setting my own defaults.

And just to add to the fire: Photoshop is *NOT* inferior to the Gimp. The license is inferior to the Gimp, but PS is by far the better tool for manipulating photos. I should know, I do it 8 hours a day, 5 days a week, and have been doing it for 15 years (since PS 2.5 was released into the wild). A full switch to the Gimp from PS would be like going back to Photoshop 4. Except that PS 4 supported CMYK and 16-bit images.

:guitar:

---

### Post by Merk42 on 2008-07-20
> **AJB2K3 said:**
> Ok IMHO there should be the single windows option..

Exactly, why can't it be an option? It's like when people want a GUI frontend for something all all the CLI avocates get up in arms.  It's not like you can't still use the CLI, but having an option is nice.  Isn't that what FOSS is about? OPTIONS?

 If it were implimented, I'd like it to be a first run tool tip. "GIMP now has the opiton for a single window click here to change to it" sort of thing.

> **pixelnate said:**
> And just to add to the fire: Photoshop is *NOT* inferior to the Gimp. The license is inferior to the Gimp.

I whole heartitly agree.  I think some people out there that believe any FOSS is better than closed source simply because it's FOSS.

---

### Post by leo_rockway on 2008-07-22
> **Merk42 said:**
> Exactly, why can't it be an option?

But it can! Start coding and it will be an option, but don't bug the developers to do something they don't believe in.

> **Merk42 said:**
> I think some people out there that believe any FOSS is better than closed source simply because it's FOSS.

Mais oui! For me it is Free Software or none at all. If more people thought like me we wouldn't have any more crazy EULAs.

---

### Post by V for Vincent on 2008-07-22
First, the lack of an EULA does not say anything about the quality of your program. Second, competition is often a good thing. A lot of great open source programs try to provide an alternative to commercial products; if those commercial products didn't exist, the aforementioned open source products would not always be of the same quality. Any distro is better off stealing some ideas from other OS'es than simply pretending those did not exist.

---

### Post by pixelnate on 2008-07-22
> **leo_rockway said:**
> But it can! Start coding and it will be an option, but don't bug the developers to do something they don't believe in.

Shouldn't it be more about what the users want? I mean, that's what commercial software vendors do. You pay for their effort, but ultimately you get what you pay for. Besides I know jack about C.

> **leo_rockway said:**
> Mais oui! For me it is Free Software or none at all. If more people thought like me we wouldn't have any more crazy EULAs.

As long as your needs for software tools are in line with what the developers believe in then you should be safe.


~Nate

---

### Post by dgrafix on 2008-07-22
This is my biggest moan! I HATE the mac-photoshop style of everything in its own taskbar item. Comming from a PSP background i just cant get why its like this. Its neither friendly or pleasant. Why cant i get the tools to just stay at the edge? Why cant the windows be nested like a proper paint prog? Other than that gimp is quite cool but find myself prefering PSP in wine more than using gimp, simply because of this.

---

### Post by pixelnate on 2008-07-22
> **dgrafix said:**
> This is my biggest moan! I HATE the mac-photoshop style of everything in its own taskbar item. Comming from a PSP background i just cant get why its like this. Its neither friendly or pleasant. Why cant i get the tools to just stay at the edge? Why cant the windows be nested like a proper paint prog? Other than that gimp is quite cool but find myself prefering PSP in wine more than using gimp, simply because of this.

I am not quite sure I follow you. Which side of the single window argument are you on again?

---

### Post by Merk42 on 2008-07-22
> **leo_rockway said:**
> But it can! Start coding and it will be an option, but don't bug the developers to do something they don't believe in.

So the only people that should get software to do what they want is by programming it themselves?  What's the point beyond the [Idea Pool](http://ubuntuforums.org/forumdisplay.php?f=306) then?  Programmers only?

> **leo_rockway said:**
> Mais oui! For me it is Free Software or none at all. If more people thought like me we wouldn't have any more crazy EULAs.

If you want to only use FOSS that's fine.  But for some of use we look at how well the program performs, to make our decision, not the license.  To paraphrase Chris Farley's character in Tommy Boy > Hey, if you want me to take a dump in a box and give you a list of what I ate, I will. I got spare time. But for right now, ya might wanna think about the quality of the software. 

---

### Post by dgrafix on 2008-07-23
> I am not quite sure I follow you. Which side of the single window argument are you on again? Not really on anyones 'side' i am just saying the fact that the gimp isn't treated as one application window (with sub-windows for images/tools) is a pain.I would like it to be like PSP & photoshop(as in win version, not osx) in the way it uses window management.

---

### Post by Orlsend on 2008-07-23
Agree, But Both options would be cool

---

### Post by pixelnate on 2008-07-23
> **dgrafix said:**
> Not really on anyones 'side' i am just saying the fact that the gimp isn't treated as one application window (with sub-windows for images/tools) is a pain.


I agree. When you are ALT-TAB-ing through the open windows, all the palettes should show as a single entity. I would also suggest that they are always in front of project windows. I don't know whether it's a GTK thing or what, but why would the project windows be allowed to cover a palette anyway?

---

### Post by leo_rockway on 2008-07-23
> **pixelnate said:**
> Shouldn't it be more about what the users want? I mean, that's what commercial software vendors do. You pay for their effort, but ultimately you get what you pay for. Besides I know jack about C.

No, it shouldn't be about what the users want if the developers don't believe in that. Commercial software vendors (although what you mean is Privative software vendors) don't do what the users want (try sending your ideas to Adobe... I still haven't seen a 64bit version of Adobe Flash).

And since you mention the "you get what you pay for" axiom, I must say that in this case it is absolutely true. The fact that you didn't pay for GIMP means that you can't complain about it. If you know jack about C, pay a developer to make the necessary changes for you... you know, like with all that Privative software you praise. You pay, you get the changes you want.

---

### Post by pixelnate on 2008-07-23
> **leo_rockway said:**
> No, it shouldn't be about what the users want if the developers don't believe in that.

Then that's where it all falls down isn't it. With a program like Gimp it's not about scratching your own itch. Many people are affected by their software. If they feel no obligation to their users then they need to get out of the software game. Software is always about the users.

> **leo_rockway said:**
> Commercial software vendors (although what you mean is Privative software vendors) don't do what the users want (try sending your ideas to Adobe... I still haven't seen a 64bit version of Adobe Flash).

No, I don't mean "Privative" software vendors. I don't mean private software vendors either. I mean COMMERCIAL software vendors. They write software, they sell it, people buy it. They are commercial software vendors. I won't bother splitting hairs more than this. You are projecting the face of a Free Software zealot, ala. Richard Stallman, and I just don't feel like duking it out over symatics.

And as far as the 64-bit version of the Flash PLAYER, why don't you just hack on Gnash for a while. Now that Adobe has opened up the format, you should have no problem whipping that up this weekend.

> **leo_rockway said:**
> And since you mention the "you get what you pay for" axiom, I must say that in this case it is absolutely true. The fact that you didn't pay for GIMP means that you can't complain about it.

I would gladly pay for it if it were worth paying for. The feature set is far too limited for me to do all my work in it. When there comes a time when that is possible, I would consider it.

> **leo_rockway said:**
> If you know jack about C, pay a developer to make the necessary changes for you... you know, like with all that Privative software you praise. You pay, you get the changes you want.

I have. I paid Adobe to put together the features I need to do my work. When the Gimp developers deliver a more usable product then I will certainly donate to their cause. By my calculations, Gimp 2.4 = Photoshop 4 (roughly), then Gimp 4 = Photoshop 6 (I think it was v6 when Adjustments layers and layer effects were added). Until then it's just one of many tools for editing uncomplicated RGB images.

---

### Post by dmn_clown on 2008-07-23
> **leo_rockway said:**
> And since you mention the "you get what you pay for" axiom, I must say that in this case it is absolutely true. The fact that you didn't pay for GIMP means that you can't complain about it. If you know jack about C, pay a developer to make the necessary changes for you... you know, like with all that Privative software you praise. You pay, you get the changes you want.

*sigh* The fact that the gimp developers have stated it is meant for "professional" users as someone stated earlier in the thread should signify that the developers don't really have a clue as to what _they_ want let alone what their users want as there isn't a stable release of the gimp that can be used professionally.  

Now, had they not had their heads firmly entrenched in their butts several years ago and had included the patches that went on to become Cinepaint[1], I could agree with them that they were aiming for professional users, but as they refused to merge those patches and give their users what should be considered basic functionality why should anyone use the program?  There are other options, and most of those options aren't going to hold their users hostage due to a political decision.

[1] the second most popular image editor in the major vfx studios behind photoshop... gimp lost out due to politics.

---

### Post by pixelnate on 2008-07-23
Thank you dmn_clown. You are right on the money. It sad that it hasn't progressed further. I really *want* to make it my app of choice, and I *want* to go fully with open source apps, but image editors and video editors are holding that decision back for me. Scribus is more than good enough to replace Quark/InDesign, Inkscape is a very good alternative for Illustrator (mostly), but Gimp is just so far behind Photoshop that it's hard to justify using sometimes.

---

### Post by leo_rockway on 2008-07-23
> **pixelnate said:**
> Then that's where it all falls down isn't it. With a program like Gimp it's not about scratching your own itch. Many people are affected by their software. If they feel no obligation to their users then they need to get out of the software game. Software is always about the users.

Oh yeah? what about Adobe Flash 64? I do __not__ use Adobe Flash and I do __not__ have a 64bit architecture, but that doesn't change the fact that software is never about the users. Privative software developers are in it for the money, Free Software developers are there to scratch their itches. And privative software developers have a tendency to not listen to users. With GIMP they do listen to you and they tell you "we are not interested in your idea". Does that suck for you? Too bad, at least you know what to expect. Now, what has been the official report on Adobe Flash 64 lately...?

> **pixelnate said:**
> You are projecting the face of a Free Software zealot, ala. Richard Stallman

Why! Thank you, that's the best thing anybody has ever told me in this forum.

> **dmn_clown said:**
> *sigh* The fact that the gimp developers have stated it is meant for "professional" users...

In their website it is never said it is for "professional" use. Nothing can be developed for "professional" use since usage dictates what is professional and what is not and not the other way around.

> **dmn_clown said:**
> There are other options, and most of those options aren't going to hold their users hostage due to a political decision.

Open your eyes, this is GNU, the fact that you are using it is a political decision by itself. If you don't like that political decision then don't use it, go buy a permission from Adobe to legally use Photoshop.
EULAs make you a hostage, not GPL.

> **pixelnate said:**
> but Gimp is just so far behind Photoshop that it's hard to justify using sometimes.

Then don't use it, but don't try to make it go in the direction you want it to go. Developers don't want a single window GIMP, then why bother them if you are not going to use GIMP anyway?

---

### Post by Merk42 on 2008-07-23
I think this needs to be its own thread. It's getting less about when there will be a single window in GIMP and more about FOSS in general.

Although it seems like the sort of "discussion" where neither side sees the validity in the others point of view.

---

### Post by suarez.duek on 2008-07-23
The window use of Gimp is just FINE, i got used to it, and find it very useful now!!!

---

### Post by leo_rockway on 2008-07-23
> **Merk42 said:**
> I think this needs to be its own thread. It's getting less about when there will be a single window in GIMP and more about FOSS in general.

Although it seems like the sort of "discussion" where neither side sees the validity in the others point of view.

+1

I won't be posting here anymore; my opinion is already more than clear. Just letting you all know there is another really good app like GIMP that follows the single window approach: Krita. I like GIMP a lot better and that coming from a big KDE fanboi means a lot, haha, but that doesn't mean Krita is bad. One of the things that kept me from using Krita was, believe or not, the single window layout (there might be an option to change that, but I never checked). Give Krita a try, you may come to like it.

---

### Post by hessiess on 2008-07-24
single window programs waste far too much space by colouring it gray os simmaler. gimp or photoshop on mac dos not do this if you arange the windows propaly. photoshop on windows SUCKS!

---

### Post by dmn_clown on 2008-07-24
> **leo_rockway said:**
> In their website it is never said it is for "professional" use. Nothing can be developed for "professional" use since usage dictates what is professional and what is not and not the other way around.

That second hand quote was taken from their BTS out of the mouth of a gimp contributer.

> Open your eyes, this is GNU, the fact that you are using it is a political decision by itself. If you don't like that political decision then don't use it, go buy a permission from Adobe to legally use Photoshop.
EULAs make you a hostage, not GPL.

Choosing a tool that provides basic functionality over a tool that doesn't _is_ _not_ a political decision.  The Gimp developers choosing to not merge the patches that became Cinepaint _was_ a political decision.  Please understand this before you flame me again :)

---

### Post by Merk42 on 2008-07-25
> **hessiess said:**
> single window programs waste far too much space by colouring it gray os simmaler. gimp or photoshop on mac dos not do this if you arange the windows propaly. photoshop on windows SUCKS!

I **think** this is a common misconception about the single window thing. For myself, and I believe others, it's not that it takes up multiple windows in the work area, but that each window takes up space at the bottom panel.

Some people do like the grey background of Windows Illustrator/Photoshop because it makes it so their eye isn't distracted by the desktop and they can focus on the colors and design of what they're working on.

---

### Post by hessiess on 2008-07-25
> **Merk42 said:**
> I **think** this is a common misconception about the single window thing. For myself, and I believe others, it's not that it takes up multiple windows in the work area, but that each window takes up space at the bottom panel.

Some people do like the grey background of Windows Illustrator/Photoshop because it makes it so their eye isn't distracted by the desktop and they can focus on the colors and design of what they're working on.

If its that big of a problem then just auto hide the panel(s). personally I just run gimp in a different workspace. and set 'always on top' on the main windows. the panels are always auto hide as they waste too much screen space, which is why ive come to like tileing window managers recently. anouther advantage to them is thay have no pannels, so the GIMP 'problem' becomes a no-issue.

---

### Post by dgrafix on 2008-07-26
> Then don't use it, but don't try to make it go in the direction you want it to go. Developers don't want a single window GIMP, then why bother them if you are not going to use GIMP anyway? and the nearest alternative is? Unfortunately its the only one. I would buy pixel as it was looking promising but it seems to have stopped development.

Anyway, for those that are interested, I have found one comprimise in the options, under dialoges->toolbox. Notice you can set a hotkey for tools. This will bring up the tool pallette. I have assigned this to the never-used "menu" key on my keyboard (the one between altgr and ctrl) 

I would still prefer to have the tools properly docked on the side of the window though.

---

### Post by leo_rockway on 2008-07-26
I said I wouldn't be posting here anymore... but... yeah, haha. I couldn't help myself.

> **dmn_clown said:**
> That second hand quote was taken from their BTS out of the mouth of a gimp contributer.

GIMP contributor, haha. This is Free Software, anyone can be a GIMP contributor, that doesn't mean that all comments on their behalf entail an official report.

> **dmn_clown said:**
> Choosing a tool that provides basic functionality over a tool that doesn't _is_ _not_ a political decision.  The Gimp developers choosing to not merge the patches that became Cinepaint _was_ a political decision.  Please understand this before you flame me again :)

Please understand that GNU is a political decision before you consider my comments flame. Choosing a GNU tool _is_ a political decision at all times. Choosing not to merge the Cinepaint patches was an objective decision. They wanted GIMP to be GIMP and not Cinepaint. Why don't you use Cinepaint if you like it so much and leave GIMP alone then?

> **dgrafix said:**
> and the nearest alternative is? Unfortunately its the only one.

No, it's not!

> **leo_rockway said:**
> Just letting you all know there is another really good app like GIMP that follows the single window approach: Krita. I like GIMP a lot better and that coming from a big KDE fanboi means a lot, haha, but that doesn't mean Krita is bad. One of the things that kept me from using Krita was, believe or not, the single window layout (there might be an option to change that, but I never checked). Give Krita a try, you may come to like it.

---

### Post by pixelnate on 2008-07-26
> **leo_rockway said:**
> Choosing not to merge the Cinepaint patches was an objective decision. They wanted GIMP to be GIMP and not Cinepaint. Why don't you use Cinepaint if you like it so much and leave GIMP alone then?

It wasn't entirely objective, but that is a discussion for another time. It would have been really nice if they had added the 16-bit support from Cinepaint, though.

---

### Post by dgrafix on 2008-07-26
> No its not! Really? I want an app thats like paintshop pro. Can you reccomend me one. (It needs to be a feasible alternative, ie just as good.)

The only half-decent 2D non vector 'art' apps i have found that come even close to rivaling PSP/PS are gimp and pixel.

---

### Post by pixelnate on 2008-07-26
> **dgrafix said:**
> Really? I want an app thats like paintshop pro. Can you reccomend me one. (It needs to be a feasible alternative, ie just as good.)

While it's not free or open (but it is fairly inexpensive), [Bibble]("http://bibblelabs.com/") is pretty close to what I understand PSP to be plus a bit more for professional photographers. Another good one is [LightZone]("http://www.lightcrafts.com/products/index.html"). Both apps are geared more toward photographers than photomanipulators, but they both look good.

---

### Post by leo_rockway on 2008-07-27
> **dgrafix said:**
> Really? I want an app thats like paintshop pro. Can you reccomend me one. (It needs to be a feasible alternative, ie just as good.)


For the third time: KRITA!

---

### Post by pixelnate on 2008-07-27
> **leo_rockway said:**
> For the third time: KRITA!

Seriously, dude, it's much worse than the gimp for photo manipulation. It is a good beginning of an image app, but the interface conventions and shortcuts are even more lacking than the gimp as well. It does allow for working with 16-bit images and has layer effects and adjustments layers, but doing any work in it is just excruciatingly slow.

I tell ya, if the Krita guys and the Gimp guys and the Cinepaint guys got together and wrote an image editing app it would rock. Each app has complementary strengths and corresponding weaknesses. Or if Pavel K. would just open-source Pixel we could get what we want. Hey, I can dream can't I.

---

### Post by dgrafix on 2008-07-27
Thanks for the pointers, ill take a look at these :D. I dont really use mine for photo editing anyway, i want an 'art' package (which is why i personally prefer paintshop pro over photoshop) but I have not yet found one on linux to match the comfortable and intuitive quality of paintshop pro (or photoshop for that matter).

However will check these others out and see.


EDIT:
Hmm, none of those seem to be any good for me.
Krita is KDE not gnome
Bibble/Lightzone dont seem to be paint packages at all, its some kind of photo filter/conversion thing.

gonna check out cinepaint although it looks like it has the same kind of separated interface as gimp :/

---

### Post by leo_rockway on 2008-07-27
> **dgrafix said:**
> 
EDIT:
Hmm, none of those seem to be any good for me.
Krita is KDE not gnome


I didn't think that would be a problem since I'm used to mixing GTK and QT apps sometimes, but I understand why some people wouldn't like to do that.

> **dgrafix said:**
> gonna check out cinepaint although it looks like it has the same kind of separated interface as gimp :/

Unfortunately (for you) it looks pretty much like GIMP; that means that the interface doesn't have a container window.

EDIT:
> **pixelnate said:**
> Seriously, dude, it's much worse than the gimp for photo manipulation. It is a good beginning of an image app, but the interface conventions and shortcuts are even more lacking than the gimp as well.

Worse than the GIMP? Only because it has a window container!
The interface conventions are KDE's interface conventions (ie. IMO great, but I don't like Gnome).
The shortcuts comment only shows that you are ignorant of KDE. You can change absolutely all shortcuts of Krita in (wait, you are going to love this) Settings > Configure Shortcuts!

---

### Post by pixelnate on 2008-07-27
> **leo_rockway said:**
> I didn't think that would be a problem since I'm used to mixing GTK and QT apps sometimes, but I understand why some people wouldn't like to do that.

Yeah, honestly, it's not really that big a deal to run KDE apps in Gnome. The only bother is that it takes a few extra seconds to start up the first time you start a KDE app. After that it's just like they were GDM apps. With one exception, that is, sometimes the fonts in the apps don't match up quite right (sizes, font families, etc.). There's a way to synchronize your fonts a bit more, but I can't remember it right now.

> **leo_rockway said:**
> Worse than the GIMP? Only because it has a window container! The interface conventions are KDE's interface conventions (ie. IMO great, but I don't like Gnome). The shortcuts comment only shows that you are ignorant of KDE. You can change absolutely all shortcuts of Krita in (wait, you are going to love this) Settings > Configure Shortcuts!

Come on, man, no need to get snippy. I am fully aware of the shortcut definitions, but Krita doesn't come set up with any but the most basic shortcuts defined. Also, there are some things that don't have any hooks for shortcuts, like resizing brushes on the fly. Photoshop and Gimp can both do this using '[' (decrease) and ']' (increase) for brushes.

Please don't give me the 'just add them yourself' line again. Once KDE goes to version 4.1, and I get a little more free time, I do plan on helping out on Krita, especially now that so many KDE apps can be modified with Ruby. If you want to know the truth, I am much more taken by Krita than Gimp, and would like to see that project move along a little faster.

---

### Post by dgrafix on 2008-07-28
Ok, im getting quite into the gimps drawing tools, but cannot seem to find a way of adding a vector layer to my drawing. I find this useful for adding construction lines, guidance geometry and occasionally text but may need to edit it afterwards quickly without having to draw it all again. (and using inkscape is not what i mean). The other problem is point to point selection, does it exist? i can only find freehand rectangle and elipse.

---

### Post by CarpKing on 2008-07-29
> **dgrafix said:**
> Ok, im getting quite into the gimps drawing tools, but cannot seem to find a way of adding a vector layer to my drawing. I find this useful for adding construction lines, guidance geometry and occasionally text but may need to edit it afterwards quickly without having to draw it all again. (and using inkscape is not what i mean). The other problem is point to point selection, does it exist? i can only find freehand rectangle and elipse.

Gimp doesn't have vector layers, but it does have paths, which are vectors and might do at least some of what you want.  Make sure to look at the Paths dialog, as new paths are not set as visible by default and so will disappear once you switch tools. SVG files can also be loaded as paths, but you will only get the outline.  Once you have a path in place, the buttons at the bottom of the paths dialog allow you to trace the path with lines or tools.  You can also convert the path to a selection, which seems to be the sort of thing you want to do with "point to point selection."  The other selection tool is "intelligent scissors," where you specify points and it will guess the route between.

---

