---
title: "Quick Time and Windows Media not launching within FF"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-09-05
OK, so this must be one of the most frequently asked questions.  Since 99.9% of all media on the web that launches in a browser is either Windows Media, Quick Time or Real Player, how do I configure Fire Fox to ensure all work.

Somehow, probably a fluke, RealPlayer actually works, but according to Yahoo Movies (trying to watch the movie previews) it tells me I have RealPlayer 10 installed, no Windows Media and no Quicktime and so, doesn't allow me to watch its clips.

The reality is, without QT and WMV, the internet experience is incomplete.

---

### Post by Dr. Nick on 2006-09-05
look into mplayer plugin for firefox, you will also need codecs for wmv and qt which are in the w32codecs package

---

### Post by Zoolook on 2006-09-05
I have the w32codecs package installed.  When I download even a normal trailer from a site such as IGN using WMV codec, all I get is sound - no picture.  I haven't tried a HD trailer yet.

---

### Post by Dr. Nick on 2006-09-05
are you using totem? I never really had good luck with totem and wmv video. I would try mplayer instead and see if it worked, or vlc. Both probably in the universe repo

---

### Post by Zoolook on 2006-09-05
I am having all sorts of fun with this codec and player lark.

I cannot install Helix for this reason

E: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb: trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay

I cannot install the Totem Gstreamer Firefox plugin for this reason

totem-gstreamer-firefox-plugin:
  Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed

Nice version control there guys.

So should I have Gstreamer 1.4.3 installed, but with no Firefox support, or totem-xine 1.4.1 installed...

After Installing Totem-xine 1.4.1 yahoo downgraded my Realplayer ability to version 7.0 from version 10.

I think media codecs are something that need a bit of work... eh?

---

### Post by linuxguiri on 2006-09-10
you can get totem-gstreamer-firefox-plugin_1.4.3-0ubuntu1_i386.deb here:
[https://launchpad.net/distros/ubuntu/dapper/i386/totem-gstreamer-firefox-plugin/1.4.3-0ubuntu1](https://launchpad.net/distros/ubuntu/dapper/i386/totem-gstreamer-firefox-plugin/1.4.3-0ubuntu1)

---

### Post by Blondie on 2006-09-10
If you want to do it an easy way use [Automatix]("http://www.getautomatix.com/") and select Multimedia Codecs and Mplayer & FF plugin.

---

