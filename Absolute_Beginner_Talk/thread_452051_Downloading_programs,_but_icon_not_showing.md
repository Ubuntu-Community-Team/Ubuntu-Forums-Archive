---
title: "Downloading programs, but icon not showing"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-22
I notice a lot of times I download a program from the Synaptic that the program's icon doesn't show in the Applications.  How do I get the icon to show?

---

### Post by Scunizi on 2007-05-22
There's a couple of ways to get the icon to show.  If you go to the Alacarte Menu Editor under applications and look in there you will probably see the program listed with a check mark in the box next to it.  Uncheck it and check it again.  It should now show up in the menu..  

The other way is to restart "x" which is your desktop.  This does not mean a full or soft boot of your computer but just a restart of the desktop.  That's accomplished by the Linux version of the three finger salute.  Ctrl-Alt-Backspace.  After doing that you'll have to log in again but your harddrive and other things will not stop and restart.  That's important if you're running a server later on your primary machine.

---

### Post by gunksta on 2007-05-22
That is sadly, easier said than done.

In order for an application to show in the menu it has to install a .desktop file in /usr/share/applications

You can go to this folder and look at examples and use existing .desktop files as a template to make your own. I also recommend you go to launchpad and file a bug report against the application(s) you installed that don't show in the menus. But, before you file that bug, double check in synaptic/adept that they don't install a .desktop file!

Or, you can just add the application to your menu. In KDE, right click on your K Menu. On Gnome, it's easy, and it's in your preferences, but I don't remember what it's called. Both desktops can make custom menu entries, but I still agree with you, it's a bug.

--andy

---

### Post by zvacet on 2007-05-22
> I notice a lot of times I download a program from the Synaptic that the program's icon doesn't show in the Applications.

There are two reasons for that.First is that you downloaded program wich don´t have GUI.That kind of programs you will run with terminal.Second reason is that icon doesn´t show in programs.In that case go to the system<settings>main menu>choose section in wich you want your icon to show>new item.That will create launcher and you will create one like this
1. name = name of program
2. command = clcick on search box and find executable file (most of them are in usr/bin)
3.icon =usr/share/icons or usr/share/pixmaps

---

### Post by Killtown on 2007-05-22
> **gunksta said:**
>  On Gnome, it's easy, and it's in your preferences, but I don't remember what it's called. Both desktops can make custom menu entries, but I still agree with you, it's a bug.

--andy
Tried that, generic icon appears, but program doesn't open.

---

### Post by Killtown on 2007-05-23
anybody can help?

---

### Post by gunksta on 2007-05-23
When you make a generic entry you will need some information, which is available in Synaptic.

First, open Synaptic. Then open up the program you used to create a new entry.

Use Synaptic to find the name of the application you installed. Right click on the program name and go down to properties. There should be a tab in the Properties dialog called "Installed Files". Go to it and find the name of the binary. You will know it's the binary because it's installed in something like /usr/bin/. Files that are stored in /usr/share/, /usr/lib/, /usr/etc/ are usually NOT binary files.

Once you know the name of the actual binary, you can go back and finish making your application launcher.

There should be an entry for "Command". Place the name (with EXACT Spelling and CAPITALIZATION) here. This will let your new menu entry launch the program.

Finally your new menu item needs a nice picture. You can manually select a new icon picture in GNOME's menu entry tool. Most of the icons installed with GTK / GNOME apps are stored in /usr/share/pixmaps. Look there for an appropriately named .png or .xpm file. If you don't find one, there may be one hiding in /usr/share/name_of_your_application/ and then you will have to poke around to find it.

I hope this rambling expose helps you. If you get stumped, tell us what the name of the application is and we can be more specific.

--andy

---

### Post by Killtown on 2007-05-23
> **gunksta said:**
> When you make a generic entry you will need some information, which is available in Synaptic.

First, open Synaptic. Then open up the program you used to create a new entry.

