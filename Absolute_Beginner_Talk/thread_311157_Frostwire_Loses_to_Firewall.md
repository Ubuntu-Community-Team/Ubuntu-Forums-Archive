---
title: "Frostwire Loses to Firewall"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-12-02
The default firewall blocks Frostwire's atempt to connect.  I have tinked around with firestarter, but that doesn't do any good.  I set the firewall on my router to off, but that doesn't help either.  If frostwire can be installed, why can't it get past the firewall?

---

### Post by msak007 on 2006-12-02
If you're referring to the fact that Frostwire says "Connecting..." and says you're behind a firewall, it's a known issue with version 4.10. You can either follow [this]("http://www.ubuntuforums.org/showpost.php?p=1724307&postcount=44") post to replace the file gnutella.net, which tells the app which peers to connect to, or upgrade to 4.13. It's not a final release yet, but fixes that problem and adds several other features.

---

### Post by hodad on 2006-12-17
MSAK007
I'm baaaack!

WHile trying to figure out how to download music files, I found out about Frostwire, and installed it.

I have gotten to the point where I am having the same firewall problem as everyone else.  I have edited the .gnutella file, and have successfully installed Frostwire 4.13.1, but I still have the firewall icon (tried turning it off with Firestarter as well with no luck).

Any ideas on what I should try?  Lots of posts on the subject, but nothing seems to turn off the](*,) 

I feel in my bones that someday I'll be listening to music on my Zen V;) 

-hodad

---

### Post by msak007 on 2006-12-19
Hey hodad :). You may want to upgrade to Frostwire 4.13 to fix that issue. It's still beta, but that issue with the firewall has been resolved. It now connects to 4 ultra-peers, so it's always running like Limewire Pro in "Ultra" mode so you get better / faster connections. It also has a bittorrent client built-in, but I haven't tested that feature. It's been stable for me so far, give it a shot and see if it resolves the issue for you. Get it [here]("http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb").

---

### Post by hodad on 2006-12-19
Sorry, but I did upgrade to 4.13.1, and the firewall icon is still there!  Also has "Starting Connection" right next to the brick wall.  One observation, however: Under "Connections" tab, I see addresses scrolling by, so it looks like it is accessing sites, but I get nothing when I do a search for a song or artist (and, of course, the brick wall is still there).  Seems a bit contradictory, but that's what's happening.

---

### Post by ciscosurfer on 2006-12-19
> **hodad said:**
> Sorry, but I did upgrade to 4.13.1, and the firewall icon is still there!  Also has "Starting Connection" right next to the brick wall.  One observation, however: Under "Connections" tab, I see addresses scrolling by, so it looks like it is accessing sites, but I get nothing when I do a search for a song or artist (and, of course, the brick wall is still there).  Seems a bit contradictory, but that's what's happening.If you have a hardware router/firewall then you should use Port Forwarding or Port Trigger and enable the ports Frostwire is using to connect in order to enable the hardware router/firewall to allow access.

---

