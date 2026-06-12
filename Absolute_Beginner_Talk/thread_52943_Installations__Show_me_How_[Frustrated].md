---
title: "Installations : Show me How [Frustrated]"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by inCo on 2005-07-29
Please could someone be kind enough to give me a walkthrough on installing aMSN to my system, and installing codecs (mp3, mpeg etc). 

[Would probably have to break the walkthrough down to bare simplicity as I am a first time user and not very Linux Savvy]

I am not lazy, I have been trying to look for a way but as I have come over from Windows XP and have used Ubuntu as my first Linux Distro, the guides i have been able to find myself i find quite confusing and frustrating, mainly down to the fact i am too used to Windows. And if I am shown how to do this it would be a good stepping-stone to advance through Ubuntu.

---

### Post by phen on 2005-07-29
hi!

take a look at [www.ubuntuguide.org](www.ubuntuguide.org), read the general notes first, because they help. then check the table of contents for your special problems!

if questions stay unanswered, pm me!

cheers,
kai

---

### Post by Sam on 2005-07-29
[list][*][How to add extra repositories](http://ubuntuguide.org/#extrarepositories)
[*][How to install codecs](http://ubuntuguide.org/#codecs)
[*]How to install amsn:
```
$ sudo apt-get install amsn
```[/list]

You can find all you need here, however if you don't understand something, please explain what's wrong.

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=inCo]Please could someone be kind enough to give me a walkthrough on installing aMSN to my system, and installing codecs (mp3, mpeg etc). 
[/QUOTE]

Ok. We have a great guide for this stuff, but you have to be willing to touch the command line. Its not a scary thing, just copy and paste. Ubuntu is not to the point where you can avoid the command line to get that stuff (easily). Its not hard though, just different from Windows (something you must accept).

Open the regular terminal (not root terminal). Its like under system tools or something.

Then do exactly as this says:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Got that? Good.

Now enter this command:

> sudo apt-get update

that made the system recognize the change you made.

Now enter this command:

> sudo apt-get install sun-j2re1.5 flashplayer-mozilla acroread w32codecs libdivx4linux libdvdcss2 totem-xine msttcorefonts amsn


There. That single command will install from the internet Java, Flash, Media Codecs, the acrobat reader, familiar fonts, aMSN and will fix totem so that is can play all that (anything. it will play just about any media file then).

Make sure that its all one line (the forum and the terminal breaks the line, thats ok just copy and paste it correctly).

Now close the terminal. You are in god shape. From here on out, install all programs in synaptic:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

Sorry you have to jump through the hoops- Ubuntu can't legally include that stuff by default. We would rather the money be spent on development, not lawyers.

---

### Post by inCo on 2005-07-30
thankyou for the help, much appreciated. although im not too adept at command line i think this way is much more powerful than windows though it is more powerful.

once again thankyou for the help :)

---

### Post by PisShivers on 2005-10-08
Does this still count for Breezy?

---

