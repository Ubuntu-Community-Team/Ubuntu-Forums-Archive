---
title: "Neworking (shared folders) question..."
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by mednamot on 2006-02-15
Since I'm not at home I can't actually do anything till tonight, but I'm trying to set it up so that my wife's computer (which she finally approved the install of Ubuntu on) and my laptop can share files back and forth (most important as I moved all her photos, music, and movies to my laptop prior to installing Ubuntu).

I set up sharing (using the GUI) this morning for both my Home folder and her home folder, but could not see either of them from the opposite computer.

So far I have found this:

[https://wiki.ubuntu.com//SettingUpNFSHowTo](https://wiki.ubuntu.com//SettingUpNFSHowTo)

I'm thinking that that more or less would set it up so that I could access my laptop from say...work...or her PC even (which could be cool) but I'm unsure if that goes above and beyond what I actually want to do...which is share her home directory and my home directory soley to each other.

Thanks all for your replies (if they indeed come...;p)

---

### Post by soonindallas on 2006-02-15
[QUOTE=mednamot]Since I'm not at home I can't actually do anything till tonight, but I'm trying to set it up so that my wife's computer (which she finally approved the install of Ubuntu on) and my laptop can share files back and forth (most important as I moved all her photos, music, and movies to my laptop prior to installing Ubuntu).

I set up sharing (using the GUI) this morning for both my Home folder and her home folder, but could not see either of them from the opposite computer.

So far I have found this:

[https://wiki.ubuntu.com//SettingUpNFSHowTo](https://wiki.ubuntu.com//SettingUpNFSHowTo)

I'm thinking that that more or less would set it up so that I could access my laptop from say...work...or her PC even (which could be cool) but I'm unsure if that goes above and beyond what I actually want to do...which is share her home directory and my home directory soley to each other.

Thanks all for your replies (if they indeed come...;p)[/QUOTE]


you don't describe how you are connecting the computers but this is accomplished quite easily and simply if you have a home network, for ex through a router you use to share internet access.

you also don't mention if your laptop is ubuntu or Windows.  If it's windows you'll need samba for shares between the 2.

if you have this set up correctly you should be able to browse the network and your shares should be visible.  you can then mount the remote share on your computer (and vice versa for the desktop) and treat the share like a folder on your own computer.

---

### Post by mednamot on 2006-02-15
ah, sorry for the lack of info...

yes, both PC's (as well as my 360, and my Vonage router) access the internet through a router.

both the laptop and desktop have Ubuntu on them (Breezy if that makes a difference)

I figured by sharing the folders I could then go to browse the network and see them, but all that shows up is the Windows Network Icon (my cousin who lives above me has his own network, seperate from mine, all windows).

I'm thinking I forgot something small...which is where my concern with the wiki page comes in - that seems to be so much more than what I actually need to do.

---

### Post by soonindallas on 2006-02-15
[QUOTE=mednamot]ah, sorry for the lack of info...

yes, both PC's (as well as my 360, and my Vonage router) access the internet through a router.

both the laptop and desktop have Ubuntu on them (Breezy if that makes a difference)

I figured by sharing the folders I could then go to browse the network and see them, but all that shows up is the Windows Network Icon (my cousin who lives above me has his own network, seperate from mine, all windows).

I'm thinking I forgot something small...which is where my concern with the wiki page comes in - that seems to be so much more than what I actually need to do.[/QUOTE]


yes.  you don't need all that wiki page stuff.

are you sure you're connected to your router ?  if all you can see is the windows network, it sounds like your connected to his network.  this is wifi, right ?

of course you could be on your router and the 360 looks like a windows network to ubuntu.

I have no experience in getting ubuntu and a 360 to cohabit on a router.

---

### Post by mednamot on 2006-02-15
sorry, yes, his network is seperate from mine, but we share the wireless connection (on my router).

I was just told by a guy I work with (longtime Ubuntu guy) that since I'm going to be streaming to my 360, in all likelyhood I should go with Samba as my share protocol (right term?)...so I'm going to give that all a go...

after sharing folders was I supposed to restart/refresh the desktop/GUI?

---

### Post by soonindallas on 2006-02-15
post back to the forums with your progress.

I agree with your colleague but I don't even know that it is necessary to run samba if you don't need the computers to talk with the 360.

With samba you can get Ubuntu to play nice with windows boxes for file and printer share purposes but if you don't need this you don't need samba.

start at the beginning and try to ping each computer from the other.

---

