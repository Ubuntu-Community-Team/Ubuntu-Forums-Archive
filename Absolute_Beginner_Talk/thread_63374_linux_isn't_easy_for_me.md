---
title: "linux isn't easy for me"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by X5-655 on 2005-09-07
i am having a hard time with linux.  im not fond of a command line, unless it's DOS (as that's what i grew up with.)

also, I noticed that in linux, installing an app is a timefull task, where in windows or Mac OS X, you just double click the installer, where in Linux, I have to mostly do it from a command line, and sometimes I even have to MAKE the installer...

isn't there an easy way?  like just being able to double click an installer and it automatically run?

---

### Post by mlomker on 2005-09-07
If you are running the I386 version then there's often .deb files available and they're easy to install.  I assume you've found Synaptic or apt-get from the command line?  RPM's are the Red Hat version of a .deb file and they can often be converted to a .deb using the **alien** command-line program.

In order to stay up with the latest and greatest you'll be compiling stuff, no doubt.  Windows costs money and linux doesn't--that's why it's easier to use.  Free doesn't mean better...linux is just different and I'm finding it intellectually challenging to learn.  Then again, I'm a Windows system administrator that has gotten bored...I certainly wouldn't recommend linux to someone that simply wants to get their work done.  Stick to Windows XP Pro for that...it's a great operating system.

---

### Post by X5-655 on 2005-09-07
[QUOTE=mlomker]If you are running the I386 version then there's often .deb files available and they're easy to install.  I assume you've found Synaptic or apt-get from the command line?  RPM's are the Red Hat version of a .deb file and they can often be converted to a .deb using the **alien** command-line program.

In order to stay up with the latest and greatest you'll be compiling stuff, no doubt.  Windows costs money and linux doesn't--that's why it's easier to use.  Free doesn't mean better...linux is just different and I'm finding it intellectually challenging to learn.  Then again, I'm a Windows system administrator that has gotten bored...I certainly wouldn't recommend linux to someone that simply wants to get their work done.  Stick to Windows XP Pro for that...it's a great operating system.[/QUOTE]
so if I download a .deb file, I have to install it from the command line?  i don't see why I can just double click it though..

also, does .deb mean that Ubuntu uses Debian Linux packages?

and yes, I used the apt-get command.   I was throwing a lot of those earlier, just to get an MP3 to play, and a DVD too...

---

### Post by xequence on 2005-09-07
[QUOTE=X5-655]so if I download a .deb file, I have to install it from the command line?  i don't see why I can just double click it though..

also, does .deb mean that Ubuntu uses Debian Linux packages?

and yes, I used the apt-get command.   I was throwing a lot of those earlier, just to get an MP3 to play, and a DVD too...[/QUOTE]

Ubuntu can install .deb packages, yes.

You mean you cant just double click it? MEPIS lets you right click and choose install for .deb files... Though mepis didnt really work for me.

There is a thread somewhere here explaining why linux doesent have files like .exe, I dont know where.

I think someone told me in the next version of ubuntu (released in october) will have the feature where you double click, or right click (and choose install) to install .deb files.

---

### Post by Lambert on 2005-09-07
linux is different and it will take a little getting used to if you're willing to give it a chance.

