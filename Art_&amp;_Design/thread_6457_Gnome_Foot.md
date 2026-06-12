---
title: "Gnome Foot"
date: 2004-11-28
forum: Art &amp; Design
---

### Post by poofyhairguy on 2004-11-28
I love this ubuntu, putting it on every machine I touch.:D  It is the only linux I've ever had where I didn't mess with the default desktop. I like it all... except one thing.

Is there a way to replace the foot next to applications on the bar with the ubuntu symbol? I would love to make a custom one, if I knew how to install it. 

Thx

---

### Post by Magneto on 2004-11-28
/usr/share/pixmaps/gnome-logo-icon-transparent.png  any custom one has to fit certain requirements otherwise the gnome-panel won't load

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=Magneto]/usr/share/pixmaps/gnome-logo-icon-transparent.png  any custom one has to fit certain requirements otherwise the gnome-panel won't load[/QUOTE]

thanks. It was easy to make a new one in gimp. If someone wants it, I'll put it in a photo bucket or something.

---

### Post by HungSquirrel on 2004-11-29
Someone wants it.  ;)

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=HungSquirrel]Someone wants it.  ;)[/QUOTE]


Sure.

[IMG]http://img108.exs.cx/img108/2702/gnome-logo-icon-tran.png[/IMG]

If this host goes down, I'll use another.

---

### Post by Magneto on 2004-11-29
MODS please move this thread to the Screenshots/ Art Talk Forum

and here's a  blue one

[img]http://ubuntu.spymac.net/blugnome-logo-icon-tran.png[/img]

---

### Post by jdodson on 2004-11-29
moved to right forum.

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=Magneto]MODS please move this thread to the Screenshots/ Art Talk Forum

and here's a  blue one

[img]http://ubuntu.spymac.net/blugnome-logo-icon-tran.png[/img][/QUOTE]

wooo, thats nice. Maybe a start of a ubuntublue theme?
 :mrgreen:

---

### Post by Magneto on 2004-11-29
[QUOTE=poofyhairguy]wooo, thats nice. Maybe a start of a ubuntublue theme?
 :mrgreen:[/QUOTE]
 maybe BVC will bless us with one 
I just mix and match themes - i would like to make an icon theme but I hit a snag on icons other than the ubuntu logo lol

---

### Post by arctic on 2004-11-29
[QUOTE=poofyhairguy]wooo, thats nice. Maybe a start of a ubuntublue theme?
 :mrgreen:[/QUOTE]
then we also need a blue ubuntu gdm-screen and a blue gnome-splash ;)

---

