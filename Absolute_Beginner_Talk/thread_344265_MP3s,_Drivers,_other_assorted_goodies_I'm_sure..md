---
title: "MP3s, Drivers, other assorted goodies I'm sure."
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by pitchpipe on 2007-01-22
I'm really new to this Linux thing. It's been a lot of fun, but now I have a bit of a concern.

MP3s - I might even answer my own question here. . .

I noticed the install had an app that looked like it could play them. Being a music major I had a lot of music and would hate to move all of those files to my designated Ubuntu space. Seeing how TECHNICALLY it's considered a new drive would it be possible to find that drive and play from there? I realize that may be absurd as they're kept on my XP partition and they probably use different. . .somethings that would make it not work.

Drivers -

ATI does make a driver for my chipset (Radeon Xpress 200, embedded) but how do I get it to work? I'd love to play around in something other than 800x600. . .

I'm also not finding anything for my Belkin Pre-N wireless card. I've only found Windows drivers. Any other solutions?

To give you an idea on how clueless I am to this, it took me 2-3 days to find the "command line". Man how that makes a difference!

---

### Post by crispy_420 on 2007-01-23
mp3 will require codecs not in the default install of ubuntu due to legal reasons (patents). look to add repos that have those codecs. you can find plenty of guides/how-tos in these forums.

as far as ati drivers. just look for some guides on fglrx. i think at the beginning of the video or hardware forum there is a sticky just on how people were able to setup ati cards.

belkin card may require drivers being installed. do you know what chipset it has? worst case scenario means looking for a guide on setup of ndiswrapper. that way non-supported devices can use windows drivers.

not to be a jerk but you do know how to issue commands as root in terminal? add sudo before command. trust me you'll need that in all these steps.

good luck.

---

### Post by ardchoille42 on 2007-01-23
XMMS plays mp3 files out-of-the-box:

```

sudo apt-get install xmms

```

There are also a lot of plugins for xmms in the universe and multiverse repos.

---

### Post by stoer on 2007-01-23
Hi and welcome to ubuntu :wink: 

I'd suggest you do a little  reading, the following links will answer just about all your questions.

Start here.
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)     Dapper

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)                      Edgy

And this is also easy to follow,
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

When you've at least looked at the 2 links above, then try reading the following 2.
If you have any questions on either Automatix or Easyubuntu they are both well doccumented  in the forums, or just ask again.

And for your multimedia needs take a look at these.

[http://www.getautomatix.com/](http://www.getautomatix.com/)
"a graphical interface for automating the installation (and uninstallation) of the most commonly requested applications in Debian based Linux operating systems.."


[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
"EasyUbuntu is an easy to use (duh!) script that gives the Ubuntu user the most commonly requested apps, codecs, and tweaks that are not found in the base distribution - all with a few clicks of your mouse."

And lastly this is also a nice site.
[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)



Success and have fun.

---

