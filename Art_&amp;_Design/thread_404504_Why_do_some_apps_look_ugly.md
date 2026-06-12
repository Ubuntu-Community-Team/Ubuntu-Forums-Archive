---
title: "Why do some apps look ugly?"
date: 2007-04-08
forum: Art &amp; Design
---

### Post by mech7 on 2007-04-08
Some applications i install have these really old / ugly looking interface elements? Why is this and isn't there a way to let it use the default theme?

[[IMG]http://img61.imageshack.us/img61/4381/screenshotloadfilesnr6.th.png[/IMG]](http://img61.imageshack.us/my.php?image=screenshotloadfilesnr6.png)

---

### Post by bashologist on 2007-04-08
Maybe this is a gnome app you're using in kde? Is this a program you launched with wine maybe? For me at least some gnome apps display strangely when I use kde. What is this program? Does this happen with most other programs?

---

### Post by Patrick K on 2007-04-08
I like that, i wish my load file dialogs looked that nice.

---

### Post by bashologist on 2007-04-08
It could also be the theme you're using. Maybe try another theme to check?

---

### Post by ComplexNumber on 2007-04-08
> **mech7 said:**
> Some applications i install have these really old / ugly looking interface elements? Why is this and isn't there a way to let it use the default theme?


its because you haven't got the correct theme engine installed. what particular theme is that called in the screenshot?

the chances are its because you need to install the gtk2-engines-pixbuf package.

---

### Post by feed_sparky on 2007-04-08
To me that looks like the Xmms add files dialog, but I could be wrong. What enviroment are you using it in? cause I think it was made for Xfce, so if you use it another enviroment that could cause it to look different, but again I could be wrong :)

---

### Post by mech7 on 2007-04-08
> **feed_sparky said:**
> To me that looks like the Xmms add files dialog, but I could be wrong. What enviroment are you using it in? cause I think it was made for Xfce, so if you use it another enviroment that could cause it to look different, but again I could be wrong :)

Yes it is XMMS.. but i have this also with Zend studio and Maya.. :confused:

[[IMG]http://img385.imageshack.us/img385/6663/screenshotnu8.th.png[/IMG]](http://img385.imageshack.us/my.php?image=screenshotnu8.png)

Look same weird buttons and everything 0_o

---

### Post by ComplexNumber on 2007-04-08
**mech7**
its because thoose apps(such as xmms) are using gtk1, the old gtk toolkit. current is gtk2. if you're using a theme for which there is no gtk theme and only a gtk2 theme, they wil look like that. if you go to the theme directory of the that you're using and have a look inside the directory, you will see if there is a "gtk-2.0" and a "gtk" directory. if it doesn't have the gtk directory, they will look as they do in your screenshot.

what theme are you using?

---

### Post by tom56 on 2007-04-08
Alternatively, you could install beep-media-player which is exactly the same as xmms but with the new gtk2 (meaning the open files window looks nicer)
```
sudo aptitude install beep-media-player
```

---

### Post by mech7 on 2007-04-08
> **ComplexNumber said:**
> **mech7**
its because thoose apps(such as xmms) are using gtk1, the old gtk toolkit. current is gtk2. if you're using a theme for which there is no gtk theme and only a gtk2 theme, they wil look like that. if you go to the theme directory of the that you're using and have a look inside the directory, you will see if there is a "gtk-2.0" and a "gtk" directory. if it doesn't have the gtk directory, they will look as they do in your screenshot.

what theme are you using?

I am using the clearlooks theme in feisty.. is there anyway to install the gtk1 theme ?

---

### Post by mech7 on 2007-04-08
> **tom56 said:**
> Alternatively, you could install beep-media-player which is exactly the same as xmms but with the new gtk2 (meaning the open files window looks nicer)
```
sudo aptitude install beep-media-player
```

Will beep work with streamtuner or does it have something like streamtuner? As i listen to radio allot and it is nice to find some stations :)

---

### Post by tom56 on 2007-04-08
> **mech7 said:**
> Will beep work with streamtuner or does it have something like streamtuner? As i listen to radio allot and it is nice to find some stations :)

I don't know what that is. However, if it works in xmms, then it will work in beep.

---

### Post by ComplexNumber on 2007-04-08
> **mech7 said:**
> I am using the clearlooks theme in feisty.. is there anyway to install the gtk1 theme ?
a gtk1 theme was never made for clearlooks AFAIK. i can give you a list of some themes that do have a gtk1 theme if you like?

---

### Post by mech7 on 2007-04-08
> **tom56 said:**
> I don't know what that is. However, if it works in xmms, then it will work in beep.

