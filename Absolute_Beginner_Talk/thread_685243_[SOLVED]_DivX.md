---
title: "[SOLVED] DivX"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-02
how do i play divx videos like (stage6)? i had divx working a couple of weeks ago but i just  switched to ubuntu 64bit version and now i have to reinstall everything. i cant remember how i was watching stage6 before but it must not have been difficult because i dont remember remember setting it up.  i think last time the bar at the top of the firefox window that usually tells you when you need a plugin came up and i did it that way but now it doesnt show up 
what do i do?

---

### Post by billgoldberg on 2008-02-02
There are a number of ways.

I assume you have the correct codecs (you can play downloaded videos from stage 6?) If not do this:

sudo apt-get install ubuntu-restricted-extras

Then go to synaptic and download the totem-mozilla file. reboot firefox and the videos should stream.

Second option:
right-click the download button on stage 6, and copy the link adress. Open up vlc mediaplayer and choose open file. Past the url.

Third option:
a firefox plugin:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

This will allow you to open embedded media in the player you want (like vlc media player for divx)

Fourth option:
the vlc firefox plugin (I think this one is still quite buggy)

---

### Post by tjwoosta on 2008-02-02
ok i did the 

sudo apt-get install ubuntu-restricted-extras

and i went to synaptic and downloaded the totem-mozilla file

and i tried the firefox addons

nothing works,  i dont know what i downloaded last time but i could play it on the web page (wihtout opening the media player) but i cant even do it by pasting the url itnto the media player now

when i click on the play button on any movie from stage 6 the progress bar at the bottom just goes straight to the end and just twitches

---

### Post by tjwoosta on 2008-02-03
is there anyway that i cam uninstall the divx codec and reinstall it?

---

