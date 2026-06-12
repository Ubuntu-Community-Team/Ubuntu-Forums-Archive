---
title: "Newb Problem - MP3s/BitTorrent/MPG"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by 70plymouth on 2008-04-08
First off MP3s/MPG/WMV

I try and install the plugin but it won't let me check the box and hit install. It just keeps asking me if I accept and live in a legal country etc. Any sites that I can manually download a MP3/MPG/WMV player for Ubuntu/Linux?

BitTorrent

It says that its installed when I go to Applications-Add/Remove and I try to install it. But I don't see it anywhere on my computer. I would like to run BitTorrent to download music/videos, and I'm not seeing it on my computer, although it says its installed.

Also,

Lots of items that I try and install from the Add/Remove option say that my computer is not supported i386?

Thanks in advance.

---

### Post by tvtech on 2008-04-08
what type of computer do you have?  is it a 64 bit or a powerpc?  

try transmission if you don't like the default bittorrent install it's stupid simple. 

you should try installing the ubuntu restricted extras package to get mp3 wmv wma support

---

### Post by AndrewEsther on 2008-04-08
For a good media player, try going to Add/Remove Applications, make sure that you're looking in "All" categories (on the left-hand side make sure it's highlighted) and just type in 'mp3' to the search box.. VLC is a good player.

and as for your bittorrent install, where have you looked?

---

### Post by Het Irv on 2008-04-08
If I remember correctly bittorrent doesn't show in the menus, try downloading a .torrent file and see what happens.  
+1 to VLC
Also for music Amarok is very good.

---

### Post by stchman on 2008-04-08
> **70plymouth said:**
> First off MP3s/MPG/WMV

I try and install the plugin but it won't let me check the box and hit install. It just keeps asking me if I accept and live in a legal country etc. Any sites that I can manually download a MP3/MPG/WMV player for Ubuntu/Linux?

BitTorrent

It says that its installed when I go to Applications-Add/Remove and I try to install it. But I don't see it anywhere on my computer. I would like to run BitTorrent to download music/videos, and I'm not seeing it on my computer, although it says its installed.

Also,

Lots of items that I try and install from the Add/Remove option say that my computer is not supported i386?

Thanks in advance.

You need the proprietary CODECs.  Make sure all the repos are enabled and do the following:

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Next install VLC.

```
sudo apt-get install vlc
```

This should take care of all your media playing needs.

For torrents use KTorrent.

```
sudo apt-get install ktorrent
```

---

### Post by AndrewEsther on 2008-04-08
beautiful.



what he ^ said

---

### Post by jseiser on 2008-04-08
you coud also try, rtorrent .  Its the best torrent client, its light, you can run in screen and not even have to look at it, it will auto add torrents from a directory, seed to a set point, remove the file, and move it.

---

### Post by 70plymouth on 2008-04-08
Im sorry, I'm extremly noob to Linux, how and where do I enter the code?

---

### Post by 70plymouth on 2008-04-09
I just found out its on the terminal, I did all the codes and it says

E: Couldn't find package ktorrent

E: Couldn't find package vlc

E: Couldn't find package gstreamer0.10-pitfdll

Any idea?

---

### Post by 70plymouth on 2008-04-09
When I go to Add/Remove programs and try to add various things it says this when I try to check the box.

JuK cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

??

Also when I try and play an MP3 it trys to auto install the codec. It won't though, it seems to go into a continuous loop of downloading something online but it wont actually install the codec. 

!!?!?!?!!!

---

### Post by 70plymouth on 2008-04-09
New story:

So I try and install stuff and right as I try to click the check box it says I need to refresh the list if I have an internet connection. I press refresh and it goes thru what looks like a downloading of some files. I try to hit the box again to install and the same message pops up again.

---

### Post by Het Irv on 2008-04-09
Dumb question, but it needs to be asked.  The computer you are on has an Internet connection correct?

In the terminal type ```
sudo apt-get update
```
In front of each line you should see "hit" or ign".  If you get all "ERR" check your internet connection.

---

