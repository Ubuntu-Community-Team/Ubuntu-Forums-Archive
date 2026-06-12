---
title: "What now?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-07-15
I was able to succesfully install ubuntu and mount all my drives. (Thanks so much for your help)

What do I do now?

My video card can't handle Beryl and some people don't think it's necessary to install. What else can I do to make the desktop more attractive?

I would like to play mp3's as well. What player should I use/install? How? Codecs?

Any other suggestions on what else I should explore?

---

### Post by Jimmyfj on 2007-07-15
Beryl is still in its beta so until it hits Final I'd suggest you wait.

As for media players and codecs it's all to be found in Programs-->Add Remove

---

### Post by AndyCooll on 2007-07-15
Well Beryl isn't necessary, it is after all only desktop candy. You can do lots to change your desktop by visiting [gnome-look.org/]("http://www.gnome-look.org/").

As for the codecs, if you're running Feisty you should be offered the opportunity to install these as and when you attempt to play certain files. You can also get help by clicking on the restricted formats link in my signature.

:cool:

---

### Post by freebird54 on 2007-07-15
Well - you could take a look [here](https://help.ubuntu.com/community/Beginners/Guide/DesktopCustomization) for starters!

Or you can Google a phrase like 'Ubuntu desktop customization' for several hundred alternatives  :)  There are as many way to customize the setup as there are users - so have fun!

---

### Post by w4ett on 2007-07-15
A base install of Compiz (Desktop Effects) is available under >System>Preferences.

What Video Card and driver do you have installed?  The command:

glxinfo

It will let you know if 3D rendering is enabled.  If so, you should be able to get a taste of things to come.  I managed to get it runnning on a 64MB ATI card, but only with 512MB system memory.

---

### Post by ron999 on 2007-07-15
Hi
A cheap and cheerful player for mp3 and other music is XMMS media player. It's very similar to Winamp.
Also VLC will play music and video.
These are both available using Synaptic Package Manager.

---

### Post by Tripmonkey_uk on 2007-07-15
XMMS music players getting a little long in the tooth nowadays & has pretty much been superseded by Audacious.
If your interested in listening/recording internet radio stations, then try the quick guide I wrote [here]("http://ubuntufs.wordpress.com/2007/05/12/internet-radio-the-easy-way/")!

---

