---
title: "TVTuner"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ZKjellberg on 2007-06-23
**Working on issue in this thread now.** [http://ubuntuforums.org/showthread.php?p=2901759#post2901759](http://ubuntuforums.org/showthread.php?p=2901759#post2901759)

Hello, I have an AverMedia pcmcia tv tuner card in my laptop. I've asked help for this a few times in the IRC channel, but I haven't had the issue resolved. 

I have TvTime installed on my machine, and when I boot it up it has a black screen(blue when I eject the card so it shows that its detecting the card as /dev/video0), but when I go into 'Input Configuiration' and try to 'Change Video Source: default', it seems to be a 'reset to defaults' button. I am currently using the tv tuner for its component cables to use my consoles, but it does not seem to get the info. I also checked to see if coaxial cable would be working(thinking that was possible the default spot being read from) and still nothing.

I was told on IRC that I probably needed to install drivers, and was told to use the command 'lspcmcia'. Heres the output.

'Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:03:01.0)
  CardBus card -- see "lspci" for more information'

So, I typed 'lspci' and heres a link to my pastebin for it.

[http://pastebin.com/934879](http://pastebin.com/934879)

Also, heres my 'dmesg'

[http://pastebin.com/934881](http://pastebin.com/934881)

Any recommendations would be greatly appreciated.

UPDATE: I spoke to a friend and made some progress, but still not having it working correctly.

I am doing the following:
"rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=##"

## being replaced by cards listed on this page: [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

I have tried almost every AverMedia ## listed on that page, but every time I have it give me 'TV, Composite1, Composite2, S-Video" And the console is always 'Composite2' but never has sound. The card seems to be #46 because I found this page(which is sadly in Russian..): [http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Plus_E501R](http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Plus_E501R) which lists it as 'card=46'. Does anyone know how I can get sound to work, and if there is a better driver for me to use?

---

### Post by studo77 on 2007-10-22
Also having trouble with my saa7134. So seeing what you have found i wass amazed of goole.
[http://www.google.com/translate?u=http%3A%2F%2Flinuxtv.org%2Fv4lwiki%2Findex.php%2FAVerMedia_Cardbus_Plus_E501R&langpair=ru%7Cen&hl=da&ie=UTF8](http://www.google.com/translate?u=http%3A%2F%2Flinuxtv.org%2Fv4lwiki%2Findex.php%2FAVerMedia_Cardbus_Plus_E501R&langpair=ru%7Cen&hl=da&ie=UTF8)
russ>en

And after alot of websurfing the conclusion is:

Go through card and tuner settings in modprobe.d/(options/saa7134)

Alot of wasted time in my future, maybe i should get a plug-it-in-and-it-works tv-card. The combinations are huge.
I got mine partially working, and onæy in tvtime using tvtime-scanner. Channels below 400MHz are not found all above are. For this result the setting is.
card:59
tuner:9

Form
[http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)
   1.  Run "modprobe bttv" with no options.
   2. Run "dmesg". Check to see if your card is autodetected, and if the tuner is correct. If everything looks fine, you're done.
   3. If the card appears as UNKNOWN/GENERIC, find the CARDLIST file in your kernel documentation and find your card in the list.
   4. Unload bttv and tuner using "rmmod bttv" and "rmmod tuner".
   5. Run "modprobe bttv card=X" where X is the number of your card.
   6. Run "dmesg" again. See if the card loaded properly and if the tuner is correct.
   7. If not, unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y".
**   8. Curse Linux for being so complicated. **

---

