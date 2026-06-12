---
title: "New To Ubuntu"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by dave--k on 2006-08-11
Hey guys, i just got Ubuntu installed yesterdat and im pritty sure i did it right :D

but i was wondering, what basic apps do i need?

Currently i need something to play Music (MP3/WMA) and something to play videos (WMA/AVI/MOV) and i need to know how to istall them too

thanks a bunch :)

---

### Post by louis_nichols on 2006-08-11
Man, you got yourself in trouble with this post. :) :p

That's because you are likely to get soooo many answers that you won't be able to process it all. :D That's because for most of the usual tasks, there ar e many ways and apps available, and everyone will tell you their opinion and favourites. In the end, it will be a matter of just making your own, which probably means that you'll have to try them all.

Now, for media I use amarok (with the xine engine - that's another story, the engines part) because I like the media library. If you are a fan of winamp, you might want xmms or beep-media-player (now evolving to BMPx, but the beta is a bit unstable), but neither of them have a decent media library.
As for movies, I use Totem, because it's simple, also with a xine engine. Other apps are: mplayer, vlc, Juk and so on and so forth.

The main issue, though, is the codecs one. Some codecs are proprietary and might involve legal issues in some countries, which is why they aren't easily available. Anyway... I use xine engines because almost everything works with it, without too much hassle.

---

### Post by dave--k on 2006-08-11
> **louis_nichols said:**
> Man, you got yourself in trouble with this post. :) :p

That's because you are likely to get soooo many answers that you won't be able to process it all. :D That's because for most of the usual tasks, there ar e many ways and apps available, and everyone will tell you their opinion and favourites. In the end, it will be a matter of just making your own, which probably means that you'll have to try them all.