You will want to read these about installing programs. synaptic is a front end for the command line apt-get. It's not double click install but it's fairly easy.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AptGetHowTo](https://wiki.ubuntu.com/AptGetHowTo)

wiki.ubuntu.com and [www.ubuntuguide.org](www.ubuntuguide.org) are good places to spend some time if you hang in there and give linux/ubuntu a chance.

---

### Post by Wolki on 2005-09-07
[QUOTE=X5-655]so if I download a .deb file, I have to install it from the command line?  i don't see why I can just double click it though..

also, does .deb mean that Ubuntu uses Debian Linux packages?

and yes, I used the apt-get command.   I was throwing a lot of those earlier, just to get an MP3 to play, and a DVD too...[/QUOTE]

Ubuntu uses the debian file format (basically) but they are not always compatible since both release at different times.

You can't easily install .debs because of sceurity concerns. Normal users should find nearly everything in Synaptic. Installing software there is a lot easiar than it is in Windows, and a lot faster, espeically if you want to install several programs.

---

### Post by wvslkr on 2005-09-07
System>Administration>Synaptic Package Manager

There should be very few packages you have to download individually.  Just make sure all of your repositories are enabled.

See the guide it is your friend.[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Wolki on 2005-09-07
[QUOTE=xequence]I think someone told me in the next version of ubuntu (released in october) will have the feature where you double click, or right click (and choose install) to install .deb files.[/QUOTE]

Not likely, for a variety of reasons.

If you want that fuctionality, look here:

[http://www.ubuntuforums.org/showthread.php?t=33584](http://www.ubuntuforums.org/showthread.php?t=33584)

---

### Post by aysiu on 2005-09-07
Synaptic Package Manager is your friend.

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

---

### Post by X5-655 on 2005-09-07
is there a way to throw multiple commands?  for example, when I had to install Xine, just to watch my Star Wars DVD, I had to throw a lot of SUDO commands for all the codecs first.

is there a way to just throw them all at once?  cause I ended up doing them one at a time, which took too much time for me..

---

### Post by X5-655 on 2005-09-07
i also noticed, that after installing all those codecs with all those SUDO commands, on one of my systems (in which i didn't install xine, just codecs), I cant even load Totem Movie Player anymore...  after loading a file into Totem, it justs closes, with no error messages or anything..

im feeling more and more tempted to switch back to Windows..

---

### Post by aveline on 2005-09-07
[QUOTE=X5-655]is there a way to throw multiple commands?  for example, when I had to install Xine, just to watch my Star Wars DVD, I had to throw a lot of SUDO commands for all the codecs first.

is there a way to just throw them all at once?  cause I ended up doing them one at a time, which took too much time for me..[/QUOTE]
 using synaptic allows you to do that alot easier... just tag your packages you want & if there are dependencies it will sort them out, like apt-get does, then search for more packages & click the install now or whatever button it is. hehe

aveline

---

### Post by X5-655 on 2005-09-07
[QUOTE=aveline]using synaptic allows you to do that alot easier... just tag your packages you want & if there are dependencies it will sort them out, like apt-get does, then search for more packages & click the install now or whatever button it is. hehe

aveline[/QUOTE]
how do i enter a certain location though?  for example, the ubuntu guide is full of terminal commands, but i don't know a thing about linux, and don't know how to enter that into synaptics...

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=X5-655]is there a way to throw multiple commands?  for example, when I had to install Xine, just to watch my Star Wars DVD, I had to throw a lot of SUDO commands for all the codecs first.

is there a way to just throw them all at once?  cause I ended up doing them one at a time, which took too much time for me..[/QUOTE]

This is my favorite thing about using hte command line over synaptic. You CAN do this easily. I'll lead by example. Lets say I want to install abiword, xcompmgr, rox, gxine and bittornado. I would do it this way:


> sudo apt-get -f install bittornado rox gxine xcompmgr abiword

One space between each for as long as you want. Form the guide just copy and paste the last word. Then hit enter when you are done.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=X5-655]i also noticed, that after installing all those codecs with all those SUDO commands, on one of my systems (in which i didn't install xine, just codecs), I cant even load Totem Movie Player anymore...  after loading a file into Totem, it justs closes, with no error messages or anything..

im feeling more and more tempted to switch back to Windows..[/QUOTE]

Not yet please. We have MANY good media players....Totem is kinda weak. Try this:

> sudo apt-get install vlc gxine

Vlc and Gxine. Please don't leave because of a media player, we have many of those.

---

### Post by X5-655 on 2005-09-07
[QUOTE=poofyhairguy]Not yet please. We have MANY good media players....Totem is kinda weak. Try this:



Vlc and Gxine. Please don't leave because of a media player, we have many of those.[/QUOTE]
i just entered the command you told me to do, for VLC, and it froze at 84% at one of the packages..  the computer responds, and the terminal has the blinking cursor, but the download just stopped, completely...

actually, as typing this, it now just said "Connection timed out", yet the internet is working on it fine, im typing this to you on it..

doesn't seem to work for me..   now, is there a way to cancel this before it installs something that doesnt even have all the packages?

---

### Post by GreyFox503 on 2005-09-07
[QUOTE=X5-655]i am having a hard time with linux.  im not fond of a command line, unless it's DOS (as that's what i grew up with.)

also, I noticed that in linux, installing an app is a timefull task, where in windows or Mac OS X, you just double click the installer, where in Linux, I have to mostly do it from a command line, and sometimes I even have to MAKE the installer...

isn't there an easy way?  like just being able to double click an installer and it automatically run?[/QUOTE]

There are a lot of threads on this forum discussing the command-line as a user interface and the reason why linux doesn't have the equivalent of an .exe.

---

### Post by Wolki on 2005-09-07
[QUOTE=X5-655]doesn't seem to work for me..   now, is there a way to cancel this before it installs something that doesnt even have all the packages?[/QUOTE]

ctrl-c will stop things in a terminal.

If your connection times out it might be that the server is a little overloaded. Just try again a little later.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=X5-655]i just entered the command you told me to do, for VLC, and it froze at 84% at one of the packages..  the computer responds, and the terminal has the blinking cursor, but the download just stopped, completely...
[/QUOTE]

Sorry. What I should have said is search for "vlc" and "gxine" in synaptic. Its was very insensitive to not tell you the GUI way. 

Too bad you did not wait til Breezy to covert, it will have a very nice installing program. Till then, just please use synaptic.

---

### Post by X5-655 on 2005-09-07
[QUOTE=poofyhairguy]Sorry. What I should have said is search for "vlc" and "gxine" in synaptic. Its was very insensitive to not tell you the GUI way. 

Too bad you did not wait til Breezy to covert, it will have a very nice installing program. Till then, just please use synaptic.[/QUOTE]
i have no idea what breezy is..  i just download the .iso to the Ubuntu i was linked to from the front site..

is Breezy a new version of Ubuntu?  if so, can I easily upgrade to Breezy from my current installation, without having to completely reinstall?  (don't want to loose settings and stuff)

---

### Post by Gary Powers on 2005-09-07
Breezy will be the next release of Ubuntu, due in October, but you probably don't want to go there yet.  I have been on it for about five days and just realized that I had not gone back to Hoary since installing it.

BTW, I just tried out the "add/remove programs" installer that "Poofy" mentioned to install Adobe Reader and it worked perfectly.  Nice!  Actually, I prefer the command line, but whatever floats your boat.  Stick around.  It gets easier.

Gary

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=X5-655]
is Breezy a new version of Ubuntu?  if so, can I easily upgrade to Breezy from my current installation, without having to completely reinstall?  (don't want to loose settings and stuff)[/QUOTE]

Breezy is the next version that will be released in about a month (its been in development for half a year).

When it comes, you can very easily upgrade. Very easy. Most settings saved if you want.

I would personally wait for at least the preview release (due any day) before switching.

---

### Post by Wolki on 2005-09-07
[QUOTE=X5-655]is Breezy a new version of Ubuntu?  if so, can I easily upgrade to Breezy from my current installation, without having to completely reinstall?  (don't want to loose settings and stuff)[/QUOTE]

Exactly, and yes you can. I would wait until it's released though, while it's getting stable it's not perfect yet. It'll be released on (if I remember correctly) October 13th.

Last release (hoary) got delayed a few days (2 or 3 I guess) so it could include some bugfixes to gnome, but it should definitely release very close to that date. Instructions on how to update will also be available then.

[edit] too late again ^^;;

---

### Post by X5-655 on 2005-09-08
i just tried installing an updated version of Firefox, and was surprised there was a double-clickable installer, and it ran just like how I was used to, it was an SH file...  :)

though, it seems I have to make a new version of Firefox, as if I can't replace the old one that came with Ubuntu..

also, I did try add remove programs, but on my two computers, get stuck here, showing nothing, and no HD activity..

---

### Post by Wolki on 2005-09-08
[QUOTE=X5-655]i just tried installing an updated version of Firefox, and was surprised there was a double-clickable installer, and it ran just like how I was used to, it was an SH file...  :)[/quote]

you don't need to do that, the Firefox with Ubuntu should be up to date (it may still show the old number, but all security fixes - everything that's been in the ff releases - are included). Installing firefox manually is not a big problem (used to do that a lot) but it might cause headache with Ubuntu updates.

