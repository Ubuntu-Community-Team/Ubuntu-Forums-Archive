---
title: "Looking for an Audio Player"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Synikk on 2006-10-21
Right now I'm using Rhythmbox to listen to audio files, but I find it a little lacking.

I'm looking for an audio player that can display full ID3v2 tags, file bitrate and whether or not a file is in mono or stereo.

Rhythmbox doesn't display ID3v2 or other metadata in detail.

Are there any GNOME audio apps that have these features (either built in or as plugins)?

---

### Post by sizzam on 2006-10-28
I use Beep Media Player.   If you are familiar with Winamp, it is essentially a clone of that.

On the main screen, it displays file bitrate and mono/stereo.  Also, if you click the "I" button on the left, it displays all of the ID3v2 data for that file.

---

### Post by randomi on 2006-10-28
Another option, like beep-media-player, is XMMS. They're both essentially the same thing but made by different people.

[http://www.xmms.org/](http://www.xmms.org/) (Although it seems they may be having database issues at the time that I'm posting this.)

I also use beep-media-player but everyone has their preferences and thought I would offer another suggestion. I've used both over time and my personal preference just happens to be beep-media-player right now.

---

### Post by Synikk on 2006-10-28
Hey guys, I found Quod Libet a week ago and have been using that. Comes with the Ex Falso tag editor as well. Top notch app.

---

### Post by GnuSense on 2006-11-04
Humm, it seems like the Edgy versions of XMMS & BEEP don't have id3v2 support (or maybe it is one of the numerous options that I missed in XMMS). The MPEG Lager 1/2/3 Player plugin shows that  'Disable ID3V2 tags' isn't disabled.  Annoying.  

XMMS is my favorite Linux audio player because it is the only one that will consistently play relative playlists (m3u) that I've made with Winamp back in Windows days. Plus, unlike Amarok, etc., it starts on a dime and is very responsive. Unfortunately, at least on my machine, the Double Size option just freezes XMMS and I have to kill the process.  I've never seen that particular bug before.  And the fonts look crummy, but that's what I've come to expect from XMMS in Kubuntu (GTK fonts look terrible in Ubuntu for some reason).

I like to organize my albums in directories that are subdirectories of 'artist' folders and put playlists for the individual albums in the parent directory. The location of my music files frequently shifts around so I don't like have a music player that requires you to scan a library and adds  playlists. Besides, when Amarok, etc. does that is also vacuums up the relative directories that are in the 'artist' folder as well as the m3us in the 'album' folders, so I get two playlists listed for each album my collection, one broken and one working, and no way to tell them apart.


Unfortunately, I don't believe ANY audio player except Amarok in Ubuntu displays full ID3V2 tags, and I think I've installed just about all of them with just about all of their bleeding appendages.  And I've installed a bunch of ones that I've always hated (Juk, Rhytmbox, Banshee, e.g., gawk, I might as well be using the hated iTunes program in Windows) looking for an audio player with V2 tag support that plays relative playlists.  No luck.  I'll just have to limp by with a semi-broken XMMS.  

It seems like more and more newer distros are screwing up XMMS. Let's see, Blag 50002 (a Fedora 5 version), MandrivaOne, it wasn't even in the repositories for ArkLinux.  I guess some folks think GTK is deprecated and the popularity of iTunes clone media players like Amarok has so much eclipsed XMMS that there isn't much development work going on in the program (it seems like I've been using 1.2.10 for years). Too bad, it is the one Linux media player that doesn't make me nostalgic for Winamp.

---

