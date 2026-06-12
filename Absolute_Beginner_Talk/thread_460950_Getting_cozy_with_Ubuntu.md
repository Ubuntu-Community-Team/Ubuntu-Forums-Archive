---
title: "Getting cozy with Ubuntu"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Games Goblin on 2007-06-01
HI ALL! I finally did it! I installed ubuntu! I connected to the internet through ubuntu thanks 2 you guys! 
I used Partition Magic 8.0 to make a 15 GB EXT3 partition to install ubuntu into and also formatted a 24GB partition into FAT32 so as to share files between windows and ubuntu. Oh..speaking of windows, Ubuntu correctly set up a dual boot with XP Pro....something even windows vista refuses to do....and XP and Vista are family and Ubuntu is the (enemy?) to them and Ubuntu plays nicer!!! :p:p

I need to frequently reboot and log into windows because of the following problems...If i get all of them solved, I can make Ubuntu my permanent residence.....until i have to play games in windows that is...

I DO NOT KNOW HOW TO USE THE TERMINAL TO DO ANYTHING...HELP REGARDING THIS WILL BE MUCH APPRECIATED!

1) I need a torrent client for Ubuntu
2) I need something to extract .rar files...will karchiver do?
3) I need to talk to my brother...I used google talk in windows..any way to make google talk work in ubuntu
4) I need a good download manager


THANKS!!:popcorn:

---

### Post by HobbitCy on 2007-06-01
hi im new to
but i know you can get [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) working in Ubuntu for your torrents
not sure about the rest

edit found this for you for rar files havent tried it but looks simple
[http://tl-tech.blogspot.com/2007/05/extract-rar-archives-in-ubuntu-704.html](http://tl-tech.blogspot.com/2007/05/extract-rar-archives-in-ubuntu-704.html)
just like right click extract here

Part 1: Installing RAR


   1. Go to [Applications] [Accessories] [Terminal]

   2. Type the following in Terminal: sudo apt-get install rar (then hit return and the program should begin to download)

   3. Type the following in Terminal: sudo ln -fs /usr/bin/rar /usr/bin/unrar (then hit return)


Part 2: Extracting a RAR archive.


   1. Go to the folder where the .rar file is located

   2. Right click on the file and select extract here

---

### Post by seshomaru samma on 2007-06-01
google talk:
open gaim or pidgin (you might need to install them)
select protocol:
 jabber (in gaim)
xmpp (in pidgin)
 and fill in rest of details like username etc
server is gmail.com and in advanced options connect server: talk.google.com

download manager:
i use downloadthemall in firefox
some people use k-get

---

### Post by southernman on 2007-06-01
> I DO NOT KNOW HOW TO USE THE TERMINAL TO DO ANYTHING...HELP REGARDING THIS WILL BE MUCH APPRECIATED!
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

BTW, Congrats on joining the Ubuntu movement! ;)

---

### Post by gh0st on 2007-06-01
Azureus is a good BitTorrent client but I found it was far too hungry on system resources so I use Ktorrent you can install it from Add/Remove programs I think. It is a KDE app but works fine for me in Gnome, it's not slow or anything as some people seem to complain. If you have trouble with Azureus check it out.

