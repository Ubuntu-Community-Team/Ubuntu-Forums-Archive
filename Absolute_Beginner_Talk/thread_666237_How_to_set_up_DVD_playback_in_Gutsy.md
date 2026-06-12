---
title: "How to set up DVD playback in Gutsy"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by futuroimperfetto on 2008-01-13
Hello,

last year I installed version 6.10 and a friend of mine suggested me to use Automatix to install stuff easily. I did so and I installed codecs and scripts to read DVDs on my laptop. I could read commercial DVDs with no problem.

This year I made a clean install of Ubuntu 7.10 and I did not install Automatix as I had read that it is not supported software, for various reasons. I did install all the codecs I needed to watch movie clips and I did follow the instructions of the Ubuntu guide at this address

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Now. I have Totem, Mplayer and VLC installed on this computer and I still can't read DVDs properly on Gutsy.

All these players now give me back a playback which is not good. They all play the DVD, except the image is always waving, like there was an "interference on the tv" (sorry I can't describe this better).

If you know a fix to this, or a link to the ultimate guide on how to fix the DVD playback on Gutsy, I'd be happy.

Thank you very much

Cheers!

---

### Post by Malta paul on 2008-01-13
Hi, Your distorted picture I would say is probably  your codec, if you could play your video before.
I had a similar problem and fix it using the info. from  [https://help.ubuntu.com/community/Medibuntu/](https://help.ubuntu.com/community/Medibuntu/)
Hope this is some help:(

---

### Post by jargs on 2008-01-13
I get this too, when i play a DVD it keeps flickering through it... I tried that Medibuntu thing but didn't fix it.

---

### Post by nikoPSK on 2008-01-13
Try this:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. 

Regards,
nikoPSK

---

### Post by AnonCat on 2008-01-13
Install the libdvdcss library

---

### Post by nikoPSK on 2008-01-13
> **AnonCat said:**
> Install the libdvdcss library

yes, but you have to configure other things.

Regards,
nikoPSK

---

### Post by jargs on 2008-01-13
ok i got dvd playback to work, but the quality is low, the image looks more pixalated than usual. You know how to fix this?

---

### Post by nikoPSK on 2008-01-13
Unless they are pirated dvd's they shouldn't appear low unless your GPU isn't up to snuff. (I am not implying they are pirated.)

Best,
nikoPSK

---

### Post by jargs on 2008-01-13
no it is a kill bill dvd and it works perfectly on my windows install and my GPU is deffinately up to scratch.

---

### Post by nikoPSK on 2008-01-13
> **jargs said:**
> no it is a kill bill dvd and it works perfectly on my windows install and my GPU is deffinately up to scratch.

could I have a screenshot just to see the quality level.

nikoPSK

---

### Post by jargs on 2008-01-13
EDIT: photobucket changed the size i'll upload again one second.

Here:

[http://filebeam.com/2e1032ee9acdf49c840aaa53a61d2493.jpg](http://filebeam.com/2e1032ee9acdf49c840aaa53a61d2493.jpg)

---

### Post by nikoPSK on 2008-01-13
> **jargs said:**
> EDIT: photobucket changed the size i'll upload again one second.

Here:

[http://filebeam.com/2e1032ee9acdf49c840aaa53a61d2493.jpg](http://filebeam.com/2e1032ee9acdf49c840aaa53a61d2493.jpg)

maybe your res or refresh rate?

nikoPSK

---

### Post by jargs on 2008-01-13
my screen is at it's highest resolution and refresh rate is set to 60hz

---

### Post by nikoPSK on 2008-01-13
> **jargs said:**
> my screen is at it's highest resolution and refresh rate is set to 60hz

Ah, then I don't really know... :(

---

### Post by jargs on 2008-01-13
argh that sucks... can anyone else shed some light on the situation?

---

### Post by futuroimperfetto on 2008-01-13
Hello all,

I did install the Medibuntu repository and I added libdvdcss2 and I still got the flickering.

However, I succeded in fixing the issue on VLC player, following the instructions of this post:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126156.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126156.html)

Inside VLC, you go to Preferences and you click on "Advanced Options" on the bottom right of the window. Then you go to Video -> Output Modules and you switch from "default" to "OpenGL video output". After doing this modification VLC works normally.

Probably something similar can be achieved playing with the preferences of Mplayer or Totem.

So I did have all the proper codecs installed, it was just a setting inside VLC to be fixed.

Remember to change this setting again when you play .avi files (or other types of files), because it changes their quality.

I'm sorry I posted this so late. I had to go to bed right after my first post.

Thanks to nikoPSK for all the help! I haven't had the time, but I want to see how it works using totem-xine. I'll do that later and maybe post the effects.

Cheers!

---

### Post by nikoPSK on 2008-01-13
> **futuroimperfetto said:**
> Hello all,

I did install the Medibuntu repository and I added libdvdcss2 and I still got the flickering.

However, I succeded in fixing the issue on VLC player, following the instructions of this post:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126156.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126156.html)

Inside VLC, you go to Preferences and you click on "Advanced Options" on the bottom right of the window. Then you go to Video -> Output Modules and you switch from "default" to "OpenGL video output". After doing this modification VLC works normally.

Probably something similar can be achieved playing with the preferences of Mplayer or Totem.

So I did have all the proper codecs installed, it was just a setting inside VLC to be fixed.

Remember to change this setting again when you play .avi files (or other types of files), because it changes their quality.

I'm sorry I posted this so late. I had to go to bed right after my first post.

Thanks to nikoPSK for all the help! I haven't had the time, but I want to see how it works using totem-xine. I'll do that later and maybe post the effects.

Cheers!

oh, that's fine, I was going to suggest vlc next. :) I hope you get good results with xine!

Best,
nikoPSK

---