### Post by Skidpad on 2007-07-15
As far as desktop customization - in addition to the link provided above by freebird54 - you can look at the "Monthly Desktops" Sticky in the [Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11").  You can see the infinite ways people customize their desktop, and many describe what they've done to get it.  Worth checking out.

Welcome to the community!

---

### Post by steve8track on 2007-07-15
Amarok is a great media player.  You can set it up to use keyboard shortcuts so you can change tracks without maximizing the play, and it can run in the system tray.  Also, assigning shortcuts lets you use any key combination you want, so if you don't have media shortcuts built in to your keyboard, this can be really handy, though it seems that you can set keyboard shortcuts for other media players using System->Preferences->Keyboard Shortcuts

Also, most people consider Beryl eye-candy, but it has functionality beyond that.  For example, System->Preferences->Keyboard Shortcuts only has a set list of keyboard shortcuts, while beryl lets you create shortcuts that do anything you want, such as running a script.  I use beryl to open different applications using shortcuts, and to minimize/maximize windows using the keyboard, as well as send applications to other desktops.  This lets me use the mouse way less that I would in metacity.  I don't know about getting it to work if the graphics doesn't support it, but if it installs but constantly crashes, you could try turning off features, like the desktop cube can instead by sliding desktops, or just turn off all the eye candy all together.  It is still great at shortcuts, though maybe there are better ways of doing it.  Despite being in development, it's VERY functional, you just have to turn features on and off so that it doesn't crash.

There is a problem I have run into with beryl though:  Java programs that use JButtons or other "J" GUI doesn't always display unless you switch to metacity and then back to beryl.

---

### Post by mdsmedia on 2007-07-15
As far as "what now", I find most suggestions/ideas just reading these forums. I generally just use Ubuntu to compute...ie. just do what I nmormally do on a computer. Occasionally I'll be reading the forums, see a topic of interest like "what are you using for xxxxx" and I'll have a read, and discover something I didn't know existed.

It's one of the reasons I love Linux. In Windows, freeware is generally sketchy at best, and often you can't find a tool which fits your need without going out and spending money just to try and see that that it's not the tool you need. With Linux, in particular Ubuntu, you need a tool, search the repositories, find the program, install it, try it. If you like it, keep it. If not, uninstall and try the next tool.

The options are virtually endless.

I haven't even tried compiz/fusion or Beryl, but my desktop has been customized to something I like, just by changing the wallpaper and transparency settings for the panels.

---

### Post by Nythain on 2007-07-15
as for making your desktop look better and funner:
gnome - look into gdesklets, adesklets, conky, [www.gnome-look.org](www.gnome-look.org), gkrellm
kde - look into superkaramba, conky, [www.kde-look.org](www.kde-look.org)

then you could check out custimizing your desktop settings, moving and rearranging menu's and installing some panel apps... change your colors, background, add some panels, remove some panels... research running gnome-terminal psuedo transparent and tinted on your desktop (looks pretty sweet)

as for media player and codecs:
gnome - i guess you could try exaile or rythmbox or whatever it is gnome has... gstreamer and vlc... im partial to amarok and would use it in gnome anyways
kde - amarok for music, vlc for video... getting amarok to play mp3s is pretty easy... open it up, load an mp3 into the playlist, try to play it, amarok will complain about not being able to play mp3's and attempt to get the proper codecs

video codecs i would recommend getting the libdvdcss2 pakcage for dvd playback and the w32codecs package from the medibuntu repository... that package will take care of all teh popular video codecs

---

### Post by Nessa on 2007-07-16
I'm trying to search for a step-by-step guide in installing conky that's newbie friendly. Do you guys have a link handy?

---

### Post by Nessa on 2007-07-17
I have Compiz-Fusion and Conky running. Amarok's great! (Can I remove Rythmbox?) I got my printer/scanner working. Woohoo! 

I can't play .avi movies in Totem eventhough I've installed the codecs. Am I missing something? Or should I use a different movie player altogether?

Also, sometimes the cpu temp seems off. Like for a few minutes it shows 2-3C and them jumps as high as 60C.

Any other suggestions?

---

### Post by steve8track on 2007-07-31
I'm glad you like Amarok.  Rythmbox can be removed by unchecking it in Synaptic, or by
(I hope I've got this right):

```

sudo apt-get remove rhythmbox

```

Or to remove even the configuration files of a peice of software if you want to reinstall something without having the old configuration (I thought I'd add this in case someone needs it for some other software, like I have when I messed up some configuration files, I used this to start from scratch with the program):

```

sudo apt-get remove --purge rhythmbox

```

Just change program_name to whatever the package for Rythmbox is.  I don't use

The following link might help with installing what's needed to play things like DVDs and videos, so maybe there is a codec you missed for avi:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Good luck!

---

### Post by Nessa on 2007-09-11
- Compiz Fusion : done.
- Conky : done.
- Mp3 playing in Amarok : done.
- VLC for online videos : done. 
- Rhythmbox removed : done.
- .avi plays in Totem : done.
- Brother DCP115C scanner/printer installation : done 

My next project is adding voip/softphone to my box. Also looking for a good peer to peer client that won't mess up my settings. Any ideas?

---

### Post by BrendanM on 2007-09-11
I highly recommend rtorrent as a BT client. It's a command line program, so it takes a little getting used to, but it uses practically no system resources (other than bandwidth, obviously). This blog post can help get you started: [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by jvc26 on 2007-09-11
It would appear noone told you how to get the codecs - see here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```
Il

---

### Post by Nessa on 2007-09-13
I already have the restricted extras installed. I went ahead and did that sudo apt, thanks for that.

It looks like Ekiga is my best bet for voip/softphone. I'm also looking for online resources about networking and administration in Linux. My knowledge is only limited to the windows environment but I'd like to learn more.

I'll give rtorrent a try. Thanks for the recommendation. :)

---

### Post by Nessa on 2007-10-08
I haven't had the time to create an account for Ekiga. Don't have a motivation to at the moment since my headset went kaput and I have to wait til I get a new one.

I've created another user account and tried out the Mac4Lin project. It looks great. :)

What should I try out next?

---

