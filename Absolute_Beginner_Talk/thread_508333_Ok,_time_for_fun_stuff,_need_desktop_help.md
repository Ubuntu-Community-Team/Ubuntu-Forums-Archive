---
title: "Ok, time for fun stuff, need desktop help"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-07-24
Hi again, 

 I am awaiting my Java question to get answered in the Ubuntu question forum\support thing over there , lol sorry forgot the main site but anyway, while i'm waiting , is there anyway someone could help me with a few um.. fun questions...

 1. How can I change my desktop as in, different shell? Is there KDE or something or some themes that would change the whole appearance? The gray bar reminds me of Windows 98, I would like to do away with it. I know in Fedora, I could make it clear, blue, etc.. 

 2. What suggestions for best themes\wallpapers\icons do you have? Any particular Ubuntu sites? I do graphics work myself and have used Gimp for a while, "put photo shop users to shame on occasion :) " and proud of it. :) So I can make some things myself. Of course, I would need to know how to associate the icons with my current ones if I make my own. 

3. I can't get the computer or any icons onto the desktop, at all. My desktop is lonely for at least a few. 

 [B]While this is important to me, if others need help first, please help those who are having bigger issues, thanks.
[/B]
 Paul

---

### Post by zanglang on 2007-07-24
1. If you meant replace your current desktop environment, you can install KDE (package name = 'kde') and select it when you're logging into Ubuntu. Or maybe you could try playing around with the Gnome themes? [http://gnome-look.org](http://gnome-look.org) is a good place to start out. :)

2. Again, gnome-look has some awesome Linux-themed wallpapers and stuff.

3. This requires some tweaking. Hit Alt-F2, enter 'gconf-editor', browse to /apps/nautilus/desktop. You can toggle a number of icons to show up on your desktop if you wish.

---

### Post by tact on 2007-07-24
Hey there ...   I am sure you have seen plenty of you tube or google videos where people are showing off their compiz-fusion or beryl eyecandy effects and so you know there is a LOT of very nice things you can to to change the look and feel of your system in linux generally and ubuntu specifically.

