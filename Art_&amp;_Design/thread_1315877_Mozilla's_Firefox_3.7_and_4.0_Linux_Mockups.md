---
title: "Mozilla's Firefox 3.7 and 4.0 Linux Mockups"
date: 2009-11-05
forum: Art &amp; Design
---

### Post by Merk42 on 2009-11-05
The following are **proposed mockups** for Firefox 3.7 (eta 1st half of 2010) and Firefox 4.0 (eta end of 2010).

I emphasize proposed mockups, because they may not ultimately look like this and you can't just go download either right now.

You can, however, read about it [here](https://wiki.mozilla.org/Firefox/Projects/3.7_and_4.0_Theme_and_UI_Revamp/Linux_Specific_Visual_Refresh)

[img]https://wiki.mozilla.org/images/8/8a/Fx-3.7-Mockup-Linux-i01-Joined-Tabs-T-Human-Orange.png[/img]
[img]https://wiki.mozilla.org/images/5/5a/Fx-4.0-Mockup-Linux-i01-ToT-T-Human-Brown.png[/img]

---

### Post by Dragonbite on 2009-11-05
I definitely like the smaller real-estate of 4.0 (I assume the lower one is 4.0, it's the more radically changed one).

---

### Post by Neon Lights on 2009-11-05
Oh my.
the 4.0 mockup is so *sexy.*

---

### Post by synicalx on 2009-11-05
They both look pretty swish, the 4.0 looks like it's trying to do what Safari did by getting rid or compressing a ton of the UI. Only difference is FF will make it customizable so I can bring my menu's back :D

Overall I'm liking both of them, dunno about the default Ubuntu colours though...

---

### Post by maandverband on 2009-11-05
I don't like 4.0, because of the following reasons;
- I just want the menu bar applications have used for years. When I was still using Windows I've never upgraded from Internet Explorer 6 to Internet Explorer 7, because of the stupid layout of that browser. Menu bar is hidden by default and when enabled, it's beneath the address bar, instead of above the address bar (although it's possible to fix that using the registry). I've alse never used Microsoft Office 2007, because of that stupid ribbon interface. Google Chrome also has a hidden menu bar. Why do 99% off all applications have a normal menu bar, but does 1% of the applications change the layout. Almost all applications have the same layout (title bar on top and menu bar right beneath the title bar) and this works great for years. There's absolutely no reason to change this. Nowadays some applications are switching to the ribbon interface, other applications are hiding the menu bar by default and who knows what other applications come up with. Just stick to the standard we've used for years. Microsoft is changing the layout of its appliactions, but they're not the standard. Why should we follow them?
- The status bar is hidden. I always have the status bar turned on, so I can see to which website a hyperlink leads. I don't just click a link. I always look at the URL in the status bar. I don't want to be rickroll'd and I don't have to see those "You are an idiot" websites.

---

### Post by Mr. Picklesworth on 2009-11-05
I don't like the 4.0 mockup because it is a technical impossibility :)

---

### Post by Merk42 on 2009-11-05
> **maandverband said:**
> LOTS OF STUFF
Well as synicalx pointed out it'll most likely be customizible.  The reason a  lot browser are doing it now is because it saves screen real estate.  
Unless of course the real reason is just you don't like chaange in your interface, but I guess you won't have to really worry until the 12.04 LTS of Ubuntu with GNOME 3.

> **Mr. Picklesworth said:**
> I don't like the 4.0 mockup because it is a technical impossibility :)
Why is it a technical impossibility?

---

### Post by days_of_ruin on 2009-11-05
> **Mr. Picklesworth said:**
> I don't like the 4.0 mockup because it is a technical impossibility :)

Well, it could be done the same way chromium does with its own window border, but the mockup implies that it would be using the default Window Decorator.

---

### Post by purplewakanda on 2009-11-05
I too didn't like the new prototype. It won't give me the feel of using FF, rather the chrome or IE feel. And FF is not known for ripping and shouldn't be. I miss the menu bar, title bar, bookmarks toolbar, status bar and of course the google search.

---

### Post by jrusso2 on 2009-11-05
The windows 4.0 mockup is glass and it looks so much better that way.

---

### Post by Mr. Picklesworth on 2009-11-06
> **Merk42 said:**
> Why is it a technical impossibility?

Okay, the window manager (which draws the window border) is a completely separate process from the client application (eg: Firefox). Some apps tell the window manager that they want to draw their own window border, but this never works out well for top-level windows because they end up horrifically inconsistent.

If they could transparently pass the unused events off to the window manager, which is possible but inexplicably unimplemented (and it's too late now to make it work easily, since client apps are greedy with events), it would make a bit more sense. However, that still leaves us with the fact that they have nothing in common with the native look. Here are the ways that bottom mockup could be achieved:

* Firefox could be hard coded to a specific style of window borders. For example, how Chromium can draw its own window borders - which is wisely not the default in Linux. Note that Chromium's close buttons, when it handles matters itself, look exactly like Windows Vista's. Also, if you have different settings for what mouse buttons do in your real window manager, Chromium ignores them and assumes that double click means Maximize.
(This is also why Chromium's "native GTK" style looks like utter garbage. GTK themes do not handle the window border, yet it expects to get remotely useful information from the GTK theme!)

* Firefox could duplicate Metacity's theme engine. It could read Metacity's theme and then render a window border just like Metacity with some small changes. Lots of lines of code, possible breakage since Metacity themes are not built to facilitate tabs and user switchers, but maybe close to working...

* Firefox could add a few more lines of pixels so that the Metacity title bar is just a Metacity title bar, give up on the user chooser thing and arbitrarily assume that the bottom of Metacity's title bar is coloured dark brown.

(And then there are other window managers).


I think I have shot those options down sufficiently.

Now, I like dreaming. Personally, I would love to see the window manager drawing enormously wasteful borders thing die an elegant death, but this needs to happen at its source; not in a pesky client application that goes out of its way to stick out like a sore thumb.

It bothers me to see a proposed interface design that is Not Possible, because the only thing that could come of this is a realization too late in the cycle that it is not going to work followed by an ugly redesign. It will cause kludges and give us an interface that is not optimized for the situation at hand, instead smothered in the sad remnants of something unnatural.

---

### Post by Nevon on 2009-11-06
4.0 is ugly as sin! Also, there doesn't seem to be a quick and easy way to access your bookmarks. I like to have the bookmarks toolbar for the sites that I visit the most.

---

### Post by Animortis on 2009-11-06
I disagree. More real-estate on screen = more space to read and use the browser. Big fan of Chrome for this reason.

Are there any add-ons that can make FF3.5 more like 4.0? Chromium has too many technical issues to use in place of FF on Ubuntu so far, imo.

---

### Post by coldReactive on 2009-11-08
Also, How will this work on XFCE4 Window Manager in the Mozilla Firefox Web Browser 4 Mockup?

---

### Post by Merk42 on 2009-11-08
> **coldReactive said:**
> Also, How will this work on XFCE4 Window Manager in the Mozilla Firefox Web Browser 4 Mockup?

That's Mr. Picklesworth's point, it could be that whoever made the mockup is unaware of the limitations/complexity of getting it to look like that in a given window manager.

It's also why I said **"I emphasize proposed mockups, because they may not ultimately look like this..."**

---

### Post by Incendia on 2009-11-08
> **Mr. Picklesworth said:**
> I don't like the 4.0 mockup because it is a technical impossibility :)

Nothing is impossible if enough people work on it.

---