### Post by TravisNewman on 2004-11-29
Very slick guys, Using the orange/red one for the gnome panel now (sorry Magneto, the blue just doesn't flow with my desktop at the moment). I never knew you could customize that or I probably already would have!

---

### Post by Xian on 2004-11-29
Thanks all for the great info and submissions. That single change makes such a huge difference.
It really personalizes the desktop for a more unified and coherent Ubuntu appearance.

---

### Post by bvc on 2004-11-30
[QUOTE=Magneto]maybe BVC will bless us with one 
I just mix and match themes - i would like to make an icon theme but I hit a snag on icons other than the ubuntu logo lol[/QUOTE]
wha?
[http://gnome-look.org/content/show.php?content=17082](http://gnome-look.org/content/show.php?content=17082)
not blue/ubuntu enough for the icon? :?

I just started this (no arrows yet)
[IMG]http://bvc.kernow-webhosting.com/theme/images/blu.png[/IMG]
but it's not ubuntuish and I haven't decided where it's going. If you have ideas, PM me so we don't mess up the thread. GTK isn't playing nice.

---

### Post by link on 2004-11-30
What's the gnome-icon-theme name that replaces the foot? gnome-main-menu?

---

### Post by Magneto on 2004-11-30
[QUOTE=link]What's the gnome-icon-theme name that replaces the foot? gnome-main-menu?[/QUOTE]
 the xml tag in the icon theme?

---

### Post by LongTooth on 2004-11-30
Can someone tell me the steps to change the 'foot' on the panel? I'd like to try the red/yellow logo but I'm not certain of the steps I have to take. Thanks.

---

### Post by bvc on 2004-11-30
The easiest way is to rename;
/usr/share/pixmap/gnome-main-menu.png
to whatever and replace with yours. Then in a terminal do;
killall gnome-panel

if you have a lot of diff ones you want to customize and are going to change them often it may be easier to keep them in a central location and make a ~/.gtkrc-2.0 and put the necessary code in there to point to your custom iconrc. This will over_ride defaults or theme settings.

~/.gtkrc-2.0
```
gtk-icon-sizes = "panel-menu=36,36:gtk-menu=16,16:panel=16,16"
include "/xdata/gui/icons/iconrc"
```

relevant part
/xdata/gui/icons/iconrc
Both the icons and iconrc are in the same dir
```
style "panel-icons"
{
	stock["panel-main-menu"] 	= {{ "gnome-main-menu.png", *, *, * }}
}
class "GtkWidget" style "panel-icons" 
```

get a very complete iconrc here
[http://gnomesupport.org/forums/viewtopic.php?p=40965&highlight=#40965](http://gnomesupport.org/forums/viewtopic.php?p=40965&highlight=#40965)

Oh, and I'm also in Houston :D

---

### Post by poofyhairguy on 2004-11-30
[QUOTE=bvc] Then in a terminal do;
killall gnome-panel
[/QUOTE]

Or press

Ctrl-Alt-Backspace

I live near Houston!

---

### Post by bvc on 2004-11-30
Or use the gnome-system-monitor or the gnome-theme-manager ....etc....there's many ways :grin:

we could have a Texan Ubuntu party :p

---

### Post by link on 2004-12-01
So there's not a way to set the icon via the icon theme (rather than the gtkrc)? That seems surprising to me, considering there are themes in gnome-themes-extras that does replace that icon.

---

### Post by bvc on 2004-12-01
sure there is. What ever is in
$ICON_THEME/sizexsize/apps/gnome-main-menu.ext

like
MMX-Mercury-L/128x128/apps/gnome-main-menu.png

BUT! If the gtk theme has a iconrc with a menu icon it will over_ride the icon theme.

I'm currently using the new Industrial Steel icon theme. It didn't have a menu icon. I didn't want the gnome default. So I put mine in /IndustrialSteel/48x48/apps/

---

### Post by poofyhairguy on 2004-12-01
[QUOTE=bvc]Or use the gnome-system-monitor or the gnome-theme-manager ....etc....there's many ways :grin:

we could have a Texan Ubuntu party :p[/QUOTE]

Cool, I'll be in Houston around the first!

---

### Post by LongTooth on 2004-12-01
You guys lost me. Can you give me a step by step ( preferably via GUI ) procedure for changing the 'Foot' on the panel? Thanks.

---

### Post by bvc on 2004-12-01
[QUOTE=bvc]The easiest way is to rename;
/usr/share/pixmap/gnome-main-menu.png
to whatever and replace with yours.[/QUOTE] :grin:

---

### Post by poofyhairguy on 2004-12-01
[QUOTE=LongTooth]You guys lost me. Can you give me a step by step ( preferably via GUI ) procedure for changing the 'Foot' on the panel? Thanks.[/QUOTE]

Right click on my picture: save as

Save in the /usr/share/pixmaps/ folder.

Should work.

---

### Post by amoser on 2004-12-01
I know this may not go over well, but the Industral theme looks pretty good, it is kinda like Ubuntu in a blue form.  I mean, well, the Human theme is based off the Industral theme.

~Alan

---

### Post by link on 2004-12-02
Drop the gnome-logo-icon-transparent.png into Theme/48x48/apps and the panel will use it. I'll be making a modification of SmoothGNOME that uses the Ubuntu logo as the panel-main-menu.

---

### Post by macewan on 2004-12-02
[QUOTE=LongTooth]You guys lost me. Can you give me a step by step ( preferably via GUI ) procedure for changing the 'Foot' on the panel? Thanks.[/QUOTE]

cd /usr/share/pixmaps/
mv gnome-logo-icon-transparent.png gnome-logo-icon-transparent2.png
cp ~/blugnome-logo-icon-tran.png ./gnome-logo-icon-transparent.png
killall gnome-panel

[IMG]http://www.macewan.org/screenshots/closeup.jpg[/IMG]

[Bigger picture](http://www.macewan.org/screenshots/menu.jpg)

---

### Post by LongTooth on 2004-12-03
Thanks for the steps. I'll try it when I get home tonight. In the mean time, just in case, what are the procedures for reverting back to the original? That last command, 'killall gnome-panel', sound very ominous. Thanks.

---

### Post by macewan on 2004-12-04
[QUOTE=LongTooth]Thanks for the steps. I'll try it when I get home tonight. In the mean time, just in case, what are the procedures for reverting back to the original? That last command, 'killall gnome-panel', sound very ominous. Thanks.[/QUOTE]
 In my case it would be:

mv /usr/share/pixmaps/gnome-logo-transparent2.png /usr/share/pixmaps/gnome-logo-transparent.png

if it bitches about permission denied then:

sudo mv /usr/share/pixmaps/gnome-logo-transparent2.png /usr/share/pixmaps/gnome-logo-transparent.png

---

### Post by bazuka on 2004-12-04
Here's another version ...

---

### Post by Xian on 2004-12-04
Sweet. I can use that color as well. 

Thanks.

---

### Post by bvc on 2004-12-04
nevermind :mrgreen:

---

### Post by adbak on 2004-12-09
Neat!  I have the Ubuntu symbol in place of my Gnome foot, but I chose my own colors.  I used the browns that Ubuntu is known for.  It's attached.

---

### Post by jakeslife on 2004-12-19
[QUOTE=macewan]cd /usr/share/pixmaps/
mv gnome-logo-icon-transparent.png gnome-logo-icon-transparent2.png
cp ~/blugnome-logo-icon-tran.png ./gnome-logo-icon-transparent.png
killall gnome-panel

[IMG]http://www.macewan.org/screenshots/closeup.jpg[/IMG]

[Bigger picture](http://www.macewan.org/screenshots/menu.jpg)[/QUOTE]


OMG that's hot.

---

### Post by Sensebend on 2005-01-03
Hehe, this really fits the feel of Ubuntu much more than the GNOME foot. I like it, I'm using the one with the Ubuntu colours. Keep up the good work people!

---

### Post by hazza96 on 2005-01-03
I love the first one posted, and have changed mine to look like that.

Is there a way to get the developers to use one of them as the default? The others are good options but the first is in the right Ubuntu colours.

---

### Post by towner on 2005-01-06
[QUOTE=adbak]Neat!  I have the Ubuntu symbol in place of my Gnome foot, but I chose my own colors.  I used the browns that Ubuntu is known for.  It's attached.[/QUOTE]
 cheers adbak,
using your ububtu symbol and all is good on my desktop

---

### Post by NeoChaosX on 2005-04-06
Apologies for bumping this thread, but I can't seem to get the Gnome foot working in Hoary since I upgraded. Has anyone got this little trick to work in Hoary, and if so, how?

---

### Post by bvc on 2005-04-06
[QUOTE=NeoChaosX]Apologies for bumping this thread, but I can't seem to get the Gnome foot working in Hoary since I upgraded. Has anyone got this little trick to work in Hoary, and if so, how?[/QUOTE]I wouldn't exactly call it a trick, but the latest hoary artwork is a trick of some sort. I can still make the gnome-main-menu anything I want in all other icon themes but the new Human. I haven't clue why. There's nothing special about the new pkg or theme, that I can see, that would cause this, so I'm baffled. Guess I'll have to use another Icon theme now, eh?

---

### Post by NeoChaosX on 2005-04-06
[QUOTE=bvc]I wouldn't exactly call it a trick, but the latest hoary artwork is a trick of some sort. I can still make the gnome-main-menu anything I want in all other icon themes but the new Human. I haven't clue why. There's nothing special about the new pkg or theme, that I can see, that would cause this, so I'm baffled. Guess I'll have to use another Icon theme now, eh?[/QUOTE]
Probably. And how'd you do the main menu icon change? I copied the icon I wanted as "/usr/share/pixmaps/gnome-main-menu.png" but the icon doesn't change after a killall gnome-panel or login in Hoary. Should I copy it to a different directory, or a different filename?

---

### Post by bvc on 2005-04-06
[QUOTE=NeoChaosX]Probably. And how'd you do the main menu icon change? I copied the icon I wanted as "/usr/share/pixmaps/gnome-main-menu.png" but the icon doesn't change after a killall gnome-panel or login in Hoary. Should I copy it to a different directory, or a different filename?[/QUOTE]

$THEME/scalable/apps/gnome-main-menu.svg
or png

I tried it from an iconrc in a gtk theme and it doesn't work with Human either. In fact, none of my gtk themes will set the menu icon from their iconrc :-x 
If this is not a bug and means they are trying to fix more stock icons, whoohoo!!! great!!! I'll be patient because stock icons are currently a mess and needs fixed!

---

### Post by wfx on 2005-04-07
Brown version:
[http://www.deviantart.com/deviation/16953270/](http://www.deviantart.com/deviation/16953270/)
and the blue version of ubutton:
[http://www.deviantart.com/deviation/16952912/](http://www.deviantart.com/deviation/16952912/)

to use the icons do:
cp gnome-logo-icon-transparent.svg /usr/share/pixmaps/gnome-logo-icon-trans parent.svg
cp gnome-main-menu.svg /usr/share/icons/hicolor/scalable/apps/g nome-main-menu.svg
killall gnome-panel (or logout and in)

---

### Post by bvc on 2005-04-07
stilll no worky with the new Human Icon Theme

---

### Post by wfx on 2005-04-07
i use gnome, 
does human use different names for the icons?

---

### Post by trygvebw on 2005-04-07
[QUOTE=wfx]i use gnome, 
does human use different names for the icons?[/QUOTE]
 The themes .gtkrc file is probably overriding it.

---

### Post by bvc on 2005-04-07
[QUOTE=wfx]i use gnome, 
does human use different names for the icons?[/QUOTE]
there's is nothing of the sort in the Human Icon Theme :???: 

[QUOTE=trygvebw] The themes .gtkrc file is probably overriding it.[/QUOTE]Doesn't matter what gtk theme. If I am using the Human Icon theme the menu icon in a gtk theme doesn't work, but does if another icon theme is being used :???:

---

### Post by Jad on 2005-04-07
Ok thank you guys 
I've lost my gnome foot icon :(

---

### Post by basse1989 on 2005-04-07
To change my gnome menu icon to a nice ubuntu logo I put the icon into /usr/share/pixmaps/gnome-logo-icon-transparent.png

I hope that helps. :)

---

### Post by Jad on 2005-04-07
worked
Thanks

---

### Post by bvc on 2005-04-08
this is fixed in the final Hoary :grin:

---

### Post by NeoChaosX on 2005-04-08
[QUOTE=wfx]Brown version:
[http://www.deviantart.com/deviation/16953270/](http://www.deviantart.com/deviation/16953270/)
and the blue version of ubutton:
[http://www.deviantart.com/deviation/16952912/](http://www.deviantart.com/deviation/16952912/)

to use the icons do:
cp gnome-logo-icon-transparent.svg /usr/share/pixmaps/gnome-logo-icon-trans parent.svg
cp gnome-main-menu.svg /usr/share/icons/hicolor/scalable/apps/g nome-main-menu.svg
killall gnome-panel (or logout and in)[/QUOTE]
When I try to download them, I view a text file instead.  :|

---

### Post by wfx on 2005-04-08
[QUOTE=NeoChaosX]When I try to download them, I view a text file instead.  :|[/QUOTE]
Oh yes, now it should work (have change it to a tar.bz2 archiv type)

---

### Post by NeoChaosX on 2005-04-08
I'm noticed for some reason, instead of *filename*.tar.bz2, DeviantArt is changing it to *filename*_tar.bz2, which is where it's going wrong. Renaming it to .tar.bz2 gets it working, though.  :-)  Excellent icon.

---