It is to search stations.. i want something like winamp where i can search shoutcast and add a bookmark but also play my own files.. this streamtuner asked to open things in xmms.

I looked for Beep and it seems is no longer being developed is no only BPMx which looks 'ok' but you can't even do simple things as bookmark  :(

---

### Post by Drezliok on 2007-04-08
Both BMP and XMMS are the same, BMP is build off of XMMS

Unfortunately both projects are defunct, they are both making new versions that don't use the winamp skin.

I love the Winamp Skins so I will be using BMP for a long time.

---

### Post by Xappe on 2007-04-08
audacious is another xmms/winamp clone, still alive, and still compatible with winamp2 skins...

---

### Post by ComplexNumber on 2007-04-08
xmms2 uses gtk2. its basically a gtk2 skin for xmms.

---

### Post by twiggyness2000 on 2007-04-08
this streamtuner asked to open things in xmms.

Open up Streamtuner and select ...

Edit   >   Preferences  >  Applications

See where it says "Listen to an .m3u file" and "listen to a stream" ?
Just to the right it should say xmms %q

in _both_ entries select the ```
xmms %q
``` and change it so it reads:

```
beep-media-player %q
```

This will tell Streamtuner to look at beep-media-player as it's player software instead of xmms.
This worked for me when I installed Beep.
Much luck to you

---

### Post by mech7 on 2007-04-09
ok thanks :D but is there a way to make maya look 'normal' too :D or install GTK 1 next to GTK 2 ?

---

### Post by gzed on 2007-04-09
> **mech7 said:**
> ok thanks :D but is there a way to make maya look 'normal' too :D or install GTK 1 next to GTK 2 ?

Unfortunately not.
Maya is based on Motif which is an ancient (older than GTK and QT) GUI toolkit for UNIX workstations, it was a standard on powerful UNIX workstations like SUNs and SGIs back in those days. Both SUNs and SGIs desktop environments were coded on top of Motif.
When Alias Wavefront did the Maya Linux port, they just adapted the Motif toolkit-based SGI port to Linux, that's why it looks as ancient as it's looking.
Maya has a GUI wrapper on top of the native GUI on every platform. It's licensed from a thirdly party company, you can see this when you start Maya from a terminal, there's a small text banner telling you this.
I think it's about time the company responsible for the GUI wrapper switches to something less obsolete.
I would complain to them if I was to spend the absurd amount of money they request for Maya.

---

### Post by twiggyness2000 on 2007-04-09
>  Originally Posted by mech7
ok thanks but is there a way to make maya look 'normal' too or install GTK 1 next to GTK 2?

> **gzed said:**
> Unfortunately not.
Maya is based on Motif which is an ancient (older than GTK and QT) GUI toolkit for UNIX workstations, it was a standard on powerful UNIX workstations like SUNs and SGIs back in those days. Both SUNs and SGIs desktop environments were coded on top of Motif.
When Alias Wavefront did the Maya Linux port, they just adapted the Motif toolkit-based SGI port to Linux, that's why it looks as ancient as it's looking.
Maya has a GUI wrapper on top of the native GUI on every platform. It's licensed from a thirdly party company, you can see this when you start Maya from a terminal, there's a small text banner telling you this.
I think it's about time the company responsible for the GUI wrapper switches to something less obsolete.
I would complain to them if I was to spend the absurd amount of money they request for Maya.

<learn>
[http://discussion.autodesk.com/adskcsp/thread.jspa?messageID=5508481]("http://discussion.autodesk.com/adskcsp/thread.jspa?messageID=5508481")
...So in theory (or rather historically), one wouldn't have to run Gnome or KDE to use the software, as long as you have an X-server...
Interesting, if I understand that correctly.
</learn>

---

### Post by finferflu on 2007-04-10
I actually don't think it's GTK 1 vs GTK 2 related. I've just installed Feisty, and some apps really look ugly, for example Automatix 2, or the Network Manager, I don't think they use a GTK 1 engine. 
Screenshot attached.

Any idea?

---

### Post by Xappe on 2007-04-11
> **finferflu said:**
> I actually don't think it's GTK 1 vs GTK 2 related. I've just installed Feisty, and some apps really look ugly, for example Automatix 2, or the Network Manager, I don't think they use a GTK 1 engine. 
Screenshot attached.

Any idea?

That's probably because you run those apps as the root user, and root has no fancy gtk themes set. You can set one by running 

gksudo gnome-theme-manager

---

### Post by finferflu on 2007-04-11
> **Xappe said:**
> That's probably because you run those apps as the root user, and root has no fancy gtk themes set. You can set one by running 

gksudo gnome-theme-manager
You're probably right, in fact the root theme is set to human, and when I try to run the gnome-theme-manager as root, I get the following message:

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

I don't even know what bonobo is... But I think you well spotted the problem, the only thing now is how to solve it...

Thanks :)

