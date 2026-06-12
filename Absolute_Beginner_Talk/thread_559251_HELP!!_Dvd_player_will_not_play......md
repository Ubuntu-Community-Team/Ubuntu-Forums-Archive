---
title: "HELP!! Dvd player will not play....."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-09-24
Well, I've tried to search to find my answer on this one and have had no luck.......

My DVD player/burner will not play DVD's unless it is a DVD that I have created myself. So, I get an error that I need libdvdcss. I have installed that and still have the same problem. 

I have also installed the win32 codecs along with everything else imaginable for Fiesty. 

What do I do next? Is there a way to check for my drivers without uninstalling Kaffiene and re-installing it?

---

### Post by reckless2k2 on 2007-09-24
try installing vlc and playing the dvd with that. you should have no problems then.

---

### Post by wheredidrealitygo on 2007-09-24
> try installing vlc and playing the dvd with that. you should have no problems then.

Quicker to the draw than I am, my exact suggestion.

---

### Post by Rabidmonkey1 on 2007-09-25
Try this, if you haven't already:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
sudo apt-get install libdvdcss2

---

### Post by chaddiesel on 2007-09-25
noob alert......

what is vlc? a player maybe?

---

### Post by mysticmatrix on 2007-09-25
> **chaddiesel said:**
> noob alert......

what is vlc? a player maybe?

Yes, Applications --> Add/Remove

---

### Post by chaddiesel on 2007-09-25
found it in the repositories.....

i'll be trying it soon

---

### Post by chaddiesel on 2007-09-25
that doesn't work either, i can't even get it to recognize that there is a disc in. 

The movie player and kaffiene try but can't display video

---

### Post by chaddiesel on 2007-09-25
vlc player is just stuck now, it won't do a thing, i can't even close it

---

### Post by reckless2k2 on 2007-09-25
xkill will kill it. i know noob alert but you can look it up real quick because i imagine by now you have rebooted. 

if you've tried vlc and the other libdvdread option, something sounds buggy. have you tried another dvd? 

something else is going on. and if it didn't play, i think ubuntu would have prompted you for additional codec install so i'm think something is up with the disc or drive.

---

### Post by chaddiesel on 2007-09-25
I ended up trying a new disc after installing vlc and it worked..

sorry for the noobyness.... :)

---

### Post by reckless2k2 on 2007-09-25
not a problem. that's what we are here for. hahaha.

i'm earning fancy cups anyway...

mark it SOLVED!!!

i get brownie points.hhaha

---

