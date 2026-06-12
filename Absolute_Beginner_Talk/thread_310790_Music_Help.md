---
title: "Music Help"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by agonoruci on 2006-12-01
I am wondering if there is a player for Edgy that can play mp3's. If not is there any site that has a lot of ogg or oog i am not familiar with this file system. I tried Audacity but it didn't work.

---

### Post by Sef on 2006-12-01
Are you using Ubuntu, Kubuntu, or Xubuntu?

---

### Post by agonoruci on 2006-12-01
Ubuntu Edgy 6.10

---

### Post by Sef on 2006-12-01
Totem which is included in as a default application plays mp3s.   

Applications > Sound & Video > Totem Movie Player

---

### Post by msak007 on 2006-12-01
Edgy (and all versions of Ubuntu) do not ship with the capability to play MP3s out of the box, and all the media players can play MP3s once the right codecs are installed. See the [Restriced Formats]("https://help.ubuntu.com/community/RestrictedFormats") wiki for additional help. I know that once I tried to double click on an MP3 and launch it with Amarok on a fresh Edgy install, and it alerted me that the right codecs weren't installed and even offered to download / install them for me! Very cool (wasn't aware of that feature), and from what I understand that's one of the [specs]("https://blueprints.launchpad.net/distros/ubuntu/+spec/easy-codec-installation") that will be included in Feisty. So once it's implemented, the system will alert you that the needed codecs aren't installed and help you install them (or at least tell you the package names) when you attempt to open a media file.

---

### Post by agonoruci on 2006-12-01
I've tried so many codecs but can't fix the prob, does anyone know of a Media PLayer for Ubuntu Edgy that can just play MP3 withought having to hassle to get codecs.

---

### Post by HokeyFry on 2006-12-01
have you tried gstreamer0.8-plugins (that should be close to the name of the package). if not, install it, then try listening to mp3s in rhythmbox. this package will install all gstreamer plugins for linux. or if you dont want to install this then i think the package name that handles mp3s is called 'gstreamer0.8-mad' or something similar.

if youve already tried both, then sorry, i dont have an answer.

if you tried and it failed, try installing the 'gstreamer0.8-mad' package from source, i had to do that with ndiswrapper to get wireless to work... just fyi

---

### Post by agonoruci on 2006-12-01
OK the files are opening up in Rhythmbox but are goin real slow, playin real slow and I cant hear anything, but if i go on youtube and listen ot a music video it works and it doesn't go slow.

---

### Post by ngch on 2006-12-01
To play mp3, you need to install the following packages:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

After that, you can use rythmebox to play mp3.

For additional help with codecs (it's quite easy once you get the hang of installing packages), read the wiki article on [installing non-free codecs]("https://help.ubuntu.com/community/RestrictedFormats")

Have fun with Ubuntu! :-D

---

### Post by agonoruci on 2006-12-02
How do I turn that Multiverse thing on?

---

### Post by HokeyFry on 2006-12-02
sudo nano /etc/apt/sources.list

add multiverse to each line cause i cant remember which ones you add them too per se. when you start up synaptic it may give you some errors dont pay attention it will grab whatever you need those errors will mean squat

---

### Post by agonoruci on 2006-12-02
Nope, even with gstreamer0.10-plugins-ugly
and gstreamer0.10-plugins-ugly-multiverse
it doesnt work, when i try to play the song it lags a lot and I think one problem might be that I haven't installed my drivers for linux, and I dont't think i can because I have a dell computer right now, and one of my cd's has all of my drivers and I think those drivers are only for XP, well im sleeping on this one tonight, if you guys have any answers plz post I will come and check in the morning and try everything

Appcreciate this a lot.

---

### Post by HokeyFry on 2006-12-02
what are your system specs

---

### Post by equal on 2006-12-02
Hey dude, go into System > Administration > Synaptic Package Manager, click Settings > Repositories, and check off the first three boxes (I forget which are already checked by default). After that, hit Close, then hit the Refresh button in the top left of the Synaptic window that's still open, and search for gstreamer. You'll find it there. Check them off and you're good to go.

I'd like to point out, it's way easier to install [Automatix]("http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-1.11-6.10edgy_i386.deb") and let it do all the work. Just open the program that opens when you click the link.

---

### Post by agonoruci on 2006-12-02
OK so now I got tha sound workin on RhythmBox but itz broke on YouTube now, I can still see tha vid but tha sound is cut on YouTube, Oh boy.

---

### Post by ngch on 2006-12-02
Did it work before? Or was the problem around since u first installed Ubuntu?

---

### Post by agonoruci on 2006-12-02
I already got teh multiverse packages, it's just that youtube's sound is screwed for now but oh well, fix it 2morro, night everyone, hope someone comes with some ideas to fix this.

---

### Post by HokeyFry on 2006-12-02
upgrade to flash 9 that fixed it for me

search the forums for 'flash 9' and look at the howto

---

