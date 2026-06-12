---
title: "Sound keeps going why?is it bittornado?restating sound?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-14
right everything was fine soundwise after a restart.then i start my downloads in BT and no sound says its in use.
how do i sort this?how do i restart the sound without a pc restart?

---

### Post by Happy_Man on 2007-04-14
Perhaps BitTornado wasn't enabling its sound notifications?

---

### Post by keef247 on 2007-04-14
what do you recommend me doing to solve this.

---

### Post by bmaxd on 2007-09-16
For what it is worth, I am having the same issue.

The funny thing is, I have been using Feisty almost from the day it was released and am an avid user of both Bittornado and Youtube yet I have not run into this issue until today.

In nigh on five months, it would seem, I have not attempted to use both simultaneously until today.

---

### Post by deadgobby on 2007-09-16
It can be the matter of how much memory you have, if you have a good sound card, your system CPU speed, and ect...  You could try this command and see if it helps. I do not know if it will help.
Open up the terminal and type in 

killall esd

 See if that helps. If not your system may be a tad slow.

Gobby

---

### Post by schtum on 2008-02-02
I'm having the same problem, and it has nothing to do with speed or RAM. It shouldn't take a gaming rig to run a bittorrent client and play audio at the same time. I currently have one torrent running at low speeds (under 35kB/s) and no sound at all. I'm using BitTornado, but there are other threads where people report the same problem with Ubuntu's built-in bittorrent client. Their solution was to switch to Deluge for torrents. That's a terrible solution, imho. Anyone figure out a real fix for this yet?

---

