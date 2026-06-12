---
title: "just installed and cant find plugins"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-08-27
Hi i just installed the desktop and tryed to get on to pogo.com and it says i need java plugin and it wont install it i download one for linux but not sure how to install it, and and i cant get the flash plugins to work either, and also i need a plugin or something to be able to play mp3's.

Thanks

---

### Post by Jerome36 on 2006-08-27
Start reading from my first post on [this page](http://www.ubuntuforums.org/showthread.php?t=236740&page=3), for MP3 playback.

---

### Post by derred on 2006-08-27
Take a look at [www.getautomatix.com]("http://www.getautomatix.com/"). It is basicaly a script that adds all sorts of functionality to your Ubuntu/Kubuntu/Xubuntu/Edubuntu system. It also installs java runtime envitoment, firefox and plugins for it(media streaming, flash...), and all sorts of (I think) usefull things.
An alternatuve to this is [EasyUbuntu]("http://users.on.net/~goetz/EasyUbuntu/"). It does mostly the same things, and for me(in dapper not in breezy) worked better than automatix, but has less features.
Give them a go and post the results.
Best of luck.:D

---

### Post by Tasu on 2006-08-27
Well! The first step is to learn this is a different operative system, not a windows clone, things are managed in a different way, so you have to free your mind from what you may have lernt on other systems.

Ubuntu as all Debian derivatives uses packages that are held in some repositories, first of all, if you are using ubuntu over kubuntu or xubuntu, is to enable multiverse and universe repositories, go to:

System->Administration->Package Manager Synaptic

Then open Settings->Package Repositories:

Click on the Add button.

Click on custom.

Paste this string in it: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Accept all the ok buttons, etc...

Click on the first button on the left: Refresh

When finished, search for a package called automatix.

Now you have in icon in your menus calle Automatix, if you launch it, you will be presented with an aesy wai ti add codecs, common loved programs, etc... Please select all the options you need, automatix will do the rest for you! ^_^

You are done, with wmv, mp3 and all that rpoprietary scum! ^_^

On the main site of the project you can find tons of infos on automatix! ^_^

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Bye! ^_^

P.S. as time goes by, you will find the power of this package management, it comes really handy to have an interface that looks for you for all the programs you can install, the magic will be adding the repos you need, and you will be always sure to find  what you need, automatix adds a lot of useful repos for you, making the first step easy, now you have just ot learn more, if you want.

---

### Post by zombietls on 2006-08-27
i copyed that link like you said and it said that it failed

---

### Post by zombietls on 2006-08-27
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---------------------------------------AND-----------------------------------

The following problems were found on your system:
E: Type 'http://www.getautomatix.com/apt' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by Bachstelze on 2006-08-27
Don't forget to paste the 'deb ' before the URL :)

---

### Post by zombietls on 2006-08-27
i still keep getting the same thing

E: Type 'http://www.getautomatix.com/apt' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

were is the repository dialog at ??

---

### Post by rcatman on 2006-09-17
Just go to [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)
and follow the installation steps. :) This worked great and i had all my favorite radio streams and dvds playing in ubuntu. Joy.

---

