---
title: "Windows user wanting to use Ubuntu as a dedicated game server"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Hospanky on 2008-01-21
I just installed Ubuntu today on a frankenstein of a machine...altho that makes it sound slow.

I built this machine with the sole purpose of running a game server or two, in a linux OS.  I chose Ubuntu because it appeared simple to work with.

Starting off, it WAS simple to work with.  installation was beautifully designed and I had it up and running within about 30 minutes.  it downloaded a pile of updates, most of which I don't know what they were (177, I'm not reading each n every one, I got bored after about a dozen).  I will assume none of them did Bad Things.  The OS runs smoothly and I can browse the internet....

I can't install anything.  and every time I try to search for installation help, the only help I get is how to install the programs that came WITH ubuntu.

I wanted to run a server for a mod of HL2, and a standard UT3 server if the system could run both reliably (3.2ghz single core, 2 gigs of ram).

I downloaded the files I need for them but they simply complain that there's no program to install them...aaand that's that.  no little "click here for more info" or anything.  after HOURS of searching, I still find nothing useful.

Oh yeah...YES, I have the bandwidth to host both servers.  I'm sure most of the power users on here will consider me a fool but I know a 2 mbit upstream is gonna do just fine.

Here's what I know:
Firefox downloads these files to the desktop.
I have created a folder in my computer called GameServers in my Home Folder
I would like to install the UT3 files into this folder and be able to launch a game server.


I've run game servers in windows before, and I have little fear of config files.  I'm not worried about setting up SPECIFICS of the game server, just how to get the damned OS to recognize it as something to RUN.  I will fiddle with the rest but I'm gonna need some hand-holding at first.  I'd hate to have to wipe the box and set it up as Windows...mostly because of the unreliability and also because it's open wide to attacks.  But if I can't figure out this OS I have no choice.  PLEASE help!!

---

### Post by apostate on 2008-01-21
Ok.

The Ubuntu supported stuff comes in a manageable package, called a .deb file. This is much like a Mac installer, a sort of special archive that self installs. Great.

What you have is a generic, distro- agnostic package, which will install on anything. To achieve this, 3rd party vedors will usually do one of two things. Give you the source via a .tar archive, or give you a "copy install" of the working binaries and other needed crap, also in a .tar archive. These sorts of packages don't *install* per se. They must be compiled, resulting in an install, or in some cases they are just folders full of working stuff that you must simply unzip and stick somewhere.

What game server are you trying now, and what is the file format of the thing you downloaded?

If it is .tar, .tar.bz, or .tar.gz,  uncompress it and tell us what was in there. If not, provide details.

-cheers

---

### Post by Hospanky on 2008-01-21
oOOoo I finally found it...

had to mark the file as "executable".

sneaky!
Ok, now things are starting to make sense again.


in case you were wondering, it was the UT3-linux-server.bin

and now I'm pretty sure I know what to do with the HL2DS bin file as well.  that oughta keep me occupied for a while :)

---