There is a thread in these forums (here...    [http://ubuntuforums.org/showthread.php?t=489082](http://ubuntuforums.org/showthread.php?t=489082) ) you should have a look at.  People post their customised desktops and generally list the names of the theme, icon set, fonts, and wallpapers etc.

I know what you mean about getting rid of the task bar at the bottom of the default desktop... it is too Windows-like and actually even in WinXP I found it limiting.  The "scale" feature in compiz-fusion and beryl is much more useful and productivity enhancing.

So I hooked up with the SVN version of Avant Window Navigator and use it now as a dock in place of the old task bar.

Looks a bit like this...

---

### Post by gimpguy2000 on 2007-07-24
Thanks all! Once again, best help here. I think even if I didn't have Ubuntu, I would come here for help, lolll. 

 I will check those links as well. I hope to make my own theme too. As far as You tube, nah, i'm not a big fan of it but my son keeps me informed even when I don't want to be. Although if anyone has seen the why you should use firefox browser , with IE going...weeeee..and the fox saying "shut up", I thought that was absolutely hilarious. 

 Back to topic, i'll do some configuring and if I have any problems, i'll be back to bug yous. 

 Thanks again

 Paul

---

### Post by RomeReactor on 2007-07-24
Hi.

1.- To change the desktop environment, you can choose to install KDE or XFCE:
```
sudo aptitude install kubuntu-desktop
```
or
```
sudo aptitude install xubuntu-desktop
```
The reason for using **aptitude** instead of **apt-get** or **Synaptic** is that, in case you later want to remove these desktop environments, you can do it like this:
```
sudo aptitude remove kubuntu-desktop
```
or
```
sudo aptitude remove xubuntu-desktop
```
Using apt-get or Synaptic to install and later uninstall the desktop package would only remove the metapackage (an empty package that calls all other needed libraries and programs for installation), but leave the actual programs installed. Using aptitude it removes everything.

**NOTE**: For anyone who installed either KDE or XFCE through apt-get or Synaptic and want to remove them, look [here]("http://www.psychocats.net/ubuntu/puregnome").

To  change the theme, go to "System->Preferences->Theme".

2,- If you want more themes, you can install **gnome-themes-extras**. Or go to [Gnome-Look]("http://gnome-look.org/"), [Art.Gnome]("http://art.gnome.org/"), or [Freshmeat]("http://themes.freshmeat.net/browse/958/").

3.- **EDIT**: **zanglang** already addressed this point.

---

### Post by dkaddict on 2007-07-24
There is loads of stuff @ Deviant Art too. As for icon associations, in Gnome, you will find any icon sets that you have installed (just drag a tar ball into the 'theme' window which you can open by 'system>preferences>theme') in your home folder in Nautilus as 'hidden' files in the '.icons' folder. The way I learnt how to change icons etc was by doing the above. G to Gnome Look, for instance, find a half decent looking icon set, install as above, and have a look at how they are named by 'system>places>home folder then clicking on 'file and 'show hidden files'.

I get most of my stuff from Deviant Art as they get uploaded there first a lot of the time. Gnome will show .png and .svg icon types but I just stick to .png 

There are 'buildset' scripts which will convert 128x128 icons in to all of the respective sizes out there. If you are not happy with basic Gnome, you can virtually have it look how you like.

Have fun m8

oh yeah, you wil need 'image magic' installed for converting. 

hope this has helped
Customizing Gnome is, some say, easier than KDE but KDE, I feel, gives the user more control. In KDE u can change the colurs of stuff really easy and with domino theme installed you can use gradients. Sorry if there is confusion but there is so much that can be done. I use Gnome mostly and have learnt how to change everything to how I want. Ask for anything else. Yo

---

### Post by dkaddict on 2007-07-24
If you want to change your panel. Make one with Gimp. Save it in a folder somewhere. Right click the existing panel and navigate to the one you made and select it. I have always used my own panel backgrounds. You will see a dialogue asking if you want to use the panel from the system theme or your own. Also, there is an app in the repositories called Gnome Colour Chooser that lets you have more control over how your desktop looks.

---

### Post by gimpguy2000 on 2007-07-24
Thanks. I am installing KDE right now as per your code, it's working great so far.  I haven't used the xfce so not sure what it's like.   I'll edit this post to let you know how it went. 

 I do have an account and such on DA, but had no idea all the other stuff existed there, i'll definately have to check it out. ! 

 There is so much to take in, really, with shifting to open source, some bad, but so much to look forward to, overwhelming amounts of software, etc...it's like early birthday presents:)

 TX

 Paul

---

### Post by gimpguy2000 on 2007-07-24
Hi all,

 Thank you so much for the help, KDE is in force and I have a decent looking system now. I am going to try the konqueror browser with java, see what happens :)

 Thanks!!

 Paul

---

### Post by Brian96 on 2007-07-24
> **gimpguy2000 said:**
> Thanks. I am installing KDE right now as per your code, it's working great so far.  I haven't used the xfce so not sure what it's like.   I'll edit this post to let you know how it went. 

 I do have an account and such on DA, but had no idea all the other stuff existed there, i'll definately have to check it out. ! 

 There is so much to take in, really, with shifting to open source, some bad, but so much to look forward to, overwhelming amounts of software, etc...it's like early birthday presents:)

 TX

 Paul

Yep, that's the double-edged sword of Linux: ENDLESS tinkering possibilities!

I've played around with the "big 4" desktop environments (Gnome [Ubuntu's default], KDE [Kubuntu's DE], Xfce [Xubuntu's DE]), and Enlightenment (do a search for E17 if you're interested) and there are really only subtle differences between them (except for E17, which is pretty different). Each is HIGHLY customizable (especially coming from Windows), and each has its drawbacks.

For example, at home I use Gnome. I've moved my panel to the side, made it bigger, made it transparent, and put only a few launchers and applets on it (as well as a task bar). At work I use Xfce with Beryl, have no panels (in Xfce you can get to a main menu by right-clicking on the desktop; this is also available in KDE), but have a clock and calendar applet on the desktop. The scale and desktop cube features in Beryl are really really cool, and really do help with productivity.

Once you get comfortable with the Linux desktop environments you can start playing around with just using a window manager. Very, very minimal, but scalable if you take the time to learn how to configure them.

A good resource that helped me get my feet wet with Ubuntu was the Ubuntu Tutorials on [www.psychocats.net](www.psychocats.net).

Anyway, have fun, and I hope you get an answer to you Java problem soon.

---

### Post by gimpguy2000 on 2007-07-24
> **Brian96 said:**
> Yep, that's the double-edged sword of Linux: ENDLESS tinkering possibilities!

I've played around with the "big 4" desktop environments (Gnome [Ubuntu's default], KDE [Kubuntu's DE], Xfce [Xubuntu's DE]), and Enlightenment (do a search for E17 if you're interested) and there are really only subtle differences between them (except for E17, which is pretty different). Each is HIGHLY customizable (especially coming from Windows), and each has its drawbacks.

For example, at home I use Gnome. I've moved my panel to the side, made it bigger, made it transparent, and put only a few launchers and applets on it (as well as a task bar). At work I use Xfce with Beryl, have no panels (in Xfce you can get to a main menu by right-clicking on the desktop; this is also available in KDE), but have a clock and calendar applet on the desktop. The scale and desktop cube features in Beryl are really really cool, and really do help with productivity.

Once you get comfortable with the Linux desktop environments you can start playing around with just using a window manager. Very, very minimal, but scalable if you take the time to learn how to configure them.

A good resource that helped me get my feet wet with Ubuntu was the Ubuntu Tutorials on [www.psychocats.net](www.psychocats.net).

Anyway, have fun, and I hope you get an answer to you Java problem soon.

Thanks for the reference, i'll definitely check into it! Yeah, so far I like some Gnome some KDE, too bad there wasn't something to take bits of each and make your own customized desktop. Although in fairness, it's close. The more people that get into open source OSs, the more support , the more that will happen for users. 

 TX

Paul

---

