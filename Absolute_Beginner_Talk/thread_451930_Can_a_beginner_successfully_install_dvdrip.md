---
title: "Can a beginner successfully install dvd::rip?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by djschwartz on 2007-05-22
I'm thinking I want to use my Ubuntu desktop to copy some DVDs rather than my XP laptop, so I hit up the forums looking for some advice on what program to use, find out dvd::rip is pretty popular so I figure I'd give it a go.

It tells me I need several other things, so I got used to the following commands (often having to repeat with sudo in front)

cd /home/me/desktop/
mv dvdrip-x.xx.tar.gz /usr/share/
cd /usr/share/
tar xfz dvdrip-x.xx.tar.gz
cd dvdrip-x.xx.tar.gz
perl Makefile.PL
make test
make install

oh, but then I didn't have libgtk2-perl so I download another file and go thru the same steps.  And then i don't have libevent-perl so I run through the now starting to get familiar process.  Finally I think I'm able to install dvd::rip!!!

But when I go to run it I get a list of required pieces, most of which are red.  Most of them are optional, so I figure I'll get the ones that are mandatory and have another go at it.  First I need transcode.  Thats it, trascode, no link to where I can get it from or anything.  A google search solves that problem pretty quick thought.

Now I've got transcode, but suddenly my normal "tar xfz" doesn't work.  More google searching tells me to do "tar xfj" and that works.  Now there are more different commands, I have to do a ./configure and maybe give it some extra information, but I don't know so I don't.  A ton on text flies by and then I have "make".  This bombs because I'm missing more stuff.

I've spent almost an hour getting up to this point by now so I decide to quit for a while.  I'm just messing around and decide to right click on the DVD icon on the desktop.  Well a "Copy DVD" option shows up there :D wonderful.  I'm copying an image right now and will happily put the installation of dvd::rip on hold for some rainy day when I've got nothing but time.

Part of this is just me venting here, but I wonder is this the typical experience of a beginner trying to install programs that are not in the Ubuntu Add/Remove Applications, or am I going about this completely wrong?

By this point I fully expect the "Copy DVD" option to not work.

---

### Post by Nekiruhs on 2007-05-22
Its in the add remove for feisty, thats how I got it.

---

### Post by BitTorrentBuddha on 2007-05-22
The program can be installed much easier by running:```
sudo aptitude install dvdrip
``` or even easier by using synaptic or add/remove programs, located at the bottom of the Applications menu and under System -> Administration, respectively. Don't mess around with source code, it's not fun.

---

### Post by djschwartz on 2007-05-22
That is all it takes huh?  I'll try that out after this hockey game is over tonight.

Thanks

Is that just Ubuntu thing, or any debian based, or any linux?  I guess it probably doesn't matter, I'll prob never (or at least for a long time) move away from Ubuntu, but I'm curious.

---

### Post by BitTorrentBuddha on 2007-05-22
sudo apt-get install <program> will work on any debian based distro (aptitude is simply a superior form of apt-get.) Some don't include aptitude, but I find it more appealing because it remembers dependencies when it comes time to uninstall.

---

