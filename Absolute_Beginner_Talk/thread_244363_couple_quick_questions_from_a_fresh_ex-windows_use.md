---
title: "couple quick questions from a fresh ex-windows user"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by spookshow on 2006-08-26
completely decided to do 100% linux on this box (with wine for a few essentials) and have a few issues i wish to ask about


1. logitech g7 cordless mouse.
i followed the directions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=219894") and when i do, the gui won't load at all... i use the logitech usb device option and nothing seems to work.. is there something i'm missing (possibly in that thread i may have overlooked maybe?)

2. logitech g15 gaming keyboard under ubuntu
i haven't actually tried anything with this yet, but i found this page about it [here]("http://www.waug.at/g15lcd/") and was wondering if anyone had any luck with it, and could help me set it up (i'm a very quick learner)

3. permissions
what are the ideal settings for all drives. i'm currently running the following

a. 40 gb drive that i have ubuntu installed on, in ext3, one partition
b. 250 gb maxtor ide internal drive that is basically my temp drive right now, copying everything to it when i was converting all the drives, so almost nothing on it (just my ex-windows system drive on it currently, just to import some settings and profiles from soulseek, firefox, etc), one partition, ext3
c. 400 gb samsung ide internal drive that houses my live recordings/dvd's of nine inch nails ((kind of obsessed, i am, really, it is almost full!)) , no partition, ext3 
(SHOULD i have a partition? or is running it like this just fine, i have it almost full of live shows, and really don't feel like copying it all off just to add a partition and copy it all back, but if it is something i should do, i will)
d. 160 gb samsung sata drive that has all my personal files ("my documents" folder from windows"), one partition, ext3 
e. 300 gb maxtor sata drive that stores all my music files (mp3, flac, ogg, etc) and videos all sorted up nicely into about 1000 directories, one partition, ext3
f. 250 gb wd external drive, which i'm using as a shared drive between this computer and the wifes pc, and my media pc (running xp pro, and xp mediacenter), one partition, vfat

a is set (as ubuntu set it) at owner: root, -rw-rw---- (i believe)
b, c, d, e are mounted and set at owner: <me>, lrwxt-xr-xr
f is mounted and set as owner: <me>, - drwx------ (another question about this one is that i can't seem to actually change the permissions on it even though i am owner.. want to change it so that my wife can access it from the xp computer, or me from the media center box.. ubuntu auto mounts it though, and won't let me change permissions from terminal or from the properties menu.. we can see it on the network, but not read or write to it, which is a problem, since this is the drive we want to share, although it doesn't have to be)

4. setting up an ftp
i have a domain, and i have an address on that domain forwarded to my ip, was wondering how to setup an ftp so that i could access my files for when i am away. i have used windows ftp server programs before and have a decent understanding of them (filezilla mostly, but have used others)

5. vnc
which vnc, or vnc type program, would be best for connecting to windows computers or running from windows computers to connect to this one and vice versa. because my mediacenter is connected to a non high def tv, and the text is really hard to read, i enjoy using vnc to connect to the computer and do any updates or any tweaking or anything like that with a different computer.

6. multiple displays
i currently have a 20.1 lg l203wt monitor, and am thinking about setting up a second on it (had this one plus 2 samsung 712n's while running windows, and installing ubuntu, but going down to (soon) 2 l203wt's running at 1680x1050 instead) just wondering if it is a hard process, and if anyone has had any issues running 2 widescreens at that res? it was a chore getting the single one working, but i have all that figured out and really loving my full native res

7. also wondering about some programs that work well under wine/gnome (eg. programs i have bought under windows that i want to use under linux)
a. video editing. i do a lot of recording of live shows with my camcorder and am looking for a decent video editor that will work under gnome, or wine if i have to (i usually use vegas, have it installed on other machines... really just need something i can splice together video with and add text overlays, as well as something to create dvd's and dvd menus with).. if it is a non-free program that is ok too (looked through google, found a couple that will do basic editing, just have a lack of overlaying options and stuff, haven't looked onto the wine side of things yet though)
although, question 5 will help that as well, as i could do all the video work off the htpc through vnc if it all gets setup properly)
b. ebay listing program. does ebay turbo lister work under wine? (sorry, just thought about it, haven't checked google or anything at all)
c. multi track sound editing/loop creation (fruitystudio, acid)
e. something similar to EAC, for perfect ripping from cd's, as well as a good frontend for flac, so i don't HAVE to use the commandline.. also an all in one, take your codec pick frontend for converting to mp3/ogg/etc (haven't checked out any of the programs that come packaged, it is on the list of things to do today)
d. list of programs i own under windows that i haven't checked to see wine compatibility yet (not OVERLY worried, i know i COULD run windows under vmware, just not really wanting to, and i can just use them on the other computers, just really feeling the need to branch from ms and switch 100% to linux in this house... i've always liked the concept of linux, and want to get as deep as possible into it)
fruitystudio, sony vegas, sony acid, dvd architect, tmpeg suite, dr divx (now free opensource for windows), divx codecs themselves, think that is about it (all vid editing shtuff that i didn't find open source replacements for)
e. emulators, emulators, emulators (don't always want to play on my actual systems)

8. (auto?) updating drivers
this question isn't really for me, my brother is REALLY considering switching to linux himself, but he is a big fan of the device manager under windows xp, with all the "update driver" and such that it has, is there a utility or somethign built in that i haven't noticed yet that will accomidate him on this?

i think that is the only main issues i'm currently having.. and i could figure them out (i HAVE spent the past few days buried in terminal getting this computer to run exactly how i want it to, so i have a fairly good, but newb like knowledge of linux)
so far i have kicked the butt out of learning how to mount/chmod/own/mkfs/

thanks in advance, and sorry for being a pain in the ***

---

### Post by bodhi.zazen on 2006-08-26
These are not a "couple quick questions". I think you should spend some (more) time searching the Ubuntu forums or Google. If you have a specific question try to post a single question in each thread. I would need more details on your mouse for example.

1. Mouse. This is a long thread and I am not sure where your problem is. Did you get some error messages? Perhaps you should look at the old thread.

2. Try keyboard and see. Basic functions should not be a problem. Extended functions can be more problematic.

3. Drives. Again, this is not a short question.
I keep drives owned by root:user or for a personal drive root:user_name.

Permissions generally 770.

For a shared drive with Windows you should look into Samba.

Is there a specific question on a specific drive?

4. ftp should be straight forward for you then.

5. VNC- Any should work. I have experience with open VNC and Tight VNC, both worked fine.

6. Again multiple displays should be no problem. You will need to re-configure X.

7. This is a long list. I suggest you look into Linux native applications first, fall back to wine if there is no alternate.

For an emulator try QEMU.

8. For the most part yes, drivers are upgraded automatically via synaptic or apt-get dist-update.

---

### Post by spookshow on 2006-08-26
those were basically the answers i'm looking for, just a point in the right direction.. it was just kind of a "wow, i've had way too much coffee this morning" and the post just kept becoming bigger and bigger, just adding stuff off the top of my head, and kind of wanted to keep it all in the same thread to keep it more compact instead of flooding the board.

in response to your comments

1. there is a couple error messages when the gui tries to load, i will post them in the mouse thread next time i try to set it up (today or tomorrow)
2. that is basically what i was going to do in the next few days, i just was wondering if anyone had tried it and what is usable and not.
3. pretty much answered my question on that one, just wanting a heads up one what i should have them at.
4. perfect.
5. again, perfect.
6. figured so, just didn't look into it yet because i haven't picked up the second display
7. i realise it was long, it was a last minute thing i just added as a "i wonder if anyone knows" thing, not REALLY looking for an answer
8. that's what i basically told him, but i figure he is lazy

---

### Post by bodhi.zazen on 2006-08-26
> **spookshow said:**
> those were basically the answers i'm looking for, just a point in the right direction.. it was just kind of a "wow, i've had way too much coffee this morning" and the post just kept becoming bigger and bigger, just adding stuff off the top of my head, and kind of wanted to keep it all in the same thread to keep it more compact instead of flooding the board.

in response to your comments

1. there is a couple error messages when the gui tries to load, i will post them in the mouse thread next time i try to set it up (today or tomorrow)
2. that is basically what i was going to do in the next few days, i just was wondering if anyone had tried it and what is usable and not.
3. pretty much answered my question on that one, just wanting a heads up one what i should have them at.
4. perfect.
5. again, perfect.
6. figured so, just didn't look into it yet because i haven't picked up the second display
7. i realise it was long, it was a last minute thing i just added as a "i wonder if anyone knows" thing, not REALLY looking for an answer
8. that's what i basically told him, but i figure he is lazy

Glad I could help.

1. With mouse, yes post error messages, mouse thread or new thread.

2. Only other comment I have is Linux is not a great OS for people who are "Lazy". Lazy people tined to become frustrated with Linux. Advise you learn LInux first, leave you brother in Windows. Windows is for the lazy.

---

