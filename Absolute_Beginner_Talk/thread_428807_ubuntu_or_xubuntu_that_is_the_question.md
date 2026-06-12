---
title: "ubuntu or xubuntu that is the question"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-04-30
i just aquired an old computer with a 10g hd and 64mb ram. should i install ubuntu or should i go with xubuntu. the problem is i am out of cd's and i don't want to have to go by more just for xubuntu.

second question.. is it possible (if i should install xubuntu) to install xubuntu but then change it to xubuntu?

---

### Post by oilchangeguy on 2007-04-30
either upgrade the ram, or use damn small linux.

---

### Post by Nythain on 2007-04-30
xubuntu would be a good shot for now... make sure you download the alternate iso if they ahve one for xubuntu, cause i dont think livecd is gonna run with those specs... and yes, if you decide at any given point in time to try ubuntu or kubuntu for that matter, all you should theoretically have to do is type sudo apt-get install ubuntu-desktop in a terminal and wait for it to grab and install everything, then select gnome from your login screen (hopefully it should automatically be put there installing via apt-get) and the same applies for kubuntu, but i dont know how well kde is gonna fly on that machine

---

### Post by walesmd on 2007-04-30
Install Ubuntu off of the CD you already have.

Then install Xubuntu:
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Then get rid of Gnome:
```
sudo apt-get remove alacarte aspell binfmt-support bittorrent bluez-cups bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dcraw deskbar-applet desktop-effects dhcdbd diveintopython ekiga eog esound espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gedit gedit-common gij gij-4.1 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-keyring-manager gnome-media gnome-media-common gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager hwdb-client-common hwdb-client-gnome libaudio2 libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcucul0 libcurl3 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj7-0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomevfs2-bin libgnomevfs2-extra libgphoto2-2 libgphoto2-port0 libgpod1 libgstreamer-plugins-base0.10-0 libgtk2-perl libgtk2.0-cil libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgucharmap6 libguile-ltdl-1 libhsqldb-java libicu36 libidn11 libiec61883-0 libieee1284-3 libjaxp1.3-java libjline-java liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmusicbrainz4c2a libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon25 libnl1-pre6 libnm-util0 liboil0.3 libopal-2.2.0 libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraw1394-8 libsane libservlet2.3-java libshout3 libslab0 libsndfile1 libsoup2.2-8 libstlport5.1 libtotem-plparser1 libungif4g libvisual-0.4-0 libvorbisenc2 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager network-manager-gnome openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-desktop python-gnome2-extras python-gst0.10 python-libxml2 python-uno rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer totem-mozilla tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds update-notifier usplash-theme-ubuntu vino whois xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop
```

