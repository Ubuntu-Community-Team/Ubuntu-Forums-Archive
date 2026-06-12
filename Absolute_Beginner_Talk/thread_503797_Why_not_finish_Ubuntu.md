---
title: "Why not finish Ubuntu?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by 4seasonphotos on 2007-07-18
I am a Ubuntu fan.. But I am a little irritated by it as well.. I have had a problem with my browsers being able to show video there are no plug ins for it. So I cannot watch any video on the web using Ubuntu..  This made me come to the conclusion that if Linux at all wants to do better then Microsoft then they have to finish the projects they start making everything work..  I must also say Ubuntu has been the best Linux program I have used so far.. But more is needed to be better then windows.. 

I have tried Lindows but it never actually worked when I loaded it. 

If anyone knows why I am not able to watch video in any web browser I have in Ubuntu please tell me what exactly will fix that..

---

### Post by dreadlord_chris on 2007-07-18
How about some examples - because, so far, I've been able to watch most videos on the net...

---

### Post by w4ett on 2007-07-18
Sounds like flash and the media codecs are not installed.  Have you installed flash?

---

### Post by Bablefish on 2007-07-18
I think his trouble is with the plugins such as Flash and Java. Remember these also have to be installed in Windows like Ubuntu it is due to copyright issues. They may be free programs but only for the cusumer, in fact no other company other than Adobe can sell or distrubute them. You can get both from Add/Remove

---

### Post by sancho panza on 2007-07-18
Hey...I just answered that [here]("http://ubuntuforums.org/showthread.php?t=503789"). Is that what you were looking for?

---

### Post by 4seasonphotos on 2007-07-18
> **dreadlord_chris said:**
> How about some examples - because, so far, I've been able to watch most videos on the net...


The only example I can give you is that it tells me I need to download a plugin to see video it says click here to download plugin I click and nothing happens..

---

### Post by aysiu on 2007-07-18
Most of the popular codecs that allow you to play multimedia are proprietary, and thus not included with Ubuntu by default (for usually a mix of ideological and legal reasons).

You can install them yourself, you can use a script to install them, or you can use another distro that doesn't share the same legal or ideological approach to proprietary codecs: Linux Mint, Mepis, or PCLinuxOS, for example.

---

### Post by testube_babies on 2007-07-18
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)


...and Lindows is linux, too.  It was made to look like Windows, but it's pure Linux.  It was also renamed to Linspire a few years back, so I assume your Lindows copy is extremely outdated.

---

### Post by mike102282 on 2007-07-18
> **4seasonphotos said:**
> I am a Ubuntu fan.. But I am a little irritated by it as well.. I have had a problem with my browsers being able to show video there are no plug ins for it. So I cannot watch any video on the web using Ubuntu..  This made me come to the conclusion that if Linux at all wants to do better then Microsoft then they have to finish the projects they start making everything work..  I must also say Ubuntu has been the best Linux program I have used so far.. But more is needed to be better then windows.. 

I have tried Lindows but it never actually worked when I loaded it. 

If anyone knows why I am not able to watch video in any web browser I have in Ubuntu please tell me what exactly will fix that..

Have you tryed the latest freespire 1.9 it is based off of ubuntu and works great with video.

---

### Post by Majorix on 2007-07-18
You could try installing the mplayer-plugin for firefox. That will play video files on the web.

---

### Post by 4seasonphotos on 2007-07-18
> **Majorix said:**
> You could try installing the mplayer-plugin for firefox. That will play video files on the web.


But how exactly is that done where and how?  I have been trying to do this the whole time nothing seems to work..

---

### Post by dpar on 2007-07-18
Applications>Add/Remove

You will find them under video

---

### Post by aysiu on 2007-07-18
> **4seasonphotos said:**
> But how exactly is that done where and how?  I have been trying to do this the whole time nothing seems to work..
These two links should help you understand software installation better:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by tahuya_rat on 2007-07-18
> **4seasonphotos said:**
> But how exactly is that done where and how?  I have been trying to do this the whole time nothing seems to work..

You may have luck with [Automatix]("http://www.getautomatix.com/"), a GUI based installer for all kinds of nifty add-ons, including the ones you seem to be having problems with.

---

### Post by gn2 on 2007-07-18
> **tahuya_rat said:**
> You may have luck with [Automatix]("http://www.getautomatix.com/"), a GUI based installer for all kinds of nifty add-ons, 


Is there another way apart from Automatix? LoL :)

---

### Post by Nythain on 2007-07-18
make sure you have all of your repositories enabled... and add the medibuntu repo
in terminal type
```
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

```
replacing feisty with edgy or dapper if you use those

then, from the terminal still you can type
```

sudo apt-get install flashplugin-nonfree mozilla-mplayer w32codecs

```that should get you going to watch almost anything on the web at least through firefox

---

### Post by dpar on 2007-07-18
> Is there another way apart from Automatix? LoL 

The right way????:biggrin:

---

### Post by 4seasonphotos on 2007-07-18
> **Nythain said:**
> make sure you have all of your repositories enabled... and add the medibuntu repo
in terminal type
```
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

```
replacing feisty with edgy or dapper if you use those

then, from the terminal still you can type
```

sudo apt-get install flashplugin-nonfree mozilla-mplayer w32codecs

```that should get you going to watch almost anything on the web at least through firefox



