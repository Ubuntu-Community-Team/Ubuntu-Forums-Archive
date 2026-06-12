---
title: "Linux Based Music Server"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by chowanec on 2007-09-30
Hey all,

Really, really new to Ubuntu.  Have it running on a dual boot pc right now to experiment with it.  Wife and I are music nuts, so we have a LOT of it on a second media PC right now.  Due to issues I won't go into about how old our house is and how hard it is to run wires, I am in the process of setting up a second media pc that will ONLY be used for Web Surfing and Music Serving.

That said -- I'm so used to Microsofts inability to control bloat that I'm not sure what specs I need.  My goals are to run something a QUIET as possible and build it as cheaply as possible.  That said, I've been looking at Mini-ITX boards (as the wife tends to approve of small geek-ware.)  There's Intel's Little Valley setup and then a host of VIA based boards that look like they could do the job.

I'm somewhat enamored by them, but am scared that I'll end up with something underpowered... Then again, note the bloatware comment above.   Maybe my barometer is just screwed... I dunno.

If you're JUST running a media player:

-How "buff" of a processor would you get?  (In MHz terms...)
-How much RAM would you get?

For reference, here's what I've been looking at:
[INDENT]Option 1:[/INDENT]
[INDENT][INDENT]

- Mainboard:    Intel D201GLY Little Valley Mainboard
- Case:    Morex 5677 Mini-ITX Case - Black
- Memory:    DDR2 533 RAM 1GB
- Hard Disk/Flash:    Emphase Industrial Flash Disk Module (40-pin) 4GB

[/INDENT][/INDENT]

[INDENT]Option 2:[/INDENT]
[INDENT][INDENT]

- Mainboard:    EPIA M10000G 1GHz
- Case:    Casetronic C134 Mini-ITX Case - Black
- Memory:    DDR266/333/400 Ultra Low Profile RAM 512MB
- Hard Disk/Flash:    Emphase Industrial Flash Disk Module (40-pin) 2GB
- A/C Adapter (brick):    A/C Power Adapter 60W (PW-AC 60W)

[/INDENT][/INDENT]

Both would use a flash disk as the main OS install drive.  Network Attached Storage would be used to pull the music.  Audio out to the stereo.  All set from there?

Thanks much,

Chow

---

### Post by tgalati4 on 2007-09-30
How big is your music collection?

For less than 10k tracks, a gnump3d system running on older hardware will be fine.

This has been running non-stop for the past year (uptimes of 130 and 165 days previously) on a 1 GHz Celeron with 512 MB of memory.  You only need 256 MB for Dapper.

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

ps:  I've tested a VIA Epia CN10000 system and it draws only 12 watts in use.  It has plenty of power as a server.  I've had a few rejects (out of a lot of 10) on the Emphase 4 GB flash modules.  I'm running Damn Small Linux on my Epia for a GPS-tracking program--it loads a read-only operating system in RAM only.  I'm not sure how well Ubuntu will run on a flash disk.

---

### Post by n3tfury on 2007-09-30
> **tgalati4 said:**
> How big is your music collection?

For less than 10k tracks, a gnump3d system running on older hardware will be fine.

This has been running non-stop for the past year (uptimes of 130 and 165 days previously) on a 1 GHz Celeron with 512 MB of memory.  You only need 256 MB for Dapper.

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

ps:  I've tested a VIA Epia CN10000 system and it draws only 12 watts in use.  It has plenty of power as a server.  I've had a few rejects (out of a lot of 10) on the Emphase 4 GB flash modules.  I'm running Damn Small Linux on my Epia for a GPS-tracking program--it loads a read-only operating system in RAM only.  I'm not sure how well Ubuntu will run on a flash disk.

don't mean to steal your thunder OP!  hey tgalati4, gnump3d shows some supported formats but no FLAC?  even if the back end (say xmms) supports it?

---

### Post by tgalati4 on 2007-09-30
gnump3 is a clever PERL script.  I don't use FLAC, but a few changes to the script should get it to stream and serve FLAC.  It just indexes and serves up files.  

For an internal network (at home for instance), you don't need anything more than Rhythmbox, Banshee, or Frostwire and DAAP sharing enabled.  You will even see your library in iTunes (but not the other way around--iTunes 7 won't share with other programs).  I'm testing Banshee 0.13.1 (the latest) with ~3k tracks and it's fast and works well with a remote share directory (on an old Pentium 1, 166 MHz machine) and wireless streaming to a powerbook running Tiger OS X and iTunes 7.0.4.

Gnump3d is useful if you need access to your music from outside of your local network.  You can add password protection as well.

---

