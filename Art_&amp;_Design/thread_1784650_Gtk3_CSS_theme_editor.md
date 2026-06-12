---
title: "Gtk3 CSS theme editor"
date: 2011-06-17
forum: Art &amp; Design
---

### Post by lucazade on 2011-06-17
**Gtk3 CSS theme editor**


_**Description:**_
A visual editor for Gtk3 CSS themes.
Something like a mix of TheWidgetFactory and Firebug.

At the moment just an idea, nothing more.
I'll try to complete this post as soon as possible with more details :)


_**Mockup:**_
[IMG]http://dl.dropbox.com/u/1338581/varie/sparkler/mockup.png[/IMG]

---

### Post by CreativeReach on 2011-06-18
That I just what I want! sounds awseome.

---

### Post by tista on 2011-06-19
Hi all.

today I'm starting new PPA!! :):
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

then I would add "The Widget Factory" for gtk3, elementary-gtk2/3 combo theme pack, elemetnary-gnome-shell theme, and more...

the next would be an application of CSS editing tools. yeah actually I've made some scratches written in Vala, but PyGTK would be more better to development speed and flexibilities on GTK....

Cheers.

---

### Post by lucazade on 2011-06-20
Great Tista :)

Nice to hear from you...
If you want you can include also my [theme]("https://launchpad.net/~lucazade/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric") which is both gtk2(murrine)/gtk3(unico),
is almost finished.. now I've to polish Ambiance theme gtk3 for OO release then we can include this as well. This way the PPA will include also some themes to work on with the CSS editor..

Let me know how to work on the app together, or how to help you.
If you want I can create the Gui of the app with Glade and Gtk3.. see you :)

Edit: ideas for the name of the application?

---

### Post by LarsKongo on 2011-06-20
Sounds like a great idea. :)

> **lucazade said:**
> gtk3(unico)
Is the Unico engine stable enough to use yet?

---

### Post by lucazade on 2011-06-20
> **LarsKongo said:**
> Sounds like a great idea. :)


Is the Unico engine stable enough to use yet?

Oh, one of the best theme maker here ;)

Unico is almost ready, at least Cimi said, lacks some bits for scrollbar, scale, expander, arrows. Gnome-panel3 also is not fully themable, like adwaita.

For the rest is great, at the moment unico packages available in OO repos are not in sync with bzr so I'm currently building from sources.. I believe in a short time will be complete (knowing Cimi super speed in development!)

This is the current state of unico, at least working on my theme:
[http://dl.dropbox.com/u/1338581/varie/sparkler/unico-state.png](http://dl.dropbox.com/u/1338581/varie/sparkler/unico-state.png)

---

### Post by tista on 2011-06-20
> **lucazade said:**
> Great Tista :)

Nice to hear from you...
If you want you can include also my [theme]("https://launchpad.net/~lucazade/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric") which is both gtk2(murrine)/gtk3(unico),
is almost finished.. now I've to polish Ambiance theme gtk3 for OO release then we can include this as well. This way the PPA will include also some themes to work on with the CSS editor..

Let me know how to work on the app together, or how to help you.
If you want I can create the Gui of the app with Glade and Gtk3.. see you :)

Edit: ideas for the name of the application?

Hi Luca.
happy 1000 posts!! ;)

OK. let's include yours on my PPA!
I have some ideas about that. yeah super-boot-manager has plymouth theme selector. it might be made by really simple script but works quickly and stable. that's nice!! if we could, download the theme and install it automatically to load them on our theme editor, how about it?

the super-boot-manager also has PPA included some themes in same place to apps. I think it's nice ideas...

hopefully I want you to make GUI. :P
because I really had poor brain for python...
C++/Vala are able to make really fast apps, but code maintaining is  wasting much time. it's the negative...
we should make it by "easy codes" and maintain it easy, right? if we could, we can update the codes within coffee breaks! :) yeah most people didn't have much time.

finally yep I'm thinking the name of apps. actually you're the originator about it, so you should name it!! ;) and I hope it would be included in OO main repository...

