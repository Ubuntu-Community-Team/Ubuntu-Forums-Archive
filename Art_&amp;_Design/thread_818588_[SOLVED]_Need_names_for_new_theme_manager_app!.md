---
title: "[SOLVED] Need names for new theme manager app!"
date: 2008-06-04
forum: Art &amp; Design
---

### Post by Flimm on 2008-06-04
Over the past month or so I've been working on a [much requested](http://brainstorm.ubuntu.com/idea/105/), long awaited theme manager application. This is the result:

[Complete Look project on Launchpad.net](https://launchpad.net/complete-look/) (EDIT: Now [Epidermis](https://launchpad.net/epidermis/))

[img]http://ubuntuforums.org/attachment.php?attachmentid=72941&d=1212608823[/img]

The idea is that you have **one application that manages all your appearance customisations**, currently that means: your wallpaper, your GTK theme, your Metacity window decoration theme, your icon theme, your splash screen for GNOME, your mouse cursor theme, your GDM login screen and even your GRUB and Usplash boot splash screens.
All of these customisations are combined into one Complete Look "scheme", applying one scheme means applying all of them at once. Schemes are downloaded from a repository, so moving your entire desktop appearance to another computer should be easy.

Attached is a screenshot of one scheme before and after it was applied.

So I'm quite happy with the progress of my project, but I don't like the name I've chosen: "Complete Look":
[LIST][*]It's two words, which means I'm constantly having to choose between Complete Look, CompleteLook and Complete-Look
[*]It's boring
[*]It's not very international.[/LIST]

**So I would like your suggestions for a new name!**

Here are some ideas I've thought of: morph something, styler, restyle, outfit, genie, Leonardo ...

What I would really like if someone could come up with a well known character that changes appearance easily or frequently. Then I would have a mascot and an icon for this app.

No idea is too crazy!

---

### Post by Wicca on 2008-06-04
> **Flimm said:**
> 
What I would really like if someone could come up with a well known character that changes appearance easily or frequently. Then I would have a mascot and an icon for this app.

Chameleon?

---

### Post by light50 on 2008-06-04
Attire

---

### Post by light50 on 2008-06-04
Ensemble

---

### Post by light50 on 2008-06-04
Apparition

---

### Post by light50 on 2008-06-04
Plummage

---

### Post by KingTermite on 2008-06-04
Wardrobe
Hat Rack
Shoe Tree

---

### Post by Wicca on 2008-06-04
Tint
(tint is no transformer)

---

### Post by Wicca on 2008-06-04
Mutalius

---

### Post by MadsRH on 2008-06-04
Costume 
Disguise
DressUp
Masks
Coated
Transformer

This is really great work! Will it make it into 8.10 as a default  appearance tool? I really hope so.

---

### Post by Neon Lights on 2008-06-04
Spectacle?

Chameleon is really awesome though. [: I second that.

---

### Post by Sealbhach on 2008-06-04
How about

**Tableau**

> 
1: a graphic description or representation : 
2: a striking or artistic grouping : arrangement, scene
3: [short for tableau vivant (from French, literally, living picture)] : a depiction of a scene usually presented on a stage by silent and motionless costumed participants

[http://www.merriam-webster.com/dictionary/tableau](http://www.merriam-webster.com/dictionary/tableau)

It sounds a bit international too....


.

---

### Post by grem91 on 2008-06-04
façade

(literally meaning "frontage" or "face")

---

### Post by Jack3760 on 2008-06-04
Presto Chanego

---

### Post by Flimm on 2008-06-05
Thanks everyone, those names are brilliant, keep them coming.

Unfortunately, Wicca, chameleon and Tint are both already taken, and they're in the Ubuntu repositories. Chameleon is an application for putting pictures or color in the root window, and TINT (TINT is not Tetris) is a game. Sad, I liked both of those.

Here two more ideas: transmorpher and masque (seems like french names are popular!).

---

### Post by aantn on 2008-06-05
> **Flimm said:**
> Thanks everyone, those names are brilliant, keep them coming.

Unfortunately, Wicca, chameleon and Tint are both already taken, and they're in the Ubuntu repositories. Chameleon is an application for putting pictures or color in the root window, and TINT (TINT is not Tetris) is a game. Sad, I liked both of those.

Here two more ideas: transmorpher and masque (seems like french names are popular!).

I haven't had a chance to download it yet, but your app sounds great! I noticed that the code is in python, so I'll definitely give it a look when I get a chance.

There are a quite a few good names in the list already. I recently went through the process of picking a name myself, and I'm beginning to regret that I didn't ask the community for advice.

Be careful if you pick a non-English name to change letters like 'Á' to 'A'. I picked a French name and I had a few problems with Launchpad and bzr when I used e´ in my filenames.

---

### Post by aantn on 2008-06-05
Have you seen GnomeArtNG? It uses mono, and it seems like it's a bit similar to your project. Maybe the two of you could work on this together.

[http://developer.berlios.de/projects/gnomeartng/](http://developer.berlios.de/projects/gnomeartng/)

---

### Post by Flimm on 2008-06-05
> **aantn said:**
> Have you seen GnomeArtNG? It uses mono, and it seems like it's a bit similar to your project. Maybe the two of you could work on this together.

[http://developer.berlios.de/projects/gnomeartng/](http://developer.berlios.de/projects/gnomeartng/)
No, I hadn't. It looks pretty cool. Unfortunately, I don't know C# so I would have to learn it to help out on this project. I can't believe I missed it. I did do a pretty thorough search for similar projects before starting my one.
My project is more ambitious than his though. I've included "schemes", packages which control all different types of different customisations at once. My project also allows you to change GRUB and Usplash themes.
On the other hand, his project is supposed to be integrated with [art.gnome.org](http://art.gnome.org), which is now on my TODO list!

---

### Post by aantn on 2008-06-05
> **Flimm said:**
> No, I hadn't. It looks pretty cool. Unfortunately, I don't know C# so I would have to learn it to help out on this project. I can't believe I missed it. I did do a pretty thorough search for similar projects before starting my one.
My project is more ambitious than his though. I've included "schemes", packages which control all different types of different customisations at once. My project also allows you to change GRUB and Usplash themes.
On the other hand, his project is supposed to be integrated with [art.gnome.org](http://art.gnome.org), which is now on my TODO list!

It is a pretty low profile project. I wouldn't have known about it if I hadn't been on irc when the developer was discussing it.

The schemes is definitely a neat idea. Once I get global-themes working in Universal Applets, I'd love to integrate them with your app.

---

### Post by KingTermite on 2008-06-05
TARDIS - Doctor Who's TARDIS (ship) was designed with a chameleon circuit so that it "blended" into the environment wherever it landed.

---

### Post by Flimm on 2008-06-05
> **KingTermite said:**
> TARDIS - Doctor Who's TARDIS (ship) was designed with a chameleon circuit so that it "blended" into the environment wherever it landed.
If I remember correctly it used to be able to do that, until it broke, and Dr. Who never got round to fixing it. That's why the TARDIS always looks like a phone box. It's not quite the picture I want for my app! ;)

---

### Post by piousp on 2008-06-05
> **Wicca said:**
> Mutalius

Nice one!

---

### Post by KingTermite on 2008-06-05
> **Flimm said:**
> If I remember correctly it used to be able to do that, until it broke, and Dr. Who never got round to fixing it. That's why the TARDIS always looks like a phone box. It's not quite the picture I want for my app! ;)

Yes, you are correct and I guess that would be a bad connotation. LOL

---

### Post by chemicaljordan on 2008-06-05
Masque (like mask)
Squanger (a cool name like changer)
Flipper
Lookilike
Themerizer

---

### Post by Mateus909 on 2008-06-05
Face Paint
Tribal Masque

---

### Post by TwYst on 2008-06-06
Houdini
Phazer
Hologram
Decor
Shadez
TDDT - the desktop decorator tool

---

### Post by oedipuss on 2008-06-07
Why not keep it simple and descriptive? 
I admit it will lack imagination, but it will feel more like a default gnome app.
Something like Complete Look & Feel or Desktop Themer, etc.

Have you considered adding more options to each meta-theme (?) like compiz settings, panel settings or even awn stuff if available ? Compiz is very detached from gnome themes at the moment, while it could integrate very nicely with wallpapers and themes, from setting appropriate reflection colors to using special plugins (i.e. autumn/fireflies).

---

### Post by TheSlipstream on 2008-06-08
Hi! I'm pretty new to Ubuntu (and Linux in general) and I've been having problems with Emerald and such, so I'm excited to try out your project. I downloaded it and installed, but I can't really find it in any of the menus, so my newbish question is: How do I run the program? :P

---

### Post by meborc on 2008-06-08
i second "facade", it is just the name the app needs... or "frontage" ;)

---

### Post by Flimm on 2008-06-09
> **TheSlipstream said:**
> Hi! I'm pretty new to Ubuntu (and Linux in general) and I've been having problems with Emerald and such, so I'm excited to try out your project. I downloaded it and installed, but I can't really find it in any of the menus, so my newbish question is: How do I run the program? :P
Open a terminal and type complete-look, then press enter. When the window appears, click find more, tick one of the schemes and click apply to install it.
My project is still in beta, which means they are still quite a few bugs and missing features, such as a menu icon under Applications! Also, Complete Look doesn't have Emerald customisation yet, although it's definately on the list on things to add.
Compiz Fusion is definately on the list as well, oedipuss.

---

### Post by Tuxoid on 2008-06-09
black foot theme manager (black foot because of the gnome logo)

---

### Post by Flimm on 2008-06-10
Here are some more ideas:
- Varmony (visual harmony)
- Epidermis
- Epicdermis
- Pigment
(The last two were suggested by a friend of mine.)

---

### Post by OZFive on 2008-06-11
Tattoo

---

### Post by Flimm on 2008-06-11
Alright! I've decide to use the word 'pigment' for a downloadable theme that customises one part of the desktop, for example, a GTK pigment, a Usplash pigment, a Metacity pigment, and so on. Pigment will replace the word 'package' which is confusing as it's not a software package.
'Epidermis' will be the word I'll use for a customisation theme that links to one pigment of every type, for example, the Ubuntu epidermis would include the Usplash, GDM, GTK, Metacity, icons, cursors, splash and wallpaper pigments. Epidermis will replace the word 'scheme' which I had been using, which I find too vague.
I'd like to find a word that would replace 'repository', but I have yet to find one, I suppose I'll just use 'pigment repository'.
All that's left is the actual program name! It looks like it'll end up being Epidermis, unless some-one has a brilliant idea that fits with the 'epidermis' and 'pigment' theme.

---

### Post by oedipuss on 2008-06-11
How about simply 'skin' for the collection of pigments , and keep epidermis for the name ?

---

### Post by Flimm on 2008-06-13
OK, it's decided, I'll use Epidermis as a name for my program. Thank you all for your suggestions, it fired up my imagination and it launched productive offline brainstorming.
My two favourite suggestions here were Attire and TINT, so I thanked them using the forum's button, but I liked all the other suggestions too, and you should consider yourselves thanked as well. ;-)
Now that this project has finally been named, I can start making a web site for it. I hope to see you there!

---

### Post by Flimm on 2008-06-17
The Launchpad admins have renamed my project to Epidermis, you can now track progress at this URL:
[https://launchpad.net/epidermis/](https://launchpad.net/epidermis/)
I'd also like to announce the program's new site, currently with just the essentiels:
[http://epidermis.tuxfamily.org](http://epidermis.tuxfamily.org)

---

### Post by Orlsend on 2008-06-28
Hey Flimm I am glad you toke my name Idea, and that you are latting me handle your web campaings.

This App made switch to Unbuntu and leave windows behind.

Thanks Again Flimm!

---

### Post by rainwalker on 2008-06-28
Aww, I was rooting for Facade...

---

### Post by Warbo on 2008-06-28
Seems pretty cool. I guess it's mainly aimed at getting themes online, but it would be nice to have some obviousness to installing themes from local files. The current theme manager has both a file selector and a simple drag and drop, but there are still masses of requests for making things 'easier'. Be nice to see how that's tackled.

PS: Pigment is a semi-3D graphics toolkit thing [https://code.fluendo.com/pigment/trac](https://code.fluendo.com/pigment/trac) (broken security certificate which you may have to force)

PPS: Any possibility of integrating DXS/"Get Hot New Stuff" technology? [http://ghns.freedesktop.org](http://ghns.freedesktop.org)

---

### Post by Zopiac on 2008-06-29
> **rainwalker said:**
> Aww, I was rooting for Facade...

me too =(

---

### Post by Flimm on 2008-06-30
> **Orlsend said:**
> Hey Flimm I am glad you toke my name Idea, and that you are latting me handle your web campaings.

This App made switch to Unbuntu and leave windows behind.

Thanks Again Flimm!
Welcome to Ubuntu, Orlsend!

> **Warbo said:**
> Seems pretty cool. I guess it's mainly aimed at getting themes online, but it would be nice to have some obviousness to installing themes from local files. The current theme manager has both a file selector and a simple drag and drop, but there are still masses of requests for making things 'easier'. Be nice to see how that's tackled.

PS: Pigment is a semi-3D graphics toolkit thing [https://code.fluendo.com/pigment/trac](https://code.fluendo.com/pigment/trac) (broken security certificate which you may have to force)

PPS: Any possibility of integrating DXS/"Get Hot New Stuff" technology? [http://ghns.freedesktop.org](http://ghns.freedesktop.org)Installing themes from a local file is what I'm coding right now!
I realise pigment is already taken, that's why I'm only using it as a name for Epidermis 'packages', not for the program itself.
Thanks for the link to GHNS, I didn't realise something like this existed. I had been writing my own data sharing mechanism for Epidermis.

---

### Post by days_of_ruin on 2008-06-30
If you haven't added it yet you should add undo buttons on everything.
That way you won't have to waste time firing up the incredible 
inefficient "Appearance" app.(Seriously why does it max out the cpu?)

---