### Post by Perfect Storm on 2006-11-05
The latest in the "winamp" clone player, audacious: [http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

---

### Post by Brownedwg89 on 2006-11-05
Amarok... Best Application EVER :D
I really suggest trying it
i love it so much <3

---

### Post by hugmenot on 2006-11-06
> **GnuSense said:**
> 
Unfortunately, I don't believe ANY audio player except Amarok in Ubuntu displays full ID3V2 tags, and I think I've installed just about all of them with just about all of their bleeding appendages.  And I've installed a bunch of ones that I've always hated (Juk, Rhytmbox, Banshee, e.g., gawk, I might as well be using the hated iTunes program in Windows) looking for an audio player with V2 tag support that plays relative playlists.  No luck.  I'll just have to limp by with a semi-broken XMMS.  


Quod Libet. Displays all.

---

### Post by GnuSense on 2006-11-06
I'll have to try Quod again when I get back to my Kubuntu box, but I gave it a try and wasn't impressed.  

Right now I'm on [Blag]("http://www.blagblagblag.org/"), a version of Fedora FC5, and I installed Audacious. Pretty much broken, won't display tags at all (they are blank), won't play playlists, displays Artist + Song with a bunch of weird verbiage (%$#).  The bug report account has been [suspended]("http://shiva.snipanet.com/suspended.page/"). 

I'm using beep-media-player (Beep) now, but it won't read relative playlists.  I installed BMPx (beep-media-player-2) and it won't even start. [Beep]("http://bmp.beep-media-player.org/index.php/BMP_Homepage") is no longer being maintained, though.
>  BMP is discontinued, now enjoy BMPx

BMPx is the codename for the next generation of BMP. It has been written from scratch to shed off the XMMS le BMP is discontinued, now enjoy BMPx

BMPx is the codename for the next generation of BMP. It has been written from scratch to shed off the XMMS legacy that had been restricting our creativity. BMPx reimplements and extends the BMP user interface (UI) we have refined over the years. Existing BMP users should feel right at home with BMPx. gacy that had been restricting our creativity. BMPx reimplements and extends the BMP user interface (UI) we have refined over the years. Existing BMP users should feel right at home with BMPx.  

I'll have to try Audacious and BMPx in Kubuntu, but I have to say, I'm pretty depressed by the state of media players in Lin these days.  

> On the main screen, it displays file bitrate and mono/stereo. Also, if you click the "I" button on the left, it displays all of the ID3v2 data for that file.

That's a handy shortcut.  It beats right-clicking on the file and choosing View Track Details.  The other options on that OAIDV line are Options, Author (restarts the status line that has artist & song), Double Size and Visualizations shortcut.

---

### Post by GnuSense on 2006-11-06
Unfortunately the Double Size option doesn't do anything in BMP.  And using the suggested [method]("http://bmp.beep-media-player.org/index.php/FAQ#How_do_I_migrate_my_XMMS_configuration.3F") of transfering the ~/.xmms/config file over to the ~/.bmp directory didn't work (there wasn't such a file and putting one there didn't seem to change much).  

BMP, which is no longer being actively developed, [forked]("http://bmp.beep-media-player.org/index.php/FAQ#How_did_the_fork_happen.3F") off of XMMS because XMMS was sticking with GTK+1 after GTK+2 came along and because they were skeptical of XMMS2 (justly so, it seems like. since the last development release of XMMS2 was in April 2005 and it was "NOT yet ready for public consumption"}.  There does, however, appear to be some signs of life on the XMMS2 IRC channel.

XMMS doesn't look like it is a going concern either.  The last two entries on the XMMS page were a picture of an old guy in a canoe waving with the enigmatic header "Bye Bye Gentoo!" and this fairly bizarre snippet from April: > No news.

DING DONG, IT'S APRIL 27TH AND ALL IS QUIET.

I would like to take the opportunity to say hello to my mother, Hi mother!

In other news there are no news. And as such, I have no reason whatsoever to actually press 'Add Post'.

But.. since we're a nifty old cool gtk+1 application, we have to be insane to actually keep this site up. We SHOULD hide xmms on a obscure japaneese ftp server and you can all go ftpsearch.. oh, I guess we outlived ftpsearch, never mind.

My slippers are gone. Please find them. The XMMS IRC channel seems dead.  The only sign of life I saw was the topic line: > (14:56:05) The topic for #xmms is: Mention gentoo and get kickbanned 

Too bad really, since XMMS is still wildly popular, and was voted Favourite Audio Tool by the readers of LinuxJournal for 5 years in a row until 2004.

---

### Post by Perfect Storm on 2006-11-07
I don't quiet understand your point when you say you're dissapointed with the state of players in linux and I havn't the issue(s) you said with audacious. How did you compile it? Don't use the --enable-gnome-vfs flag as it's full of bugs and have been removed. How long since it that you have tried it?
And it's been old news (2 years or so) that xmms and bmp is dead, so I don't know what you're complain about.

Most people want players like Listening and amarok so it's common sense that alot of development and support goes that way.

---

### Post by GnuSense on 2006-11-15
> I havn't the issue(s) you said with audacious. How did you compile it? Don't use the --enable-gnome-vfs flag as it's full of bugs and have been removed. How long since it that you have tried it? I didn't compile it, I installed it from the Blag repository and it was borked.  

I really don't want to have to compile a main stream media player, particularly if I'm using a distro like Ubuntu which is supposed to be easy to use and have a vast selection of software.  

I just checked and neither bmpx nor audacious are in the standard set of Ubuntu repos (i.e universe, backports, main, updates, multiverse, whatever garbage Automatix2 writes there, etc.)  I gather that they are or soon will be in Etch, I can't wait for December, Etch going stable is gonna be better than Xmas.  Anywho, according to the Audacious [downloads page]("http://audacious-media-player.org/Downloads") you can get it by enabling a special experimental repository, but it still won't work out of the box in Ubuntu.  With BMPX the situation is slightly better, you can install it by enabling a special repository.  With its dependencies it was a 21.1 MB download and sucked up 92.9MB of hard drive space.  > # apt-get install bmpx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libboost-regex1.33.1 libglademm-2.4-1c2a libraptor1
Recommended packages:
  raptor-utils
The following NEW packages will be installed:
  bmpx libboost-regex1.33.1 libglademm-2.4-1c2a libraptor1
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.1MB of archives.
After unpacking 92.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  bmpx
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe libboost-regex1.33.1 1.33.1-7ubuntu1 [538kB]
Get:2 [http://files.beep-media-player.org](http://files.beep-media-player.org) edgy/main bmpx 0.34.4-bmp0ubuntu1 [20.4MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libglademm-2.4-1c2a 2.6.3-0ubuntu2 [22.3kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libraptor1 1.4.9-2 [143kB]
Fetched 21.1MB in 1m43s (204kB/s)
Selecting previously deselected package libboost-regex1.33.1.
(Reading database ... 229920 files and directories currently installed.)
SNIP
Setting up bmpx (0.34.4-bmp0ubuntu1) ...
  It is utterly different than the earlier versions of BMPX I have seen. Instead of being a kind of spindly lame XMMS clone with far fewer options, it is now a ridiculous do-it-all suite with Podcast, Icecast, Fast.FM, just about everything you could want except being a fast simple media player that you can start quickly by double clicking on a file.  Trying to start the program by associating it with MP3s would just start the program (if you were lucky), then you had to navigate to where your file was (and it couldn't remember said folder from session to session). In fact, trying to use it that way was a great way to spawn a bunch of processes with no visible GUI program.  Simply doing a *kill process* or *kill all* didn't even stop one of the processes.  I had to use a *kill -9* on it.  Or if the GUI interface was still visible I could point it at a relative playlist (m3u).  That would cause the whole stack to go tits up.  If you want, you can see a screen shot of the whole ugly thing complete with some of the processes that it spawns [here]("http://us.f13.yahoofs.com/bc/43dffae6m21acfa04/bc/public/snapshot3.jpg?BCf3tWFBy6zp18Tz").

Oh, and as near as I can tell, the BMPX player doesn't display ANY tag metadata these days (I'm not sure, because when I tried to navigate to a directory with MP3s it died again, but as I recall it only had very few options and the only one concerning tags was simply to strip them away, and I didn't see any way to elicit metadata).  Just how many sluggish, buggy Amarok/Juk/Rythmbox/Banshee/Quod Libet iTunes-wannabe library music management systems do developers think we need?  

I remembered from my Windows days that zinf wasn't too bad, so I installed it from the Edgy repositories.  It crapped out immediately. >  $ zinf

(<unknown>:8943): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8943): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8943): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8943): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1835 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