Hello I tried to do what you said but maybe I missed something: Here's what it said..   

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
david@david-desktop:~$ sudo apt-get install flashplugin-nonfree mozilla-mplayer w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

Does that make sense to you?

I don't know what you mean by repositories?

---

### Post by aysiu on 2007-07-18
> **4seasonphotos said:**
> 
I don't know what you mean by repositories? Read this, then:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by 4seasonphotos on 2007-07-18
I loaded on automatix2 but it still is not fixed...  Now I also noticed when I tried to use a mic on skype that that does not work but I can hear some sound..   I thank you guys for at least trying to help me that is appreciated.. :)



> **tahuya_rat said:**
> You may have luck with [Automatix]("http://www.getautomatix.com/"), a GUI based installer for all kinds of nifty add-ons, including the ones you seem to be having problems with.

---

### Post by bigboy_pdb on 2007-07-19
I think that you should first try installing the GStreamer plugins. You can do this by going to "Applications -> Add/Remove...". Select "Sound & Video" and then click the boxes beside the GStreamer plugins to mark them to be installed. Following this click "Apply"

For the flash plugin, go to "System -> Administration -> Synaptic Package Manager". Search for flash, right click on the "flashplugin-nonfree" package and click "Mark for Installation", and then click "Apply".

---

### Post by jonathanmotes on 2007-07-19
You can use Automatix to install Swiftfox (a Linux optimized "version" of Firefox) and Swiftfox media plugins. Install Swiftfox first, then the plugins. The only thing you really have to install after that really is Flash (You can use Add/Remove Programs to install it). It has worked much better than anything else I've tried. Flash videos, for example, load much faster for me  - but there is some controversy over the author refusing to release some of his source code -- I think.

---

### Post by fatfranko on 2007-07-19
do you have 32bit or 64bit ubuntu?  one of my comps is 64bit and i had a hell of a time installing flash.  if youre running 64bit ubuntu then you especially want to listen to jonathanmotes and install swiftfox because its a 32bit browser and it worked great on my 64bit comp.

---

### Post by antiemptyv on 2007-07-19
> **4seasonphotos said:**
> The only example I can give you is that it tells me I need to download a plugin to see video it says click here to download plugin I click and nothing happens..

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by 4seasonphotos on 2007-07-19
I loaded Swift fox on but no difference. I have 64 bit setup.. for the moment I will put that on hold the net vodeo problem.. Now I have some trouble with my audio I may have always had trouble since I have Feisty installed.. I do get audio on my pc sound but I cannopt play cd's or use the microphone for skype.. I looked into whether my system see a sound card and I looked in terminal... It says my video card NVidia is my sound card... But My pc really has realtek for my sound card.. I don't know why I get pc sounds opening windows closing etc.. But no sound from a cd??  It's a mystery to me.. When I put a cd in it reads it cause I can see the readout of who it is in the cd player.  Somehow either something is muted somewhere but I don't know where.. I looked in volume control and nothing there is muted.. Any ideas?? 


Thanks!

---

### Post by 4seasonphotos on 2007-07-19
Just to update you all I found out that sound in Ubuntu works but when I log in using KDE 3.5.6 then I no longer have all the sound..  But if I log in through Gnome it works..  Any thoughts??

---

### Post by asmoore82 on 2007-07-19
To get sound from audio CD's on the default setup you NEED to have the AUDIO CABLE installed in your system that connects the CD drive to the Sound card.

about the nVidia sound card thing... double check what it says of course but linux always tells you who actually  made the chips on your hardware; not simply the brand name of the hardware.

---

### Post by 4seasonphotos on 2007-07-19
Thanks but the cable is already connected. I am already getting sound through the Gnome Ubuntu interface. But when it comes to the KDE 3.5 Desktop then I don't get sound from the player although I get pc sounds..  It's a tough one to figure..

---

### Post by asmoore82 on 2007-07-20
oops.. duh! on my part ...

naturally there is also a specialized mixer channel for the specialized audio cable.... it needs to be unmuted and turned up; it's either called "CD" or "AUX" in the mixer

---

### Post by Lord_Dicranius on 2007-07-20
> Thanks but the cable is already connected. I am already getting sound through the Gnome Ubuntu interface. But when it comes to the KDE 3.5 Desktop then I don't get sound from the player although I get pc sounds.. It's a tough one to figure..

I'm at work right now and don't have a Kubuntu box in front of me, so this is from memory...

I had a problem with sound in KDE before.  At the terminal, type
```
alsamixer
```
...and it should bring up a command line based volume mixer.  Using the arrows keys, scroll to the right making sure nothing's muted. I found that all the way to the right, there was a channel that was muted and caused ALL sound to be muted: speakers and headphones.  I believe green means they're unmuted, and you can unmute by pressing the "m" key.

Hope this helps.

---

### Post by 4seasonphotos on 2007-07-21
I checked that out and it appeared the only thing that was muted was the head phones so I unmuted them.. This is odd.. The sound works under gnome.. But Kde itworks only on pc actions like if I click on a window.. But with cd music nothing.. The player works though but no sound I just can figure this one out... Its a shame cause I really like KDE.. 

Do any of you guys have superkaramba?  How do you uncheck the widgets? I want to re-install a widget but it says it's installed when it is clearly not.  If you know I would appreciate help on that as well.. Thanks..

---

