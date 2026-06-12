---
title: "problem watching videos and seeing video players"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by endtheembargo on 2008-04-16
I'm running 7.1 on my toshiba a135 series laptop and I'm having a few issues.

1. When I log into websites like myspace and I go to people's music pages, the music player comes up on the screen but then it looks all distorted and won't play the music.

2. youtube vdeos are the same. The either come up as blank white/grey screens or they look fragmented.

what should I try?

---

### Post by john91 on 2008-04-16
```
sudo apt-get install flashplugin-nonfree
``` should work to solve your youtube and myspace issues, though I could never get youtube video controls to work properly (ie volume, skip ahead/back).  

also, check add/remove for gsreamer plugins and install all of those.  

Just so you know, I've had a much easier time in hardy than I did in gutsy getting videos and such to work.

---

### Post by bumanie on 2008-04-16
Have you installed java or gnash and multi-media codecs? If not follow this guide [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) Just be aware to choose the correct distribution when copy/pasting commands

---

### Post by endtheembargo on 2008-04-16
John91,

I did as you suggested and then I got a message that said:

flashplugin-nonfree is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

hmmm.....

---

### Post by endtheembargo on 2008-04-16
Bumanie, I'm sorry I don't mean to be a pain... I followed the link you gave me, but I'm not terribly computer saavy so I'm having trouble figuring out what to do next.

---

### Post by john91 on 2008-04-16
Odd... flashplugin-nonfree always did the trick for me on gutsy.  Definitely check add/remove for the gstreamer plugins, and take a look at medibuntu (the site bumanie provided).  Medibuntu is the best resource for anything relating to video media problems in ubuntu.

EDIT:  looks like you already took a look at bumanie's link...

make sure that you've got the medibuntu repository in your sources.list:```
cat /etc/apt/sources.list | grep medibuntu
```
if you get an output from this, then I don't know what you need to do since it would seem that you've already added the medibuntu repositories.  If you get no output, then run these commands to add the medibuntu repositories:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update
```

then, try ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by bumanie on 2008-04-16
You are not a pain. Firstly open terminal Applications --> Accessories --> terminal and copy and paste this into terminal (assuming you are using gutsy gibbon) > sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list hit enter. Then>  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update This will add medibuntu to your /etc/apt/sources.list and enable the authentication key.
Then follow this guide [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability) Then follow this to enable mozilla plugins
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)
I personally use gnash and find it fine, that's not everyone's experience however. I would advise installing vlc player as it plays almost every codec there is.
Hope this works for you.

---

### Post by endtheembargo on 2008-04-16
Thanks for your patience.

When I put the initial code in I got the following message:

"wget:  invalid option -- 0
Usage: wget [option]... [URL]..."

so then I thought, perhaps I should have typed the letter "O" rather than zero.... so I put the initial code in again, and then I get this:

"gpg: no valid OpenPGP data found"

---

### Post by bumanie on 2008-04-16
Try copying and pasting the commands in case you have made a syntax  error. Highlight the commands and then click mousewheel in terminal. This is the easiest way to copy/paste in linux. If that doesn't work, post again and I'll try to take you through the manual method of enabling medibuntu.

---

### Post by pedro_orange on 2008-04-16
Have you tried:

```
sudo apt-get install ubuntu-restricted-extras
```

This should install mp3/dvd codecs, JRE, fonts and flash player.

---

### Post by endtheembargo on 2008-04-16
wow.... now I'm really at a loss.

I finally figured out medibuntu, and I downloaded every plug-in known to man. Then I downloaded the unrestricted ones. And still, when I log into myspace and try to view/hear a music player it comes up flashy and fragmented.

---

