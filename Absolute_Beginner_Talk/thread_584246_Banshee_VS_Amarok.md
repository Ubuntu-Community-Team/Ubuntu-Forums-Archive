---
title: "Banshee VS Amarok"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-20
hey all,

Does Banshee have problems with big music libraries as Amarok (sans mysql) does?

thanks

I cant get mysql on amarok set up- I dont get the instructions on their wiki

---

### Post by Kingsley on 2007-10-20
We can help with the wiki instructions. Which part is confusing you?

---

### Post by JasonBourneLinux on 2007-10-20
hey,

1) Please also make sure you have the libmysqlclient libraries, along with the development headers (-dev packages) installed

2) If your locale is UTF-8, make sure the default character set for your mqsl daemon is set up to utf8, so that all databases and tables are created with character set utf8. In Debian: 

            1) Edit /etc/mysql/my.cnf, adding this line to stanzas [client] and [mysqld]: 

              default-character-set = utf8 

              2) Restart the mqsql daemon to pick up the new default charset 

              Do this before you create the database for amarok. 
 
              Make sure the MySQL daemon is running. If necessary, add it to your linux startup scripts, via            whatever method your distro uses

thanks all!

---

### Post by Frak on 2007-10-20
Amarok should use SQLite by default (and I recommend it since it autoconfigures, and amarok is a great player)

Am I wrong?

---

### Post by JasonBourneLinux on 2007-10-20
I heard the Amarok has trouble with large libraries if you dont configure mysql

---

### Post by PmDematagoda on 2007-10-20
I didn't have any problem concerning Amarok with my library which is about 6Gb in size(I admit it is rather small:)).

---

### Post by barkej on 2007-10-20
IMHO using sqlite is a little slower than mysql but not enough to warrant the extra hassle of setup.

---

### Post by JasonBourneLinux on 2007-10-20
i have round 4000 songs in my collection- will sqlite die on me? lol

---

### Post by FredB on 2007-10-21
I used Amarok and it had no problem with a 1500 songs collection. Don't use it anymore, because it cannot transfer filename with accent caracters in it on my Samsung YP-U3 digital player (MTP one) :(

---

### Post by JasonBourneLinux on 2007-10-21
has anyone used Banshee and would reccomend it?

---

### Post by Frak on 2007-10-21
For openSUSE, Yes, because its just about all you can get, but for Ubuntu, go with your ability to try Amarok OOTB. I'm sure you'll think its at least kind of cool.

---

### Post by FredB on 2007-10-21
Well, I don't have a lot of good time with banshee. Even Rhythmbox is better ;)

---

### Post by HokeyFry on 2007-10-21
i used banshee for a while but if you have a gigantic library like mine (5259 and growing) it gets super slow. also, sorting sucks in banshee, i switched to amarok and am much happier, though instead of gstreamer it uses the xine engine. downloading the "libxine1-ffmpeg" package via synaptic should enable mp3 and m4a support  (if you use either format).

---

### Post by hyper_ch on 2007-10-21
I run amarok on 12k songs and it's no problem with mysql... as I setup web developement I have mysql/php/apache installed anyway...

---

### Post by Paqman on 2007-10-21
Exaile is well worth a look, too. It's a Gnome-flavoured clone of Amarok.

---

### Post by dynamethod on 2007-10-21
banshee works real well for me, and has some good radio stations built in(dnb radio!) even recommends similar artists

---

### Post by transgress on 2007-11-28
I use banshee with around 21 gigs of music... 3575 songs... works great for me.  i can't stand the cluttered layout of amarok, but it never had any trouble with sqlite and my library... didn't notice a huge difference between performance with that and mysql...

---

### Post by lvleph on 2007-11-29
Looks like no one here has tried to use Amarok with SQLite on a large collection, so I will chime in.

I currently have 13k+ songs, and tried to Amarok with SQLite. I think it took 2 hours to load my library. The whole things seems to be a bit clumsy with that large of a library. But iTunes wasn't much better at loading my library initially either. I haven't bothered trying to figure out how to setup mysql yet.

---

### Post by junkmailking2k on 2007-12-02
I have about 40 gigs (6000 songs) and I've been using banshee for months and it works great. I tried Amarok, but its way too slow/clunky with my library.

---

### Post by burnttoast11 on 2007-12-03
I am also a fan of Banshee.  My favorite feature is that it automatically recommends similar artists and does a very good job at it.  Does Amarok have a plugin that will recommend similar artists?  If it does I will probably give Amarok a try since everyone seems to love it.  By the way, I have about 5500 songs and Banshee is plenty fast for me.

---

### Post by Frak on 2007-12-03
> **burnttoast11 said:**
> I am also a fan of Banshee.  My favorite feature is that it automatically recommends similar artists and does a very good job at it.  Does Amarok have a plugin that will recommend similar artists?  If it does I will probably give Amarok a try since everyone seems to love it.  By the way, I have about 5500 songs and Banshee is plenty fast for me.
Yes, it does. Look in the scripts.

---

