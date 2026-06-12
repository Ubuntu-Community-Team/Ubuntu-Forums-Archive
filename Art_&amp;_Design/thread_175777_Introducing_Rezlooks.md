---
title: "Introducing Rezlooks"
date: 2006-05-13
forum: Art &amp; Design
---

### Post by Gnobody on 2006-05-13
[LEFT]Rezlooks is a gtk theme engine based on the cairo-enabled CVS clearlooks engine code.   It looks prettier and is a lot faster than Clearlooks CVS too!

You can learn more @ [http://www.gnome-look.org/content/show.php?content=39179]("http://www.gnome-look.org/content/show.php?content=39179")


I have made an Ubuntu 6.06 .deb and an archive full of themes, they are both in the attachments to this thread -->

***Fixed package***
[/LEFT]

---

### Post by IYY on 2006-05-13
Cool!

---

### Post by Rotarychainsaw on 2006-05-14
This is pretty cool. Been a while since I used an animated clearlooks. Is there anyway to get the ubuntulooks scrollbar and rezlooks everything else? that would be ideal I think.

---

### Post by Gnobody on 2006-05-14
[LEFT]Not without motifiying the Clearlooks source style.c, and essentially creating a new theme engine.
[/LEFT]

---

### Post by bvc on 2006-05-14
Sure you can. Put this
```
style "theme-scrollbar"
{
engine "ubuntulooks" {
   }
}
class "GtkScrollbar" style "theme-scrollbar"
```

just before
```
# widget styles
class "GtkWidget" style "theme-default"
class "GtkButton" style "theme-button"
class "GtkCombo"  style "theme-button"
class "GtkRange"  style "theme-wide"
class "GtkFrame"  style "theme-wide"
class "GtkMenu"   style "theme-menu"
class "GtkEntry"  style "theme-button"
class "GtkMenuItem"    style "theme-menu-item"
class "GtkStatusbar"   style "theme-wide"
class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "GtkCheckButton" style "theme-check"
class "GtkRadioButton" style "theme-check"
```

I don't get this engine to be honest. Why not use the smooth engine which is so much faster? Unless you actually like a mix of gradient and solid widgets for some reason. The original square hack of clearlooks was great and would have went much further than this. He got code edit happy and killed it :(

---

### Post by Rotarychainsaw on 2006-05-14
Hey BVC thanks, that worked. Looks pretty OK lol. Where should I be looking to get new engines? Gnome-look doesnt seem to include the engines... Or maybe I'm not looking right.

---

### Post by bvc on 2006-05-14
[QUOTE=Rotarychainsaw]Hey BVC thanks, that worked. Looks pretty OK lol. Where should I be looking to get new engines? Gnome-look doesnt seem to include the engines... Or maybe I'm not looking right.[/QUOTE]Creation of new engine are rare. [a.g.o.]("http://art.gnome.org/themes/gtk_engines/") post some but as you can see, you have them all except maybe eXperience which I think used to be in the apt repos but... Someone needs to create a real pixmap engine but gtk has so many limitaions no one wants to write an engine for 2 years, and I don't blame them.

---

### Post by Rotarychainsaw on 2006-05-14
Ohh, I thought there were a lot more out there. Basically I just want the animated clearlooks, with the ubuntulooks scrollbar, and maybe some other little things. Is it possible to create a theme using bits and pieces from all different engines like you just showed me a few posts up?

Also, isn't there a super animated clearlooks out there? Like tabs are animated and stuff like that?

---

### Post by bvc on 2006-05-14
[QUOTE=Rotarychainsaw]Ohh, I thought there were a lot more out there. Basically I just want the animated clearlooks, with the ubuntulooks scrollbar, and maybe some other little things. Is it possible to create a theme using bits and pieces from all different engines like you just showed me a few posts up?

Also, isn't there a super animated clearlooks out there? Like tabs are animated and stuff like that?[/QUOTE]
Many are installed by default. Others can be found in the repos (search gtk2-engines). Most are just variants of something else. Smooth
[http://gnome.org/~thos/Smooth-Docs/](http://gnome.org/~thos/Smooth-Docs/)
was the first original engine and is very flexible, then came Clearlooks. Everytthing else is pretty boring.

Yes, you could use a diff engine for every widget if you want to.

I know nothing about a super animated clearlooks.

---

### Post by ComplexNumber on 2006-05-14
most engines are usually included.
according to my install list, all(AFAIK) the engines are:
rezlooks
bluecurve(wonderland)
anachron
experience
crux
dwerg
lighthouse blue
clearlooks
cleanice
industrial
smooth
xfce
ubuntulooks

---

### Post by Gnobody on 2006-05-15
I updated the package to ver. 0.3.1

---

### Post by brainkilla on 2006-05-17
I've just seen 0.4... could you provide an update? Thank you.

---

### Post by Gnobody on 2006-05-17
[LEFT]It's in the first post now.
[/LEFT]

---

### Post by rezza on 2006-05-21
[QUOTE=bvc]I don't get this engine to be honest. Why not use the smooth engine which is so much faster? Unless you actually like a mix of gradient and solid widgets for some reason. The original square hack of clearlooks was great and would have went much further than this. He got code edit happy and killed it :([/QUOTE]

I didn't write this for you to "get". I wrote this because it is what I wanted. Why not use the smooth engine? Because it doesn't do what I want it to do. Also bear in mind that this is an ongoing project... I'm gradually making more and more elements fit with the idea I have in my head. People expressed an interest in the engine from my screenshots so I released it while I was still working on it.

You are of course welcome to take my original hack of clearlooks and run with it - hell, package it up and call it bvclooks if you like, doesn't bother me :P

---

### Post by bvc on 2006-05-22
little late......
look at the date........05-14-2006

When I wrote that it was much different than now and was very much like a cairo smooth engine. As I have said at gnome-look I very much like the changes and where it's going, so what is the purpose of your post? Doesn't make any sense and is not in sync, with the follow up post. If you have a bone to pick you'll have to look elsewhere.[QUOTE=bvc May 17 2006 at gnome-look]At first, I was dissapointed that this was not like your square hack of clearlooks. Which I'd still like to see as it's own engine named Rezlooks, so people can easily change between them. But now, I like where this is going and what you have done with the buttons. Do you plan to unify the other widgets (scrollbars etc..) to match? Then separate it with its own name, since it's not much related anymore?

Good work!
Thank you![/QUOTE]

---

### Post by rezza on 2006-05-22
[QUOTE=bvc]little late......
look at the date........05-14-2006

When I wrote that it was much different than now and was very much like a cairo smooth engine. As I have said at gnome-look I very much like the changes and where it's going, so what is the purpose of your post? Doesn't make any sense and is not in sync, with the follow up post. If you have a bone to pick you'll have to look elsewhere.[/QUOTE]

Hmm, no bones to pick, I was answering those questions because I didn't want to leave them unanswered here. I know you have since commented on gnome-look ;)

---

### Post by bored2k on 2006-05-22
Cute. Definitely trying it out on the next linux box I get my hands on.

And which music player is that (on the glook screenshot)? Reminds me of muine, but it didn't look that way when i used it.

---

### Post by rezza on 2006-05-22
[QUOTE=bored2k]Cute. Definitely trying it out on the next linux box I get my hands on.

And which music player is that (on the glook screenshot)? Reminds me of muine, but it didn't look that way when i used it.[/QUOTE]

That's gmpc from svn ([https://svn.musicpd.org/gmpc/trunk)](https://svn.musicpd.org/gmpc/trunk)).

---

### Post by pain of salvation on 2006-06-14
0.5 is out! [http://www.gnome-look.org/content/show.php?content=39179&PHPSESSID=20b2e43f61c6e083d71e376200557797](http://www.gnome-look.org/content/show.php?content=39179&PHPSESSID=20b2e43f61c6e083d71e376200557797)

Can someone make a .deb with this one?

---

### Post by pain of salvation on 2006-06-15
I tried:

./configure
make
sudo make install

But I can't get the theme working..

Then I tried:

./configure --prefix=/usr
make
sudo make install

But I still only get the old default gtk engine..

May someone help me installing this theme?

---

### Post by ComplexNumber on 2006-06-15
when you tried it with ./configure (without the --prefix=/usr), did you uninstall it afterwards? if not, please do so. 

this is the correct way:
>  ./configure **--prefix=/usr**
make
sudo make install it has to go into /usr rather than /usr/local, otherwise it won't work.

---

### Post by pain of salvation on 2006-06-15
When I do 'make',I get this error in the end:

[COLOR="Red"]make: ** [librezlooks.la] Erro 1[/COLOR]

---

### Post by bvc on 2006-06-15
use at your own risk
[http://kwh.kernow-gb.com/~bvc/theme/not_mine/rezlooks-0.5.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/not_mine/rezlooks-0.5.tar.gz)
animation enabled

---

### Post by jozmak on 2006-06-15
The theme is good but i have one serious problem with it, the color scheme. The warm yellowish beige and the blue slider just don't go together. For those either chose a warm or a neutral color.

J. Mak
[http://jozmak.googlepages.com/](http://jozmak.googlepages.com/)

---

### Post by bvc on 2006-06-16
I like the candy color scheme
[http://kwh.kernow-gb.com/~bvc/wp/?p=31](http://kwh.kernow-gb.com/~bvc/wp/?p=31)
...made a metacity for rezlooks

---

### Post by raptxt on 2006-06-16
i just downloaded and installed the .deb package attached to this thread and it says it is now installed succesfull, but nothing happens.
how can i activate rezlooks on my ubuntu dapper?
thank you!

---

### Post by bvc on 2006-06-17
I have made 5 nm156 metacity versions now.
[http://kwh.kernow-gb.com/~bvc/wp/?p=31](http://kwh.kernow-gb.com/~bvc/wp/?p=31)
-light/dark
-gtkrc base and metacity>bg[SELECTED]
-thin/wide(dark)

little something for everyone

---

### Post by L2wis on 2006-06-20
[QUOTE=raptxt]i just downloaded and installed the .deb package attached to this thread and it says it is now installed succesfull, but nothing happens.
how can i activate rezlooks on my ubuntu dapper?
thank you![/QUOTE]

I've also just downloaded and installed and not noticed any changes. Could anyone point me in the right direction?

---

### Post by bvc on 2006-06-21
use at your own risk
[http://kwh.kernow-gb.com/~bvc/theme/not_mine/gtk2-engines-rezlooks-0.6.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/not_mine/gtk2-engines-rezlooks-0.6.tar.gz)
*animation enabled

---

### Post by IbeeX on 2006-06-25
I made

./configure --prefix=/usr
make
sudo make install

and still i con't find theme istalled?

I have 6.06 amd64 version ?

---

### Post by Nonno Bassotto on 2006-06-25
Sorry if I'm a bit off-topic, but what actually IS an engine?

---

### Post by bvc on 2006-06-25
[QUOTE=IbeeX]I made

./configure --prefix=/usr
make
sudo make install

and still i con't find theme istalled?

I have 6.06 amd64 version ?[/QUOTE]
well without the posting of errors there not much we can say. Did this not work?
[QUOTE=bvc]use at your own risk
[http://kwh.kernow-gb.com/~bvc/theme/not_mine/gtk2-engines-rezlooks-0.6.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/not_mine/gtk2-engines-rezlooks-0.6.tar.gz)
*animation enabled[/QUOTE]

---

### Post by bvc on 2006-06-27
[nm156]("http://gnomethemes.org/?p=31") has been [updated]("http://gnomethemes.org/forum/index.php?topic=46.0")

---

### Post by samoht on 2006-06-28
This theme is great! Thanks!

---

### Post by ostkaka on 2006-07-31
The download link is broken, can someone fix it? I realy like this theme :)

---

### Post by saracen on 2006-08-06
Ok ladies and gents, i've created a deb for rezlooks 0.6.  It's gzipped so use the archive manager or gunzip from the command line to extract the deb from inside.  

I've also attached a couple of themes based on the rezlooks engine.  First install the .deb and then install the themes as you normally do (e.g. using System->Preferences->Themes).

---

### Post by phlexy on 2006-09-04
Uh oh, help! 

I'm pretty new to this stuff hehe. 

I tried sudo dpkg -i rezlooks-0.6_0.6-1_i386.deb but terminal returns: 
(Reading database ... 82819 files and directories currently installed.)
Unpacking rezlooks-0.6 (from rezlooks-0.6_0.6-1_i386.deb) ...
dpkg: error processing rezlooks-0.6_0.6-1_i386.deb (--install):
 trying to overwrite `/usr/lib/gtk-2.0/2.4.0/engines/librezlooks.la', which is also in package rezlooks-0.4

I tried installing rezlooks-0.4_0.4-1_i386, and I presume all I have to do is remove all the files I installed through that (that right?)

Help appreciated.

---

### Post by Genix on 2006-10-15
Anyone have a .deb for amd64?

---

### Post by ChaKy on 2006-10-16
> **phlexy said:**
> Uh oh, help! 

I'm pretty new to this stuff hehe. 

I tried sudo dpkg -i rezlooks-0.6_0.6-1_i386.deb but terminal returns: 
(Reading database ... 82819 files and directories currently installed.)
Unpacking rezlooks-0.6 (from rezlooks-0.6_0.6-1_i386.deb) ...
dpkg: error processing rezlooks-0.6_0.6-1_i386.deb (--install):
 trying to overwrite `/usr/lib/gtk-2.0/2.4.0/engines/librezlooks.la', which is also in package rezlooks-0.4

I tried installing rezlooks-0.4_0.4-1_i386, and I presume all I have to do is remove all the files I installed through that (that right?)

Help appreciated.

Yes, just first uninstall rezlooks-0.4 and after that install rezlooks 0.6. It seems that the first package rezlooks-0.4 was build with checkinstall and somebody named the package "rezlooks-0.4" and not "rezlooks" as it should be. So now, you are trying to install rezlooks 0.6 which is in conflict with another rezlooks package named "rezlooks-0.4".

---

### Post by mooey on 2006-10-20
deb attached for 0.6 on edgy. the deb is inside the archive, as I can't attach debs directly :-k

---

### Post by cb951303 on 2006-11-08
I installed rezlooks-0.6 and rezlooks-graphite
it works perfectly. But with root applications like synaptic there is no theme. It's just plain gtk without a theme nor engine.

Anyone knows a workaround?

PS: Other engines work great with root apps too...

---

### Post by d_fens on 2006-11-17
sudo ln -s /home/username/.themes /root/.themes
sudo ln -s /home/username/.icons /root/.icons
sudo ln -s /home/username/.fonts /root/.fonts

---

### Post by Zyphrexi on 2007-01-04
yeah all local stuffs you install w/o root privileges get installed into home and aren't read during sudo/gksudo app execution.

---

### Post by sha_man on 2007-02-02
can anyone please post a good .deb for amd64 (edgy). thanks :D

---

### Post by dbbolton on 2007-08-13
it seems that the edgy deb works on feisty, but has anyone made a feisty deb?

---

