---
title: "Help with this Xubuntu based distro: Voyager 12.10"
date: 2013-05-02
forum: Any Other OS
---

### Post by UltimateCat on 2013-05-02
:DHi:

I found a distro that I would like to try and install; "Voyager 12.10"

It is based on Xubuntu and a derivative of Ubuntu 12.10- (sounds like a solid foundation to me)

The page to the 3 different kinds of downloads are in french. At the top of the page there is an English translator icon button.
Looking at that page:
> [http://voyager.legtux.org/index.php/live-voyager-12-10/](http://voyager.legtux.org/index.php/live-voyager-12-10/)
[http://voyager.legtux.org/index.php/a-propos-2/](http://voyager.legtux.org/index.php/a-propos-2/)

Under "Live Voyager USB/DVD 12.10" there is a 64-bit Download *torrent*

Now when I click on that torrent it's either not available in english because the translator is not on that page or I get "Firefox can not connect"

Any ideas on how I could obtain this in some other way?

If "torrent" is the only way could you tell me or show me a link how to work with the torrent to be able to install this distro?
I don't know how-:confused:

---

### Post by mips on 2013-05-03
The linuxtracker site is very slow and I cannot find the voyager torrent on it. The direct download link also does not work. They do have a free torrent tracker though.

[http://www.freetorrent.fr/download.php?id=c8a4f24426b9f06ab6b51ef642cbdd57225dd1e5&f=Live.Voyager.12.10.desktop.64.iso.torrent](http://www.freetorrent.fr/download.php?id=c8a4f24426b9f06ab6b51ef642cbdd57225dd1e5&f=Live.Voyager.12.10.desktop.64.iso.torrent)
[http://www.freetorrent.fr/index.php?page=torrent-details&id=c8a4f24426b9f06ab6b51ef642cbdd57225dd1e5](http://www.freetorrent.fr/index.php?page=torrent-details&id=c8a4f24426b9f06ab6b51ef642cbdd57225dd1e5)

---

### Post by slickymaster on 2013-05-03
Over at [http://w.linux23.com](http://w.linux23.com), there's also a Voyager 12 10 Desktop 64 Iso torrent, via bittorrent in Other Distros  category.

[http://www.linux23.com/torrent/live-voyager-12-10-desktop-64-iso:a353a57742730cdf3fedda9511884cee08846dc6](http://www.linux23.com/torrent/live-voyager-12-10-desktop-64-iso:a353a57742730cdf3fedda9511884cee08846dc6)

---

### Post by UltimateCat on 2013-05-04
Mips and Slickymaster:

Thanks so much for helping me with that!

Any last words on this LIVE Torrent that you could elaborate on or what I could anticipate before proceeding?

I do not understand how this torrent works but I'll see if there are some you tube videos to teach me how--
;)

---

### Post by Buntu Bunny on 2013-05-06
Very interesting. I hadn't heard of Voyager until I read this thread. I found a YouTube review, and wow, it looks really good. UltimateCat, please let us know how the install goes and what you think.

---

### Post by UltimateCat on 2013-05-06
Sure thing! ;)

---

### Post by UltimateCat on 2013-05-06
Sure thing! ;)

  

I downloaded the torrent seed file-
> Live.Voyager.12.10 desktop.64.iso.torrent 


I have on my system the application: 'qBittorrent' --

Don't have any clue what to do with this file-

Got some searching to do-

---

### Post by mips on 2013-05-07
Just double click the .torrent file and qbittorrent should open it or simply drag and and drop the .torrent file onto the qbittorrent window once open. Alternatively from within qbittorrent just go file open and point it to the torrent file.

I've never used qbittorrent but it can't be that complicated. I just use Transmission for my torrent stuff.

---

### Post by UltimateCat on 2013-05-08
Got it; just right click on the torrent-:)

Now I have an older version of the application "qbittorent" shouldn't I install the newer one: qbittorrent- 3.0.9?

BTW, I downloaded it to my Downloads directory just having "Errors" in terminal (that I don't understand) right now so I can't un-tar and install the new tar.gz; right now-:(

You have been helping here a lot longer than I so I am trusting you as I am not sure what is going on-
Sticking with me is greatly appreciated!

---

### Post by slickymaster on 2013-05-08
UltimateCat, you might want to take a look at this: [qbittorrent 3.0.9 Install and Live Voyager 12.10 seed file]("http://www.linuxquestions.org/questions/linux-software-2/qbittorrent-3-0-9-install-and-live-voyager-12-10-seed-file-4175461088/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxquestions%2Flatest+(LQ+-+Latest+Threads)").
Hopefully will help you some how.

---

### Post by Buntu Bunny on 2013-05-08
UltimateCat, I don't know if either of these links would help. I'm following your progress and researching as well, because this will be a learning curve for me too. 
[URL="http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file"]
http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file[/URL]
[http://www.techsupportforum.com/forums/f64/how-to-open-tar-gz-files-in-ubuntu-254092.html]("http://www.techsupportforum.com/forums/f64/how-to-open-tar-gz-files-in-ubuntu-254092.html")

Thanks for keeping us updated.

---

### Post by UltimateCat on 2013-05-08
Slickymaster:
That was a good webpage; thank you. This is what I gathered from it and interpreted what I should do-
(Installing with the terminal has always been hard for me; generally I avoid it!)

I hope these step's work: And that I have  right-
Worse case the terminal will give me a warning or an error I could learn from-

1. Open the terminal and run 
```
tar -zxvf qbittorrent-3.0.9.tar.gz

```

2. cd Downloads (that's were the new version of qbittorrent 3.0.9 is) 

3.Than run 
```
./configure

```

4. Than make, sudo su, and make install? ? All together or one at a time?

I found the Install file-
```

1) Compile and install qBittorrent with Qt4 Graphical Interface

  $ ./configure
  $ make && make install
  $ qbittorrent

  will install and execute qBittorrent hopefully without any problems.

  Dependencies:
    - Qt >= 4.6.0 (libqtgui, libqtcore, libqtnetwork, libqtxml, libqtdbus/optional)

    - pkg-config executable

    - libtorrent-rasterbar by Arvid Norberg (>= 0.15.0)
        -> http://www.libtorrent.net
        Be careful: another library (the one used by rTorrent) uses a similar name.

    - libboost 1.34.x (libboost-filesystem°) + libasio
      or
    - libboost >= 1.35.x (libboost-system, libboost-filesystem°)
      
    °libboost-filesystem is not needed if libtorrent-rasterbar >= v0.16.x is used

    - python >= 2.3 (needed by search engine)
        * Run time only dependency

    - geoip-database (optional)
        * If qBittorrent cannot find this database, it will try to resolve countries using the Internet but it will be a lot slower.
        * Run time only dependency

2) Compile and install qBittorrent without Qt4 Graphical interface

  $ ./configure --disable-gui
  $ make && make install
  $ qbittorrent

  will install and execute qBittorrent hopefully without any problems.

  Dependencies:
    - Qt >= 4.4.0 (libqt-devel, libqtcore, libqtnetwork)

    - pkg-config executable

    - libtorrent-rasterbar by Arvid Norberg (>= v0.15.0)
        -> http://www.libtorrent.net
        Be careful: another library (the one used by rTorrent) uses a similar name.

    - libboost: libboost-filesystem, libboost-date-time, libboost-thread, libboost-serialization


DOCUMENTATION:
Please note that there is a documentation with a "compiling howto" at http://wiki.qbittorrent.org.

------------------------------------------

```
This install file is explainatory but very confusing as I have never performed this task before-
I'll see if going to the qbittorrent wiki page helps.

I usually only have to pratice a task once and than I've got it; this is really challenging me.

---

### Post by UltimateCat on 2013-05-08
> **Buntu Bunny said:**
> UltimateCat, I don't know if either of these links would help. I'm following your progress and researching as well, because this will be a learning curve for me too. 
[URL="http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file"]
http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file[/URL]
[http://www.techsupportforum.com/forums/f64/how-to-open-tar-gz-files-in-ubuntu-254092.html](http://www.techsupportforum.com/forums/f64/how-to-open-tar-gz-files-in-ubuntu-254092.html)

Thanks for keeping us updated.

Your are Welcome Buntu Bunny!

Determined to get this new version of qbittorent installed and the new Voyager up and running!

---

### Post by drawkcab on 2013-05-09
I was initially impressed with voyager but it became old very quickly.

---

### Post by slickymaster on 2013-05-09
> **UltimateCat said:**
> 4. Than make, sudo su, and make install? ? All together or one at a time?


Issue those commands one at a time.

---

### Post by mips on 2013-05-09
Stop making your life so difficult by trying to compile qbittorrent. Install Transmission and use that, it works as I've tested it with that voyager torrent.

[IMG]http://ompldr.org/vaWNzeQ/transmission.png[/IMG]

---

### Post by slickymaster on 2013-05-09
> **mips said:**
> Stop making your live so difficult by trying to compile qbittorrent. Install Transmission and use that, it works as I've tested it with that voyager torrent.

[IMG]http://ompldr.org/vaWNzeQ/transmission.png[/IMG]

@[COLOR=#000000]UltimateCat
[/COLOR]That's the best advise.

---

### Post by Buntu Bunny on 2013-05-09
> **slickymaster said:**
> That's the best advise.

I'm glad to know this too. Transmission is what I already have installed so I'll give it a go. I used it once, for my Xubuntu 12.04 download, but ended up going with the direct download anyway because the torrent file didn't have the option to try before installing. (More timidness on my part.) ;)

---

### Post by slickymaster on 2013-05-09
> **Buntu Bunny said:**
> ...More timidness on my part. ;)

I think that's more of a wise approach than timidness.

---

### Post by UltimateCat on 2013-05-09
Thank you! Slickymaster for teaching me how to do that.
I needed that confirmation: one at a time--:D

In the future I will be able to practice this if I need to.

---

### Post by UltimateCat on 2013-05-09
Got it; Mips advice taken!

Thanks for the pic. I have never done this before--


When the transmission is complete I should be able to burn to a DVD/CD and install it on my laptop right?

---

### Post by UltimateCat on 2013-05-09
I know wisdom and wise cousel when I hear it:-
Thank you! :D

Be back after the transmission:~$[-o<

---

### Post by Buntu Bunny on 2013-05-09
[http://voyager.legtux.org/index.php/live-voyager-12-04-lts/]("http://voyager.legtux.org/index.php/live-voyager-12-04-lts/")

Could someone please tell me the difference between torrent and page torrent? There are links for both. Thanks!

---

### Post by mips on 2013-05-09
> **UltimateCat said:**
> 
When the transmission is complete I should be able to burn to a DVD/CD and install it on my laptop right?

Yes, or you could write it to a usb stick.

---

### Post by UltimateCat on 2013-05-09
This was a success!
The new Iso for Voyager is on my Desktop! Thank you MIPS!
You have been a great help!;)

Screenshot:
[http://s1052.photobucket.com/user/Ultimatecat/media/Screenshotfrom2013-05-08215025.png.html](http://s1052.photobucket.com/user/Ultimatecat/media/Screenshotfrom2013-05-08215025.png.html)

And while I am at it here is the (off topic) painting that I have been working on for the last 3 days since I installed Black Opal Ubuntu 12.04!
Sharing it with you--
[http://s1052.photobucket.com/user/Ultimatecat/media/BlkOpalCat.jpg.html?sort=3&o=24](http://s1052.photobucket.com/user/Ultimatecat/media/BlkOpalCat.jpg.html?sort=3&o=24)

---

### Post by UltimateCat on 2013-05-09
:D....A very special thanks to Mips and Slickymaster for staying with me and helping me along the way!
Cheers

---

### Post by Buntu Bunny on 2013-05-09
Congrats UltimateCat! Feels like a good days work, doesn't it, LOL. I just finished getting my iso downloaded too. Checksum checked! I should add my thanks to you for letting me tag along, and also to Mips and Slickymaster as well. You guys helped me too. :)

---

### Post by UltimateCat on 2013-05-09
If I am not mistaken the 'page torrent' will start the direct download--
The  'torrent' it's self is the actual 64bit Download.

Glad to hear you now have that ISO too! Enjoy....and BTW didn't mind you tagging alone-

---

### Post by UltimateCat on 2013-05-09
Going to share this new distribution with a friend that is starting to like linux-
Cheers :popcorn:

---

### Post by slickymaster on 2013-05-10
> **UltimateCat said:**
> :D....A very special thanks to Mips and Slickymaster for staying with me and helping me along the way!
Cheers

No need to thank, we're all here to help each other. Just glad you got it running.

---

### Post by slickymaster on 2013-05-10
> **Buntu Bunny said:**
> Congrats UltimateCat! Feels like a good days work, doesn't it, LOL. I just finished getting my iso downloaded too. Checksum checked! I should add my thanks to you for letting me tag along, and also to Mips and Slickymaster as well. You guys helped me too. :)

It's a good thing everything is working now. This forum  is an excellent community where everyone helps everyone.

---

### Post by Buntu Bunny on 2013-05-10
> **UltimateCat said:**
> If I am not mistaken the 'page torrent' will start the direct download--
The  'torrent' it's self is the actual 64bit Download.

Thanks! I couldn't find any information so just went for the torrent itself. This is good to know for the future.

---

### Post by Buntu Bunny on 2013-05-10
> **slickymaster said:**
> This forum  is an excellent community where everyone helps everyone.

Agreed. Besides things like this, I can never count on my hardware's technical support any more, ("we don't support Linux"), but this community always comes through. It's actually one of the nicer, i.e. kinder forums I'm on, very supportive and encouraging.

---

### Post by Lampmeister on 2013-05-10
UltimateCat, I don't know where you are with the Voyager project, but I'll tell you what I did. (I'm a bit of a noob myself) I've always had great luck using Transmission when I need to download torrents. (it's in the Ubuntu Software Center) Just save the torrent file to your desktop and drag it into Transmission. Once you've downloaded the iso file, you just burn it to a DVD and install. (or test live) The installation process is a breeze, not unlike Ubuntu itself. I've been running Voyager for a few days, and I like it a [I]lot!

OK, I'm an idiot...I didn't see that the thread continued to a 2nd page. Glad you're up to speed![/I]

---

### Post by pootan on 2013-05-12
Very nice painting.

---

### Post by finny388 on 2013-05-13
I've been using Voyager since 12.04 and it is a very good distro.

From my experience it differs from xubuntu with:

interface: conky is preconfigured, has a bunch of configs installed so you can change it like a theme
the windows/icons are nice and dark
the wallpaper collection is second to none if you enjoy photography (over a 100 wallpapers)
very nicely curated collection of programs preinstalled
altogether it is a distro very well thought out and with style.

only thing is french does come up in some apps.

---

### Post by Buntu Bunny on 2013-05-13
> **finny388 said:**
> I've been using Voyager since 12.04 and it is a very good distro.
From my experience it differs from xubuntu with: ...... [snip]


Finny388, thank you for that. 12.04 is the one I downloaded. The new releases sound amazing, but  I just don't have enough time to keep up every 6 months or so.

> only thing is french does come up in some apps.

Even with English being selected as your preferred language? That may be a bit of a problem for me. I know trying to get download and installation information and in English has been a challenge!

---