Now, for media I use amarok (with the xine engine - that's another story, the engines part) because I like the media library. If you are a fan of winamp, you might want xmms or beep-media-player (now evolving to BMPx, but the beta is a bit unstable), but neither of them have a decent media library.
As for movies, I use Totem, because it's simple, also with a xine engine. Other apps are: mplayer, vlc, Juk and so on and so forth.

The main issue, though, is the codecs one. Some codecs are proprietary and might involve legal issues in some countries, which is why they aren't easily available. Anyway... I use xine engines because almost everything works with it, without too much hassle.

yay a reply :D

So, i will try Amarok and Totem.

but, what files to download? im using XP cos i cant get wireless on Ubuntu yet :( so i have to download on XP, then reboot to Linux and get the files.

So, where do i get the files and how do i install?:razz:

---

### Post by louis_nichols on 2006-08-11
oh... that will not be so easy, unfortunatelly...

That's because each app comes with dependencies. Unlike in windows, in Linux apps don't come with all included, to avoid having duplicates of the same libraries on your system.

So... Totem will be a package called [totem-xine]("http://packages.ubuntu.com/dapper/gnome/totem-xine") and amarok will be.. well, [amarok]("http://packages.ubuntu.com/dapper/kde/amarok"), but will also need [amarok-xine]("http://packages.ubuntu.com/dapper/kde/amarok-xine") and a long list of other dependencies, because it uses a KDE gui. Now, packages and deps are all listed on [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") but I sincerely doubt you'd be able to track down all deps and download the packages. So, you're quite likely better off installing [beep-media-player]("http://packages.ubuntu.com/dapper/sound/beep-media-player"), whose deps are mostly already installed.

Anyways... you download the debs from the links, store them somewhere and then, to install them, you boot ubuntu, open a terminal window, navigate to where they are stored and enter the command:

```
sudo dpkg -i *package-name1 package-name2* ...
``` (without dots, but with as many packages as you like).

Now, if you were able to connect to internet with Ubuntu, it would be MUCH easier, as deps are handled automatically. A good place to start on these matters (i.e. beginner stuff) are the [help page]("http://help.ubuntu.com"), of which most is already listed under System>Help (I STRONGLY recommend you read the info there, as it is an excellent place to start understanding Ubuntu) and [the wiki]("http://wiki.ubuntu.com"). Specifically, a page about installing apps if [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html")

---

### Post by dave--k on 2006-08-11
> **louis_nichols said:**
> oh... that will not be so easy, unfortunatelly...

That's because each app comes with dependencies. Unlike in windows, in Linux apps don't come with all included, to avoid having duplicates of the same libraries on your system.

So... Totem will be a package called [totem-xine]("http://packages.ubuntu.com/dapper/gnome/totem-xine") and amarok will be.. well, [amarok]("http://packages.ubuntu.com/dapper/kde/amarok"), but will also need [amarok-xine]("http://packages.ubuntu.com/dapper/kde/amarok-xine") and a long list of other dependencies, because it uses a KDE gui. Now, packages and deps are all listed on [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") but I sincerely doubt you'd be able to track down all deps and download the packages. So, you're quite likely better off installing [beep-media-player]("http://packages.ubuntu.com/dapper/sound/beep-media-player"), whose deps are mostly already installed.

Anyways... you download the debs from the links, store them somewhere and then, to install them, you boot ubuntu, open a terminal window, navigate to where they are stored and enter the command:

```
sudo dpkg -i *package-name1 package-name2* ...
``` (without dots, but with as many packages as you like).

Now, if you were able to connect to internet with Ubuntu, it would be MUCH easier, as deps are handled automatically. A good place to start on these matters (i.e. beginner stuff) are the [help page]("http://help.ubuntu.com"), of which most is already listed under System>Help (I STRONGLY recommend you read the info there, as it is an excellent place to start understanding Ubuntu) and [the wiki]("http://wiki.ubuntu.com"). Specifically, a page about installing apps if [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html")

well, i got Beep-Media-Player which was good, but i like the looks of Amarok

So, you said 'to install them, you boot ubuntu, open a terminal window, navigate to where they are stored and enter the command:'

OK, i booted Linux and opened a Terminal Windows but what do you mean by 'navigate to where they are stored' you mean open the folder that they are in or what?

sorry about all this im just new to all  of this :P

---

### Post by Ambimom on 2006-08-11
A lovely person named mathewv shared this with me yesterday and I'll pass it on to you. This is what you need to do to load codecs.....the best part is that it worked!


[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Learning is frustrating, but it's also fun when you finally understand.

---

### Post by macca87 on 2006-08-11
Yeah the link above is what helped me.
Also, check out [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper), it has lots of useful instructions to set up stuff. :)

---

### Post by dave--k on 2006-08-11
Ok, im gonna work on that soon or tomorrow.

but first, i urgently need my Wireless setup because its a pain in the rear to try and work on XP.

i have a Belkin High-Speed Mode Wireless G USB Network Adaptor.

i need Wireless, anyone help me on this?

---

### Post by louis_nichols on 2006-08-11
> **dave--k said:**
> well, i got Beep-Media-Player which was good, but i like the looks of Amarok

So, you said 'to install them, you boot ubuntu, open a terminal window, navigate to where they are stored and enter the command:'

OK, i booted Linux and opened a Terminal Windows but what do you mean by 'navigate to where they are stored' you mean open the folder that they are in or what?

sorry about all this im just new to all  of this :P


Well, commands that I write in source code window are entered in a terminal window. So you open the application "terminal" from the menu, type in the text I wrote and press enter. It's best to get used to the terminal, because most of the advice you will get on these forums involves a certain amount of using the terminal. Coming from windows, it seems strange but, although not believable at first, there are tasks easier done at the command line than with a GUI. It would be a good idea to google around for most common Unix terminal commands and maybe store a local copy, so you have them handy in case you need them. Of course, instructions for any command can be found by typing *man command-name* in a terminal window (or the search bar from System>Help>System help, or at least I think this is the name - I'm not at the box right now) but to do this you first have to know they exist. :)

Going on to "navigating" to where the files are, what I meant was: in a terminal window, use the command *cd directory-name* to go to the directory where the files are saved.

As for amarok, it does look pretty cool but, as I said, I wouldn't recommend trying to install it without an internet connection, in which case the procedure is different and much simpler.. No! I mean MUUUUCH SIMPLER than the one I've described so far. :) 

Now, one thing that is quite likely to happen in your case is that you try installing with dpkg -i and it will complain about some missing package. You just have to download that too, store it in the same place and then try installing them in the same command.

---

