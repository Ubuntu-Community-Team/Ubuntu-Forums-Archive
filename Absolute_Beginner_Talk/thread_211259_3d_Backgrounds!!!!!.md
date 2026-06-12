---
title: "3d Backgrounds!!!!!"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-08
Alrite, 
one of the reasons i switched to Linux is for the 3d moving backgrounds

I am using Dapper Drake 6.06 Ubuntu Linux

How do i go about getting a 3D background.
Not a screensaver, but a background!

---

### Post by MetalMusicAddict on 2006-07-08
Where did you see this? Its possiable with Enlightenment I believe.

> Alrite,
one of the reasons i switched to Linux is for the 3d moving backgrounds
And if thats you reason for switching I fear you going to be dissapointed.

---

### Post by woedend on 2006-07-08
you can do it with xwinwrap but its a huge waste of resources.

---

### Post by IrishGangsta on 2006-07-08
my friend uses Debian and said he got snow with a simple apt-get xsnow command

Or something along those lines.

Is it pointless to try for a 3D background with ubuntu?

---

### Post by woedend on 2006-07-08
any moving 3d backgroun is pointless.  its cool for about 10 minutes, then gets to be a b*tch when your computer slows down.

---

### Post by raldz on 2006-07-08
it seems you like a decorative desktop.. how about using widgets? looks cool when your desktop is showing.. try "gdesklets" for Ubuntu and "superkaramba" for Kubuntu.. then try to install different themes.. looks nice..

---

### Post by IrishGangsta on 2006-07-08
ok i installed gdesklets but where are they located and how do i use them?

---

### Post by raldz on 2006-07-08
just execute "gdesklets" from the terminal or run dialog box if you can't find it from the Accesories menu.. it will run on your system tray.. open it and just add "themes" or desklets to your dekstop.. some nice desktlets includes system infos, calendars, notes, weather, feeds reader.. there tons in there..

---

### Post by mcduck on 2006-07-08
'sudo apt-get install xsnow xpenguins' and then start them from a terminal with 'xsnow' or 'xpenguins'

---

### Post by richbarna on 2006-07-08
You've also got 3D desktop in the repositories :-
> "Three-dimensional" desktop switcher
3D-Desktop is an OpenGL program for switching virtual desktops in
a seamless 3-dimensional manner.  The current desktop is mapped into a
fullscreen 3D environment where you may choose other screens.  Several
different visualization modes are available.  A window manager
compatible with the GNOME pager standard is required.

The transition from working desktop to fullscreen 3D environment is
seamless: when the pager activates you see your current desktop appear
to zoom out to a point in space where you can see your other virtual
desktops allowing you to select another.

The program is rather memory-hungry and it is CPU intensive, but it's
accessible from the command line, which makes it perfect for show
floors and impressing your non-UN*X-using friends. 
Or from the terminal:-
> sudo apt-get install 3ddesktop

---

### Post by Spleenie on 2006-07-08
xdesktopwaves is reasonably cool too, not to mention a bit easier on system resources. Although I must second (or third? dunno lost count) the above sentiments ie why have dynamic desktops when all the fun to be had is away from the desktop?

Swish

---

### Post by IrishGangsta on 2006-07-08
well thanks for all the input guys
Yes i noticed 3D Desktops last night and its pretty kool
But i do like the falling penguins and snow, but is there anyway to keep it there?

I mean, when i close the terminal the penguins dissapear.  Can i make it so the penguins dont stop!!?

thanks

---

### Post by Perfect Storm on 2006-07-08
You could try make it so that it's starting up everytime you turn on Ubuntu.

System tab ---> preferences ---> Sessions

Start up tab. Fill in the command.

---

### Post by testube_babies on 2006-07-08
HA!  Those penguins are hilarious!  Thank you so much.

---

### Post by IrishGangsta on 2006-07-08
What i would like to have is like i saw a kool desktop image for slackware Linux

And i want something like that and make the water move and stuff

Does anyone know where i can find a cool desktop background with animation?

---

### Post by Perfect Storm on 2006-07-09
> **IrishGangsta said:**
> What i would like to have is like i saw a kool desktop image for slackware Linux

And i want something like that and make the water move and stuff

Does anyone know where i can find a cool desktop background with animation?