Cheers.

---

### Post by lucazade on 2011-06-20
I was thinking to Sparkler or PimpMyGnome as name of the app, i'm open to suggestion.
Thopiekar is going to help us with python..he doesn't know gtk bindings so well but for the rest he's good. Yep, this is a spare time project :)
I'm going to open on lp a project with bzr and create a skeleton of pygi and gui.

---

### Post by slooksterpsv on 2011-06-20
Hmmm... I really like the name Sparkler, it has a nice ring to it. 

No offense, but PimpMyGnome sounds like something you'd use to theme your myspace profile haha - again no offense. Sparkler, I just love it, it sounds amazing =D

---

### Post by tista on 2011-06-20
Hey Luca.

see my shot.
here is what I'm doing now... ;)

Ciao!

---

### Post by lucazade on 2011-06-20
> **tista said:**
> Hey Luca.

see my shot.
here is what I'm doing now... ;)

Ciao!

:)

Nice.. I was playing as well..
I've to remove some rust from my python reminiscences, and learn new PyGi and gtkbuilder (I knew pygtk and glade)

[http://dl.dropbox.com/u/1338581/varie/sparkler/glade.png](http://dl.dropbox.com/u/1338581/varie/sparkler/glade.png)

@slooksterpsv

Sparkler seems the most decent name I thought :P

---

### Post by lucazade on 2011-06-20
Created a new project on Launchpad called "Sparkler"
[https://launchpad.net/sparkler](https://launchpad.net/sparkler)

and a related team:
[https://launchpad.net/~sparkler](https://launchpad.net/~sparkler)

I've also pushed a first commit, just a placeholder, nothing special:
[https://code.launchpad.net/sparkler](https://code.launchpad.net/sparkler)

I've added both Tista and Thopiekar to team, anyone else want to contribute ask for enter the team.

(looking for a nice icon/logo for the app!)
see you

---

### Post by tista on 2011-06-20
Thanks Luca.

now I'm seeing rev01... that's really fun!! :)

and then, I've already forked your themings to my PPA:
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

also my gnome-shell theme for elementary had landed....;)
but this initial release didn't handle pre-existed theme directory, so you first move to back-up this dir...

finally, I would fork my themings for OO, too.

cheers.

---

### Post by lucazade on 2011-06-20
> **tista said:**
> 
now I'm seeing rev01... that's really fun!! :)

more than fun..
I was testing/tasting python/glade with gtk3.. nothing serious :)

---

### Post by bmbaker on 2011-06-20
> **lucazade said:**
> I was thinking to Sparkler or PimpMyGnome as name of the app, i'm open to suggestion.
Thopiekar is going to help us with python..he doesn't know gtk bindings so well but for the rest he's good. Yep, this is a spare time project :)
I'm going to open on lp a project with bzr and create a skeleton of pygi and gui.
this sounds great look forward to playing with "it" whatever you end up calling it! Sparkler does have a nice ring to it :-)
though PimpMyGnome sounds like the red light district of Amsterdam :-) :-)

---

### Post by lucazade on 2011-06-20
> **bmbaker said:**
> 
though PimpMyGnome sounds like the red light district of Amsterdam :-) :-)
can't stop laughing :)

---

### Post by AleveSicofante on 2011-06-20
Sparkler is a very nice name.

This piece of software is a very much needed one. Contratulations for the idea.

---

### Post by tista on 2011-06-20
Hi guys. ;)

Just now I've updated the widget factory to 0.2.1-2-natty3!!
yeah I've fixed "theme" button could select gtk3 theme properly...
these include /usr/share/themes/ and $HOME/.themes/. and twf would search proper gtk.css automatically and liseted them up in "theme" button's pull-down lists.

soon launchpad would publish this version, so you guys give a try!! :)

cheers.

P.S:
[IMG]http://i55.tinypic.com/ei6xdf.png[/IMG]
I thought "sparkler" as umm... Spark Plug?!
here was the mockup for icons...

or something like that...

---

