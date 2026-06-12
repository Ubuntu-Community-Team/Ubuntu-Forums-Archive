---
title: "Mozilla software - updates or not quite?"
date: 2011-11-15
forum: Apple Hardware Users
---

### Post by canhoto on 2011-11-15
Hi.

I recently upgraded my Firefox and Thunderbird to the 7.0.1 release, using [this]("http://ubuntuforums.org/showthread.php?t=1816161") - very useful and highly recommended - thread by pauljwells.

It all went breat, I have a wonderful browser and a fast email client.

But... I think I lost something with the upgrade.

To be specific:

- In Firefox I lost the gnash-plugin compatibility, apparently. At least the flash videos are not working (I have to download the videos) and the plugin is not listed in the installed add-ons tab

- In Thunderbird, I lost compatibility with the very useful Lightning calendar. It says there's no compatibility from Lightning with 7.0.1, but I'm using 8.0 in my Macbook and it's working.

I think these are Linux on power pc specific questions.

Any help?

---

### Post by hellfire695 on 2011-11-16
sudo wget [http://switch.dl.sourceforge.net/projec ... ozilla/apt]("http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt")

then 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 812347DD

try adding that repo apt-get update and apt-get update and apt-get  upgrade. that will get the newest versions of thunderbird and mozilla. if gnash still dont work try the getting flashplayer here

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

or you can try the software center

---

