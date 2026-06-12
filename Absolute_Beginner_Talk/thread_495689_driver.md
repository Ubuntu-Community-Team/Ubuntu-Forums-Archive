---
title: "driver"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by bondi007 on 2007-07-08
how do i install a wireless card driver if the driver on the website is only compatible for windows

---

### Post by Happy_Man on 2007-07-08
Just use ndiswrapper.

---

### Post by bondi007 on 2007-07-08
how do i install it and what do i do from there

---

### Post by Outrunner on 2007-07-08
Assuming you aren't connected to the internet, you can mount your Ubuntu CD as a repository like this:

```
sudo apt-cdrom add
```

Then just go into Synaptic and search for ndiswrapper and install it. As to what to do after that, I suggest you search for a guide.

---

### Post by bondi007 on 2007-07-08
what do you mean and what does this do

---

### Post by Outrunner on 2007-07-08
> **bondi007 said:**
> what do you mean and what does this do

OK, I'm sorry if I wasn't clear enough.
Go to Applications-> Accessories-> Terminal

Then type the code I posted above and follow instructions.

Then go into the Synaptic Package Manager (System-> Administration I think) and press CTRL-F to open the 'Find' window. Then search for 'ndiswrapper'

---

### Post by bondi007 on 2007-07-08
it came up commen at utles summat wich one shall i choose

---

### Post by Outrunner on 2007-07-08
It's a bit hard to tell you that without knowing their names... You can install the one that seems relevant. I think it should be something along the lines of ndiswrapper-#.# where #.# is the version number. Install the newest one.

---

### Post by bondi007 on 2007-07-08
it keeps telling me i need internet but what can i do im on a windows machine now downstairs and ubuntu machine upstairs cant i get it from the windows machine

---

### Post by Outrunner on 2007-07-08
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)

Download ndiswrapper from there and get it to your Ubuntu /home partition then install the .deb with

```
sudo dpkg -i *.deb
```

---

### Post by bondi007 on 2007-07-08
i just double clicked the file and it said it installed it what do i do now

---

### Post by bondi007 on 2007-07-08
what do i do now

---

### Post by Outrunner on 2007-07-08
OK first of all you've got to chill. Honestly you cant bump a thread every 3 minutes. Now go to google and search for "YOUR_WIFI_CARD_MODEL + linux" and you should find some guides.

---

### Post by bondi007 on 2007-07-08
but how do i acces wrapper thing

---

### Post by Outrunner on 2007-07-08
> **bondi007 said:**
> but how do i acces wrapper thing

You don't access any "wrapper thing", it is command line only and you will have to use a guide to find out what driver to downloand and what command to use next.

---

### Post by bondi007 on 2007-07-08
cheers im just new to this im only 13

---

### Post by bondi007 on 2007-07-08
cheers im just new to this im only 13

---

### Post by bondi007 on 2007-07-08
it comes up 2 wireless cards wlan0 wlan master and i dunno what my essid how can i search for available wireless networks in the area

---

### Post by Outrunner on 2007-07-08
Well, I haven't done this in a while, but if I remember correctly, the command is

```
iwlist ath0 scan
```

Replace ath0 with your wireless device(possibly wlan0)

---

### Post by bondi007 on 2007-07-08
it says no results and the light is flashing on my card and it doesnt when it isnt installed does that mean its working but not picking upthe connection

---

### Post by Outrunner on 2007-07-08
I'm not sure. Try restarting your computer and then do a scan again.

---

### Post by bondi007 on 2007-07-08
kk

---

### Post by bondi007 on 2007-07-08
dun but no result but when i start ubuntu the wireless card light comes on so that could be something

---

