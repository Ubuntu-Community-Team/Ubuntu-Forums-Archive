---
title: "ubuntu is great but...."
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Angry penguin on 2007-02-26
Ubuntu is a great operating system. I have been using it since Warty and have been extremely pleased with the progress. There are only 2 or 3 things that are really holding me back from going 100% Ubuntu (still have an XP partition for gaming).

1. My 5 button mouse doesn't work outta the box. I would settle for easily configureable. I have done the 5 button mouse howto and have managed to get my forward/back buttons to work in firefox, and in the past managed to get them working in nautilus also, somehow. But even when they worked in those two apps, they didn't work in my games (CS:S). This is the only reason I haven't deleted winbloze.

Howto for 5 buttons:
[http://ubuntuforums.org/showthread.php?t=3828](http://ubuntuforums.org/showthread.php?t=3828)

2. Easy management of multiple X-sessions. When playing games in Ubuntu, it would be nice to be able to easily manage Xsessions so that I can run a game on one and my desktop on the other. Yes I know, there is a howto for that. But I just got beryl working the way I want it, my desktop the way I want it and when I saw the dpkg-reconfigure xserver-common command, I became quite leery of what might happen to my xserver I have painstakenly taken the time to configure. 

Here's the thread in question:
[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

3. What is with the icons for the system being scattered all over the freaking OS? Why cant the gnome project stick all the icons for the window manager in 1 spot? I know this isn't Ubuntu's fault but can't we use some of our pull in the open source community to make this happen? When I was making a launcher for my home folder, I had a hell of a time tracking down the Home folder icon that was included with my icon pack. I ended up just copying the icon i wanted from the tar pack to a directory and pointing to it.

What triggered this rant? I just spent the entire weekend tweaking my desktop, installing doomsday, creating launchers for my games that are installed, reinstalling beryl because it freakin broke the last time I updated it, setting up a dock, tracking down and replacing icons...etc.

Anyway, thanks for listening, I'll attach some screens for your viewing pleasure, thanks for your patience, I had to get that out of my system.

[[IMG]http://img176.imageshack.us/img176/6388/final21024wz4.th.png[/IMG]](http://img176.imageshack.us/my.php?image=final21024wz4.png)

[[IMG]http://img377.imageshack.us/img377/108/final31024ab7.th.png[/IMG]](http://img377.imageshack.us/my.php?image=final31024ab7.png)

---

### Post by UltimaDude on 2007-02-26
You know you can move icons around.

---

### Post by Tomosaur on 2007-02-26
The directory structure takes a little gettting used to, but it makes sense once you're passed the initial confusion. It's better to have icons from different things all mixed together, because that way - it's easier for other apps to take advantage of these icons, and it's easier for you to find ones you like without going through a billion different directories. It's different from Windows, yes - but Windows is based on the idea of a monolithic design - everything is provided by the manufacturer - whereas Linux is based on a modular, extendable design. This encourages co-operation, sharing, and drives down costs (in both time and money). Now that you know where those icons are - your job is done. In Windows, I have to search through loads of different places on the system to build up a 'set' of files I want to use. In Linux, I just 'know' where a particular kind of file will be.

---

### Post by StarscreamD on 2007-02-26
I totally agree with number two. X server is really difficult to configure for beginners. Add into the fact that I use an NVIDIA card(extra configuration), an onboard video card that is automatically assumed the primary video card by Ubuntu install, and with this new sexy beryl technology about(but man, is it finicky!), it's a minefield. I spent most the weekend fixing my X server due to a simple beryl install script. Noooo! :lolflag:

---

### Post by Marious on 2007-02-26
Hey angry what themes you got going there, I see Amarok, beryl just wondering what else you got there. And the Mac Os X at the bottom, I could not get it going for nothing when I tried it which one you use? Oh and the temp. one on the bottom right I seen that before and I like to get it, where can I find it? And I know what you are saying  about the mouse I have a Kensington mouse and I only got two buttons working plus the Scroller, And beryl lol I broke it, Probably have to reinstall it.

---

### Post by Angry penguin on 2007-02-26
Perhaps I wasn't clear enough about the icons. As far as I can tell icons for the OS(home folder, drive icons,...etc) are located in the following places.

/usr/lib/firefox
/usr/share/pixmaps
/usr/share/app-install
/usr/lib/python/2.5/idlelib
/usr/local/share
/usr/share/icons
...etc...

my question is....why can't all the icon folders just have the same parent directory? SO, there is one place to go for icons For example: stick all icon folders, eg. firefox, nautilus, gimp, devces, gnome, in /usr/share/icons/?

Maybe im just a n00b and don't know anything, but this proposal seems logical to me.

---

### Post by Angry penguin on 2007-02-26
> **Marious said:**
> Hey angry what themes you got going there, I see Amarok, beryl just wondering what else you got there. And the Mac Os X at the bottom, I could not get it going for nothing when I tried it which one you use? Oh and the temp. one on the bottom right I seen that before and I like to get it, where can I find it? And I know what you are saying  about the mouse I have a Kensington mouse and I only got two buttons working plus the Scroller, And beryl lol I broke it, Probably have to reinstall it.


Let's see here, I'm using an emerald theme, since I'm using the emerald theme manager that comes with beryl. The theme I'm using is called empty skies.

The dock at the bottom is a gdesklet called starterbar. I like this one better than the gnome-dock because it doesn't use up as much resources and isn't laggy, and also because it doesn't take up any screen area when you maximize a window. It has a hide/unhide hotkey.

The temp monitor monitors the temp over the last 24 hours and is also a gdesklet, believe it is called temp, in the misc category.

Generally speaking, I am pretty pleased with my setup considering I have beryl running smooth on a Athlon XP 2600+ 1 gig kingston hyperex ram and an nvidia 6200 agp. :)

*sips tea*

---

### Post by bodhi.zazen on 2007-02-26
Hey angry - You know you can configure different servers for X and run multiple X sessions.

Take a look at these two threads :

[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

[http://www.ubuntuforums.org/showthread.php?t=271674](http://www.ubuntuforums.org/showthread.php?t=271674)

/bodhi.zazen ~ drinks coffee

---

### Post by Angry penguin on 2007-02-26
> **bodhi.zazen said:**
> Hey angry - You know you can configure different servers for X and run multiple X sessions.

Take a look at these two threads :

[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

[http://www.ubuntuforums.org/showthread.php?t=271674](http://www.ubuntuforums.org/showthread.php?t=271674)

/bodhi.zazen ~ drinks coffee

Just to clarify, my goal here is to have a launcher for each game on my desktop as I do right now. Upon clicking the launcher, that launches a new xserver without a window manager or anything, just the game and will allow me to toggle back and forth between my game and desktop. Is that what the second link there show you how to do?

---

### Post by bodhi.zazen on 2007-02-26
Yep.

You will need to write the server and the start command.

Something like

startx <start game> -- :1 -layout <new server name>

The scripts should give guidance ;)

---

### Post by Tomosaur on 2007-02-26
> **Angry penguin said:**
> Perhaps I wasn't clear enough about the icons. As far as I can tell icons for the OS(home folder, drive icons,...etc) are located in the following places.

/usr/lib/firefox
/usr/share/pixmaps
/usr/share/app-install
/usr/lib/python/2.5/idlelib
/usr/local/share
/usr/share/icons
...etc...

my question is....why can't all the icon folders just have the same parent directory? SO, there is one place to go for icons For example: stick all icon folders, eg. firefox, nautilus, gimp, devces, gnome, in /usr/share/icons/?

Maybe im just a n00b and don't know anything, but this proposal seems logical to me.

The normal directories are /usr/share/icons and /usr/share/pixmaps.

/usr/share/icons is normally reserved for theme icons (ie - folders, devices, menus etc)
/usr/share/pixmaps is normally reserved for actual application icons, such as firefox, gaim, whatever.

Occasionally yes, these do get a bit mixed up - there's no real convention for it - it's more or less up to the software creator, and for many developers - they just don't concern themselves with this kind of thing.

You can, however, do the following:
```

sudo slocate -u
slocate *.png

```

The first line builds up an index of everything on your system. The second one finds all files in the .png format. You can alter it of course - if you wanted to find all firefox files with extensions, you could type:
```

slocate firefox.*

```

Not a perfect solution, but there's probably a million ways of doing this kind of thing.

---

### Post by Luk0r on 2007-02-26
This is pretty unrelated to your questions, but how did you get your Beryl thumbnals looking so smooth and nice? I think it might be because your card supports anti-aliasing or something, but then again I'm pretty sure mine does too.

---

### Post by Angry penguin on 2007-02-27
I didn't have to do anything to get my thumbnails the way they are, lucky me I guess. I heart nVidia. I haven't really played with beryl a whole lot yet, just enough to figure out where everything is at now with the new settings manager, so everythings pretty much default.

---

### Post by Bagboy23 on 2007-02-27
If only things were easy to configure, i.e. there was one prime location for all desktop modifications like a control centre and you could save the settings with an option of import/export.

I've made so many changes that I'm not sure I could honestly work them all out again, nor do I have the patience for it all.

---

### Post by Angry penguin on 2007-02-27
By the way, after getting everything just the way I wanted it yesterday, I killed the xsession and logged back in. Boy was that a mistake, beryl started screwing with my gdesklets, it started placing them in differnt spots on my desktop, then it got to the point where gdesklets wouldnt even start if beryl was running. So i ended up getting rid of my my desklets :(  I did find a stellar system monitor that I absolutely love, (conky). But,I miss my animated dock. Now I am just going to have to settle for this stagnant, simple taskbar-made-to-look-like-a-dock.....dock. Being that resources are kinda scarce, I guess it's for the better. So now it looks like this...

[[IMG]http://img183.imageshack.us/img183/1252/screenshotrq9.th.png[/IMG]](http://img183.imageshack.us/my.php?image=screenshotrq9.png)

EDIT: I agree with you bagboy, I think having the ability to save all this hard work I have put into this desktop quickly and easily would help alot. I feel that I am apprehensive when it comes to messing with my OS for fear I will screw something up so badly that I will have to reinstall. In that event, all of my work would be lost. Or if something should warrant a reinstall, like for instance dist-upgrade fails miserably like it did on my dapper>edgy upgrade, then you could just import your previous settings and done. Anymore, I'm pretty good about recognizing commands that are dangerous and figuring out how to undo what I am about to do in the event that something goes catastrophically wrong. This practice has saved my bacon more than once in the past.

---

