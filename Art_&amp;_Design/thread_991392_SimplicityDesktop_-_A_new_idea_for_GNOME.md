---
title: "SimplicityDesktop - A new idea for GNOME"
date: 2008-11-23
forum: Art &amp; Design
---

### Post by LegoAddict on 2008-11-23
So I got thinking about desktops recently, and thought about the way we have it now.

Think about it:  GNOME is my favourite desktop environment.  It doesn't carry app launchers (usually), just stuff I haven't cleared off in to other folders and mounted drives.  But it really doesn't do anything.  It's just organizational space.

What if we took the desktop and remade it for multitasking and productivity?  The comp (which I've called Simplicity) below is what I was thinking of

[IMG]http://i107.photobucket.com/albums/m286/LegoAddict/simplicitydesktop.jpg[/IMG]

The semitransparent windows are windows stuck to the desktop, not actual app windows.  For the SimplicityDesktop "desklet" all you do to add a launcher of an often-used app is drag and drop it from the app bar.  The box keeps it organized so we don't have the common woe of Windows desktops.

SimplicityReader allows users to check their news or whatever at a glance, without opening an app.

The sidebar would be completely customizable.  This screenshot shows Sidebar running a mail reader, an applet with facebook and IM integration, and SimplicityOnTask.

OnTask is a special part of this idea.  If you click on a package, a popup appears with a checklist of what needs to be done in that project.  Depending on how you set the urgency or the due date, the package changes colour.  It's a simple way to keep your tasks on your mind.

One special idea that isn't conveyed in the comp is the idea of maximizing windows.  Specifically, you could tell a window to maximize and only cover the screen not covered by the task bar.  I know this would get annoying for some people and we would have to figure out how to tell it when and when not to do it, but imagine this:

You have a multitasking student.  They have OpenOffice open "semi-screened" on the right and the sidebar on the left.  If they're like me and are obsessive about checking, say, facebook, they can have it right there a blink away while not having to navigate away from their project.  It would also keep OnTask within reach.

Another way of managing this would be to put all this in Compiz's wiget's layer.  When you boot up, all of these apps are on the desktop but they stay glued to the desktop as you fullscreen apps.  However, if I want to - say, check my email in the sidebar, I just press the Super/Windows key which would bring your desktop to the front.

An obvious absence from this desktop is a task switcher.  I believe that the way we currently switch tasks (with a dedicated bar or a dock) isn't the best way.  GNOME's system is great, but it draws your attention to the two opposite ends of the screen.  This dock would be out of sight until you hit Super.  You could also use ALT-TAB.  It just doesn't need to always take up screen space.  (A note about the switcher in the comp (which is on the right hand corner), if there are multiple windows of the same app open, a click on that app's logo would open a stack).

-----

I made sure that all of this could be accomplished by using things like Screenlets.  There are no changes to GNOME required, and we can build on existing technology.  Simplicity would be available as a script that would give your system these features.

I am a technical person but do not know how to code outside of X-HTML/CSS and would love it if someone who could code scripts and screenlets would help me make this happen.  I could do the art bits.

This is a rough copy, but I want to know what the Ubuntu community thinks of it.  It would be thoroughly extendable.  I know I'd have to pretty it up a little more...  There would be a default metacity/gtk/whatever theme packaged.

Other desklets could be things like calendars, photo viewers,etc.

The icons are Eikon, a personal collection by fmrbpensador from GnomeLook.  I'd love to use them as the default in Simplicity, but I'd have to ask.

Opinions?  Raves?  Rotten tomatoes?

---

### Post by Merk42 on 2008-11-23
For something called simplicity, I'm really confused.

So the left hand side, is a sidebar with RSS and tasks that change color based on due date?  I don't really have time oriented tasks, but I see how some could.

The Window titled "SimplicityDesktop" is, what? a favorite application launcher? I hate the idea of GUI in the center of the screen like that, as it gets blocked as soon as an application is opened.

And the right, is, more of a OS X dock but anchored to the right instead of the bottom gnome panel?  I'm not even sure people can legally copy the dock anymore, regardless.

---

### Post by LegoAddict on 2008-11-23
The bar would be whatever people need.  It would be just a repository for screenlets and stuff.

And I'm sorry for the lack of simplicity :P  I'm not the clearest person in town...

That's an app launcher, yeah.  Any favourite files or apps that you want in there can be there.  And even though it's blocked, by pressing one key that's usually wasted on a linux keyboard (Super) you can bring it to the top again.  And the normal menus are still there.  It's just like having launchers on your desktop but they are confined and organized instead of being higgledy piggledy

All of this can be disabled.  I like this idea because I think of the desktop as dead space.  But it is kind of scratching my own back in that respect.  It's kind of like something I saw in KDE4...

The app switcher is dockish but it wouldn't have any animations, it would just be a bar with launchers.  I don't think even Microsoft could patent it.

EDIT:  I would also like to add that there would be a centralized control panel, which would make configuring this thing easy for even a novice user.

The task manager was a suggestion from my father, who thought that would make it a must-have tool for professionals - a simple, integrated task manager.

---