Use Synaptic to find the name of the application you installed. Right click on the program name and go down to properties. There should be a tab in the Properties dialog called "Installed Files". Go to it and find the name of the binary. You will know it's the binary because it's installed in something like /usr/bin/. Files that are stored in /usr/share/, /usr/lib/, /usr/etc/ are usually NOT binary files.

Once you know the name of the actual binary, you can go back and finish making your application launcher.

There should be an entry for "Command". Place the name (with EXACT Spelling and CAPITALIZATION) here. This will let your new menu entry launch the program.

Finally your new menu item needs a nice picture. You can manually select a new icon picture in GNOME's menu entry tool. Most of the icons installed with GTK / GNOME apps are stored in /usr/share/pixmaps. Look there for an appropriately named .png or .xpm file. If you don't find one, there may be one hiding in /usr/share/name_of_your_application/ and then you will have to poke around to find it.

I hope this rambling expose helps you. If you get stumped, tell us what the name of the application is and we can be more specific.

--andy
Ok, I tried to do that for the program "Lame" (giggle) and here is the bin name:  /usr/bin/lame

I put that in the command line, but still won't open.

And btw, where/how would a find the program using the "browse" button next to the command line?

---

### Post by Scunizi on 2007-05-23
Lame is not neccessarily a program that you run independant of any other program.  It sounds like you are trying to get your system to encode audio in an mp3 format or something similiar.  Think of lame as a configuration file or a windows dll file.  It is something that is used by the options in other programs.  If you are trying to convert mp3 in one direction or another try Ripper X.  I think it's in the repos.  If you're simply trying to play mp3, lame is not the right tool.  Audacity will also use lame to encode an audio file into mp3 format.. 

I hope this helps..  Knowing what the actual program is upfront will typically help diagnostics in the future.

---

### Post by Killtown on 2007-05-23
> **Scunizi said:**
> Lame is not neccessarily a program that you run independant of any other program.  It sounds like you are trying to get your system to encode audio in an mp3 format or something similiar.  Think of lame as a configuration file or a windows dll file.  It is something that is used by the options in other programs.  If you are trying to convert mp3 in one direction or another try Ripper X.  I think it's in the repos.  If you're simply trying to play mp3, lame is not the right tool.  Audacity will also use lame to encode an audio file into mp3 format.. 

I hope this helps..  Knowing what the actual program is upfront will typically help diagnostics in the future.
Ah I get it.  I was trying out Lame cause I wanted a program to convert .wav files to mp3 and hopefully be able to convert .ogg files to mp3 if need be.

---

### Post by Scunizi on 2007-05-23
Sounds like RipperX is what you are looking for.  It will do things "in mass".  It's in the Dapper repos so hopefully it will also be included in Feisty & edgy repos.

---

### Post by Killtown on 2007-05-23
> **Scunizi said:**
> Sounds like RipperX is what you are looking for.  It will do things "in mass".  It's in the Dapper repos so hopefully it will also be included in Feisty & edgy repos.
That program looks like it just for ripping CDs.  I'm looking for something to convert existing audio files, specifically convert .ogg to .mp3.

---

### Post by Scunizi on 2007-05-23
Sorry.. you're right.. check out [http://viiron.googlepages.com/](http://viiron.googlepages.com/).  This is a perl program so I'm not sure if it will work on gnome or only kde.  The download section does have a debbian install package...  Looks like just what  you need.

---

### Post by Killtown on 2007-05-23
> **Scunizi said:**
> Sorry.. you're right.. check out [http://viiron.googlepages.com/](http://viiron.googlepages.com/).  This is a perl program so I'm not sure if it will work on gnome or only kde.  The download section does have a debbian install package...  Looks like just what  you need.
Do you know which file is the one I should down?  

It listed a ton of files:  [http://linuxappfinder.com/debian/pool/main/p/pacpl/](http://linuxappfinder.com/debian/pool/main/p/pacpl/)

---

### Post by Killtown on 2007-05-23
I just found a program to convert ogg to mp3:

[http://ubuntuforums.org/showpost.php?p=2708792&postcount=3](http://ubuntuforums.org/showpost.php?p=2708792&postcount=3)

---

