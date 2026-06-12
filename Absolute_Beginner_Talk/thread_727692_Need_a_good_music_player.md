---
title: "Need a good music player"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-18
Hello all
I use Banshee 0.13.1
I need something that would have a fast library (Amarok is too slow on Gutsy + Gnome)
I have used Rhythmbox but I don't seem to like it.
Both Banshee and Rhythmbox are just "simple" and I need that looks good.

---

### Post by sayakb on 2008-03-18
Or someone could tell me where I can find the new Banshee.. ?? I have heard that an alpha has been released..

---

### Post by forestpixie on 2008-03-18
[http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee](http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee)

---

### Post by BillDozer on 2008-03-18
> **LinuxIsInnovation said:**
> Hello all
I use Banshee 0.13.1
I need something that would have a fast library (Amarok is too slow on Gutsy + Gnome)
I have used Rhythmbox but I don't seem to like it.
Both Banshee and Rhythmbox are just "simple" and I need that looks good.

Have you been using Amarok with Sqlite or with MySQL. I am using MySQL and do not find it too slow on an old 800 Mhz machine

---

### Post by sayakb on 2008-03-18
> **BillDozer said:**
> Have you been using Amarok with Sqlite or with MySQL. I am using MySQL and do not find it too slow on an old 800 Mhz machine

I use SQLite, since I don't know how to configure MySQL..

---

### Post by sayakb on 2008-03-18
> **forestpixie said:**
> [http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee](http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee)

Thank you. 
Btw, is it safe to try the alpha one over the current release?

---

### Post by housam on 2008-03-18
look at this[[COLOR="Red"]_ lists _[/COLOR]]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html#41")you'll find what you need

---

### Post by forestpixie on 2008-03-18
> Btw, is it safe to try the alpha one over the current release?

It gets installed seperately - from the Banshee site -

> It has also been designed to be both installed and run in parallel with previous Banshee releases, so you can test the release out without breaking your stable Banshee setup.

> I use SQLite, since I don't know how to configure MySQL.

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by sayakb on 2008-03-18
> **forestpixie said:**
> [http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee](http://ubuntuforums.org/showthread.php?t=724337&highlight=banshee)

The deb file is for i386 architecture, while I use an amd64 OS.. will it make my Ubuntu crash if I use the force architecture option?

---

### Post by BillDozer on 2008-03-18
> **LinuxIsInnovation said:**
> I use SQLite, since I don't know how to configure MySQL..

Before giving a thumbs down to amarok. I would suggest to use MySQL as the library.

Install MySQL:
```
sudo apt-get install mysql-server
```

Take a look here to set up MySQL [http://amarok.kde.org/wiki/MySQL_HowTo]("http://amarok.kde.org/wiki/MySQL_HowTo") check out the **MySQL setup** section.

I really would give it a try if I were you. :-)

---

### Post by sayakb on 2008-03-18
> **BillDozer said:**
> Before giving a thumbs down to amarok. I would suggest to use MySQL as the library.

Install MySQL:
```
sudo apt-get install mysql-server
```

Take a look here to set up MySQL [http://amarok.kde.org/wiki/MySQL_HowTo]("http://amarok.kde.org/wiki/MySQL_HowTo") check out the **MySQL setup** section.

I really would give it a try if I were you. :-)

I too like Amarok :)
Downloading mysql-server. Thank you forestpixie and BillDozer for your help.

---

### Post by sayakb on 2008-03-18
> **housam said:**
> look at this[[COLOR="Red"]_ lists _[/COLOR]]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html#41")you'll find what you need

Thanx for the link.. Excellent page for software lists :)

---

### Post by kleo skywalker on 2008-03-18
You could try Listen or Exaile. Both are in the repos.

---

### Post by linux phreak on 2008-03-18
+1 for exaile

---

### Post by forestpixie on 2008-03-18
I find that Exaile is really clunky with big playlists and takes an age to load them.

---

### Post by housam on 2008-03-18
> **LinuxIsInnovation said:**
> Thanx for the link.. Excellent page for software lists :)

+2 for Exaile , also see this one :[[COLOR="Red"]_http://gqmpeg.sourceforge.net/mpeg-shot.html_[/COLOR]]("http://gqmpeg.sourceforge.net/mpeg-shot.html")

---

### Post by sayakb on 2008-03-18
Mysql error:

```
root@Muzic-Jukebox:~# mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
root@Muzic-Jukebox:~# 

```

Plus, I have also installed Exaile, but I wish it had a notification area icon. I have to keep it minimized everythime while using it..

---

### Post by chronographer on 2008-03-18
I vote 1 for mpd with sonata. Its a little tricky to install, but easier imho than SQL setup. You get mpd with apt-get, then get sonata too, then configure mpd (/etc/mpd.conf) and point it to your music, then run "sudo mpd --create-db" and it goes, then Sonata is lightning fast! I have it always running and even when playing music it uses ~10 mb ram and ~0 cpu !!!!
Looks good too. Oh I also installed pitchfork, which is a web interface so I can control my desktops music playing (which pumps to all my radios with a FM-transmitter) with my mac !! Cool huh?

---

### Post by sayakb on 2008-03-18
Sounds good to me :)
But does it have an attractive UI?

---

### Post by kleo skywalker on 2008-03-18
> **LinuxIsInnovation said:**
> Plus, I have also installed Exaile, but I wish it had a notification area icon. I have to keep it minimized everythime while using it..

You can minimize it to panel. Exaile-->Edit-->Preferences-->General, make sure "Show Tray Icon" is checked.
If you like Exaile, you might want to consider giving Listen a shot too.

---

### Post by Oldsoldier2003 on 2008-03-18
> **BillDozer said:**
> Have you been using Amarok with Sqlite or with MySQL. I am using MySQL and do not find it too slow on an old 800 Mhz machine

even though i like amarok, -100 for having to install MYSQL to get decent performance out of a media player....

---