In general, I recommend for new users to install everything with synaptic. These versions are tailored for Ubuntu, and pretty much guaranteed to work. Everything esle can introduce new bugs, and make life for those helping you a little harder.

> also, I did try add remove programs, but on my two computers, get stuck here, showing nothing, and no HD activity..

Add/remove programs isn't worth anything in Hoary. Wait for Breezzy, where it's a great tool. There has been a lot of development on this component lately.

---

### Post by tonysathre on 2005-09-08
i have read about a new program coming out in the next few months called autopackage that lets you just click on a .deb or .tar.gz/bz2 file and it will install itself

---

### Post by Wolki on 2005-09-08
[QUOTE=tonysathre]i have read about a new program coming out in the next few months called autopackage that lets you just click on a .deb or .tar.gz/bz2 file and it will install itself[/QUOTE]

No, autopackage is used to install software in it's own format ("autopackage"). It's already here so you can use it todayif you want; a lot of distro developers don't like autopackage however, so I wouldn't hope on getting it included in Ubuntu soon.

There are also other ideas for new ways of installing software like [ZeroInstall](http://zero-install.sourceforge.net/) or [Klik](http://klik.atekon.de/) 

Installing debs with a right click is here: [http://www.ubuntuforums.org/showthread.php?t=33584](http://www.ubuntuforums.org/showthread.php?t=33584)

And installing from source with a right click probably won't be possible for quite some time, as that is a really complex task that probably would need a portage-like system in Ubuntu to track dependencies.

---

### Post by Kyral on 2005-09-08
I'm just gonna throw my two cents in.

There is one thing that ALL Potential Converts are going to have to realize. [b]This isn't Windows and things aren't done the Windows way!

[/b]This is a whole new way of doing things. And its gonna seem hard. But think back to when you started using Windows, wasn't it hard at first? But then you learned how to do things and it became easier. Same thing with Linux. You are going to have to learn a new way of doing things. We will make it easier and help you learn, but you ultimately have to make an effort to learn and read guides and whatnot.

Of course the opposite is true. If I was forced to go back to XP right now, I would have a hard time. I'm used to "throwing commands" to get things to work and to install stuff. Hell I was working on a Windows machine the other day and jabbed Scroll Lock (my keymap to the Terminal) and sat dumbfounded for a second as to why the terminal wasn't appearing.

And honestly, compiling can get ***ugly. ***Don't do it unless you absolutely have to. I'm an intermediate level user and I still dislike compiling and the possibility of Dependacy Hell (Try compiling E17 from CVS and you'll see). So sit back, soak in our vast amounts of Linux Knowledge, and hope that you to will one day be able call yourself a Linux Guru.

</rant>

Wow, that was more like a dollar and change...

Now for me to be helpful :P

For Totem to work it needs a backend. GStreamer is default, but GStreamer sucks like you wouldn't believe. So use the Xine backend. Install totem-xine using whatever method. Then it should work. But VLC does own like you wouldn't believe. Just make sure you have the right sound output plugin installed. Just do a search for VLC and it will be something like vlc-plugin-whatever.

Oh and why we all tell you commands, its because its easier to type out "sudo apt-get install package" then to type "Go to System -> Admin -> Synaptic and check blah blah". Also it allows you to just cut and paste into the terminal.

---

### Post by X5-655 on 2005-09-08
ok, synaptic won't even work for me now, it says some error message about repositories not being available..

and the reason i wasn't happy about it being easy to use, was because both Windows and Mac I quickly understood, and second, i'm autistic...

---

### Post by Kyral on 2005-09-08
[QUOTE=X5-655]ok, synaptic won't even work for me now, it says some error message about repositories not being available..

and the reason i wasn't happy about it being easy to use, was because both Windows and Mac I quickly understood, and second, i'm autistic...[/QUOTE]
Okay, one note. Saying your autistic means nothing to me, 'cause I have ADHD, OCD, and Asbergers Syndrome and I still function (relatively)normally in society. And don't use it as an excuse either 'cause that will make me insta-flame you to hell, because I hate people who do that with a passion

---

### Post by Wolki on 2005-09-08
[QUOTE=X5-655]ok, synaptic won't even work for me now, it says some error message about repositories not being available...[/QUOTE]

Either you made a typo in your sources.list or the server are down. If it's the first, remove them and add them again (for example using synaptic's repository management), if it's the second wait a little until they're up again or try a different mirror.

---

### Post by X5-655 on 2005-09-08
[QUOTE=Kyral]Okay, one note. Saying your autistic means nothing to me, 'cause I have ADHD, OCD, and Asbergers Syndrome and I still function (relatively)normally in society. And don't use it as an excuse either 'cause that will make me insta-flame you to hell, because I hate people who do that with a passion[/QUOTE]
yea, i have asberger syndrome too, but for me, it makes me extremely slow at understanding things I don't really want to learn, which here for example, is command lines...  called selective learning, and in this case, is making me not even want to use Linux, as I prefer an operating system that runs totally on a GUI level..

---

### Post by Kyral on 2005-09-08
I knwo all about selective learning. Ask my Calculus professors :P

---

### Post by Wolki on 2005-09-08
[QUOTE=X5-655]called selective learning, and in this case, is making me not even want to use Linux, as I prefer an operating system that runs totally on a GUI level..[/QUOTE]

I think we've provided you with GUIs for every task you told us you want to do. When it's not possible yet people will provide you with something you can just copy and paste so you won't have to learn anything. (tip: selecting copies and middle click pastes, makes it much faster). People here are trying to help you, and they tend to be very supportive; it's the spirit of Ubuntu. However, we can't do anything without some good will.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=X5-655]yea, i have asberger syndrome too, but for me, it makes me extremely slow at understanding things I don't really want to learn, which here for example, is command lines...  called selective learning, and in this case, is making me not even want to use Linux, as I prefer an operating system that runs totally on a GUI level..[/QUOTE]

Thats called "SUSE 9.3"

Has more GUIs than Windows 2K....

---

### Post by X5-655 on 2005-09-08
[QUOTE=Wolki]I think we've provided you with GUIs for every task you told us you want to do. When it's not possible yet people will provide you with something you can just copy and paste so you won't have to learn anything. (tip: selecting copies and middle click pastes, makes it much faster). People here are trying to help you, and they tend to be very supportive; it's the spirit of Ubuntu. However, we can't do anything without some good will.[/QUOTE]
i know, but some of the GUIs I am supposed to use, fail to even run..

for example, synaptics failed to do anything earlier, and out of the clear blue, just went and worked out of nowhere...

luckily, someone in my A+ certification course is a Ubuntu user, and walked me through a little today..

---

### Post by Wolki on 2005-09-08
[QUOTE=X5-655]i know, but some of the GUIs I am supposed to use, fail to even run..

for example, synaptics failed to do anything earlier, and out of the clear blue, just went and worked out of nowhere...[/QUOTE]

If such a thing happens, you can always ask. I've never had a problem with synaptic in nearly 3/4 of a year in Ubuntu. One thing that can help is starting a program from the commandline (in this case "gksudo synaptic")  because it will then show you error messages. People here or on the IRC Channel will walk you through everything if you ask nicely.

---

### Post by X5-655 on 2005-09-08
ok, here's a good question for you all ;)

my father just installed Ubuntu on his PC 2 days ago, and would like to use his TV tuner on it.

his tuner is an ATI All-in-wonder, with the Rage 128 Pro chipset.  is there a easy way to do this?

---

### Post by Wolki on 2005-09-08
[QUOTE=X5-655]my father just installed Ubuntu on his PC 2 days ago, and would like to use his TV tuner on it.

his tuner is an ATI All-in-wonder, with the Rage 128 Pro chipset.  is there a easy way to do this?[/QUOTE]

Can't really help you here. From some googling it seems like there is project working on TV-In drivers for All-in-Wonders. It might work already, but I doubt it's easy. Try asking in the hardware forums, maybe someone has an answer/experience with that card. Not everyone reads all posts in a long thread on the new users forum :)

[edit] [http://gatos.sourceforge.net/supported_cards.php](http://gatos.sourceforge.net/supported_cards.php) claims it should work. Not sure how to set it up though. Like i said, maybe you'll have better luck in the hardware forums.

---

### Post by r_a_trip on 2005-09-09
I have read all the posts in this thread and it took some patience to do (a thing I very much lack, especially when encountering the typical "I have hands, but I want you to wipe my butt" syndrome).

One question kept reoccuring to me. Why, in the name of the Goddess, do you want to use GNU/Linux X5-655? 

You want it easy.  You keep "threatening" to go back to Windows. You keep hammering on a total GUI concept.

It makes me reach the conclusion that GNU/Linux is simply not your cup of tea. Contrary to what the stereo-typical view of GNU/Linux fans is, I won't try to keep you from going back to Windows. It seems that Microsoft can provide you with an OS that meets your needs.

We GNU/Linux users sometimes forget in our enthusiasm for GNU/Linux, that not all people are enthralled with the limitless possibilities of GNU/Linux. We love GNU/Linux for the Freedom and the abundance of choice it brings.

All those neat options come at a price however. You need to be willing to accept total noob status in the beginning and you must be absolutely willing to gain more computing knowledge. If this willingness is absent, forget about GNU/Linux. 

GNU/Linux will never show its golden qualities if you are not willing to learn its ways and eventually its intricacies and idiosyncrasies. Being able to cope with choice requires knowledge.

No matter how much the community works at making the future ultimate, no-brainer, narrow and limited eternal noob interface, that requires no thinking or learning whatsoever, it will fail. Because GNU/Linux is riddled with choice and alternatives.

Sooner or later the "eternal noob" will discover the multi-faceted nature of GNU/Linux and he will want it all, but as all "eternal noobs" he will want it without learning anything whatsoever. This wanting to eat your cake and have it too will always haunt GNU/Linux.

A vast army has been trained into accepting a computing world in which everybody is "condemned" to the same limited computing environment as everybody else. These people are so accustomed to have the same what everybody has, that they will always assume that everything in a computing environment should be equally available to them, regardless of the fact that it may not suit their needs or even that they don't need everything that the Goddess has under the sun.

---

