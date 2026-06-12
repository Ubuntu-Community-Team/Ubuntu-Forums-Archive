---
title: "Error installing codecs and a single .deb package."
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by saptarshi.roy on 2008-01-29
Greetings everybody,
I am a beginner in the journey of Ubuntu. I am facing a few issue which I would like to mention here. I tried searching resolutions for similar issues but couldn't find any.
I have downloaded "ymessenger_1.0.4_1_i386.deb" to my desktop; and then I run the following command in a terminal

sudo dpkg -i ymessenger_1.0.4_1_i386.deb

after which I get this error

dpkg: unknown option -y


My second issue is that I cannot install a suitable codec from the list of codecs available. I have a set of mp3 and mpeg files, whenever I try to play them through the movie player, I get a pop up box stating, 'search for suitable codec',  The search yields the following results, GStreamer extra plugins and GStreamer ffmpeg video plugin. They are restricted software so I confirm their installation but alas I get another pop up box stating 'the list of applications is not available and it asks me to refresh, I refresh it but it again starts from the codec search results. I have tried it with both internet on and off but to no avail.

I would be very grateful if someone guides me through these issues.
Thanks and regards.
Roy.

---

### Post by Kevbert on 2008-01-29
For codecs, try this link [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html")

---

### Post by erfahren on 2008-01-29
you could just double-click on the ymessenger .deb file. It will open in Gdebi and prompt for your password to install. (It's possible that it may not work in Ubuntu if it was packaged for Debian - there are *some* differences from what I understand).

There is an open-source IM client included with by default in Ubuntu Gutsy - [Pidgin](https://help.ubuntu.com/community/Pidgin) - it should work with Yahoo. See the bottom of that page for more information on it.

for the codecs also see:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

---

### Post by mikewhatever on 2008-01-29
Can you post your sources list, <sudo cat /etc/apt/sources.list>

---

### Post by saptarshi.roy on 2008-01-29
Thank you Kevbert, Erfahren and Mikewhatever, the command for the codecs to install and execute
sudo apt-get install ubuntu-restricted-extras
made it possible for me to enjoy multimedia.
Regards.
Roy.

---

