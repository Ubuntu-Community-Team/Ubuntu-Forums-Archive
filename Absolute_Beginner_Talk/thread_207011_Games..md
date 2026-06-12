---
title: "Games."
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-07-01
There are only 2 main games that I play frequently on Windows, and they are Quake 3 and America's Army, now I know both have Linux ports/versions, so I am wondering how I would go about installing them? Would I install them like any other application?

---

### Post by Max Luebbe on 2006-07-01
Depends on what form theyre in when you get them.
If they're in a .deb or rpm, its a no-brainer as you can use alien and dpkg to set things up nicely.

If its a tar.gz, you can get things going just by decompressing the archive, but the best way would be definately to convert the archive to a deb package, and then install it using dpkg

---

### Post by crane on 2006-07-01
As far as AA goes, you can download the .run file adn just run it to install.
Quake3 can be just as easy as long as you have the original CD to copy some files from.
Do a search for "installing qiake3" you should find plenty of info.
I'll run through the basics.
Create folders
[COLOR="Blue"]
sudo mkdir /usr/local/games/quake3
sudo mkdir /usr/local/games/quake3/baseq3[/COLOR]
insert quake3 arena cd in cdrom
[COLOR="Blue"]
sudo cp /media/cdrom0/Quake3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3
[/color]
Then download [Linux quake3 installer]("http://www.cranework.com/Downloads/linux/quake3/linuxq3apoint-1.32b-3.x86.run")
 then mv to the directory you downloaded the file (I think default is Desktop)
[COLOR="Blue"]
cd Desktop
sudo linuxq3apoint-1.32b-3.x86.run
[/COLOR]
once it is finished installing you can exit.
I believe is installs a short cut to the menu although it's been soo long ago since I've done this I can't remember.If not creating one is simple.
To play the game just type quake3 in the terminal and it should work, provided all the correct drivers (3D) are installed for your vid card.

Once you start the game it will create a hidden folder in your home directory. (control H to see hidden files) called .q3a.
You will notice ine this folder there is a baseq3 folder just like usr/local/games/quake3
This is what is know as your working folder. install you autoexec.cfg in this baseq3 folder.
You can also install mod to the .q3a folder but I always copy them over to /usr/local/games/quake3.
The reason is so the base install of the game and mods is in /usr/local/games/quake3 and everything else, configs, pb updates, and custome maps are put into the .q3a folder.
 This way, if for some reason, you screw up something while your playing or tweaking and you can't seem to recover from it. You can just delete the .q3a folder from your home directory. When you start the game again it will recreate the folder and you will be back to base install without having to reinstall game.

I hope some of this made since:D 

If you have any questions check the ubuntu gaming section for some help. If a search doen't turn up an answer the post your question in that area.
Also check out my site for quake 3 maps as well
[Cranework.com]("http://www.Cranework.com")
 Good luck!

---

