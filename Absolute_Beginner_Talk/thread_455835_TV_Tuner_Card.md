---
title: "TV Tuner Card"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-27
I'm finally very very comfortable with Ubuntu (Dapper) after switching and removing all WIndows partitions and software from my hard drive. I'm insanley happy I did this but I'm needing help with something. I have a K-WOrld Tv TUner card, model number : KW-LTV7131RF. Here's a nice link: [http://www.buy.com/prod/kworld-tv-tuner-video-capture-mpeg-4-2-1-recording-remote-pci/q/loc/101/10405687.html]("http://www.buy.com/prod/kworld-tv-tuner-video-capture-mpeg-4-2-1-recording-remote-pci/q/loc/101/10405687.html")
Now what I'm looking to do is figure out a way to get that seen by Ubuntu and up and running so I can fully utilize it again as I was. Anyone have any ideas or any way of pointing me in the right direction? Thank you in advance!! :) :popcorn:

---

### Post by Tumpster on 2007-05-29
Bump!

---

### Post by Tumpster on 2007-06-03
any ideas?

---

### Post by jgrabham on 2007-06-03
[http://www.kworld.com.tw/en/index_support.htm](http://www.kworld.com.tw/en/index_support.htm)

The click product support

The thing I noticed is it said "OS" -windows xp home windows xp pro windows xp media centre edition so on; no linux, no mac!!

---

### Post by BaffledMollusc on 2007-06-03
You might want to look into Myth TV. As far as I know, that's what most people use to watch TV under linux. Might help, might not. Google "Myth TV" and take the first result.

---

### Post by Jose Catre-Vandis on 2007-06-03
From Linux Tech Toys
> The KWorld Studio TV Terminator is based on the SAA7131E Chipset. and should be well supported in Linux Distributions containing kernel versions 2.6.14 and up. TV-Tuner, Radio, Sound and remote control features are supported under v4l. The card does not have an eeprom so it is necessary to pass card=65 and possibly tuner=54 as options to the saa7134 kernel module. Automatic tuner detection works starting with distributions using kernel version 2.6.15. On the application sde, TV-Time, KdeTv and KRadio work well with this card

So it should work out of the box if you are running Edgy or Fiesty. Suggest you avoid Myth TV and use TvTime (very simple and easy and straight forward)

Install the card in your PC, reboot and then type dmesg in a terminal you should see a line about autodtecting your card. if it lists your KWorld - or similar, then you should be good to go. if not you will need to pass some parameters as above.

If your card is found, install Tvtime and run a channels search

Please report back on success :-)

---

### Post by mect on 2007-06-22
If you haven't figured this out yet, here are instructrions that get it to work for me.
[http://ubuntuforums.org/showthread.php?t=357706]("http://ubuntuforums.org/showthread.php?t=357706")

The steps to follow
sudo sh -c 'echo "options saa7134 card=65" > /etc/modprobe.d/saa7134'
edit /etc/modules
by adding
saa7134
to the end of the file.
Restart your computer.

Hope this helps.

---

### Post by Gmbrdilos on 2007-06-22
I never got my card to work, I had an nvidia NVTV. most tv tuners are specificly designed to work with windows media center edition (mine wouldnt even work with vista)

---

