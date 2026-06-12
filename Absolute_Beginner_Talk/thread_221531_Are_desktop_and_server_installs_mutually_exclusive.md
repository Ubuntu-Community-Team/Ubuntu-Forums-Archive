---
title: "Are desktop and server installs mutually exclusive?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by millerk123 on 2006-07-23
Can the desktop installation and the server co-exist on the same machine or do you have to choose one or the other when you intall from DVD?

---

### Post by steve.horsley on 2006-07-23
The server install is a minmal install for running services only - no GUI and therefore no desktop apps either. It is therefore not compatible with the desktop install, which is a full installincluding the GUI and a good selection of GUI applications. 

You could make them coexist by making two installs and dual-booting. Or you could just shut down the GUI on the desktop install when you're not using it.

---

### Post by T700 on 2006-07-23
Functionally, there is no reason you couldn't do a server install, install all the desktop apps, and then run it as a desktop.  You could also do a desktop install and then add all the things needed to run a server.  

That said, it is really best practice for a box to be one or the other.  No one wants their webserver going off line when somehow a game of Frozen Bubbles manages to crash the OS!

Paul

---

### Post by millerk123 on 2006-07-23
Good point. But since my server duties will be limited to my personal LAN it should not be a problem if it crashes. My main use for the server will be a LAMP platform for getting me up to speed on PHP.

I sure hope I can do all this through my one router, i.e. linux desktop connects to Internet, linux server connects to the other computers on the LAN, all through one ethernet wire. Windows does something like that with local file and printer sharing between computers on the LAN combined with a common Internet gateway that they share. I'm hoping linux can do that too.

I guess that's a question for the networking section here, actually.

---

### Post by steve.horsley on 2006-07-24
Yes it can. Except that other PCs connect to the server, not the server connecting to the other PCs. You should have no problems there.

---

### Post by hairygerman on 2006-07-24
I have exactly this configuration on my gateway (albeit in 5.10).
Initially it was only a server install (didn't have enough RAM), but after upgrading my RAM and Video card, I now have a fully functional gateway (which runs my website, mail server, DNS and various other bits and pieces) and it also serves as a desktop for games and PHP work. No probs.

---

