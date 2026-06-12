---
title: "Gnome Bit Torrent 8K/sec - Azureus on PC 20+K/sec: same file/same time!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-19
Well, that will be the first and last time I ever try that pile of junk (in ubuntu as standard)
[http://gnome-bt.sourceforge.net/](http://gnome-bt.sourceforge.net/)

Thought (as I'd not tried it before) to run the Gnome on on my fast machine (with ubuntu on it) side by side against my old Pentium 3 machine struggling to run the latest Azureus.

Note, both machines on the same network and both have the same wires connections to the outside world.

Picked a random file (couple of gigs) with plenty of seeds and peers.

Watched the speeds on both, and after about 5 mins:

Ubuntu with Gnome Bit Torrent client = 8K a second (and struggling to keep that up)

Old PC running Azureus = an easy 20K+ a second.

Both client set to 10k upload speed, though of course, neither had got to upload yet.

So, I won't be bothering with that gnome pile of elephant droppings a second time!

Now, I'd like to stay away from Azureus on ubuntu if I can (as I know it's overblown and a system hog) but anyone care to recommend something else.

I'd like to actually see how many peers/seeds, how much of a file they have got (that kinda thing)

---

### Post by om1 on 2008-02-19
try bittornado... its in add/remove
if it is bad there is a problem with a port or NAT issue most likely.

---

### Post by Joeb454 on 2008-02-19
To give Torrent client's their due - I believe that it depends how much the seeder's and peer's send to your computer, and how good your own connection is.

The speed depends on a great number of things, such as encryption - ISP's tend to filter torrent traffic.

Hope this helps :)

---

### Post by PiggiePaul on 2008-02-19
Had a little scan around these forums (and as always, different people like different things)

But, Deluge got a few good mentions, so went to their web site, and like the sound of it, the fact they supply a Ubuntu self installing package download (like EVERYONE SHOULD DO!) and the screen shots looked impressive.

So downloaded and installed it.

And Impressed. It almost looks like Azureus, just a VERY lightweight version. Screen layout and the info it shows you all very similar.

Started it off on the same file.

Now remembering the PC is still running so had had a good 15 mins to get settled down.

But after about 5 mins, Deluge is running at, well, it's difficult to give it a figure as it's jumping about quite a bit.

It went to 5k/sec very quick, then topped out at about 40k/sec, then hovered back to 20k/sec, and now it's about 8K

That's my only observation at the moment.

Wheras Azureus on the PC, (generally) starts off slow and gradually builds up to a steady flow (it does move about of course, but pretty steady) 

Deluge is quite all over the place. it was 8k/sec moments ago, now it back up to 30k/sec. Looked again and it's back down to 7k/sec..

Looking back at the PC for a couple of mins. It seems to be holding 30K/sec to 40K/sec with the occasional drop to 25K/sec.

Deluge (apart from the odd burst) after going down to under 10k/sec for some time is now looking like it's going to be hovering around 15 to 20k/sec though it does keep dropping quite low (erratic) Back down to 8K/sec again.

Hmmm, well, it looks good, and has all I want, but (As I'm reporting about) It's a bit erratic in the speeds.

Odd?

---

### Post by PiggiePaul on 2008-02-19
Yawn.............

One last "numbers" update before I go to bed (1am in the morning here)

Now both the PC and Ubuntu (Deluge) have been running ans settled down it seems.

My OLD PC running Azureus is still averaging out at about 40K/sec
My FAST PC running Deluge is still averaging out 15 to 20k/sec

Both connected via Gigabit network cards into a Gigabit switch and the Gigabit switch connected to a cable modem.

So both machine have identical connections to the net and both are downloading the same file at the same time with the same upload rate setting.

Odd huh?

========= EDIT ==========

Just had to come back and add this before I went.
Just went to shut all progs down and Deluge had dropped to 4K/sec and now it's back to 15K again.

All over the place!

---

### Post by om1 on 2008-02-19
well most clients only allow 1 connection from the same ip... since both of them are on the same network your public ip is the same on each of the systems... so therefore the peers and seeders will allow one to connect but not the other... so the ubuntu system might be getting the short end of the stick so to speak

---

### Post by PiggiePaul on 2008-02-20
> **om1 said:**
> well most clients only allow 1 connection from the same ip... since both of them are on the same network your public ip is the same on each of the systems... so therefore the peers and seeders will allow one to connect but not the other... so the ubuntu system might be getting the short end of the stick so to speak

Good point.

I shall do another test tonight, but keep them seperate.
and see how the speed goes.

---

