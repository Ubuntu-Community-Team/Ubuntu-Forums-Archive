---
title: "Windows Media Player Alternative"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by RLovelett on 2007-03-22
Ok I'll admit it.  I might just like Ubuntu a crap ton more than I like Windows XP.  That having been said there is a lot that I don't know in this OS that was a given in my former.

Like for instance, I have a gigantic music collection.  I want to be able to browse it and interact with it just like I did in Windows Media Player 11.  The features I am specifically referring are: I just tell it a directory on my computer and it monitors said directory for new music, organizes the music into fancy little folders, finds album information (name, artist, album art, etc...) and does this automatically.

I really am hoping that somewhere in the universe an open-free program like this exists!  Please tell me it is so!

Thanks,
Ryan

---

### Post by stijngysemans on 2007-03-22
Banshee may suit your needs!

---

### Post by ant1060 on 2007-03-22
Hi RLovlett,
You REALLY can't do better than AmaroK! It's absolutely excellent, and you can stream music from it to your Apple Airport Express too (like you can in iTunes).
Enjoy your Ubuntu - it takes a bit of getting used to, but I am never going back to Windows! :) 
/Ant
Bruxelles, Belgique

---

### Post by jkeyes0 on 2007-03-22
I used Rhythmbox for a while, and it did all that you've asked. It's a little bloated (like WMP, actually), but still a very decent solution. It should come with Ubuntu, and if it doesn't, you can sudo aptitude install rhythmbox to get it.

---

### Post by SunnyRabbiera on 2007-03-22
amarok is a great windows media player/ itunes alternative.
I like the program myself, its much better with media then any other linux music app as it recognizes some proprietary formats that say exaile and rhythmbox miss

---

### Post by tallman9 on 2007-03-22
try exaile, amarok, rhythmbox, juk...all of them can organize your music in a number of ways.
But first be sure you've installed all the needed codecs.

---

### Post by go2dell on 2007-03-22
[Banshee]("http://banshee-project.org/") is good, but also take a look at [Listen]("http://www.listen-project.org/") (still buggy but my fav), and [Exaile]("http://www.exaile.org/trac").

Don't forget on KDE there's Amarok.

---

### Post by RLovelett on 2007-03-22
Now on the Amarok website it seems that they are writing their app for KDE/Kubuntu.  But when you go into the Add/Remove Applications list Amarok appears for just GNOME/Ubuntu.  Is their going to be a compatability issue that I should steer away from; or will it work ok since I can get to it from Add/Remove Applications?

---

### Post by go2dell on 2007-03-22
[AmaroK]("http://amarok.kde.org/") is a KDE app.  The reason you can install it is that the necessary KDE dependencies will be installed at the same time.  Some people don't like having these on their Gnome machines, but there's no real reason to avoid it if you like the application enough.

---

### Post by RLovelett on 2007-03-22
I have not quite got it where it will auto-organize my music for me.  But I like the interface and once I installed xine it is playing my MP3's.  So, I am very pleased with the ease of use it brought me.

---

### Post by Rizlaw on 2007-03-22
My 2 cents. For the Gnome environment, I have looked at all of the solutions mentioned above, but IMHO I find "gmusicbrowser" superior.

It is not in the default Ubuntu/Debian repositories, however, it can be added to your Synaptic Package Manager installer's "Third Party" Tab by adding the following line in "Settings > Repositories > Third Party:

**deb [http://squentin.free.fr/gmusicbrowser](http://squentin.free.fr/gmusicbrowser) ./**

Once added, you can then click on "Search" in Synaptic and enter "gmusicbrowser". It will find the package. Click to mark the package for installation and then click on "apply" to actually install the program. When done, you will find a "gmusicbrowser" icon in "Applications > Sound & Video".

You will also want to install:

** libgtk2-trayicon-perl** and all of the "gstreamer-plugins" you require for music files: like "ugly" for mp3's; "bad" for mpc; "good" for flac. A search in Synaptic will show you all of the gstreamer packages.

More info can be found at [http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html).

---

### Post by at0mik on 2007-03-23
> **tallman9 said:**
> try exaile, amarok, rhythmbox, juk...all of them can organize your music in a number of ways.
But first be sure you've installed all the needed codecs.
I can't seem to find the required codecs, could you please link them for me?

---

### Post by saadakhtar on 2007-03-23
my personal suggestion would be amorok since it has a very extensive play list assorting mechanism. it uses mysql backend to organize ur music. works like  a charm for me. abt video players. the one i use is VLC.
simply start synptic and search for VLC and amorok. all dependencies should be taken care of automatically.

hope this helps.

cheers,

---

### Post by AndyCooll on 2007-03-23
> **at0mik said:**
> I can't seem to find the required codecs, could you please link them for me?

See the "Restricted Formats" link in my signature. That tells you all you need to know.

:cool:

---

### Post by AndyCooll on 2007-03-23
Got to admit I'm a big fan of Amarok, there really is nothing to beat it. I'm a GNOME user but none of the GNOME based apps can touch it. I've tried Exaile, Listen, Rhythmbox and they're all ok ...but they ain't a patch on Amarok.

Even my missus can use Amarok and she's a casual computer user. Amarok was one of the apps I introduced her to when I was converting all our boxes. She took to it like duck to water.

:cool:

---

### Post by DougieFresh4U on 2007-03-23
I also really like amarok, but let ask this, why does amarok cause CPU usage to spike to almost 100% ??  Any one else have the same problem?

---

### Post by macogw on 2007-03-23
I'm with the Banshee camp.

---

### Post by tallman9 on 2007-03-24
another good idea is to try Songbird.

---

### Post by at0mik on 2007-03-24
> **AndyCooll said:**
> See the "Restricted Formats" link in my signature. That tells you all you need to know.

:cool:
Thanks :D.

---

### Post by camz on 2007-03-24
Well, all of these programs are also very good, but if you are looking for something very similar to WMP, you could try RealPlayer 10, as there is a Linux version. [www.real.com](www.real.com).

Thanks

---

### Post by AndyCooll on 2007-03-24
> **DougieFresh4U said:**
> I also really like amarok, but let ask this, why does amarok cause CPU usage to spike to almost 100% ??  Any one else have the same problem?

When I get this it is usually because artsd is running and that seems to eat up CPU usage. I kill this process. Not sure why Amarok starts it.

:cool:

---