This was pulled from these two articles:
[http://www.psychocats.net/ubuntu/xubuntu]("http://www.psychocats.net/ubuntu/xubuntu")
[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by alexlex on 2007-04-30
> **oilchangeguy said:**
> either upgrade the ram, or use damn small linux.

there is no point in upgrading the ram. it's not worth it. i am just going to give this to my brother inlaw to use.

---

### Post by alexlex on 2007-04-30
> **walesmd said:**
> Install Ubuntu off of the CD you already have.

Then install Xubuntu:
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Then get rid of Gnome:
```
sudo apt-get remove alacarte aspell binfmt-support bittorrent bluez-cups bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dcraw deskbar-applet desktop-effects dhcdbd diveintopython ekiga eog esound espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gedit gedit-common gij gij-4.1 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-keyring-manager gnome-media gnome-media-common gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager hwdb-client-common hwdb-client-gnome libaudio2 libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcucul0 libcurl3 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj7-0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomevfs2-bin libgnomevfs2-extra libgphoto2-2 libgphoto2-port0 libgpod1 libgstreamer-plugins-base0.10-0 libgtk2-perl libgtk2.0-cil libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgucharmap6 libguile-ltdl-1 libhsqldb-java libicu36 libidn11 libiec61883-0 libieee1284-3 libjaxp1.3-java libjline-java liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmusicbrainz4c2a libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon25 libnl1-pre6 libnm-util0 liboil0.3 libopal-2.2.0 libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraw1394-8 libsane libservlet2.3-java libshout3 libslab0 libsndfile1 libsoup2.2-8 libstlport5.1 libtotem-plparser1 libungif4g libvisual-0.4-0 libvorbisenc2 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager network-manager-gnome openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-desktop python-gnome2-extras python-gst0.10 python-libxml2 python-uno rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer totem-mozilla tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds update-notifier usplash-theme-ubuntu vino whois xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop
```

This was pulled from these two articles:
[http://www.psychocats.net/ubuntu/xubuntu]("http://www.psychocats.net/ubuntu/xubuntu")
[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

thankyou. this was te kind of answer i was hopeing for :)

---

### Post by oilchangeguy on 2007-04-30
i'd still use damn small linux. because even if you do get a version of ubuntu to actually install you're not going to have a very happy computer with only 64mb of ram.

---

### Post by GrueTamer on 2007-04-30
I think that Damn Small is a limited OS, really, lacking in many areas.  I myself have a system with 64mb of ram, and I use [Zenwalk Linux]("http://zenwalk.org").  However, if slackware based OS's are too much for you, then I'd get the alternate CD version of xubuntu, because I'm not sure if your system can even boot into the livecd.  If you can boot off the cd, install, and follow walesmd's instructions, then by all means, do that.  But I strongly recommend getting more cd's, since you can get like, 10 cd's for just a few bucks.  There's more uses for cd's than just xubuntu.

Note:  In a battle between Zenwalk and Xubuntu, based on my experiences, Zenwalk has better media support out of the box, and Xubuntu has better wifi support, but Xubuntu is easier to use in general, although it lacks the advantages of slackware.  Go with what you want, it's your decision.  (If you haven't guessed, I love slackware ;) )

---

### Post by lepz on 2007-04-30
I doubt very much that 64mb of ram is going to be enough for xubuntu.

---

### Post by jklslvch on 2007-04-30
install fluxbox on that bitch

---

### Post by Wiebelhaus on 2007-04-30
> **oilchangeguy said:**
> either upgrade the ram, or use damn small linux.

/agree.

Xubuntu requires 128mb if I'm not wrong.

---

### Post by GrueTamer on 2007-04-30
> **lepz said:**
> I doubt very much that 64mb of ram is going to be enough for xubuntu.Not with the livecd, but I think that the alternate cd should be fine for it.  That's why I recommended that cd in particular.  As to running xfce or fluxbox...well, fluxbox will definitely be faster, but xfce is IMO easier to customize and stuff.  But fluxbox is definitely faster...

---

### Post by stchman on 2007-05-03
> **alexlex said:**
> i just aquired an old computer with a 10g hd and 64mb ram. should i install ubuntu or should i go with xubuntu. the problem is i am out of cd's and i don't want to have to go by more just for xubuntu.

second question.. is it possible (if i should install xubuntu) to install xubuntu but then change it to xubuntu?

What are the specs?  I have an old PC (P3-450, 256MB) I installed Xubuntu and it is still a little slow but not near as slow as Ubuntu was on it.  Go with Xubuntu as it is a little more lightweight.  Blank CDs are pretty cheap.  You can sometimes find them for around $12 for a 100 spindle.

As far as RAM, I got 256MB of PC133 RAM off ebay for $11.

---

### Post by Mairi on 2007-05-03
Puppy Linux might be another possiblity.

---

### Post by dptxp on 2007-05-03
> **Mairi said:**
> Puppy Linux might be another possiblity.

Live on RAM puppy needs 128 MB.
The Bare bone one may work.
Maybe fluxbuntu is an option.

Wndows 98 will work.:( 
Works on my P-100, 64 MB.
3 cheers for Microsoft.

---

### Post by alexlex on 2007-05-03
windows xp was installed on it and as you can imagine it was really slow. i would think that xubuntu would at least be faster than xp.

---

### Post by ZeroWing on 2007-05-03
> **dptxp said:**
> Live on RAM puppy needs 128 MB.
The Bare bone one may work.
Maybe fluxbuntu is an option.

Wndows 98 will work.:( 
Works on my P-100, 64 MB.
3 cheers for Microsoft.

 Wait, 64MB? Do they still make 64MB chips?

 Why don't you go on Ebay of check out your local hardware store. I went to mine, and bought a high-performance 1GB RAM stick for around $75. A  good 128MB stick would cost, like, ten dollars.

---

### Post by Mairi on 2007-05-03
Not to beat a dead Puppy or anything, but I think the 128 RAM issue has much to do with a live CD, just as running a live CD of Ubuntu costs more RAM than a CLI install. Just for research's sake, here are some comments of people who use the distro. It comes in more than one build too, I believe. 

[http://puppylinux.org/wikka/MinReq?show_comments=1#comments](http://puppylinux.org/wikka/MinReq?show_comments=1#comments)

Good luck and have fun bringing that box back, however you do it!

---

### Post by cage27 on 2007-05-03
muLinux is another option
[http://mulinux.dotsrc.org/](http://mulinux.dotsrc.org/)

---

### Post by Pugwash on 2007-05-03
Why not fluxbuntu? Try Fluxbuntu!

---

### Post by stchman on 2007-05-03
> **alexlex said:**
> windows xp was installed on it and as you can imagine it was really slow. i would think that xubuntu would at least be faster than xp.

Windows XP has lower system requirements that Ubuntu.  XP came out in 2002 and 1.5GHZ procs were considered top of the line.  Most folks had a PC with a 300-400MHZ proc.  XP had requirements of 300MHz proc and 128MB RAM.

Ubuntu has a requirement of at least 256MB RAM for the desktop version.  I recommend that you have at least a 1GHz proc too as my P3-450 has a hard time running Xubuntu.

So as you can see Ubuntu has greater system requirements than XP

---

### Post by dptxp on 2007-05-04
You got some useful information on your site Stchman.
I have bookmarked your site. I have to install Acrobat Reader.

---

### Post by stchman on 2007-05-04
> **dptxp said:**
> You got some useful information on your site Stchman.
I have bookmarked your site. I have to install Acrobat Reader.

Thank you very much.  I have worked very hard on the website.

I cannot take full credit for all the information though as I have done a lot of compilation.  I have done a massive amount of reading here on the forum and much googling.

---

### Post by aysiu on 2007-05-04
I wouldn't use Xubuntu or Ubuntu on 64 MB of RAM.

Fluxbox or IceWM would be better choices. Instructions for using those in Ubuntu here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Otherwise, you can use Damn Small Linux (Fluxbox) or Puppy Linux (IceWM)

---