---

### Post by Xappe on 2007-04-11
ah, you need to run a second gnome-settings-daemon as root for that to work I guess, not a good idea. Another possible solution could be to use switch2 (gtk-theme-switch) to set the theme for root apps...

You should only use switch2 as root in your case as your user is getting the settings from gnome-settings-daemon.

---

### Post by finferflu on 2007-04-11
> **Xappe said:**
> ah, you need to run a second gnome-settings-daemon as root for that to work I guess, not a good idea. Another possible solution could be to use switch2 (gtk-theme-switch) to set the theme for root apps...

You should only use switch2 as root in your case as your user is getting the settings from gnome-settings-daemon.
But still, I don't remember doing such a thing on Edgy, everything just worked, there must be a bug or something has gone wrong...

---

### Post by Perfect Storm on 2007-04-11
If you want root apps looking exact like the rest of your theme;

```

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```

Just remove the symblinks if you don't want to use this.



I can recommend Audacious instead of xmms/xmms2/bmp/bmp+ which is still active and evolving.

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page) 
there's a repo there for Ubuntu users but it's recommenable to compile it yourself as it's an old version there for ubuntu (1.2.2) and the newest one is 1.3.2 with many improvement, bugs fixes and alot of new features.

Screenshot: [http://ubuntuforums.org/g/index.php?n=250](http://ubuntuforums.org/g/index.php?n=250)

---

### Post by ComplexNumber on 2007-04-11
> If you want root apps looking exact like the rest of your theme;or put the themes in /usr/share/themes instead of in .themes in the user's home directory.

---

### Post by finferflu on 2007-04-11
> **ComplexNumber said:**
> or put the themes in /usr/share/themes instead of in .themes in the user's home directory.
I tried with the symlink, but no joy. I guess there's some issue with bonobo (whatever that is), as mentioned before. Even though I can access the theme manager as root, I am not able to change anything since gnome-settings-daemon cannot be started. I'll just re-post the error message I get:

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Also, I think there's some problem with the session management. For example, there are no window borders if I don't manually start Beryl, and only after I start Beryl the startup apps I have set, turn up (or maybe they take a long while before turning up).

---

### Post by ComplexNumber on 2007-04-11
> I tried with the symlink, but no joy. I guess there's some issue with bonobo (whatever that is), as mentioned before. Even though I can access the theme manager as root, I am not able to change anything since gnome-settings-daemon cannot be started.because you quoted me, i'm assuming that you placed the themes in /usr/share/themes instead of the users home directory....but that didn't work.


btw have you installed kde and had it running as you main desktop at any time since the last install? that may be the problem - there is probably a qt setting that the system is still using. i can't rememebr what exactly it is, but it may be a directory called 'default' in the /usr/share/theme directory.

---

### Post by IYY on 2007-04-11
The original poster's app is GTK1, so he could find a theme that matches his GTK2 theme's colour, but it will still look blocky and ugly because that's just how the toolkit is made!

finferflu's problem is different, because the applications do use GTK2 themes (the default one, in fact), but just don't use the one that he wants. This could be fixed by making sure that gnome-settings-daemon is running.

---

### Post by finferflu on 2007-04-11
> **ComplexNumber said:**
> because you quoted me, i'm assuming that you placed the themes in /usr/share/themes instead of the users home directory....but that didn't work.


btw have you installed kde and had it running as you main desktop at any time since the last install? that may be the problem - there is probably a qt setting that the system is still using. i can't rememebr what exactly it is, but it may be a directory called 'default' in the /usr/share/theme directory.

I actually was trying to quote even the previous message, but it didn't work with the quick reply. Anyways I've only tried with the symlink, since I believe it doesn't make any difference, but as I have pointed out, the problem doesn't seem to be related to that.

As for KDE, no, I haven't installed it. The problem seems to be related to bonobo, going by exclusion.

> **IYY said:**
> 
finferflu's problem is different, because the applications do use GTK2 themes (the default one, in fact), but just don't use the one that he wants. This could be fixed by making sure that gnome-settings-daemon is running.

Exactly, now the question is: how do I make sure it's running? And as you can see, there is a bunch of problems session-related.

---

### Post by ComplexNumber on 2007-04-11
**finferflu**
the reason why i mentioned about placing themes in /usr/share/themes is that that's the only place where root can access them. if the theme that you're using is in your home directory, all root apps will be un-themed. just to show you, i've going to move of one my themes(ie vicious apple) from /usr/share/themes to .themes in my home directory. i'm then going to select  that theme, then fire up a root app such as synaptic. this is how it looks in the 1st screenshot. notice the difference between gnome-theme-manager and synaptic? just after that, i reverted back to my normal theme. notice how its now themed. the reason being is that, at that time, all my themes were in /usr/share/themes(they still are) except vicious apple.

---

### Post by finferflu on 2007-04-11
> **ComplexNumber said:**
> **finferflu**
the reason why i mentioned about placing themes in /usr/share/themes is that that's the only place where root can access them. if the theme that you're using is in your home directory, all root apps will be un-themed. just to show you, i've going to move of one my themes(ie vicious apple) from /usr/share/themes to .themes in my home directory. i'm then going to select  that theme, then fire up a root app such as synaptic. this is how it looks in the 1st screenshot. notice the difference between gnome-theme-manager and synaptic? just after that, i reverted back to my normal theme. notice how its now themed. the reason being is that, at that time, all my themes were in /usr/share/themes(they still are) except vicious apple.
Thanks a lot ComplexNumber, you're very patient :)
You were right, now it's working fine. 
So from now on I'll not install a theme through the theme manager. Even though it's kind of weird for new users, I really don't mind untarring and moving the extracted folder to /usr/share/themes.

Thanks a lot! :D

---

### Post by ComplexNumber on 2007-04-11
glad to help, as always :)