Another cool torrent client to check out is Deluge - [http://dev.deluge-torrent.org/](http://dev.deluge-torrent.org/)

For download managers you can use something like the Gnome frontend for wget it's called gwget and you should be able to find it an add/remove programs. It's definitely in the main repositories.

For more info - [http://www.gnome.org/projects/gwget/index.html](http://www.gnome.org/projects/gwget/index.html)

You could also use a Firefox extension, there are loads of good ones about, have a look here - [https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:5](https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:5)

Welcome to Ubuntu and good luck, freedom is great isn't it :D

---

### Post by topsites on 2007-06-01
Sorry but I dont sleep with my OS, much as it might dismay the creators :-\"

---

### Post by Games Goblin on 2007-06-01
> **topsites said:**
> Sorry but I dont sleep with my OS, much as it might dismay the creators :-\"

Ha Ha :D :D 

When I started using Ubuntu, I felt like sleeping with it.....the only thing preventing me from doing so are these nagging problems which I am trying to fix now

---

### Post by Crafty Kisses on 2007-06-01
> **Games Goblin said:**
> Ha Ha :D :D 

When I started using Ubuntu, I felt like sleeping with it.....the only thing preventing me from doing so are these nagging problems which I am trying to fix now

Good news, there is a program where you can run pretty much all your Windows Games. :p

[http://www.cedega.com]("http://www.cedega.com")

---

### Post by Games Goblin on 2007-06-01
> **Codename said:**
> Good news, there is a program where you can run pretty much all your Windows Games. :p

[http://www.cedega.com]("http://www.cedega.com")

THAT IS SO COOL...I'll try it out now

Thx very much!!:popcorn::popcorn:

---

### Post by phr0ze on 2007-06-01
Most first person shooters already have a solution to run in Linux. IF you play FPS, just look around.

---

### Post by Games Goblin on 2007-06-01
OK .. first i must get my nVidia drivers to install in ubuntu...will search forums for that....i'll post the results..

---

### Post by Josey on 2007-06-01
> **Games Goblin said:**
> 
1) I need a torrent client for Ubuntu
ktorrent in add/remove programs
> 2) I need something to extract .rar files...will karchiver do?
in add/remove programs search for rar
> 3) I need to talk to my brother...I used google talk in windows..any way to make google talk work in ubuntu
I think gaim can help you there
> 4) I need a good download manager
kget in add/remove programs

---

### Post by Josey on 2007-06-01
> **Games Goblin said:**
> OK .. first i must get my nVidia drivers to install in ubuntu...will search forums for that....i'll post the results..

menu - system - administration - restricted drivers manager
enable nvidia driver there

---

### Post by Games Goblin on 2007-06-01
How do i get into "ADD/REMOVE PROGRAMS"?

EDIT: Never mind, I found it...on with installing....

---

### Post by Hobo Joe on 2007-06-01
```

sudo aptitude install pidgin

```
That is the new version of GAIM.

---

### Post by noerrorsfound on 2007-06-01
> **Codename said:**
> Good news, there is a program where you can run pretty much all your Windows Games. :p

[http://www.cedega.com]("http://www.cedega.com")
Wine is better, and free: [http://winehq.org/](http://winehq.org/)

Wine runs most games better than Cedega, but unlike Cedega, Wine does not currently support copy protection. You can still run the games using a no-cd patched executable.
[http://en.wikipedia.org/wiki/Cedega#.22Free_riding.22_on_the_free_software_movement](http://en.wikipedia.org/wiki/Cedega#.22Free_riding.22_on_the_free_software_movement)
> Transgaming obtained the source to the original Wine project when it was under the MIT License (non copyleft) and this license placed no requirements on how TransGaming published their software. TransGaming, unlike other companies with similar models, decided to release their software as proprietary software. Transgaming does release portions of the source code via CVS; however, it attaches legal restrictions which mean that it is not free software. Cedega includes licensed support for several types of CD-based copy protection (notably SecuROM and SafeDisc), the code for which TransGaming say they are under contract not to disclose.

In reaction, the Wine project changed its license to the GNU Lesser General Public License (LGPL). This means that anyone who publishes a modified version of Wine must publish the source code under an LGPL-compatible (and therefore free software) license. TransGaming halted using code contributed to Wine when the license was changed, though this has resumed recently with TransGaming integrating certain LGPL portions of Wine into Cedega and placing those portions of the source code on their public servers.

---

### Post by Games Goblin on 2007-06-01
Hm......whatever I do in the terminal seems to go wrong...

I hunted the forums for the following:

1) Installation of my nVidia driver
2) Insrallation of fonts

I found solution to both of these problems in the forums but none of the terminal commands work!!

Please help...how can i directly copy over the fonts to the fonts folder? I located it and when I tried to copy it into ubuntu's font folder it gave me an error saying that "You do not have the privilages..." or something like that...

Oh..and I did manage to install the nVidia drivers...by letting restricted driver manager download and install them.....but it felt less satisfying than a manual install...y'know...


@noerrorsfound - The Wine program is so cool...i never dreamt that i would be able to run windows apps in linux! Let me see if google talk works...I managed to get google talk working in Gaim...but I still cannot voice chat with my brother

---

