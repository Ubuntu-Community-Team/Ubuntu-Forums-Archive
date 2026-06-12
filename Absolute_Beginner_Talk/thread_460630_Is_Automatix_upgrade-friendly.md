---
title: "Is Automatix upgrade-friendly?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-31
I'm quite capable of going after all the nice plugins on my own, but I was thinking about trying out Automatix.  But will installing things through Automatix make it more likely for things to break when I upgrade to the next version of Ubuntu?

---

### Post by drowner on 2007-05-31
15 pages coming right up

Basically, the official stance is that Automatix is not supported. It is designed to help you install non-free codecs and the like easily. Others will tell you it doens't make it any easier.

Automatix fans will tell you it is no problem, others will tell you it could mess around with your sources etc.

In my opinion, if you are capable of installing the things yourself, then i suggest do it the 'official' way.

---

### Post by raja on 2007-05-31
There have been problems reported definitely. But more than that, I think it is sort of obsolete with the current Ubuntu - everything is easy to install from the repositories anyway. For multimedia codecs, look at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs).

---

### Post by Crafty Kisses on 2007-05-31
> **laptoplinux said:**
> I'm quite capable of going after all the nice plugins on my own, but I was thinking about trying out Automatix.  But will installing things through Automatix make it more likely for things to break when I upgrade to the next version of Ubuntu?

In some sense yes, but others no. 
I would recommend it for the codecs and installing the messengers but that's pretty much it.

---

### Post by starcraft.man on 2007-05-31
LOL at drowner.

I'm not gonna start nailing Automatix, all I will say is that I have seen threads with people who have happened to have had problems after using it, you draw your own conclusions.

If your perfectly capable of using the terminal/synaptic for getting all your packages I don't really see any reason for you to install Automatix, its just a GUI to install things into Ubuntu. Plus I doubly agree with Raja, automatix really isn't needed much anymore in Ubuntu, things are easy to install with Envy/Restricted driver management for drivers, and Ubuntuguide answers all your questions about installing programs and simple tasks :).

No need to install an extra (redundant) program if you know you can do it all yourself, thats what I think at least.

Edit: Installing messengers codename? Whats wrong with gaim in by default and aMSN just a click away with synaptic?

---

### Post by loathsome on 2007-05-31
> **Codename said:**
> In some sense yes, but others no. 
I would recommend it for the codecs and installing the messengers but that's pretty much it.
Nah. I suggest you rather do something like this: ```
sudo apt-get install -y gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-pitfdll gstreamer0.10-sdl libxine-extracodecs
```

I'm sure the above command will play 99% of all available media files out there ;-)

---

### Post by deadgobby on 2007-05-31
I like Automatix and it takes about an hour for the script to run and you can grab all the restricted codecs all in one shot. It is a 3rd party program and is not supported by Ubie. Yet, a very good script program and well taken care of. Till the author no longer wants to support it or has a kid and that is it. Restricted formates are done by installing by your own will. Till some on screams foul and no longer can install them with out paying some cash for them. So take it like a grain of salt. 
Gobby

---

### Post by earobinson on 2007-05-31
In the past many users have reported that automatix is not upgrade friendly, but the project has come a long long way. Im sure the devs are doing the best they can to make it so. We wont really know till another upgrade happens.

---

### Post by deadgobby on 2007-05-31
I would use AT with out question. Before AT was Easy Ubuntu. Man that program is slick and saved me from a lot of work. That was back from the Breezy days and just started to learn on Linux. At saves a lot of time of going of going from "Oh I F up" to where I want it to be.
Gobby

---

### Post by STREETURCHINE on 2007-05-31
you can use automatix till you are ready to upgrade then uninstall it as it will need to be reinstalled for the new version of ubuntu anyway.
then remove automatix from the repo's (sources.list)
and then comment out any unofficial repo and then the upgrade should go ok.

i have a seperate home partition so i wait for the dvd and do a fresh install of the root partition and wallah all is good.

---

