---
title: "Playing music and movies"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by circa85 on 2006-08-22
I've just installed Ubuntu 6.06 on my dell 700m laptop after winXP got messed up. I am deployed currently and dont have an internet connection available for my laptop. 
Alright, I know it is addressed a lot in different threads, but i need to play mp3s, wma, wmv, avi,divx and encrypted DVDs. I can burn cds or put stuff on a flash drive with the software/binaries/ports/codecs that i need and put them on my laptop but i have no idea what i really need and where to get it. I would really appreciate any help with this. 
I have no real experience with linux besides changing theme colors and installing both SuSE and Ubuntu on my laptop in the past day. 

Also, my monitor should have a resoloution of 1280x800 but its at a lower default resoloution. Any answers?:D 
Thanks a lot.

---

### Post by Major_Stitch on 2006-08-22
Go to this site: [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

There see what codec do you need, write them down and go (from a computer with internet access) to [Ubuntu Packages]("http://packages.ubuntu.com/") and download what is needed!

---

### Post by encompass on 2006-08-22
Thank you for serving...
To bad you can't jsut plug into a lan and get this information... it would be ALOT easier.
automatix is your best bet.  Just search the forums here and it will show you.  BUT you much have an internet connection.  It will get everything you requested working in a snap.
Outside of that... we can try to do each thing manually.Yikes.
Ubuntu is built for the internet sir.
Perhaps everyone can get a list of packages to get with wget and make a scipt for you.

---

### Post by Major_Stitch on 2006-08-22
> **encompass said:**
> 
automatix is your best bet. (...)  BUT you must have an internet connection.

It really isn't neccessary. Everything can be put from another computer and he doesn't need anything afterwards if its just for multimedia.

---

### Post by circa85 on 2006-08-22
I went to the restricted formats page you guys linked to and went saw the "How to Make Things Work in a Hurry" (how convenient ;) ). I downloaded all the stuff under Ubuntu except win32 because it didn’t show up when I entered it in search in the package search. So now I have seven .deb files. Once I get them on my laptop what do I need to do to install them?

Do i need Gdeb to install thses?

Thank you all for your quick replies, I really do appreciate you help.

---

### Post by circa85 on 2006-08-22
It says i need a bunch of different lib files. But half of them i can't find.

---

### Post by 3rdalbum on 2006-08-23
Those library files should be on the Packages site. If you're having trouble finding them, they are linked from the pages which contain those 7 .deb files.

---

### Post by derred on 2006-08-23
You can use apt to just download the programs you want in .deb format. then you just move them to the laptop(burn them to a CD or whatever) and install them with dpkg.

I recommend that you install: 

Codecs:
   gstreamer0.10-plugins-ugly mpg321 vorbis-tools gstreamer0.10-ffmpeg gstreamer0.10-gl libxine-main1 libxine-extracodecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll

Proprietary format:
   w32codecs
Players:
   totem-gstreamer vlc mplayer gxine xmms
Plug-ins:
   mozilla-mplayer
DVD(*caution may be ilegal):
   libdvdread3 regionset libdvdcss2*

Hope this helps!;)

---

### Post by derred on 2006-08-23
> **circa85 said:**
> I went to the restricted formats page you guys linked to and went saw the "How to Make Things Work in a Hurry" (how convenient ;) ). I downloaded all the stuff under Ubuntu except win32 because it didn’t show up when I entered it in search in the package search. So now I have seven .deb files. Once I get them on my laptop what do I need to do to install them?

Do i need Gdeb to install thses?

Thank you all for your quick replies, I really do appreciate you help.

You just have to use dpkg. Go to the directory where you have the .deb files in a terminal and type in sudo "dpkg -i package_name.deb" just replace package_name with the name of the one you wish to install or to install them all at once *.deb

---

### Post by benfindlay on 2006-08-23
You could just download and install vlc media player (videolan controller) from their website (think its [http://www.videolan.org]("http://www.videolan.org")). It will play just about anything, is very simple to use and is FREE. It also uses next to no memory when compared to other proprietary media players, so if your system is old it will run fine too!

---

