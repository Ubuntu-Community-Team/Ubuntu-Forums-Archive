---
title: "New Clearlooks GTK+ Theme Engine"
date: 2005-01-16
forum: Art &amp; Design
---

### Post by Daniel G. Taylor on 2005-01-16
There is a new theme engine out called Clearlooks that sort of mashes together some of the best theme engines out there and then some. It has a very nice look to it, and because it's a theme engine it is [relatively] fast.

I've been using the Clearlooks Human (Ubuntu colored) theme for a few days now and really like it. I don't like the scrollbars so much, but the author is apparently working on it, but having difficulties.

It's available on gnome-look.org here:
[http://gnome-look.org/content/show.php?content=19527](http://gnome-look.org/content/show.php?content=19527)

I just thought I'd post it since a Human theme is available for us Ubuntu users 8-)

---

### Post by bvc on 2005-01-17
me likes to...and I usually do not use engines....they bore me. But I can't stop using this one. My first 3 color mods are in the engine install as of v 0.2 but I have another 3 for thos interested. I like ClearlooksChocolateMilk
link removed

---

### Post by Tato on 2005-01-17
Hello, I have a fresh Ubuntu install and I installed this engine withouth problems, but how do I use it ?, I cant see the themes that come with the engine in the Gnome Control Manager so I appreciate any help, thanks.

EDIT: Nevermind, I figured it how. Incase someone else have the same problem, what you have to do to setup the skins is:

```
gnome-theme-manager
``` 

Then click on [Details] and in the new window you will see the Clearlooks themes.

---

### Post by bvc on 2005-01-17
are they there...in
/usr/share/themes
???

You could try to completely logout and back in to gnome.
You could open gconf-editor>desktop>gnome>interface
and set the gtk_theme to one of the Clearlooks themes in /usr/share/themes

ClearlooksBlueish

---

### Post by macewan on 2005-01-20
Installing Clearlooks theme engine on Ubuntu Linux Warty with the Bluecurve theme.

[http://gnome-look.org/content/download.php?content=19527&id=1](http://gnome-look.org/content/download.php?content=19527&id=1)

Save to disk

bunzip2 19*.bz2
tar xf 19*.tar
cd clear*

./configure –prefix=/usr && sudo make install

right click and save

sudo alien -i redhat-artwork*

Computer > Desktop Preferences > Theme

This brings up the Theme Preferences window. On the right hand side of this window you will notice the second button down is Theme Details, click it. This brings up the Theme Details window. There are three tabs across the top, Controls, Window Border, Icons. The default tab is Controls. Scroll down and select Clearlooksblueish, click the Window Border tab and select Bluecurve, click the Icons tab and select Bluecurve.

In the bottom right hand corner of the current window you will see the Close button, click it. You’ll notice we’re in the Theme Preferences window again with Custom Theme highlighted at the top. Look to the right hand side of this window and notice that there is a Save Theme… button, click it. This brings up the Save Theme window. Name the theme and click the Save button. This brings us back to the Theme Preferences window. In the bottom right corner you will see the Close button, click it.

Done
:)

---

### Post by DoubleDangerClub on 2005-01-21
Does anyone know what metacity theme the author's screenshots are of?  I've been trying to find those themes.

DDC

---

### Post by albersag on 2005-01-21
I get this error when compiling. What im doing wrong?

./configure: line 10830: --variable=gtk_binary_version: command not found
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: GTK+-2.0 is required to compile clearlooks-engine

---

### Post by mr_ed on 2005-01-21
You need to install the libgtk2.0-dev package.

---

### Post by albersag on 2005-01-21
[QUOTE=mr_ed]You need to install the libgtk2.0-dev package.[/QUOTE]


Thanks. Now installing and i supposed it to work right now.

Thanks again :)

---

### Post by Buffalo Soldier on 2005-01-21
My heart is torn between the default Ubuntu theme vs Clearlooks Human theme. I hope Clearlooks engine will be included in the repositories.

---

### Post by bvc on 2005-01-21
[QUOTE=DoubleDangerClub]Does anyone know what metacity theme the author's screenshots are of?  I've been trying to find those themes.

DDC[/QUOTE]
Remenic's screenshots are of xfce4, not metacity.

---

### Post by Daniel G. Taylor on 2005-01-21
[QUOTE=DoubleDangerClub]Does anyone know what metacity theme the author's screenshots are of?  I've been trying to find those themes.

DDC[/QUOTE]
 The author is using XFCE4 in the screenshots.

I've started a port of the theme (XFCE-Winter) and will post it soon. The current (work in progress) version I'm playing with is a modified version of another Metacity theme that [mostly] has the correct look but still needs to be cleaned up. If you want to preview it:

[http://programmer-art.org/files/themes/metacity-winter-1.tar.bz2](http://programmer-art.org/files/themes/metacity-winter-1.tar.bz2)

---

### Post by bvc on 2005-01-21
hey sweet!
thx!
look forward to the release as I know many do. I've seen this this requested many times!

I see what you mean about clean up....you're almost there though! Thx!

---

### Post by bvc on 2005-01-21
nvm

---

### Post by bvc on 2005-01-23
Clearlooks Engine 0.2.2 Released

k...disregard all Clearlooks links posted for my versions previous to this one. All is now in a Clearlooks-Big_Pack
ClearlooksBluey
ClearlooksAna
ClearlooksMilk
are in the engine install but are different in thicknesses and do not include stock icons from roberTO's Milk-2.0 which are bluecurve stock, Ana stock icons from Ana, and My Edge stock icons.....well, like them more than Milks. Here's what is in the pack

[http://bvc.kernow-webhosting.com/theme/gtk...Big_Pack.tar.gz](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack.tar.gz)
```
ClearlooksAna            ClearlooksEtiquette  ClearlooksOrange
ClearlooksBlue-L         ClearlooksGONX       ClearlooksTiSkin
ClearlooksBluey          ClearlooksMilk       Clearlooks_Phacile-blue
ClearlooksChocolateMilk  ClearlooksNuvola
```
Here's ClearlooksNuvola which requires gnome-themes-extras Nuvola to be installed
[http://bvc.kernow-webhosting.com/theme/scr...looksNuvola.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksNuvola.jpg)

Here's ClearlooksOrange that includes and uses gartoon stock icons
[http://bvc.kernow-webhosting.com/theme/scr...looksOrange.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksOrange.jpg)

hence...a Big_pack

---

### Post by macewan on 2005-01-24
[QUOTE=Daniel G. Taylor]The author is using XFCE4 in the screenshots.

I've started a port of the theme (XFCE-Winter) and will post it soon. The current (work in progress) version I'm playing with is a modified version of another Metacity theme that [mostly] has the correct look but still needs to be cleaned up. If you want to preview it:

[http://programmer-art.org/files/themes/metacity-winter-1.tar.bz2](http://programmer-art.org/files/themes/metacity-winter-1.tar.bz2)[/QUOTE]


Could you tell me how you producted those .ogg tutorials?

---

### Post by Daniel G. Taylor on 2005-01-25
[QUOTE=macewan]Could you tell me how you producted those .ogg tutorials?[/QUOTE]

I'm still working on them, actually. Here is the workflow I'm working on:

Create an introduction [done, with still images]
Record a tutorial [done, using xvidcap/gvidcap, saving still images]
Optionally record audio
Create a movie from the images [working on it]
Optionally add audio to the movie
Save/Export/Convert to Ogg Theora/Vorbis [use gstreamer or ffmpeg2theora]

The example that I posted was recorded using gvidcap. I recorded to MPEG4 and then used mplayer + the example theora encoder provided with libtheora's source. The quality is below what I'd like (because of the double compression used, MPEG and then Theora), and I'd like to add my introduction into the clip. Check out [theora.org](http://www.theora.org) for more info about converting to Theora.

I've talked to the [PiTiVi](http://www.pitivi.org) developers, and they said what I'd like to do should be possible by March or so.

If anyone has any advice, don't be shy!

---

### Post by Yukonjack on 2005-01-25
[QUOTE=bvc]Clearlooks Engine 0.2.2 Released
[http://bvc.kernow-webhosting.com/theme/gtk...Big_Pack.tar.gz](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack.tar.gz)
```
ClearlooksAna            ClearlooksEtiquette  ClearlooksOrange
ClearlooksBlue-L         ClearlooksGONX       ClearlooksTiSkin
ClearlooksBluey          ClearlooksMilk       Clearlooks_Phacile-blue
ClearlooksChocolateMilk  ClearlooksNuvola
```
Here's ClearlooksNuvola which requires gnome-themes-extras Nuvola to be installed
[http://bvc.kernow-webhosting.com/theme/scr...looksNuvola.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksNuvola.jpg)
Here's ClearlooksOrange that includes and uses gartoon stock icons
[http://bvc.kernow-webhosting.com/theme/scr...looksOrange.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksOrange.jpg)
hence...a Big_pack[/QUOTE]

Thanks a lot bvc way cool  :mrgreen:

---

### Post by macewan on 2005-01-25
[QUOTE=Daniel G. Taylor]I'm still working on them, actually. Here is the workflow I'm working on:

Create an introduction [done, with still images]
Record a tutorial [done, using xvidcap/gvidcap, saving still images]
Optionally record audio
Create a movie from the images [working on it]
Optionally add audio to the movie
Save/Export/Convert to Ogg Theora/Vorbis [use gstreamer or ffmpeg2theora]

The example that I posted was recorded using gvidcap. I recorded to MPEG4 and then used mplayer + the example theora encoder provided with libtheora's source. The quality is below what I'd like (because of the double compression used, MPEG and then Theora), and I'd like to add my introduction into the clip. Check out [theora.org](http://www.theora.org) for more info about converting to Theora.

I've talked to the [PiTiVi](http://www.pitivi.org) developers, and they said what I'd like to do should be possible by March or so.

If anyone has any advice, don't be shy![/QUOTE]


After watching the 10meg tutorial I started playing around with xvidcap, after a bit of googling.

> Create a movie from the images [working on it]
That's where I stopped. Didn't get around to it - think I started looking into possible ways of exporting to flash format.

Do share please any suggestions on this subject.

---

### Post by Daniel G. Taylor on 2005-01-28
For people watching here about my XFCE-Winter port for Metacity, final release is here:

[http://programmer-art.org/files/themes/metacity-winter-2.tar.bz2](http://programmer-art.org/files/themes/metacity-winter-2.tar.bz2)

The theme isn't perfect but it works for me. I'd be happy to take any ideas and or modifications and add them to my releases, just contact me. I will also be posting this on GNOME-look.org in a few minutes.

---

### Post by mirtux on 2005-02-05
Hi everybody,
   i'm trying to install clearlooks theme engine on my Warty, but i've got one problem. Compiling and so on went smoothly and i copied the themes on /usr/share/themes. I can even see the names of the themes in gnome-theme-manager. 
The problem is that when i try to use it it just change the windows control ... in worse... I can't see, for example, text when I open the Application bar in GNOME desktop, it disappears under a white highlight. Does somebody of you has this problem? Maybe i've made some mistakes during the installation process!

Thanks,
MC

---

### Post by bvc on 2005-02-05
hi,
try this
[http://gnomesupport.org/forums/viewtopic.php?t=8645&postdays=0&postorder=asc&start=15](http://gnomesupport.org/forums/viewtopic.php?t=8645&postdays=0&postorder=asc&start=15)

---

### Post by mirtux on 2005-02-06
Hi bvc,
   thanks for help tomorrow i'll try to solve this out!

MC

---

### Post by doni on 2005-02-06
my problem:

i wanted to install the theme, but got an error during install:

```
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: GTK+-2.0 is required to compile clearlooks-engine
``` 

others had the same problem, they just installed libgtk2.0-dev, and so i tried it too but that gave me an error too:
```
Paket libgtk2.0-dev ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
Doch die folgenden Pakete ersetzen es:
  libgtk2.0-bin
E: Paket libgtk2.0-dev hat keinen Installationskandidaten
``` 

>> no install candidate

what is my problem?

thanks
doni

---

### Post by bvc on 2005-02-06
I don't know. I'm hoary.
I'm english only. Does that say libgtk2.0-dev can't be installed because it needs libgtk2.0-bin that is not available?

---

### Post by mirtux on 2005-02-07
[QUOTE=doni]my problem:
 
 i wanted to install the theme, but got an error during install:
 
 ```
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
 Perhaps you should add the directory containing `gtk+-2.0.pc'
 to the PKG_CONFIG_PATH environment variable
 No package 'gtk+-2.0' found
 configure: error: GTK+-2.0 is required to compile clearlooks-engine
``` 
 
 others had the same problem, they just installed libgtk2.0-dev, and so i tried it too but that gave me an error too:
 ```
Paket libgtk2.0-dev ist nicht verfügbar, wird aber von einem anderen
 Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
 ist oder nur aus einer anderen Quelle verfügbar ist.
 Doch die folgenden Pakete ersetzen es:
   libgtk2.0-bin
 E: Paket libgtk2.0-dev hat keinen Installationskandidaten
``` 
 
 >> no install candidate
 
 what is my problem?
 
 thanks
 doni[/QUOTE]
 Well, you could try installing **libgtk2.0-0**. If you didn't have it for sure that the other package doesn't work.
 
 Regards,
 MC

---

### Post by Daniel G. Taylor on 2005-02-07
It's been a while since I've translated, lol. Hoffentlich ist mein Deutsch nicht zu schlim geworden!
> Paket libgtk2.0-dev ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
Doch die folgenden Pakete ersetzen es:
  libgtk2.0-bin
E: Paket libgtk2.0-dev hat keinen Installationskandidaten
Package libgtk-2.0-dev is not available, but is referenced by another package. This can mean that the package is missing, old, or only available through another source.
The following package(s) replace it:
  libgtk2.0-bin
E: Package libgtk2.0-dev has no installations candidate.

---

### Post by mirtux on 2005-02-07
Hi,
   can you find the packages you're trying to install (**libgtk2.0-0** **and libgtk2.0-dev**) on synaptic list? 
 
 MC

---

### Post by Spark* on 2005-02-25
0.3 got released now: [http://gnome-look.org/content/show.php?content=19527](http://gnome-look.org/content/show.php?content=19527)
Please give it a try, we worked very hard on it. :)

---

### Post by ember on 2005-02-25
I am impressed - actually ClearLooks is the only theming engine I ever found useful.

Good work.

---

### Post by Paool on 2005-02-25
cc1: Permission denied: opening dependency file .deps/clearlooks_rc_style.Tpo
make[1]: *** [clearlooks_rc_style.lo] Error 1
make[1]: Leaving directory `/home/paool/clearlooks-0.3/src'
make: *** [install-recursive] Error 1

what's wrong?

---

### Post by Spark* on 2005-02-25
Did you do make install with sudo ("sudo make install")?

---

### Post by Paool on 2005-02-25
ok, that was the problem :P thanks

---

### Post by Daniel G. Taylor on 2005-02-25
I already posted on GNOME-look.org, but I figured I'd say it again here:

Excellent new release! I really appreciate you sticking with the wholistic widget view. I'm not so sure about the concave menu items again, but I'm not complaining ;-)

---

### Post by Spark* on 2005-02-25
The what widget view? ;) Poor german here, we suck at english.
The menu has been a cause of much debate, so we are very much looking for comments on this. :) However, Richard and me both like the new look much better than the old one meanwhile. It took some getting used to... Notice that we made the menus smaller again, but only for the three included styles (Clearlooks, -Olive and -DeepSky), so if you are using an older color scheme, then it might still be using the large menu paddings and look bad.

---

### Post by Daniel G. Taylor on 2005-02-25
Lol, poor [half] German here too ;-) 

Ich meinte nur, das ich es gut finde das manche Widgets so aussehen als ob sie ein einziges Objekt sind, anstat aus kleinere Elemente gebaut zu sein. Ich finde das es einfacher ist die Widgets so zu erkennen und es sieht einfach eleganter aus. Leider habe ich keine Usability Tests um das zu unterstuetzen!

About the themes, I am still using the old Human theme.

---

### Post by bvc on 2005-02-25
I'll be updating all my color schemes tonight or tomorrow. In the future, a heads up email, with the new changes to the gtkrc's might be an idea for quicker updating :grin:

I'll also include the human version in my pack since it and the milk has been omitted from the engine for whatever reason. :neutral: I can understand the milk as mine included the icons and smaller widgets/menus etc.. which is much more desired for most.

---

### Post by macewan on 2005-02-25
work on 2.9.1'ish just fine - using hoary in sources.list

---

### Post by bvc on 2005-02-25
k...I think it's all covered
[Clearlooks-Big_Pack-0.3.tar.bz2](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2)
includes
ClearlooksAna
ClearlooksBlue-L
ClearlooksBluey
ClearlooksChocolateMilk
ClearlooksEtiquette
ClearlooksGONX
ClearlooksGreen
ClearlooksHuman
ClearlooksLime
ClearlooksMilk
ClearlooksNuvola
ClearlooksOrange
ClearlooksTiSkin
Clearlooks_Phacile-blue

includes icons added by me from NikolaP's Smooth-Human gtk theme
[ClearlooksHuman.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksHuman.jpg)

---

### Post by Yukonjack on 2005-02-25
[QUOTE=bvc]k...I think it's all covered
[Clearlooks-Big_Pack-0.3.tar.bz2](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2)
includes
ClearlooksAna
ClearlooksBlue-L
ClearlooksBluey
ClearlooksChocolateMilk
ClearlooksEtiquette
ClearlooksGONX
ClearlooksGreen
ClearlooksHuman
ClearlooksLime
ClearlooksMilk
ClearlooksNuvola
ClearlooksOrange
ClearlooksTiSkin
Clearlooks_Phacile-blue

includes icons added by me from NikolaP's Smooth-Human gtk theme
[/QUOTE]

[COLOR=Sienna][SIZE=4]Thank You THANK YOU Thank You[/SIZE][/COLOR]   :mrgreen:

---

### Post by bvc on 2005-02-25
ur welcome!
they all need work now that there's a notebook style. We can change the color of the active tab and notebook. That'll take more time but I wanted to get them out there for ya'll (I'm from Texas) to use :D

oh, and don't forget that you need gnome-themes-extras for the ClearlooksNuvola!

---

### Post by Daniel G. Taylor on 2005-02-26
Nice work!

With the Human theme I find I like the look of tabs much better when setting bg[ACTIVE] = "#cecece" (it's a less harsh grey for the inactive tabs). I also disabled quite a few of the new icons because I'm not sure I like them, but I am happy to see people working on Ubuntu icon themes!

---

### Post by bvc on 2005-02-26
I'll check that out. I just copied over the stock-icon theme thinking surely anything is better than the default :mrgreen: ...but personally, I don't like the brown, and I don't like suede.  But someone should continue to offer it for those that do, so I'm open to suggestions.

---

### Post by pampa on 2005-02-26
I think this is one of the best themes available for gnome.  It gives life back to it.  Congratulations!!!! =D> 

Now, is there anyone with a deb package for it?  I'm using Hoary but I don't like to install things manually.  I know there is a package for version 0.2 but I want to try the new one  [-o<  [-o<  [-o<

---

### Post by pampa on 2005-02-26
By the way, why do the emoticons not show correcly?

---

### Post by Daniel G. Taylor on 2005-02-26
[QUOTE=pampa]Now, is there anyone with a deb package for it?  I'm using Hoary but I don't like to install things manually.  I know there is a package for version 0.2 but I want to try the new one[/QUOTE]
You got me interested in trying to make a debs again. This is my first "real" package, so no promises. It may make your system explode, etc, etc :-D 

[http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb](http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb)

Note: The Metacity theme was giving me trouble, so it isn't included in the release. For those interested it seems to be hardcoded to some path and fails in the fakeroot.

[Edit] I should mention that this is for Hoary, not Warty!

---

### Post by pampa on 2005-02-26
[QUOTE=Daniel G. Taylor]You got me interested in trying to make a debs again. This is my first "real" package, so no promises. It may make your system explode, etc, etc :-D 

[http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb](http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb)
[/QUOTE]

Thanks!!!  It is working fine!!!  I don't know if feeling guilty or not for making you package it!!!!

---

### Post by bvc on 2005-02-27
by request....
-added a Glider color scheme
-added a Lila color scheme (requires Lila icons in /usr/share/icons)
[http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksLila.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksLila.jpg)
(no, I don't use gentoo)

[http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2)

---

### Post by macewan on 2005-02-27
[QUOTE=bvc]by request....
-added a Glider color scheme
-added a Lila color scheme (requires Lila icons in /usr/share/icons)
[http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksLila.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksLila.jpg)
(no, I don't use gentoo)

[http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2](http://bvc.kernow-webhosting.com/theme/gtk/Clearlooks-Big_Pack-0.3.tar.bz2)[/QUOTE]


wondering if there could be a Ubuntu theme like the Lila with a Ubuntu logo for the gnome foot on the application menu

---

### Post by graigsmith on 2005-02-27
i think you can also put the clearlooks folder into /home/*yourname*/.Theme

folders with dots in front of them are hidden.

so you might have to open a terminal, and go into your home folder, and type 
ls -a   if i remember correctly, that should show you the hidden files

---

### Post by bvc on 2005-02-27
[QUOTE=macewan]wondering if there could be a Ubuntu theme like the Lila with a Ubuntu logo for the gnome foot on the application menu[/QUOTE]
[http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksUbuntu.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/ClearlooksUbuntu.jpg)
Done. The ClearlooksUbuntu colors are diff than the ClearlooksHuman. They are mine from the SmoothMan gtk theme intended to go more with the Etiquette Icon Theme.

if you look in the;
ClearlooksHuman
ClearlooksUbuntu
ClearlooksEtiquette
icon dir's you'll find a few to choose from. Set the one you want in the iconrc file. Credits in the respective README's.
/this is getting confusing blublubluwoo  :-P

---

### Post by bvc on 2005-02-27
Hold up! I'm about to change the stock icons for the Milk and ChocolateMilk schemes.

---

### Post by bvc on 2005-02-27
k...sorry....scratch that for now.....we don't want 11MB of stock icons....hmmm ](*,)

---

### Post by shimon on 2005-02-28
bvc i can give you hosting on my server at savvis... (totally free...)

But why don't i get the cool effects on menu on XUL programs like firefox?

---

### Post by Daniel G. Taylor on 2005-02-28
[QUOTE=shimon]bvc i can give you hosting on my server at savvis... (totally free...)

But why don't i get the cool effects on menu on XUL programs like firefox?[/QUOTE]
 I'm not 100% sure but I think that XUL programs don't directly use GTK widgets. Instead they use GDK/GTK to **draw** their widgets, which means they are different than the normal widgets. That's why OOo and Mozilla/Firefox/etc present a problem for themers. The thing I'm not sure about: who's fault is it?

---

### Post by Spark* on 2005-02-28
That's right... They are basically using the Gtk building blocks to build new widgets, which is fine, but it fails where we special case certain Gtk widgets to look more coherent (like the scrollbars and comboboxes). At least Firefox doesn't look totally alien this way, but it will never be as good as using Gtk directly.

---

### Post by Nikola on 2005-02-28
[QUOTE=macewan]wondering if there could be a Ubuntu theme like the Lila with a Ubuntu logo for the gnome foot on the application menu[/QUOTE]

I've made ubuntu lila color mod, with ubuntu logo plus ubuntu lila wallpapers. You can see screenshots in this thread:
[http://lila-theme.uni.cc/forum/index.php?showtopic=129](http://lila-theme.uni.cc/forum/index.php?showtopic=129)

See it in my screenshot (I use huge fonts, I know:-))
[[img]http://img219.exs.cx/img219/730/screenshot9cw.th.png[/img]](http://img219.exs.cx/my.php?loc=img219&#8465;=screenshot9cw.png)
Unfortunately download link is not working anymore, I don't have upload space, so I've used free file hosting.
If anyone knows where i can upload it, let me know at pizurica_at_neobee DOT net.

---

### Post by mahnve on 2005-03-01
As everyone else I really like this theme. I have come upon a small problem however. When installing on my notebook everything is just fine, but when installing on my workstations at work and at home the window borders do not work. 

I have diffed the output from the configure script for the different machines, seeing no differences. Any clues?

---

### Post by Spark* on 2005-03-01
I think it doesn't install the metacity theme correctly if libgnome2-dev isn't installed. Pretty silly, I know. :) You should get the slightly newer version from here and install manually:
[http://gnome-look.org/content/show.php?content=21237](http://gnome-look.org/content/show.php?content=21237)

---

### Post by yoha on 2005-03-01
When i run gnome-theme-manager from the command line, i got the following error: 

Window manager warning: Failed to read theme from file /usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml': No such file or directory

anyone got this as well?

---

### Post by Spark* on 2005-03-01
This probably means that the metacity theme wasn't installed correctly and the metatheme is looking for it.

---

### Post by bvc on 2005-03-01
[QUOTE=yoha]When i run gnome-theme-manager from the command line, i got the following error: 

Window manager warning: Failed to read theme from file /usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml': No such file or directory

anyone got this as well?[/QUOTE]I did, til I copied the metacity from the source, which is not the Clearlooks metacity but a modified Industrial. ..and again I say: the metacity is not installed with the engine. I've tried 4 times, redownloading the tarball 3 times. Get the Clearlooks Metacity here
[http://www.gnome-look.org/content/show.php?content=21237](http://www.gnome-look.org/content/show.php?content=21237)

---

### Post by landotter on 2005-03-01
looks great here, I'm loving the olive theme (yeah it looks like XP olive, but that's one thing I actually like about XP lol).

Only problem is one it shares with the Gnursid theme, it doesn't jive with Eog, causes it to crash. :/

---

### Post by yoha on 2005-03-01
[QUOTE=bvc]I did, til I copied the metacity from the source, which is not the Clearlooks metacity but a modified Industrial. ..and again I say: the metacity is not installed with the engine. I've tried 4 times, redownloading the tarball 3 times. Get the Clearlooks Metacity here
[http://www.gnome-look.org/content/show.php?content=21237](http://www.gnome-look.org/content/show.php?content=21237)[/QUOTE]
 bvc,
  thanks! it solves the problem. now, any of you guys put the themes on ~/.themes or /usr/share/themes? cos, when i put the themes on the former, the contents are not detected by gnome-theme-manager, only when i put them on the latter, does gtm sees them.

---

### Post by yoha on 2005-03-01
[QUOTE=yoha]bvc,
  thanks! it solves the problem. now, any of you guys put the themes on ~/.themes or /usr/share/themes? cos, when i put the themes on the former, the contents are not detected by gnome-theme-manager, only when i put them on the latter, does gtm sees them.[/QUOTE]
 btw, i am referring to the "big pack" contributed by bvc. also, bvc, how/where can i get that ubuntu logo on your "start menu"?

---

### Post by bvc on 2005-03-01
do the same for the ubuntu and etiquette color schemes...
example:
open the iconrc in the icon dir of the color scheme and make sure only the icon you want to use for the menu is uncommented
```
style "icons" {
#stock["panel-main-menu"] = {{ "gnome-main-menu.svg", *, *, * }}
stock["panel-main-menu"] = {{ "gnome-main-ubuntu-menu.png", *, *, * }}
#stock["panel-main-menu"] = {{ "gnome-main-ubuntu_flat-menu.png", *, *, * }}
```

---

### Post by yoha on 2005-03-02
[QUOTE=bvc]do the same for the ubuntu and etiquette color schemes...
example:
open the iconrc in the icon dir of the color scheme and make sure only the icon you want to use for the menu is uncommented
```
style "icons" {
#stock["panel-main-menu"] = {{ "gnome-main-menu.svg", *, *, * }}
stock["panel-main-menu"] = {{ "gnome-main-ubuntu-menu.png", *, *, * }}
#stock["panel-main-menu"] = {{ "gnome-main-ubuntu_flat-menu.png", *, *, * }}
```[/QUOTE]
 bvc,  but i dont have an iconrc file / icon dir. can you point the flash light? actually, i am confused to what you wrote.

---

### Post by hantsy on 2005-03-02
[QUOTE=Daniel G. Taylor]You got me interested in trying to make a debs again. This is my first "real" package, so no promises. It may make your system explode, etc, etc :-D 

[http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb](http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb)

Note: The Metacity theme was giving me trouble, so it isn't included in the release. For those interested it seems to be hardcoded to some path and fails in the fakeroot.

[Edit] I should mention that this is for Hoary, not Warty![/QUOTE]
I've also built a debian package for Ubuntu Hoary,in clude threes basic themes and metacity ......deb and source package can be download from :
[LinuxFans](http://www.linuxfans.org)
 (But this site is in Chinese , I've no open ftp to upload ^-*)

---

### Post by hantsy on 2005-03-02
[QUOTE=Daniel G. Taylor]You got me interested in trying to make a debs again. This is my first "real" package, so no promises. It may make your system explode, etc, etc :-D 

[http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb](http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.3_i386.deb)

Note: The Metacity theme was giving me trouble, so it isn't included in the release. For those interested it seems to be hardcoded to some path and fails in the fakeroot.

[Edit] I should mention that this is for Hoary, not Warty![/QUOTE]
I've also built a debian package for Ubuntu Hoary,which include threes basic themes and metacity ......deb and source package can be download from :
[LinuxFans](http://www.linuxfans.org)
 (But this site is in Chinese , I've no open ftp to upload ^-*)

---

### Post by mahnve on 2005-03-02
[QUOTE=Spark*]I think it doesn't install the metacity theme correctly if libgnome2-dev isn't installed. Pretty silly, I know. :) You should get the slightly newer version from here and install manually:
[http://gnome-look.org/content/show.php?content=21237](http://gnome-look.org/content/show.php?content=21237)[/QUOTE]
 Thanks a lot - it works now on all my machines. I thought you might like to know though that I indeed do have libgnome2-dev installed on all of them.

---

### Post by yoha on 2005-03-02
currently i am using the ClearLooks-Olive theme. I love the color. Unfortunately, there are no icons associated w/ it and i love the icons on ClearLooks-Ubuntu. I tried copying the icon folder from ClearLooks-Ubuntu to ClearLooks-Olive but obviously the newly copied icons do not work w/ ClearLooks-Olive. Do i need to change something on ClearLooks-Olive's gtkrc file? i did diff command between the gtkrc files on ClearLooks-Olive and ClearLooks-Ubuntu and there are some differences although they dont make sense to me. Can someone point me in the right direction to what i am trying to do?

---

### Post by bvc on 2005-03-02
add
include "icons/iconrc"
at the top of the Olive gtkrc, like it is in Ubuntu gtkrc

---

### Post by HungSquirrel on 2005-03-02
This is a really nice theme engine!  I love it!  Any chance someone could make a darker theme for it?

---

### Post by bvc on 2005-03-02
At this time, because of the white bevel, dark themes are pretty much an impossibility.
Load Clearlooks-Glacier and look at the tabs. Not a great example but you'll get the idea.
[http://bvc.kernow-webhosting.com/theme/clearlooks/Clearlooks-Glacier.tar.gz](http://bvc.kernow-webhosting.com/theme/clearlooks/Clearlooks-Glacier.tar.gz)
or Clearlooks-TiSkin (worse example)
Clearlooks-devel are already aware of this.

---

### Post by HungSquirrel on 2005-03-02
Oh well, it was worth a shot.  :)

I am working on making my own theme for Clearlooks.  In fact I am close to done, but I ran into a problem.  When the file selection dialog opens, the second background color for filenames shows up pinkish/purplish.  The hex value for the color is #fedbfe, but that hex value doesn't appear anywhere in the gtkrc file.  I made my theme colorscheme by hacking your Clearlooks-GONX theme, and the color in question appears light grey in that theme.  I have no idea where the pink is coming from!  What have I done wrong?

[http://hungsquirrel.org/images/clearlooks_gondola.jpg](http://hungsquirrel.org/images/clearlooks_gondola.jpg)

Here's the section of the gtkrc I modified:

```
  bg[NORMAL] = "#e0d9d3"	
  bg[SELECTED] = "#87b08d"
  bg[INSENSITIVE] = "#e0d9d3"
  bg[ACTIVE] = "#b2ae98"
  bg[PRELIGHT] = "#c9cdc9"
  bg[SELECTED] = "#87b08d"

  fg[NORMAL] = "#000000"
  fg[SELECTED] = "#fffdff"
  fg[ACTIVE] = "#000000"
  fg[PRELIGHT] = "#000000"

  base[NORMAL] = "#fffdff"
  base[ACTIVE] = "#667766"
  base[SELECTED] = "#87b08d"

  text[SELECTED] = "#000000"
  text[ACTIVE] = "#000000"
  text[SELECTED] = "#ffffff"
  text[INSENSITIVE]       = "#565248"
```

---

### Post by yoha on 2005-03-03
[QUOTE=bvc]do the same for the ubuntu and etiquette color schemes...
example:
open the iconrc in the icon dir of the color scheme and make sure only the icon you want to use for the menu is uncommented
```
style "icons" {
#stock["panel-main-menu"] = {{ "gnome-main-menu.svg", *, *, * }}
stock["panel-main-menu"] = {{ "gnome-main-ubuntu-menu.png", *, *, * }}
#stock["panel-main-menu"] = {{ "gnome-main-ubuntu_flat-menu.png", *, *, * }}
```[/QUOTE]
 bvc,
   regarding my intention to change the start menu logo from gnome to ubuntu, i saw that the iconrc file on the theme folder default to indeed "gnome-main-ubuntu-menu.png"(being uncommented). Hence, the start menu logo should have been the ubuntu logo instead of the gnome logo. I have tried both restarting x and my box, but the start menu logo keeps on staying  on gnome. 
    one thing strikes me as odd. The ClearLooks-Human's gnome icon /*gnome-main-menu.svg*/ is brown in color and the one on the start menu logo currently is black, which leads me to believe that the icons or rather some of the icons within the ClearLooks-Human's icons folder are not properly applied. some do work however like the "back", "forward", "home", "Volume"etc. From the gnome-theme-manager, these are the settings that are being used > Theme: ClearLooks, Controls: ClearLooks-Ubuntu, Window Border: ClearLooks, and Icons: Gnome. Now when i click on "Go to Theme Folder" button within the Icons' section leads me to ~/.icons and gnome folder is there but contains nothing. 
    I hope i have been clear. I am as confused as a monkey myself.

---

### Post by bvc on 2005-03-03
are you using the main menu? or the menubar?
have you tried this?
[http://www.ubuntuforums.org/showthread.php?t=6457&highlight=icons](http://www.ubuntuforums.org/showthread.php?t=6457&highlight=icons)
You say it's black....do you mean it is gnomes or the ubuntu logo is black? If the ubuntu logo is black...redownload>delete the old and install the new.

---

### Post by HungSquirrel on 2005-03-03
Nevermind my above post.  Somehow GTK decided *base[NORMAL] = "#fffdff"* meant make the second file chooser color *#fedbfe*.  No idea why, but it's fixed now.

Here's my colorscheme, I'm calling Clearlooks-Gondola.

Screen:
[http://hungsquirrel.org/images/clearlooks-gondola-new.jpg](http://hungsquirrel.org/images/clearlooks-gondola-new.jpg)

Package:
[http://hungsquirrel.org/clearlooks-gondola.tar.bz2](http://hungsquirrel.org/clearlooks-gondola.tar.bz2)

First theme ever!  Be nice!  :P

---

### Post by yoha on 2005-03-03
[QUOTE=bvc]are you using the main menu? or the menubar?
have you tried this?
[http://www.ubuntuforums.org/showthread.php?t=6457&highlight=icons](http://www.ubuntuforums.org/showthread.php?t=6457&highlight=icons)
You say it's black....do you mean it is gnomes or the ubuntu logo is black? If the ubuntu logo is black...redownload>delete the old and install the new.[/QUOTE]
 bvc,
  i tried your suggestion on anothe thread you pointed out by replacing the gnome-logo-icon-transparent.png found on /usr/share/pixmaps with whatever. it worked obviously, but isn't the iconrc file in Clearlooks-whatever's icon folder gonna automatically override the usage of gnome-logo-icon-transparent.png in /usr/share/pixmaps? this is the part i am confused at. for example, i m using Clearlooks-Olive. I also liked the icons from Clearlooks-Ubuntu. Therefore, i copied the icon folder from Clearlooks-Ubuntu to Clearlooks-Olive and add the command: include "icons/iconrc" to the gktrc file inside Clearlooks-Olive so the icons will be used. Then, i opened the iconrc file and found this:
...
#stock["panel-main-menu"] = {{ "gnome-main-menu.svg", *, *, * }}
stock["panel-main-menu"] = {{ "gnome-main-ubuntu-menu.png", *, *, * }}
#stock["panel-main-menu"] = {{ "gnome-main-ubuntu_flat-menu.png", *, *, * }}
...
looking at the second line which has by default uncommented, shouldnt the icon by the name of gnome-main-ubuntu-menu.png (which is an Ubuntu logo) inside the icon folder of Clearlooks-Olive be the start menu logo and override the gnome-logo-icon-transparent.png found on /usr/share/pixmaps ?

---

### Post by Jad on 2005-03-03
well its cool 
but I fall in love with merging between gnome and XFCE 
in my gnome theme details I have XFCE in control and human in borders and icons

---

### Post by shimon on 2005-03-03
[QUOTE=Spark*]That's right... They are basically using the Gtk building blocks to build new widgets, which is fine, but it fails where we special case certain Gtk widgets to look more coherent (like the scrollbars and comboboxes). At least Firefox doesn't look totally alien this way, but it will never be as good as using Gtk directly.[/QUOTE]
*evil*

---

### Post by vassie on 2005-03-03
Help!!!
I've just installed clearlooks, but all the clearlooks themes looks like this

[img]http://www.benvassie.net/files/images/clearlooks.png[/img]

Ben

---

### Post by landotter on 2005-03-03
[QUOTE=vassie]Help!!!
I've just installed clearlooks, but all the clearlooks themes looks like this

Ben[/QUOTE]

Did you compile it or just throw the themes into ~.themes?

BTW, that screenshot is 500k and doesn't convey enough information to make the bandwidth worth it. Remember, posting resized pictures with links to larger versions if needed is more polite. The Gimp is your friend. ;)

---

### Post by bvc on 2005-03-03
Clearlooks-0.4 has been released
[http://www.gnome-look.org/content/show.php?content=19527](http://www.gnome-look.org/content/show.php?content=19527)
with an optional animated progressbar! (see screenshot below)

[Clearlooks-Big_Pack-0.4.tar.bz2](http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Big_Pack-0.4.tar.bz2)
[Clearlooks-Big_Pack-0.4-Preview.png](http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Big_Pack-0.4-pre.png)

---

### Post by Daniel G. Taylor on 2005-03-03
Woo! I'm going to boot my desktop box just to check this out!

Clearlooks is quickly becoming the coolest GTK+ theme engine ever!

[Edit] For those that want a package and are running the latest Hoary:
[http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.4_i386.deb](http://programmer-art.org/files/themes/gtk2-engines-clearlooks_0.4_i386.deb)

[Edit 2] I should mention the deb has animated scrollbars compiled in.

---

### Post by Spark* on 2005-03-03
[QUOTE=Daniel G. Taylor][Edit 2] I should mention the deb has animated *scrollbars* compiled in.[/QUOTE]
We are not THAT crazy. ;) But you are not the only one to mix this up occassionally, we even have a little test app for progressbars called "scrollbar".

---

### Post by Daniel G. Taylor on 2005-03-03
Bah, I meant progressbars. I even typed scrollbars and erased it, then I guess I typed it again without thinking...

Hmmm, editing posts doesn't seem to work in Safari :-(

---

### Post by dude2425 on 2005-03-03
I like this theme, but I'm wondering if there is anyway I can add stripes to the metacity theme?
I found a line in it that looks something like **<tile name="title_tile"** or something, and uncomented that, but I only get it on windows that aren't maximized. I can't seem to figure out how to get it on maximized windows too.

Other than that I love this theme. very much. I actually ditched Glider for this one it's so good, and I'm not the type to accept change very easily.

---

### Post by bvc on 2005-03-03
[QUOTE=dude2425]I like this theme, but I'm wondering if there is anyway I can add stripes to the metacity theme?
I found a line in it that looks something like **<tile name="title_tile"** or something, and uncomented that, but I only get it on windows that aren't maximized. I can't seem to figure out how to get it on maximized windows too.

Other than that I love this theme. very much. I actually ditched Glider for this one it's so good, and I'm not the type to accept change very easily.[/QUOTE]

you need to add
```
<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
``` to > <draw_ops name="round_bevel">

<draw_ops name="round_bevel_shaded">

<draw_ops name="bevel_border">

<draw_ops name="title_bg">



Like```
<draw_ops name="bevel">
  <!-- ** 3d beveled frame ** -->
  <line color="shade/gtk:bg[NORMAL]/0.9" x1="1" y1="height - 2" x2="width - 2" y2="height - 2"/>
  <line color="shade/gtk:bg[NORMAL]/0.9" x1="width - 2" y1="title_height + 3" x2="width - 2" y2="height - 2"/>
  <line color="shade/gtk:bg[NORMAL]/1.4" x1="1" y1="title_height + 7" x2="1" y2="height - 2"/>
  <line color="shade/gtk:bg[SELECTED]/0.9" x1="width - 2" y1="3" x2="width - 2" y2="title_height + 6"/>
  <line color="shade/gtk:bg[SELECTED]/1.4" x1="3" y1="1" x2="width - 4" y2="1"/>
  <line color="shade/gtk:bg[SELECTED]/1.4" x1="1" y1="3" x2="1" y2="title_height + 5"/>

  <!-- ** fancy gradient ** -->
  <gradient type="vertical" x="2" y="2" width="width - 4" height="title_height + 4">
    <color value="shade/gtk:bg[SELECTED]/1.2"/>
    <color value="gtk:bg[SELECTED]"/>
  </gradient>
  <line color="shade/gtk:bg[SELECTED]/0.7" x1="1" y1="title_height + 6" x2="width - 2" y2="title_height + 6"/>



<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>


  <rectangle color="#000000" filled="false"
       x="0" y="0"
       width="width - 1"
       height="height - 1"/>

</draw_ops>

<draw_ops name="round_bevel">
  <include name="bevel"/>
  <include name="corners_outline"/>
  <include name="corners_hilight"/>
<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
  <!--<include name="focus_outline"/>-->
</draw_ops>

<draw_ops name="round_bevel_shaded">
  <include name="bevel"/>
  <include name="corners_outline"/>
  <include name="corners_hilight_shaded"/>
<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
</draw_ops>

<draw_ops name="bevel_border">
  <include name="bevel"/>
  <include name="focus_outline"/>
<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
</draw_ops>

<!-- ::: TITLES ::: -->

<draw_ops name="title_bg">
  <!-- tile name="title_tile" tile_width="4" tile_height="10" x="0" y="2" width="(width-title_width)/2-4" height="11"/>
  <tile name="title_tile" tile_width="4" tile_height="10" x="(width-title_width)/2+title_width+4" y="2" width="(width-title_width)/2-4" height="11"/ -->
<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
</draw_ops>
```

---

### Post by bvc on 2005-03-04
by request, I made a Clearlooks-Chocolate based on a screenshot of a theme called Industrial Chocolate?
download
[http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Chocolate.tar.gz](http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Chocolate.tar.gz)
[IMG]http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Chocolate.png[/IMG]

---

### Post by dtessier on 2005-03-04
[QUOTE=bvc]do the same for the ubuntu and etiquette color schemes...
example:
open the iconrc in the icon dir of the color scheme and make sure only the icon you want to use for the menu is uncommented
```
style "icons" {
#stock["panel-main-menu"] = {{ "gnome-main-menu.svg", *, *, * }}
stock["panel-main-menu"] = {{ "gnome-main-ubuntu-menu.png", *, *, * }}
#stock["panel-main-menu"] = {{ "gnome-main-ubuntu_flat-menu.png", *, *, * }}
```[/QUOTE]

Sorry to bring this subject back up, but I can't seem to get the menubar icon to change to the Ubuntu logo using this method. I've gotten it to work by replacing gnome-logo-icon-transparent.png in /usr/share/pixmaps, but I would much prefer a method that allows me to set different menubar icons with different themes.

One difference I noticed with some other themes is that my gtkrc does not have a line that looks like this:
```
gtk-icon-sizes = "panel-menu=36,36:gtk-menu=16,16:panel=16,16"
```

Any suggestions?

---

### Post by bvc on 2005-03-04
[QUOTE=Daniel G. Taylor]Clearlooks is quickly becoming the coolest GTK+ theme engine ever![/QUOTE]
Those that have known me for years know I have always bashed engines. I realize they have their place for older machines but as far as I was concerned that's where they could stay :mrgreen: . Smooth was the first engine I ever cared for and only because it was so customizable. But Clearlooks rocks my socks off to go jump in the river! :lol: I now have 20 of my own color schemes...I'll just delete everything else and never svg theme again 8-[

---

### Post by bvc on 2005-03-04
[QUOTE=dtessier]Sorry to bring this subject back up, but I can't seem to get the menubar icon to change to the Ubuntu logo using this method. I've gotten it to work by replacing gnome-logo-icon-transparent.png in /usr/share/pixmaps, but I would much prefer a method that allows me to set different menubar icons with different themes.

One difference I noticed with some other themes is that my gtkrc does not have a line that looks like this:
```
gtk-icon-sizes = "panel-menu=36,36:gtk-menu=16,16:panel=16,16"
```

Any suggestions?[/QUOTE]
gee I d/k...I don't use the menu bar (I guess you mean in the panel). I just loaded it up and it was there, but I have it in so many places, and I'm also use the lila-brown icons. To be honest, I've only ever chaned the gnome-main-menu icon and never played with this gnome-logo-icon-transparent.png that others are changing.

---

### Post by kassetra on 2005-03-04
[QUOTE=bvc]I now have 20 of my own color schemes...I'll just delete everything else and never svg theme again 8-[[/QUOTE]

Nooooo!  must have new svg themes!!

---

### Post by HungSquirrel on 2005-03-04
bvc, what exactly is a theme engine?  What does it do?

---

### Post by Daniel G. Taylor on 2005-03-04
[QUOTE=kassetra]Nooooo!  must have new svg themes!![/QUOTE]
 Lol, SVG themes are better for icons than for widget themes, and many of the Clearlooks themes from bvc actually use SVG icons ;-) 

Interesting to hear you use Lila, bvc :-D (The curious should check [http://programmer-art.org/lila-theme](http://programmer-art.org/lila-theme) and svg-utils, which were used to create the brown version)

---

### Post by Daniel G. Taylor on 2005-03-04
[QUOTE=HungSquirrel]bvc, what exactly is a theme engine?  What does it do?[/QUOTE]
A theme engine is what draws your controls (like buttons, menus, scrollbars, progressbars). There is a simple pixmap-based theme engine available that lets you use pictures for all the controls, but it is slow. Other theme engines like Bluecurve, Industrial, Clearlooks, Smooth, etc all have their own specific look and are drawn using C code so they are very fast compared to just using pictures. The different themes that are available for these engines typically just change some colors and a few other parameters, like where to place scrollbar arrows or how rounded to make an edge.

---

### Post by bvc on 2005-03-04
> **Daniel G. Taylor]Lol, SVG themes are better for icons than for widget themes, and many of the Clearlooks themes from bvc actually use SVG icons  said:**
> http://programmer-art.org/lila-theme[/url] and svg-utils, which were used to create the brown version) :lol: many would disagree including me. Just look at the top 6 (highest rated) at gnome-look 
4.Wintah
5.Ana
6.Edge
all svg. Phacile (png) will come down. It's up that high because it is new. MacOSX, well we know why it's there, and Clearlooks will stay on top.

I like uniformity. Lila-brown, it's wallapers and either Clearlooks-Ubuntu or Clearlooks-Chocolate give me that. I never liked the ubuntu brown til these. I hate Industrial anything and think is a horrid engine and 2 years dead. :lol:

---

### Post by kassetra on 2005-03-04
[QUOTE=Daniel G. Taylor]Lol, SVG themes are better for icons than for widget themes, and many of the Clearlooks themes from bvc actually use SVG icons ;-) 
[/QUOTE]

I still have this freaky dream where I can use css (or css-like) and svg in order to theme all of my desktop components...  That way I could use my mad leet css skillz to rock the desktop.  heh.  yeah, it's my dream.  heh.

---

### Post by bvc on 2005-03-04
edited above post
The svg's will stay up high because they are more eyecandyish...more like a windowblinds skin, if you will.

---

### Post by bvc on 2005-03-04
[QUOTE=kassetra]I still have this freaky dream where I can use css (or css-like) and svg in order to theme all of my desktop components...  That way I could use my mad leet css skillz to rock the desktop.  heh.  yeah, it's my dream.  heh.[/QUOTE]
oooo...nice concept hmmm....
like how svg (xml) can call java on a web page!

---

### Post by kassetra on 2005-03-04
[QUOTE=bvc]I like uniformity. Lila-brown, it's wallapers and either Clearlooks-Ubuntu or Clearlooks-Chocolate give me that. I never liked the ubuntu brown til these. I hate Industrial anything and think is a horrid engine and 2 years dead. :lol:[/QUOTE]

Clearlooks-Chocolate is GORGEOUS.  (even if the scrollbars aren't flat)

---

### Post by HungSquirrel on 2005-03-04
That WOULD be awesome.  Then even *I* could do some theming.  :P

---

### Post by kassetra on 2005-03-04
[QUOTE=HungSquirrel]That WOULD be awesome.  Then even *I* could do some theming.  :P[/QUOTE]

My whole idea behind the css-style theme files was that if css styles web documents, why can't it style my desktop documents/objects as well?  Then I thought, how many people (especially designers - who are the first to say, ewww it's ugly!) could use/change their settings to match their preferences with just some css code, which, now, there are many apps that let you edit css files with a wysiwyg / gui interface...

---

### Post by HungSquirrel on 2005-03-04
The idea makes sense and has a lot of merit.  It should have been done that way from the beginning in my opinion.  One of my complaints with Gnome is that it is not easy for the user to adjust colorschemes, as is the case in KDE.  Using CSS would make it easy to build a WYSIWYG frontend to allow users to adjust colorschemes to their heart's content.

---

### Post by yoha on 2005-03-04
[QUOTE=bvc]Clearlooks-0.4 has been released
[http://www.gnome-look.org/content/show.php?content=19527](http://www.gnome-look.org/content/show.php?content=19527)
with an optional animated progressbar! (see screenshot below)

[Clearlooks-Big_Pack-0.4.tar.bz2](http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Big_Pack-0.4.tar.bz2)
[Clearlooks-Big_Pack-0.4-Preview.png](http://bvc.kernow-webhosting.com/theme/clearlooks-0.4/Clearlooks-Big_Pack-0.4-pre.png)[/QUOTE]
 Since Clearlooks v0.4 is released and i have the older version installed, can i just overwrite the old version? how do i uninstall the old version? i am kinda new to installing stuff from source.

---

### Post by HungSquirrel on 2005-03-04
I just compiled and installed the new one over the old one, and it worked fine.

Be sure to do *./configure --enable-animation* if you want the animated progressbars (they look snazzy IMO).

---

### Post by cka on 2005-03-04
[QUOTE=HungSquirrel]
Be sure to do *./configure --enable-animation* if you want the animated progressbars (they look snazzy IMO).[/QUOTE]


 8-) I'll have to go recompile clearlooks in a minute it seems.

---

### Post by yoha on 2005-03-04
when i invoke gnome-theme-manager on terminal, i got this: "art_render_invoke: no image source given". the theme manager shows up nevertheless just like normal but wondering what that message means.

---

### Post by bvc on 2005-03-04
[QUOTE=yoha]when i invoke gnome-theme-manager on terminal, i got this: "art_render_invoke: no image source given". the theme manager shows up nevertheless just like normal but wondering what that message means.[/QUOTE]I d/k what it means but I've been getting it for a long time with all themes.

---

### Post by jmather on 2005-03-04
I noticed several people had there panel setup to have there window list display two levels of applications....is this part of a this theme?  Yes or No....how do I do it? :)

[http://hungsquirrel.org/images/clearlooks_gondola.jpg](http://hungsquirrel.org/images/clearlooks_gondola.jpg)

Notice the bottom panel...? ;)

---

### Post by darrenadams on 2005-03-04
[QUOTE=jmather]I noticed several people had there panel setup to have there window list display two levels of applications....is this part of a this theme?  Yes or No....how do I do it? :)

[http://hungsquirrel.org/images/clearlooks_gondola.jpg](http://hungsquirrel.org/images/clearlooks_gondola.jpg)

Notice the bottom panel...? ;)[/QUOTE]


You need to increase the size of the panel. Anything from 45 pixels up should do it

---

### Post by bvc on 2005-03-04
[QUOTE=darrenadams]You need to increase the size of the panel. Anything from 45 pixels up should do it[/QUOTE]
correct
if you want a smaller panel that does the same look at this
[http://gnomesupport.org/forums/viewtopic.php?t=8645&start=15](http://gnomesupport.org/forums/viewtopic.php?t=8645&start=15)

---

### Post by jmather on 2005-03-04
Great! Thanks for the prompt reponses....I got it working np.

-jm

---

### Post by Daniel G. Taylor on 2005-03-04
[QUOTE=bvc]:lol: many would disagree including me. Just look at the top 6 (highest rated) at gnome-look 
4.Wintah
5.Ana
6.Edge
all svg. Phacile (png) will come down. It's up that high because it is new. MacOSX, well we know why it's there, and Clearlooks will stay on top.[/QUOTE]

Okay, I'm an idiot. #-o I do however have one issue with the eye-candy reason. I think that you can pretty much do anything with pixmaps that you could with scalable graphics given a reasonable resolution. Especially since most of the widgets just need the borders to be strictly defined. So I don't really see the advantage of SVG over pixmaps if you are going to theme widgets with images, whereas with SVG icons you have the entire icon that will be scaled, and it can be scaled pretty large compared to a normal widget. I don't know, maybe I just don't get it.

I've always prefered engines to image-based widget themes anyway, even though I used to use Windowblinds years ago.

---

### Post by bvc on 2005-03-04
[QUOTE=Daniel G. Taylor]Okay, I'm an idiot. #-o I do however have one issue with the eye-candy reason. I think that you can pretty much do anything with pixmaps that you could with scalable graphics given a reasonable resolution. Especially since most of the widgets just need the borders to be strictly defined. So I don't really see the advantage of SVG over pixmaps if you are going to theme widgets with images, whereas with SVG icons you have the entire icon that will be scaled, and it can be scaled pretty large compared to a normal widget. I don't know, maybe I just don't get it.

I've always prefered engines to image-based widget themes anyway, even though I used to use Windowblinds years ago.[/QUOTE]
the advantage is still the same. A 3kb svg button 'should' be lighter and faster than a 8kb png button. We just need an efficiant librsvg. For most, me included, creating an svg is far faster than a png not to mention the easy of making changes for not only the designer but anyone else that wants to edit it.

---

### Post by kassetra on 2005-03-04
[QUOTE=bvc]the advantage is still the same. A 3kb svg button 'should' be lighter and faster than a 8kb png button. We just need an efficiant librsvg. For most, me included, creating an svg is far faster than a png not to mention the easy of making changes for not only the designer but anyone else that wants to edit it.[/QUOTE]

CAIRO!  :)  It's coming soon!  I like vector graphics for the simple reason that whatever I do is not "stuck" on the canvas like bitmapped graphics... I can edit, resize, change, warp, etc without pixelizing.

---

### Post by Daniel G. Taylor on 2005-03-04
Good point. No more arguments from me ;-)

P.S. Also eagerly awaiting GTK2.8 (with Cairo integration)

---

### Post by Nikola on 2005-03-04
[QUOTE=bvc]the advantage is still the same. A 3kb svg button 'should' be lighter and faster than a 8kb png button. We just need an efficiant librsvg. For most, me included, creating an svg is far faster than a png not to mention the easy of making changes for not only the designer but anyone else that wants to edit it.[/QUOTE]

But one problem with svg icons still remains. When scaled down they look like shit. There is no suplement to creating bitmap icons for small sizes, like 16x16 pixels. And for creating small images, you have to be genius (like jimmac). Look at his work for all those stock icons for Ooo.
SVG icons are very easy to work on, you can reuse elements, but unfortunately when scaled down, it just can't be compared to nicely done bitmap image.

---

### Post by kassetra on 2005-03-04
[QUOTE=Nikola]SVG icons are very easy to work on, you can reuse elements, but unfortunately when scaled down, it just can't be compared to nicely done bitmap image.[/QUOTE]

Depends on the icon... I have quite a few I've worked with that look wonderful scaled down, *much* better than the bitmap... but more complex icons tend to look poor.

Jimmac actually had a GREAT idea about what to do about this!  He suggested that maybe themes could read layer sets or named objects, etc. *inside* the scalable file, and if there was an icon created for say, 16x16 inside the vector file to use that icon instead of scaling the larger one.

That suggestion would make svg the best of both worlds!

---

### Post by bvc on 2005-03-04
Create it at the smaller size and you won't have to scale it down, and it'll look fine. Svg icons are best at 48x48 if you just want one size because they'll then look good in the menu and toolbar, yet can be your wallpaper if you want it to 8-)  Originally, Edge-Icons were 48x48 but because of svg bugs I made them 128x128 so that I could export them to png and look better.

---

### Post by ohman11 on 2005-03-05
I get this error..

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@ubuntu:/home/dave/clearlooks-0.4 #

---

### Post by HungSquirrel on 2005-03-05
sudo apt-get install build-essential

---

### Post by kassetra on 2005-03-06
[QUOTE=bvc]Create it at the smaller size and you won't have to scale it down, and it'll look fine.[/QUOTE]

Hmmm... usually my smaller sized icons are simpler than the larger one... say like an icon for gthumb at 48x48 or larger shows a couple of slides and a magnifying glass... at 16x16 I'll just show a single slide...

If I made just the single slide at 16x16 and scaled it up... that would be pretty boring and plain.

---

### Post by NeoChaosX on 2005-03-06
Just tried out the latest version of Clearlooks with the Big Pack. Clearlooks-Milk goes great with my wallpaper.  :grin:

EDIT: Oh, and does anyone know where I can get a seperate icon set for the ones used by Clearlooks-Milk? Really liking hte icons used by the theme in Nautilus, would like to apply it to the whole desktop.

---

### Post by bvc on 2005-03-06
[QUOTE=kassetra]Hmmm... usually my smaller sized icons are simpler than the larger one... say like an icon for gthumb at 48x48 or larger shows a couple of slides and a magnifying glass... at 16x16 I'll just show a single slide...

If I made just the single slide at 16x16 and scaled it up... that would be pretty boring and plain.[/QUOTE]
that's why a happy medium is good. 16x16 is too small.... 24, 32, or 36 is good for small icons IMO but I'm no icon expert either. Sure, take a 128 icon and slap it on a toolbar, it is going to look bad. 24 or 36 svg in a toolbar ain't bad and is just a tad worse than a png. JMO.

---

### Post by drew_t on 2005-03-18
Newbie here.  Could someone explain how to install the Big Pack themes on a Hoary system?   The regular Clearlooks theme is already installed and available through System --> Preferences --> Theme.

---

### Post by bvc on 2005-03-18
uncompress the bz2 and put the theme dirs in .themes

**commandline**
tar -xjf Clearlooks-Big_Pack-0.4.tar.bz2

or use file-roller (Menu>Accessories>Archive Manager)
when you tell it to extract and get the Extract window, rt-click and choose 'Show Hidden Files'>browse to and highlight .themes> and click OK ...or whatever

---

### Post by Spark* on 2005-03-18
It should also be possible to go to Theme Preferences -> Details -> Go To Theme Folder and then drag and drop the themes from file roller into it. 
If the themes would be packed individually, you could also just drag and drop the archive on the Theme Preferences window.

---

### Post by bvc on 2005-03-20
[http://home.houston.rr.com/bvc/gtk/Clearlooks-Big_Pack-0.5.tar.bz2](http://home.houston.rr.com/bvc/gtk/Clearlooks-Big_Pack-0.5.tar.bz2)

---

### Post by bvc on 2005-03-23
I've updated it again.

Added a scrollbar 'style' and other color stuff to the gtkrc's of the 2 new color schemes and Lucidity for a more usable gtkrc. You'll notice the widgets stand out more. I'll probably continue to see what I can do to the others.
**the new are**
Clearlooks-3.1-Ergo
Clearlooks-Gull
*these are diff than what was posted in the desktop thread in the past few days* 

**Old**
Clearlooks-Ana
Clearlooks-Bluey
Clearlooks-Coffee
Clearlooks-Etiquette
Clearlooks-Glider
Clearlooks-Lila
Clearlooks-Lucidity
Clearlooks-Milk
Clearlooks-Nuvola
Clearlooks-Phacile_blue
Clearlooks-Ubuntu

[download Clearlooks-Big_Pack-0.5](http://gnome-look.org/content/show.php?content=22259)

---

### Post by NeoChaosX on 2005-04-10
Bring this thread back because when I installed Big Pack 0.5, I noticed that Synaptic went back to an older-looking theme instead of matching with GTK. The only way it matched the GTK theme was if I switched it back to plain Clearlooks. I'm a fan of Clearlooks-Etiquette, so just wondering if you knew of this problem, and when it will be fixed.  :-|

---

### Post by sanjeevdas on 2005-04-10
[QUOTE=NeoChaosX]Bring this thread back because when I installed Big Pack 0.5, I noticed that Synaptic went back to an older-looking theme instead of matching with GTK. The only way it matched the GTK theme was if I switched it back to plain Clearlooks. I'm a fan of Clearlooks-Etiquette, so just wondering if you knew of this problem, and when it will be fixed.  :-|[/QUOTE]

I think some apps don't look at ~/.themes for the theme files. If you copy the theme files from ~/.themes to /usr/share/themes synaptic will start working again (with the theme).

---

### Post by NeoChaosX on 2005-04-10
Okay, why didn't I think of that.  :-P Thanks.

---

### Post by bvc on 2005-04-10
I do not understand. The Big_Pack doesn't conflict with any .deb pkg/engine/default clearlooks color schemes. Apps do not look in either /usr/share/themes or .themes but at gnome config files. Try reloading the themes and then do
killall nautilus
killall gnome-panel

---

### Post by Buffalo Soldier on 2005-04-10
[QUOTE=NeoChaosX]Bring this thread back because when I installed Big Pack 0.5, I noticed that Synaptic went back to an older-looking theme instead of matching with GTK. The only way it matched the GTK theme was if I switched it back to plain Clearlooks. I'm a fan of Clearlooks-Etiquette, so just wondering if you knew of this problem, and when it will be fixed.  :-|[/QUOTE]I had the same problem. Found the solution. Many thanks to Artificial Intelligence. [HOWTO: Change GTK themes for root application & Standard greeter](http://ubuntuforums.org/showthread.php?t=23798)

---

### Post by sanjeevdas on 2005-04-10
[QUOTE=bvc]I do not understand. The Big_Pack doesn't conflict with any .deb pkg/engine/default clearlooks color schemes. Apps do not look in either /usr/share/themes or .themes but at gnome config files. Try reloading the themes and then do
killall nautilus
killall gnome-panel[/QUOTE]

Maybe because synaptic is running as root and therefore cannot (or is not trying to) load the theme from  my home folder? Your solution above does not seem to be working. The only way I know to make this work is to copy the theme files to /usr/share/themes.

BTW, this has nothing to do with the Big_Pack files. I think it happens with all themes that you install to your .themes folder.

---

### Post by kassetra on 2005-04-10
[QUOTE=sanjeevdas]Maybe because synaptic is running as root and therefore cannot (or is not trying to) load the theme from my home folder?[/QUOTE]

Any app run as root will look in root's theme setup in order to know what themes to use -- with the exception of the metacity theme and such.  Those are from the user's theme.

Many people actually use a different theme for root apps.

---

### Post by bvc on 2005-04-10
oh yeah....forgot about that. All my stuff is on another partition being shared with other distros, so they are already all symlinked.

just symlink from root to the user ;-)

as root;
rm -fr .themes
ln -s /home/user/.themes .themes

---

### Post by shimon on 2005-04-11
[QUOTE=NeoChaosX]Bring this thread back because when I installed Big Pack 0.5, I noticed that Synaptic went back to an older-looking theme instead of matching with GTK. The only way it matched the GTK theme was if I switched it back to plain Clearlooks. I'm a fan of Clearlooks-Etiquette, so just wondering if you knew of this problem, and when it will be fixed.  :-|[/QUOTE]

I found this bugs a long long long time ago They can not fix it because you could put a theme with some damaging code in ~/.themes and when and sudo app runs it... it can do real damage... so just think of it as a security issue

---

### Post by bvc on 2005-04-11
[QUOTE=shimon]you could put a theme with some damaging code in ~/.themes[/QUOTE]/bvc scratches his head and wonders.....

oh, and it's not a bug...it's how it is suposed to work and has always worked

---

### Post by deviant03 on 2005-04-24
I was already using it on Warty, glad I dont have to configure anything now to use it on Hoary :)

---

### Post by Quest-Master on 2005-06-02
I keep getting this when I start gnome-theme-manager..

(gnome-theme-manager:10091): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

---

### Post by Quest-Master on 2005-06-06
[QUOTE=Quest-Master]I keep getting this when I start gnome-theme-manager..

(gnome-theme-manager:10091): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",[/QUOTE]

Bump.... :(

---

### Post by bvc on 2005-06-06
how did you install the clearlooks engine? ...not the themes, the engine.

Instructions are in the Description
[http://www.gnome-look.org/content/show.php?content=19527](http://www.gnome-look.org/content/show.php?content=19527)

or you can get it with apt or synaptic

---

### Post by Quest-Master on 2005-06-10
[QUOTE=bvc]how did you install the clearlooks engine? ...not the themes, the engine.

Instructions are in the Description
[http://www.gnome-look.org/content/show.php?content=19527](http://www.gnome-look.org/content/show.php?content=19527)

or you can get it with apt or synaptic[/QUOTE]
 Standard ./configure;make;sudo make install.

I didn't know it was in apt though. Going to get it from there then.

---

### Post by bvc on 2005-06-10
apt won't get you the 0.6 version released yesterday

sounds like you installed the engine to the default
/lib
instead of
/usr/lib


this installs to /usr;

./configure --prefix=/usr --enable-animation
make
sudo make install

---

### Post by Kumagoro on 2008-09-12
May i ask you guys one thing...

What's the diff between a GTK engine and a GTK theme?

---

### Post by Daniel G. Taylor on 2008-09-12
> **Kumagoro said:**
> May i ask you guys one thing...

What's the diff between a GTK engine and a GTK theme?

A GTK+ theme normally sets information like the main text color, the main window color, various other colors, and any other settings that can be exposed by the theme engine. The theme engine is a program that literally draws the menus, buttons, and other widgets based on the colors and settings defined in the theme.

There is a bit of overlap of course, as an engine may not need any settings in the theme file (if it doesn't accept different colors, styles, etc). On the other side there are engines that just take images and draw them, so the theme file really defines everything. Complex :-)

---

### Post by days_of_ruin on 2008-09-12
> **bvc said:**
> me likes to...and I usually do not use engines....they bore me. But I can't stop using this one. My first 3 color mods are in the engine install as of v 0.2 but I have another 3 for thos interested. I like ClearlooksChocolateMilk
link removed

You are always using a gtk engine on gnome.

---

