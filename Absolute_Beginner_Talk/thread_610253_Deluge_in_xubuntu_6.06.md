---
title: "Deluge in xubuntu 6.06"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by shplog on 2007-11-11
Will it work?
Ive downloaded and tried to install all 4 options from here: [http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

I use Gdebi package installer, and I get:
Error: Dependency is not satisfiable: Libc6

So I can't install?


EDIT: I also tried this: 
> ryan@ubuntu:~$ sudo aptitude install deluge-torrent
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "deluge-torrent"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
ryan@ubuntu:~$ sudo aptitude install deluge -torrent


---

### Post by shplog on 2007-11-13
Bump...

I have no options for torrents....
Azureus **** out on my because of firewalls.  I can't get into my router's page to change the settings...
Frostwire won't work for any torrents I find.
Bittorrent blows.
Bittornado didn't work...
ktorrent + Utorrent...nope.


Everybody (well, many people) has/have said that deluge is the way to go...but I cant.  

Libc6...

BUMPPPPPP!!!

---

### Post by SOULRiDER on 2007-11-13
Have you tried rTorrent? its the best client around IMHO.

---

### Post by mcduck on 2007-11-13
> **shplog said:**
> Will it work?
Ive downloaded and tried to install all 4 options from here: [http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

I use Gdebi package installer, and I get:
Error: Dependency is not satisfiable: Libc6

So I can't install?

EDIT: I also tried this:

They only seem to have packages for Feisty (7.04) and Gutsy (7.10) there. It's not likely that either one of these would work for you.. You could try installing it from source, but it could easily be that Deluge needs something Dapper doesn't have to work, and is therefore not possible to get running on Dapper..

---

### Post by shplog on 2007-11-13
Thank you.

I've dl'd rtorrent 0.7.9-1 
and libtorrent 0.11.9-1

They are both installed.

However, rTorrent is not in my Applications>Network.  In Synaptic, they are installed.

In Terminal:
> ryan@ubuntu:~$ rtorrent
rtorrent: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory


Any ideas?

Thanks again.

---

### Post by shplog on 2007-11-14
Bump**

---

### Post by Inxsible on 2007-11-14
AFAIK, rtorrent is a command line app. I could be wrong tho. 

if you want a gui over rtorrent, have a look at [ntorrent]("http://code.google.com/p/ntorrent/")

---

### Post by shplog on 2007-11-14
I don't understand, I'm still quite the nOOby.  What is AFAIK?  What is a GUI?

I used to have UTorrent w/ Win, which was pure awesomeness.  So, I'll stick w/ torrents.


How can I get rTorrent installed and running?

Thank you.

---

### Post by shplog on 2007-11-14
Blump

---

### Post by Inxsible on 2007-11-14
AFAIK = As far as I know

install rtorrent with,```
sudo aptitude install rtorrent
```you might also consider upgrading to the latest version on Ubuntu which is the Gutsy Gibbon or 7.10

---

### Post by shplog on 2007-11-14
> **Inxsible said:**
> AFAIK = As far as I know

install rtorrent with,```
sudo aptitude install rtorrent
```you might also consider upgrading to the latest version on Ubuntu which is the Gutsy Gibbon or 7.10
Yah, but I just installed 6.06 like one week ago.  Still much learning to do.  I just ordered more ram a couple days ago, so once I get that (tomorrow) I'll probably play w/ 6.06 for another day or so then upgrade.

I really just don't want to go through the whole "burn disc-installation" again.

OK, I did the code, then type rtorrent and it says 
>                    *** rTorrent 0.5.3 - libTorrent 0.9.3 ***
[View: main]




















[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6945] [U 0/0] [S 0/1/768] [F

>


Now what?
It's not in apps>network...
I don't know how to use rtorrent yet, so I'm sure running it in terminal won't do me much good.

Ideas?

---

### Post by Inxsible on 2007-11-14
As I told you already, rTorrent is a CLI app. there is no gui. you will probably have to install nTorrent which provides a GUI over rTorrent. Follow the link i gave you earlier. I have never used nTorrent or rTorrent, so I cannot really help you with the CLI commands to download something. but if you do this it should tell you how to use is```
rtorrent -h
``` or ```
rtorrent --help
```

---

### Post by shplog on 2007-11-14
I'd like a GUI. Ill give nTorrent a shot.

Thanks!!

---

### Post by Inxsible on 2007-11-14
> **shplog said:**
> I'd like a GUI.

So, I guess I'll just have to upgrade and get Deluge.  Thanks all!!!Yeah. Try out Gutsy

---

### Post by shplog on 2007-11-14
Well...
128 ram
pentium 3
20g HD.

Im going 128->512, once it happens, I'll go 7.10.  I'll have to update it though right?  Like, dl java and flash and etc.

---

### Post by Inxsible on 2007-11-14
you may want to perform a clean install rather than upgrading.

I don't think you can upgrade directly from 6.06 to 7.10.

After you install 7.10, installing java, flash etc is very easy. just running one or two commands thats all.

---

### Post by shplog on 2007-11-15
> **Inxsible said:**
> you may want to perform a clean install rather than upgrading.

I don't think you can upgrade directly from 6.06 to 7.10.

After you install 7.10, installing java, flash etc is very easy. just running one or two commands thats all.Yah, that's what I meant.  DL the image, etc..
The first time I installed java, it was a pain...that's why I kinda dred it.  But yah, shouldn't be bad the 2nd time.

---

### Post by Inxsible on 2007-11-15
> **shplog said:**
> Yah, that's what I meant.  DL the image, etc..
The first time I installed java, it was a pain...that's why I kinda dred it.  But yah, shouldn't be bad the 2nd time.its become much easier in 7.10. simply run this command to install the jre```
sudo aptitude install sun-java6-bin
``` you do have to enable the universe and multiverse repos before you do that tho. if you need the jdk you simply replace the package name with sun-java6-jdk. That takes care of your java :). Flash is easy too. But we'll get to it later, after you have got yourself 7.10 installed.

---

### Post by shplog on 2007-11-15
Awesome.  Commands rule when they work.

Thank you.

---

### Post by ellgor on 2007-11-15
Hi,

As a 6.06 user I tried to install deluge as well, only to find that it is not compatible with 6.06, its in the read.me doc I think, anyway if you want an easy on your system app, try Transmission which is in the Gnome site, latest version being 0.93.

Regards, Ellgor.

---