### Post by madmatrixz3000 on 2007-09-30
I am a bit confused with your question, are you building a new computer or using an old one.  If you go with a new build I can suggest the media center mini cases from newegg.  I personally have looked at them for a similar system, but for my work computer to run basic ubuntu with only a few of my recording programs on

---

### Post by mrreality13 on 2007-09-30
i would go with the via as they have been makin mini itx for many years also look at there new nano itx for smaller size

---

### Post by chowanec on 2007-09-30
To answer multiple questions:

-I have 180 gigs of music.  Track count is definitely > 10,000.
-I will be buying a new machine for this -- I like the idea of the mini-ITX setup.  I'd go NanoITX, but it's too damn expensive.  I'm trying to keep the build under 400 bucks if I can.
-Ubuntu is all I know right now... not sure how confident I am going to be to try a different distro.

General consensus is that either of those machines will work, assuming I don't get any d.o.a. parts.

Thanks much.

-Chow

---

### Post by madmatrixz3000 on 2007-09-30
I say check newegg for different parts and consider a self buid if you haven't already.  It's not that hard and you know you get what you need.  Ex. if you want high quality vid or sound.  or perhaps you only want to access from other computers.  I don't know the situation, so right now it sounds to me like you want a media center type setup?

I would say go with a good vid card so you can put the pc in your AV setup and when you want to watch a movie, just pop it into the media center.  Ok I have to stop, I'm getting ideas that I might over think.

---

### Post by chowanec on 2007-09-30
Thanks for all the feedback... :)

I failed to mention that we already have a primary media center PC that we use to view movies, play music, etc.  It's just in a separate part of the house.  I'm quite literally only planning for this box to shuttle music from a NAS device through to the stereo.

I've bought and built a plenty on newegg... just don't want to screw around with embedded CPUs, tiny, tiny cases, etc.

All said and done both the builds up top are <$375.  If I take the spare desktop PC i currently have, and buy a fanless video card and a media pc case, I'll be in the 200 range in no time.  Plus a new CPU fan -- which is why I was going to go this route.

---

### Post by mcduck on 2007-10-01
I would suggest MPD instead of gnump3d. MPD has better support for different file formats, and wider range of available clients, including Windows, OSX and web-based clients. It also handles big music libraries very well, better than any other music player I've ever tried.

And it will probably run in any machine you can find that actually is able to play a music file ;)

---

### Post by jd65pl on 2008-01-11
mt-daap can serve files to itunes, amarok, rhythmbox, its pretty easy to setup.

[here]("http://jamiedumbill.com/index.php?page=28") is the guide I wrote

---

### Post by jseiser on 2008-01-11
i Have a spare older pc, with no HD, if i stick a usb stick in it, and fill it with all my music an dplug it into my router, i should be able to play the music files from it on my pc right?  What about my girlfriends windows PC?  Also, would playing a song, waste one of the rites to the flash drive?


I just want a common box between the computers where downloads are sent/stored.  I would prefer it to be headless, controlled over ssh or something along those lines.

---

### Post by jd65pl on 2008-01-11
> would playing a song, waste one of the rites to the flash drive?
Not sure what you mean by that? The files would be served, you could access them from more than one machine at a time. Does that answer your question?

I have a similar set-up to the one you have described, its got a number of servers on it and is all configured through ssh.

---

### Post by frankos44 on 2008-04-21
> **tgalati4 said:**
> How big is your music collection?

For less than 10k tracks, a gnump3d system running on older hardware will be fine.

This has been running non-stop for the past year (uptimes of 130 and 165 days previously) on a 1 GHz Celeron with 512 MB of memory.  You only need 256 MB for Dapper.

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

ps:  I've tested a VIA Epia CN10000 system and it draws only 12 watts in use.  It has plenty of power as a server.  I've had a few rejects (out of a lot of 10) on the Emphase 4 GB flash modules.  I'm running Damn Small Linux on my Epia for a GPS-tracking program--it loads a read-only operating system in RAM only.  I'm not sure how well Ubuntu will run on a flash disk.

I have tested the EPIA CN10000EG. I've got Gutsy Server running on a 4Gb flash and it runs well. 

I've also tried Gutsy Desktop with a SATA drive but it uses the generic graphics driver so no acceleration.  The driver from nvidia wont work properly either in as much I cannot default the resolution even after dpkg-reconfigure. 

Same issues apply to Hardy RC although things are worse because you cant use dpkg-reconfigure to set up the monitor and graphics in hardy, secondly the nvidia havent released a driver for Hardy yet.

I am impressed with the EPIA board all the same.
 I would love to hear from someone who has had some success in this area.

---

