---
title: "Apple Remote (2009) + Mac Mini + LIRC, Anyone?"
date: 2010-03-03
forum: Apple Hardware Users
---

### Post by felipao on 2010-03-03
Hello All,

I am trying to make my apple remote (2009 version) to work under Ubuntu 9.10 running on a new mac mini.

My intention is to be able to control Rhythmbox, Totem, system volume and XBMC with the remote.

I have been googling for a couple of months already and I haven't found any instructions, howtos, guides, etc.

Does anybody has any idea where I can go for instructions? 
Any help is much appreciated!

Thanks!8-)

---

### Post by linuxopjemac on 2010-03-03
did you try
```
sudo apt-get install gnome-lirc-properties
```

and see if you get an entry "Infrared Remote Control" in menu System > Administration. After launching this it will guide you through the configuration.

[https://help.ubuntu.com/community/MacBookAir1-1/Karmic](https://help.ubuntu.com/community/MacBookAir1-1/Karmic)

---

### Post by portiris on 2011-03-17
I was able to get lirc working on my Mac mini yesterday (havent mapped out keys yet, but button presses were recognized while running irw). but after installing the properties manager for gnome (like above) and attempting to add another remote, it no longer recognizes my apple remote or any other remote. Property manager shows up in the system->preferences menu but will not open.
I tried purging lirc and reinstalling, but remote still won't work. Any ideas?

Running Maverick.
lirc.conf is back to the same defaults as when it was working.
Remote is still working on my MBP using OSX.

---

### Post by YfoMp5QBh2 on 2011-03-17
when you press a button on your remote which programs are working/recognising the commands? Also which remote are you using?
 
In XBMC under the 'settings' menu make sure you enable the option 'allow other programs to control XBMC'. Lirc should work out of the box with XBMC but unless you 'tick' that box in the XBMC menu it wont work at all.
 
have a look at the attached also; [http://wiki.xbmc.org/index.php?title=HOW-TO_setup_Lirc_to_talk_to_XBMC](http://wiki.xbmc.org/index.php?title=HOW-TO_setup_Lirc_to_talk_to_XBMC)

---