### Post by slooksterpsv on 2011-06-21
> **tista said:**
> Hi guys. ;)

Just now I've updated the widget factory to 0.2.1-2-natty3!!
yeah I've fixed "theme" button could select gtk3 theme properly...
these include /usr/share/themes/ and $HOME/.themes/. and twf would search proper gtk.css automatically and liseted them up in "theme" button's pull-down lists.

soon launchpad would publish this version, so you guys give a try!! :)

cheers.

P.S:
...
I thought "sparkler" as umm... Spark Plug?!
here was the mockup for icons...

or something like that...
Sparkler:
[IMG]http://static.howstuffworks.com/gif/firework-sparkler.jpg[/IMG]

---

### Post by lucazade on 2011-06-21
My idea of the name came from an episode of The Simpsons... 
Where Homer sees his face on a box of Japanese detergent and is like, holy crap, they stole my face?
Anyway, that logo is actually a meld of two big corporate logos -- a fish and a lightbulb -- and they call it Mr. Sparkle.

[IMG]http://m.profilelayouts.com/pl/ss/2086.jpg[/IMG]

[http://www.youtube.com/watch?v=VUNHwP2q7bA](http://www.youtube.com/watch?v=VUNHwP2q7bA)

---

### Post by tista on 2011-06-21
@slooksterpsv

OMG! thanks. finally I could understand what the "sparkler" was... ;)

@Luca

OK. I'm thinking the combination of fish and lightbulb....;)

---

### Post by bmbaker on 2011-06-21
> **lucazade said:**
> My idea of the name came from an episode of The Simpsons... 
Where Homer sees his face on a box of Japanese detergent and is like, holy crap, they stole my face?
Anyway, that logo is actually a meld of two big corporate logos -- a fish and a lightbulb -- and they call it Mr. Sparkle.

[IMG]http://m.profilelayouts.com/pl/ss/2086.jpg[/IMG]

[http://www.youtube.com/watch?v=VUNHwP2q7bA](http://www.youtube.com/watch?v=VUNHwP2q7bA)

wow homer as a cross between a light-bulb and a fish !! hehe :-)

---

### Post by lucazade on 2011-06-21
Slowly taking a shape.. 

[[IMG]http://dl.dropbox.com/u/1338581/varie/sparkler/pic1s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/sparkler/pic1.png")

---

### Post by tista on 2011-06-22
Hi Luca.

What a nice GUI you made?! lol
keep up the amazing work...

then, today I've opened my PPA's theme on "Gnome-Look".
[http://gnome-look.org/content/show.php/elementary-borderless-elegance?content=142930&PHPSESSID=833bf8190f491a7c3e081bcdea04fde0]("http://gnome-look.org/content/show.php/elementary-borderless-elegance?content=142930&PHPSESSID=833bf8190f491a7c3e081bcdea04fde0")

if you could, you should also open yours to everybody might need gtk3/Unico theming!! ;)

cheers.

---

### Post by jpfle on 2011-09-12
See GTK Theme Maker:

[http://opendesktop.org/content/show.php?content=144321](http://opendesktop.org/content/show.php?content=144321)

---

### Post by ThrashManiac on 2013-01-16
> **tista said:**
> Hi Luca.

What a nice GUI you made?! lol
keep up the amazing work...

then, today I've opened my PPA's theme on "Gnome-Look".
[http://gnome-look.org/content/show.php/elementary-borderless-elegance?content=142930&PHPSESSID=833bf8190f491a7c3e081bcdea04fde0]("http://gnome-look.org/content/show.php/elementary-borderless-elegance?content=142930&PHPSESSID=833bf8190f491a7c3e081bcdea04fde0")

if you could, you should also open yours to everybody might need gtk3/Unico theming!! ;)

cheers.

Wow! Very nice theme! Is it's based on Greybird? Doesn't matter)) Is this theme compatible with Fedora 18 (today is the release day, btw) ?

---

### Post by Runningclams on 2013-01-17
Sounds like a good idea, I'm completely new to Ubuntu and Linux in general and I'm still looking for a good theme.

---