Perhaps this: [http://ubuntuforums.org/showthread.php?t=112333](http://ubuntuforums.org/showthread.php?t=112333)

---

### Post by mcduck on 2006-07-11
I'm using XGL and xwinwrap to run the GLSlideshow screensaver as my wallpaper, with slow panning&zooming and even slower fading, browsing through my collection of +300 wallpaper images.. It looks absolutely amazing, and with good settings it doesn't even take too much resources (less than running gDesklets..)

And you can run any screensaver that way, or even several at the same time. Or you can make the screensaver run *above* your desktop; flying toasters screensaver is pretty cool this way, altough not something you would want to have always running.

But XGL doesn't work with every machine around, and it's still a bit hard to get running, so you mifgt want to familiar with Ubuntu&Linux before you try that..

---

### Post by IrishGangsta on 2006-07-11
> **Artificial Intelligence said:**
> Perhaps this: [http://ubuntuforums.org/showthread.php?t=112333](http://ubuntuforums.org/showthread.php?t=112333)

Yes, i actually have this.
It is pretty cool but it uses alot of resources.
It makes my CPU usage 100% when it is running. 

I am in the process of install XGL/Compiz
I hope that i will get it to work out alrite.

Thanx for the suggestion tho

---

### Post by Blondie on 2006-07-12
Xgl water effects are cool. If you have problems getting xgl to work, and aren't doing so already I would recommend the howtos on the compiz boards.
[http://www.compiz.net/viewforum.php?id=5](http://www.compiz.net/viewforum.php?id=5)

For example
[http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652)
for Nvidia cards on Ubuntu Dapper.

---

### Post by eoghanmurray on 2007-07-31
Compiz Fusion is what you should install. See [http://www.fusioncast.blogspot.com](http://www.fusioncast.blogspot.com) for more. It's a merge of Compiz and Beryl - so you can make it rain on your desktop, or make water drop from your cursor, you have wobbly windows, desktop cube, fire on screen (you can write with fire :D ) and more. It's actually quite easy to get working under XGL and ATi. Even easier is vVidea.

---

### Post by ethana2 on 2007-08-02
I hope that's what you tell windows users.  "Don't bother switching, the superiority wears off."

As a person fully aware of the fact that it will "wear off" and consume processing power...
(Compiz fusion user)
I submit a refined question:

How do I force xscreensaver and mplayer/other to replace nautilus in drawing my desktop?
Surely some desktop managers directly support such functionality(in real time)?
-(icons are but clutter to me anyway, and I want the memory nautilus occupies)

If CPU time will be a factor (If I'm not satisfied with a dynamic 2d screenhack), how do I limit cpu usage by applications?  Come to think of it, it would be nice to cap Firefox at 50% as well...

This general functionality should be good for anyone.  If anyone has succinct answers, I suspect the author of this thread, as well as myself, would appreciate them greatly.

If there is no current elegant solution, please teach me how to code so I can change that.  I need a mentor who knows what's important towards learning C/Python.  Print references are of no use to me now.  (I don't need another thing to move up to Alaska with me this fall.)  I would like to learn to code even if there is such solution, to bring open source gaming up to spec via open frag.  (Encouraging trem dev and nexiuz to port to it would be a _huge_ step in the right direction... but I'd like to have the power to port them myself.)

Have a good day.

---

### Post by mcduck on 2007-08-02
> **ethana2 said:**
> I hope that's what you tell windows users.  "Don't bother switching, the superiority wears off."

As a person fully aware of the fact that it will "wear off" and consume processing power...
(Compiz fusion user)
I submit a refined question:

How do I force xscreensaver and mplayer/other to replace nautilus in drawing my desktop?
Surely some desktop managers directly support such functionality(in real time)?
-(icons are but clutter to me anyway, and I want the memory nautilus occupies)

If CPU time will be a factor (If I'm not satisfied with a dynamic 2d screenhack), how do I limit cpu usage by applications?  Come to think of it, it would be nice to cap Firefox at 50% as well...

This general functionality should be good for anyone.  If anyone has succinct answers, I suspect the author of this thread, as well as myself, would appreciate them greatly.

If there is no current elegant solution, please teach me how to code so I can change that.  I need a mentor who knows what's important towards learning C/Python.  Print references are of no use to me now.  (I don't need another thing to move up to Alaska with me this fall.)  I would like to learn to code even if there is such solution, to bring open source gaming up to spec via open frag.  (Encouraging trem dev and nexiuz to port to it would be a _huge_ step in the right direction... but I'd like to have the power to port them myself.)

Have a good day.

Just remove Nautilus from your session in System/Preferences/Session,and add command you use to start the screensaver you want with xwinwrap.

To limit the CPU usage of a program (or user!) you can use the 'nice' command. Check 'man nice' for more detailed info. Also check the manual for the screensaver you are running, many of them have built-in options that affect the CPU usage of the screensaver.

---