### Post by lyceum on 2008-11-24
I think that would be great for Gnome 3.0! Sadly, there will not be one, so this would just be another add-on to make this great user-friendly DE less ugly :)

Seriously though, I really think you have something here and I would love to see Gnome step up to the plate and do something like this. If I knew how to program, I would help. I'd offer help on design, but it looks like you have it down. 

:guitar:

---

### Post by mewithafez on 2008-11-24
This looks a little bit like this:

[http://live.gnome.org/GnomeShell]("http://live.gnome.org/GnomeShell")

which is a new shell being made for Gnome 3.0 using Javascript and Clutter. It'll look something like this:

[http://fishsoup.net/blog_images/gnome-shell-20081122.png]("http://fishsoup.net/blog_images/gnome-shell-20081122.png")

which is the product of the first 3 weeks of development. Impressive and gives hope for the future! The full post about the first 3 weeks is available at:

[http://blog.fishsoup.net/2008/11/22/gnome-shell-status/]("http://blog.fishsoup.net/2008/11/22/gnome-shell-status/")

---

### Post by LegoAddict on 2008-11-24
That looks cool.  I'll have to try it out.  Thanks for the link :)

What I propose wouldn't restructure GNOME at all, however, making it -perhaps- a little easier to use and stable.  It would really be an implementation of the existing screenlets framework.  I think they can be made in HTML but I'm not sure...  It would be a collection of screenlets with the app itself scaled down and rebranded.  It would also involve structuring a sidebar (for those who want it) so that you could, say, drag a desklet to the sidebar and it would integrate itself there.  Drag one out and it becomes a desklet.

This is, of course, conjecture because I have yet to find someone who actually knows the technical ins and outs of this stuff.

---

### Post by lyceum on 2008-11-25
> **mewithafez said:**
> This looks a little bit like this:

[http://live.gnome.org/GnomeShell]("http://live.gnome.org/GnomeShell")

which is a new shell being made for Gnome 3.0 using Javascript and Clutter. It'll look something like this:

[http://fishsoup.net/blog_images/gnome-shell-20081122.png]("http://fishsoup.net/blog_images/gnome-shell-20081122.png")

which is the product of the first 3 weeks of development. Impressive and gives hope for the future! The full post about the first 3 weeks is available at:

[http://blog.fishsoup.net/2008/11/22/gnome-shell-status/]("http://blog.fishsoup.net/2008/11/22/gnome-shell-status/")


They are working on 3.0? That is awesome!

---

### Post by mewithafez on 2008-11-28
Yes 3.0 looks like it is going to be pretty good, they are stepping up their game and all of the action over at [http://planet.gnome.org]("http://planet.gnome.org") sounds great!

Edit: Sorry for the proselytising, just excited. KDE also looks incredible, and XFCE is the come-from-behind kid from what I've seen in the screenshot thread.

---

### Post by lyceum on 2008-11-28
> **mewithafez said:**
> Yes 3.0 looks like it is going to be pretty good, they are stepping up their game and all of the action over at [http://planet.gnome.org]("http://planet.gnome.org") sounds great!

Edit: Sorry for the proselytising, just excited. KDE also looks incredible, and XFCE is the come-from-behind kid from what I've seen in the screenshot thread.

I switched to Kubuntu with 8.10 because I got sick of the ugly. If they can make Gnome look as slick as the new KDE I will gladly switch back. I think Gnome is better oriented (more user friendly), just ugly.

---

### Post by LegoAddict on 2008-11-29
meh.  KDE has always seemed either too gaudy or really counterintuitive.  I run DarkRoom in Intrepid and it's great.  IMHO, GNOME looks more sophisticated than KDE (if you're running a good theme, oc.  Ugly by default, ok in Human).  And what's with KDE's window decs?

But I digress :P

I can't wait for G3 either.  Each release impresses me even more.

---

### Post by Dullstar on 2009-10-22
I can't say I'm a huge fan of the SimplictiyDesktop thingy.  I really hope that doesn't happen, or I will be forced to switch to XFCE, sigh.

---

### Post by Merk42 on 2009-10-22
> **Dullstar said:**
> I can't say I'm a huge fan of the SimplictiyDesktop thingy.  I really hope that doesn't happen, or I will be forced to switch to XFCE, sigh.

Considering it was a mockup by someone completely unrelated to any DE and the last post was almost a year ago, you have nothing to worry about.


Well, maybe you do, that depends on your thoughts of GNOME Shell

---

### Post by alex.rayu on 2009-10-23
Looks like moblin'95

---

### Post by niel6 on 2010-04-05
When they suddenly changed from kde 3.5 to 4.x I got a lot of problems with using kde 4.x - and I was angry.
Now after a lot of extra work I have learned to use kde 4.x and am happy.
When 10.04 stable arrives I will as usual install using the alternate cd and install encrypted ubuntu (/boot partition of 100 mb, / of 30 gb and no swap).
I will newinstall as upgrading always has given me problems of some kind with former ubuntu versions, probably because I use to install various deb packages, which was not included in the default version's repositories.
Then I will install kde using synaptic, so I have both gnome 3 and kde installed.
Then I will use kde as default, and try gnome from time to time to gradual learn gnome 3.
Above I give out as a suggestion for other people.

---