---

### Post by Zdravko on 2007-04-13
> **mech7 said:**
> Some applications i install have these really old / ugly looking interface elements? Why is this and isn't there a way to let it use the default theme?

[[IMG]http://img61.imageshack.us/img61/4381/screenshotloadfilesnr6.th.png[/IMG]]("http://img61.imageshack.us/my.php?image=screenshotloadfilesnr6.png")

Yes, this looks like XMMS. It is a terrible application. I don't know who programmed it, but its GUI is a disaster. How can even such trash enter into Ubuntu? :confused:

---

### Post by Stone123 on 2007-04-13
> **Zdravko said:**
> Yes, this looks like XMMS. It is a terrible application. I don't know who programmed it, but its GUI is a disaster. How can even such trash enter into Ubuntu? :confused:

:P I ave heard original writer of xmms (swedish ) cursing over it and calling it somewhat desaster. How it made this far in Linux is a mistery.

---

### Post by fakie_flip on 2007-05-03
I am having the same problem with this theme.

[http://www.gnome-look.org/content/show.php/Ubuntulooks-LegacyHuman?content=41394](http://www.gnome-look.org/content/show.php/Ubuntulooks-LegacyHuman?content=41394)

What should I do to get Synaptic and other apps to use the theme?

---

### Post by Perfect Storm on 2007-05-03
Read post 27 if you use downloaded theme.

---

### Post by fakie_flip on 2007-06-21
> **Artificial Intelligence said:**
> Read post 27 if you use downloaded theme.

My theme still looks ugly :(
[http://img518.imageshack.us/img518/9340/themedl4.png](http://img518.imageshack.us/img518/9340/themedl4.png)

It is supposed to look like this.
[http://gnome-look.org/content/preview.php?preview=1&id=54755&file1=54755-1.png&file2=&file3=&name=Nimbus+%28Ubuntu+and+Debian%29](http://gnome-look.org/content/preview.php?preview=1&id=54755&file1=54755-1.png&file2=&file3=&name=Nimbus+%28Ubuntu+and+Debian%29)

I got the theme from here.
[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)

---

### Post by ComplexNumber on 2007-06-21
> **fakie_flip said:**
> My theme still looks ugly :(
[http://img518.imageshack.us/img518/9340/themedl4.png](http://img518.imageshack.us/img518/9340/themedl4.png)

It is supposed to look like this.
[http://gnome-look.org/content/preview.php?preview=1&id=54755&file1=54755-1.png&file2=&file3=&name=Nimbus+%28Ubuntu+and+Debian%29](http://gnome-look.org/content/preview.php?preview=1&id=54755&file1=54755-1.png&file2=&file3=&name=Nimbus+%28Ubuntu+and+Debian%29)

I got the theme from here.
[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)

read my posts after post 27 ;)

---

### Post by fakie_flip on 2007-06-25
> **ComplexNumber said:**
> read my posts after post 27 ;)

That has nothing to do with my problem. I need to compile the library of the theme's engine into a 64 bit library. The 32 bit library is only theming programs that are 32 bit. I can't find the source code. I found a gentoo ebuild whatever that was and it had no directions at all.

---

