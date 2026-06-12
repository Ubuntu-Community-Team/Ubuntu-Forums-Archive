---
title: "System slowly grinds to a complete halt"
date: 2005-05-24
forum: Apple PPC Users
---

### Post by supernaut on 2005-05-24
This is a funny one - I had no trouble with Warty, or Debian before that, but 2 out of 3 times with Hoary my system slowly grinds to a complete and utter halt, usually 1-10 minutes after start up. 1 out of 3 times it will run fine. At first I thought GNOME was just to heavy for this machine, but it even happens with ratpoison!

The one time that I managed to get to a console and top, it didn't show anything out of the ordinary, which only puzzled me more.

Could my swap file not be initialising properly perhaps?

Any help would be much appreciated.

---

### Post by ssam on 2005-05-24
is it something like updatedb kicking in and doing heavy disk stuff, which will slow down the swap? if you leave it long enough does it recover?

how much ram do you have? does it happen in a lighter window manager?

sam

---

### Post by Len on 2005-05-24
If you think it is the new automatic update program the solution is simple: pull out your network cable and see if the problem persists.

This is a very strange problem though... Maybe it helps if you provide your system specs, although I've never seen this happening on a PPC 5500 running Gnome on 64 MB of RAM either. It could be a disk error.

---

### Post by supernaut on 2005-05-24
[QUOTE=Len]If you think it is the new automatic update program the solution is simple: pull out your network cable and see if the problem persists.

This is a very strange problem though... Maybe it helps if you provide your system specs, although I've never seen this happening on a PPC 5500 running Gnome on 64 MB of RAM either. It could be a disk error.[/QUOTE]
 Hey, it's a 1GHz G4 with 128 of RAM (yes, yes, I know). What's funny though is that it doesn't happen consistently. Also, it's funny that top doesn't show anything.

ssam: As I said in my original post, it even happens with ratpoison! Bizarre huh?

---

