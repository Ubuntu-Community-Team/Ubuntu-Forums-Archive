---
title: "My next step"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-05
It looks like I have my video card installed correctly, It looks like I get sound from my speakers. I want to rip my entire CD collection to my hard drive. But before I do that, I really could use some help getting the best experience out of that. I will also want to watch DVD's and video files as well. I also got rid of the brown desktop but I would like to know where I can find themes as well.

Need recommendations on which jukebox is the best. I want to be able to search on Album Title, Artist, and perhaps even song. Other stuff would be a plus but those matter the most. If there isn't a jukebox that will do that perhaps there is some sort of music collection software out there? In Windows I used Windows Media Player and Win Amp. I was not satisfied with the sound out of either one. And I have a good sound card which unfortunately doesn't work in Linux unless someone knows how to make it work and can tell me. It is a Creative Extreme Gamer X-fi.  If the ripping process is different than in windows, I need to know how to that too.

Also, will need to know what codecs etc that I should install. 

After that I would like to set up e-mail. I have never used outlook, or outlook express because quite franky, I didn't know how to set them up. I have a hotmail e-mail account, a comcast e-mail account, and a yahoo email account. I am willing to even change my email addresses and use something else if someone could teach me how to do this.

After that, I would like to work on setting up a virtual machine so that I can run windows in Linux, possibly to play a game or two. I also have a program that I want to set my wife up with a program that she needs for work. 

Can anyone help or direct me to where I can find this information in very simple terms.

---

### Post by eternalsword on 2007-11-05
I personally use gmail with thunderbird.  gmail's site has instructions for how to set things up in thunderbird.  If I recall correctly thunderbird 2 adds a little help in it's accounts manager in setting up gmail.  

Playing games in virtual machines is currently not possible as there is no 3d rendering in vmware, but running windows in a virtual machine is not that hard (assuming you have a legal key and the installation disc).  You'll want to install vmware-server, not vmware-player.  

As far as I know, Creative Extreme Gamer X-fi is indeed not yet supported.

