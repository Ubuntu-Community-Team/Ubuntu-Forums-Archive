---
title: "Making Ubuntu Faster"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by twirp on 2006-04-11
I'm sorry if this thread has come up alot,
But I was wondering what are the different ways to make Ubuntu faster.
I'm trying to bring an old computer back to life.
The stats:
 - 64 MB Ram (Saving up for more)
 - 16 MB Video Card (I think, that's what my brother told me it had).
 - 10 GB Hard Drive (I don't think that really matters).

I did the server install, then installed Xfce.
That made it a bit faster than when it was GNOME, but when I run multiple things at once, it starts to lag.

I saw that using Fluxbox can make it faster, and that's currently being installed.
I also came across a post about Openbox being used instead of Metacity could make GNOME faster.
So I'm wondering which would run fast, and be nice to use (I like Xfce and GNOME, but can settle for something else).
I've never used Openbox by itself, or at all.  And I was wondering what would work best.

I've also seen other X Window managers like Waimea and Kahakai and wondering if anyone has treid those and how they work.

Thankyou for your time.

*Edit: I've seen alot of people have puffy avatars, are they in a special group?*

---

### Post by xXx 0wn3d xXx on 2006-04-11
[QUOTE=twirp]I'm sorry if this thread has come up alot,
But I was wondering what are the different ways to make Ubuntu faster.
I'm trying to bring an old computer back to life.
The stats:
 - 64 MB Ram (Saving up for more)
 - 16 MB Video Card (I think, that's what my brother told me it had).
 - 10 GB Hard Drive (I don't think that really matters).

I did the server install, then installed Xfce.
That made it a bit faster than when it was GNOME, but when I run multiple things at once, it starts to lag.

I saw that using Fluxbox can make it faster, and that's currently being installed.
I also came across a post about Openbox being used instead of Metacity could make GNOME faster.
So I'm wondering which would run fast, and be nice to use (I like Xfce and GNOME, but can settle for something else).
I've never used Openbox by itself, or at all.  And I was wondering what would work best.

I've also seen other X Window managers like Waimea and Kahakai and wondering if anyone has treid those and how they work.

Thankyou for your time.[/QUOTE]

1. Disable unneeded services from starting
2. InitNG (Search in wiki)
3. Prelink
4. Tweak reisers/ext3 filesystem for a proformance boost
5. Get the latest kernel from kernel.org, I wouldn't recommend if you are very new to Ubuntu but it can really improve performance.

---

### Post by nalmeth on 2006-04-11
The lighter and lighter desktop you go, the more functionality you're going to lose.
Do some research into prelinking apps to make them start faster.
Also, you can use lighter webbrowsers and file managers if it starts to get really rough.
Apps like firefox and openoffice can be hogs on a slow system.
Dillo is the lightest browser I've seen, but like I said you lose functionality. 
Epiphany and galeon are lighter browsers, that might help. Abiword is a GREAT wordprocessor, quite fast for me.
There is ubuntulite, which install's icewm, but I think it looks terrible by default, and has to be heavily modified to look nice. I have seen some beautiful screenshots though.
If you want a really fast system, I would install Dapper Drake Flight 6, and go with one of the lighter window managers, and use lighter apps. I've seen some big speed improvements in my dapper testing, and it is very stable for me right now, still like 2 months or so away from official release.

---