> Most people want players like Listening and amarok so it's common sense that alot of development and support goes that way.Most belike, but may thousands want something that they can start quickly by double clicking on a file in a file manager that can read a wide variety of files and read ID3V2 tags and use relative playlists.  Not too much to ask, I would think.  The only program that meets these requirements in Linux (that I know about) is XMMS and it is moribund and increasingly unsupported by modern distros.

---

### Post by GnuSense on 2006-11-19
> Unfortunately, at least on my machine, the Double Size option just freezes XMMS and I have to kill the process.  Apparently it is not just on my machine, but rather a known [bug]("https://launchpad.net/distros/ubuntu/+source/xmms/+bug/63144").  The work around is to beckon the program with the following verbiage:
> export XLIB_SKIP_ARGB_VISUALS=1 && xmms

---

### Post by yigal.weinstein on 2007-01-30
This is a few months later than the last post but I thought I should thank everyone for letting me change from that ugly X motif to gtk2 environment.  xmms ---> audacious.  However mpd w/mpc is quite nice for my collections for streaming audacious is great.

---

### Post by quirt3 on 2007-01-30
I suggest Listen. Better then iTunes!
[http://listengnome.free.fr/](http://listengnome.free.fr/)

> **GnuSense said:**
> 
 I gather that they are or soon will be in Etch, I can't wait for December, Etch going stable is gonna be better than Xmas. 

Yeah, that was when, In y oppinion, Linux outdid Windows, I start Linux full time.

---