You can find themes at [http://www.gnome-look.org/](http://www.gnome-look.org/)

You can find some useful info at [https://help.ubuntu.com/7.04/musicvideophotos/C/index.html](https://help.ubuntu.com/7.04/musicvideophotos/C/index.html) for setting up your media.

---

### Post by daimaru on 2007-11-05
ok i guess at the time i'm finished writing this someone else will already have responded to you. but here it goes. 
**1**. music player: either use amarok (either use synaptic package manager under system -> admin or terminal)
```
sudo apt-get install amarok
```
well i like amarok but there are other music players.
**2**
go to [http://www.medibuntu.org]("http://www.medibuntu.org")
click repository howto , add the medibunt repository as it says under gutsy gibbon 7.10 then either search in synaptic or use terminal to install libdvdcss. either way you just have to read what they say on the page. that will get you to watch dvds and when you install the w32cocdecs it will let you watch all the encodes videos you want. you can also install google earth , skype, realplayer etc just follow directions.
**3**
gaming: ok i have a nvidia graphics card and i am a first person shooter kind of guy so i have steam installed and counter strike source (using wine) . also Enemy territory quake wars. but for all other games you will have to see if they have a  linux installer (quake does and some other games do too)  or if they work through "wine". 
**4**
for email i recommend mozilla thunderbird (thats just my choice i dont like evolution) but its up to you. just to tell you in advance if you want to use any email program you have to have a pop3 account. i know that yahoo does not support this anymore, they used to. but if you get a google mail account you can use pop3. 
**5:virtual machine**
well virtualbox is free (its in synaptic just search for it or go to webpage) and  lets you run windows in ubuntu and you can even seamlessly integrate it, but i haven't gotten that to work yet. just installed it yesterday so... theres a lot of threads in this forum about it though and there are answers, just havent gotten to reading them all.

and here are some links that are very usefull for installing new stuff etc
[http://ubuntuguide.org]("http://ubuntuguide.org")

[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon")

as for programs (windows programs) "wine" can install windows programs on linux systems (not all but you can always try) check wine.hq website for info on apps that work . 

hope it helps a bit

EDIT:
of course you have to install wine first just search for wine in synaptic

---

### Post by bgast1 on 2007-11-05
Does Amarok work in Gnome? I am an absolute beginner with Linux, but I only saw it in KDE. So far I haven't had much problem using Gnome.

---

### Post by Dr Small on 2007-11-05
Yes. You can run KDE apps in Gnome.

---

### Post by Maestro23 on 2007-11-05
> **bgast1 said:**
> Does Amarok work in Gnome? I am an absolute beginner with Linux, but I only saw it in KDE. So far I haven't had much problem using Gnome.

Yes, I use it in Gnome with no problems.  You can also check out Banshee and Exaile as well.

Banshee: [http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

Exaile: [http://www.exaile.org/](http://www.exaile.org/)

---

### Post by daimaru on 2007-11-05
amarok is just a suggestion you could also use exaile or any other prog. i just like amarok. 
i also love streamtuner and streamripper . which lets you record internet radio as mp3 files with tags and all :)

---

### Post by mivo on 2007-11-05
> **bgast1 said:**
> Also, will need to know what codecs etc that I should install. 

Installing the totem-xine package took care of all of my codec needs, and it provides a nice player for songs and videos. The codecs will work with dedicated jukeboxes like Exaile (this would be my recommendation if you use Gnome). (For watching DVDs you will need an additional codec from the Medibuntu repository -- ask if you need details here. Totem-Xine also makes a good player for commercial DVDs.)

> After that, I would like to work on setting up a virtual machine so that I can run windows in Linux, possibly to play a game or two. I also have a program that I want to set my wife up with a program that she needs for work. 

Wine is the better approach. For gaming, unless you absolutely must play a specific Windows-only game, consider getting native Linux games. There are great ones available for free (Nexuiz, Battle for Wesnoth, OpenArena, etc.) and also commercial titles: Neverwinter Nights, Unreal Tournament 2004 and 2008, Dominions 3, X3 (Elite), and others. Wine also runs many Windows programs fine if you depend on them, but there are Linux equivalents in many cases.

Welcome to Ubuntu. :)

---

### Post by bgast1 on 2007-11-05
I remember when I was trying to use Linux before, and was unsuccessful that Amarok was the most recommended player for media. I suppose that was for a reason. I have gotten it from synaptic and I am going to give it a whirl. 

What about for video and DVD. I used VLC in windows and also had it installed on an earlier installation. You wouldn't believe it, I went through PCLOS, Suse, Ubuntu first, Mepis, and finally have ended up back with Ubuntu. Thanks everyone for the support. Actually at one of the other distro's forums they dump on Ubuntu pretty badly. It's a shame because actually my exerience is that you all are the best!

---

### Post by Dr Small on 2007-11-05
I would recommend VLC for DVD's. It works great out of the box, but you can get Totem to play them with some tweaking ;)

---

### Post by bgast1 on 2007-11-05
The games that I currently play are Command and Conquer - Tiberium Wars, Command and Conquer Decade, Civilization III and IV, Doom 3, Fear (paid for downloaded version, I never made discs) Half Life 2 (paid for downloaded version, I never made discs for that either. I don't even know how.) Tiger Woods PGA Tour 2008, 2007, Links 2003. I want to get Bioshock too. 

I have tried Cedega in the past and had nothing but problems. One of the reasons that I went back to windows exclusively.

---

### Post by mivo on 2007-11-05
To enable DVD playback in Totem (I really recommend the Xine version, not the GStreamer one) or VCL, you need a specific library. To install it, do this in a terminal window:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then add the GPG key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

This adds the Medibuntu repository. The package you want is **libdvdcss2**.

DVD playback should now work in all players that support it. :)

---

### Post by Maestro23 on 2007-11-05
> **mivo said:**
> To enable DVD playback in Totem (I really recommend the Xine version, not the GStreamer one) or VCL, you need a specific library. To install it, do this in a terminal window:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then add the GPG key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

This adds the Medibuntu repository. The package you want is **libdvdcss2**.

DVD playback should now work in all players that support it. :)

Just to tack on the source doc: [https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29)

---

### Post by daimaru on 2007-11-05
@bgast1 
hl2 and doom should be no problem. doom3 has a linux installer and hl2 works great with wine.

---

### Post by bgast1 on 2007-11-05
I heard that Doom 3 has a linux installer but I don't have the foggiest idea how to do it.

---

### Post by Maestro23 on 2007-11-05
> **bgast1 said:**
> I heard that Doom 3 has a linux installer but I don't have the foggiest idea how to do it.

If it's a .run file:

> sudo chmod + x filename.run

./filename.run

---

### Post by bgast1 on 2007-11-06
I don't even know what kind of file it is. I just remember something about this about 6 months ago when I tried unsuccessfully to switch to Linux.

---

