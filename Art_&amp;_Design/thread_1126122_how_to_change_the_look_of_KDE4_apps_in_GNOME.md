---
title: "how to change the look of KDE4 apps in GNOME?"
date: 2009-04-15
forum: Art &amp; Design
---

### Post by sherl0k on 2009-04-15
Seriously, this is really starting to get on my nerves. I use GNOME apps for basically everything but kTorrent and nothing I do will let me change the looks of the app. All I want to do is reduce the font size! And there is NO documentation I have found anywhere that explains this for me.

And before you say "qtconfig" I've already tried it and it doesn't do a thing. Please please please help me find a solution :(

---

### Post by Incognito-Here on 2009-04-15
Use deluge. It's better, really.

---

### Post by morgengenuss on 2009-04-15
@incognito-here: well, yes, but actually your comment misses the point... (and personally i prefer transmission, lightweight and fast)

basically i have the same problem with kile. at least i could change the icon theme after installing the package "systemsettings". somehow though the other settings (e.g. theme) are missing...

---

### Post by sherl0k on 2009-04-16
Yeah I tried that and I'm seeing what looks like to be the same thing you see. I still can't change the font size or the theme at all.

@Incog: I like kTorrent because I can change the download directory from inside the torrent, Deluge doesn't let me do that. I also use k3b because it's so much better than Brasero. :P

---

### Post by nwarrenfl on 2009-04-16
You can select the GTK theme in the settings.
Your KDE applications will look exactly like GNOME applications.

---

### Post by sherl0k on 2009-04-17
where might i find these settings?

---

### Post by nwarrenfl on 2009-04-18
Install the package named 'systemsettings', and it will appear in your menu.

I made a post on my blog about that, but it's in french, so to resume, you can use the program or use the command-line:
```
kwriteconfig --file kdeglobals --group General --key widgetStyle gtk
kwriteconfig --file kdeglobals --group Icons --key Theme Human
```

The first command is to change the theme and the second to change the icon theme.

Hope you will like KDE applications on GNOME now, it looks so good!

---

### Post by sherl0k on 2009-04-18
That did the trick! Thank you sooo much!

---

### Post by morgengenuss on 2009-04-19
wow, can't trust my eyes! - thanks a lot, nwarrenfl!

(postscript: for some reason this setting does not appear in the systemsettings dialog)

---

### Post by Cresho on 2009-04-26
Your such a newb!!!!!  Damn and not even hitting the post 100 mark and you gave me advice on this very important matter.



I give you 

:KS:KS:KS:KS:KS

---

### Post by Blacklemon67 on 2009-04-27
how do you change it back cli?

---

### Post by x1um1n on 2009-04-30
Yeah, seriously, where are these settings?

Older KDE apps can be configured by System-->Preferences-->QT4 Settings
This def works for SMPlayer and K3B

but newer apps like Amarok2 use the KDE4 look which clearly works differently (see screenshot)..

surely we're not back to the bad old days where you had to install KDE to theme it's apps??

---

### Post by sherl0k on 2009-04-30
Well k3b still adheres to QT3 settings which means there's no way to get it to look like GNOME unless you skin it manually. Kinda annoying.

---

### Post by Confuseling on 2009-05-07
> **nwarrenfl said:**
> Install the package named 'systemsettings', and it will appear in your menu.

I made a post on my blog about that, but it's in french, so to resume, you can use the program or use the command-line:
```
kwriteconfig --file kdeglobals --group General --key widgetStyle gtk
kwriteconfig --file kdeglobals --group Icons --key Theme Human
```

The first command is to change the theme and the second to change the icon theme.

Hope you will like KDE applications on GNOME now, it looks so good!

System settings isn't doing anything for me, and I too am keen to know how to revert this before I try it. Can anyone enlighten us?

---

### Post by morgengenuss on 2009-05-27
> **Blacklemon67 said:**
> how do you change it back cli?

maybe you figured this out already, but that's how you go back:
```
kwriteconfig --file kdeglobals --group General --key widgetStyle default
```

---

### Post by spinstartshere on 2009-06-07
> **nwarrenfl said:**
> Install the package named 'systemsettings', and it will appear in your menu.

I made a post on my blog about that, but it's in french, so to resume, you can use the program or use the command-line:
```
kwriteconfig --file kdeglobals --group General --key widgetStyle gtk
kwriteconfig --file kdeglobals --group Icons --key Theme Human
```

The first command is to change the theme and the second to change the icon theme.

Hope you will like KDE applications on GNOME now, it looks so good!
I tried this but the fonts haven't changed.  Were they meant to?

---

### Post by kapz on 2009-09-23
[B]I did what nwarrenfl has mentioned and it worked perfectly fine for me on Ubuntu 9.04. Thanks!
[/B]

---

### Post by frankob on 2009-11-06
Unfortunately, this solution works only partially in Karmic... Pieces of the KDE4 windows change to conform the gtk widgets, while other pieces keep the default KDE4 theme. :-/

Is there any better solution for Karmic?

---

### Post by morgengenuss on 2010-01-18
funny you're saying that, i can't notice any difference in look and feel from jaunty to karmic...

---

### Post by frankob on 2010-02-07
Not generally, only the KDE4 applications inside a Gnome2 session...

Funny or not, I am just saying what I am seening...

---

### Post by morgengenuss on 2010-02-08
well, i didn't literally mean it's "funny", more in the sense of surprising or interesting.

but since you're saying you're using gnome(-session), maybe that's what makes the difference, i'm using xfce. maybe some other gnome-users can help you out here...

it might also help if you give a more detailed account of what you're seeing there - maybe even screenshots?

---

### Post by morgengenuss on 2010-02-08
sry, unintended doublepost...

---

### Post by banago on 2010-02-08
@nwarrenfl: Rally great trick - thanks!

---

### Post by sigurnjak on 2010-02-08
Here is a screenshot of K3B in gnome . I just used KDE sysytem settings .

---

### Post by durand on 2010-02-11
Uhm, I use [apt:qt4-qtconfig]("apt:qt4-qtconfig") which works really well. There's also [apt:qt3-qtconfig]("apt:qt3-qtconfig") for older kde apps.

---

### Post by frankob on 2010-03-24
> **morgengenuss said:**
> well, i didn't literally mean it's "funny", more in the sense of surprising or interesting.

but since you're saying you're using gnome(-session), maybe that's what makes the difference, i'm using xfce. maybe some other gnome-users can help you out here...

it might also help if you give a more detailed account of what you're seeing there - maybe even screenshots?

Sorry for not answering so long...

A screenshot? Here you are. The attachment shows how my Okular looks like.

As you can see, the KDE theme has changed only partially.

Maybe I should switch to Xfce, too...

---

### Post by frankob on 2010-04-11
> **durand said:**
> Uhm, I use [apt:qt4-qtconfig]("apt:qt4-qtconfig") which works really well. There's also [apt:qt3-qtconfig]("apt:qt3-qtconfig") for older kde apps.

qt4-qtconfig is good for non-KDE qt4 applications, like VLC, but not for KDE4 apps, like Okular or K3B. If you read the whole thread you will see we already know about it.

---

### Post by durand on 2010-04-11
> **frankob said:**
> qt4-qtconfig is good for non-KDE qt4 applications, like VLC, but not for KDE4 apps, like Okular or K3B. If you read the whole thread you will see we already know about it.

Oops, sorry, I just glanced over it..

---

