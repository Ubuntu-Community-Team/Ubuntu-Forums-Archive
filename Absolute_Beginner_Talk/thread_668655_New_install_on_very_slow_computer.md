---
title: "New install on very slow computer"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by JamesAG on 2008-01-15
So I've been working with ubuntu for a while now. Not exactly a beginner, but I'm no where near as good as alot of people.

I've been working on using ubuntu with Virtual PC, and I've installed it on my tablet pc M275 (which i'm very happy about). But my most current project is with a car pc. Specifically an MW520.

For those who don't know the MW520 is considered a Cop Car Computer. It comes with windows 2000 pro installed, with some motorola text message software for packet radio. And Delrome for the GPS.

The computer itself has 256mb of ram, and a pentium 2 @ 277mhz. I was able to get ubuntu's live CD running last night. But of course it was slow. I'm looking to use it specifically for kismet and GPS. But I need it to run better. I know I need to upgrade the ram, but that's just about money.

A few things I ran into, since the screen runs at 800x600, I couldn't get to see the entire windows for installing. Is there a console way to install ubuntu?
Should I install ubuntu server?
Which direction should I take this toy for wifi, gps, and maybe music?

I was able to rezise the NTFS partition (same as I did on my tablet) with no problem. So it's now just about installing the OS.

Any suggestions about optimization for such a low speed computer?

I would like to have a desktop also. Something to use the touch screen with, which I need to setup also. Not too familier with how to do that other than for a tablet pc, which that was pretty much setup already in the config file.

Any suggestions is helpful, and I'll be glad to run any tests that anyone wants me to do.

What a first post:lolflag:, thanks all for reading this and willingness to help me out on my project.

-James G.

---

### Post by hogman500 on 2008-01-15
well i think that all you really need to do is upgrade your ram. if your satisfided with ubuntu enouph you could delete your whole windows partition and use ubuntu as your whole OS. this is what i suggest since i like ubuntu way more than any windows OS smply because it dosent restrict you as much as windows u can modify almost anything you want. 

*note: if you do delete your windows you sholuld back it up to a disk (if its possible) so if somthing goes wrong with ubuntu you can revert back to windows.*

---

### Post by dgray_from_dc on 2008-01-15
Two things:

For better performance, try xubuntu.  Descent GUI, lower resource requirements.

To get a command line system and/or text install, download the alternate install cd.  The option exists there.

---

### Post by JamesAG on 2008-01-15
> **hogman500 said:**
> well i think that all you really need to do is upgrade your ram. if your satisfided with ubuntu enouph you could delete your whole windows partition and use ubuntu as your whole OS. this is what i suggest since i like ubuntu way more than any windows OS smply because it dosent restrict you as much as windows u can modify almost anything you want. 

*note: if you do delete your windows you sholuld back it up to a disk (if its possible) so if somthing goes wrong with ubuntu you can revert back to windows.*

Well I'm planning on leaving the windows partition on there for a dual boot reasons. it's a 40gb drive. So i've got enough room for "fun". :-D
I'm just not ready to give up the win partition for now.

My major concerns are getting ubuntu installed.
Getting the GPS working (com1)
Getting the Wifi working with kismet.
and getting the touch screen working.
(and the ram upgraded... once i get the wireless card, a quick browse at crucial should get me on the right track for that)

Any good links for the gps and touchscreen would be great... or some instructions.

---

### Post by JamesAG on 2008-01-15
> **dgray_from_dc said:**
> Two things:

For better performance, try xubuntu.  Descent GUI, lower resource requirements.

To get a command line system and/or text install, download the alternate install cd.  The option exists there.

I will look into it. But is there any good information about it working on a 270mhz machine? I will of course upgrade the ram asap.

---

### Post by crjackson on 2008-01-15
xbuntu would certainly be faster than ubuntu or kubuntu.  I would also have a look at pupplylinux.  Boot the live CD and have a look.  The support is pretty good, but not on par with U/K/X-Buntu.  It will be much faster than any -Buntu version.  You wouldn't need to up the ram either because it can run entirely in a smallish about of ram.  64mb I think.

---

### Post by dgray_from_dc on 2008-01-15
> **JamesAG said:**
> I will look into it. But is there any good information about it working on a 270mhz machine? I will of course upgrade the ram asap.

I've installed Xubuntu on a 333Mhz machine with 256MB of RAM or less (I think) and it was useable.  I don't remember whether or not performance was stellar (it was about a year ago) but it wasn't mind-numbingly slow.

---

### Post by JoshuaRL on 2008-01-15
I have Xubuntu installed and it's great.  But I've also heard good things about fluxbox and the XFCE-based Linux Mint.  Mint is based off of Ubuntu so it is well supported, and the user experience is supposed to be pretty great.

---

### Post by nikoPSK on 2008-01-15
Xuubntu, vector, damn small, puppy... etc.. :)

---

### Post by EmoDx on 2008-01-15
On the computers I had on the ship, they were all a Linux derivitive. They were a Dual processor set up with either 128 or 256 megs of ram. The processor was a 100mhz off brand. We used them for sat tty, had gps going intoi, and to issue basic controll commands to other gear. They ran decently. It took a little while to bring up different apps, but once they were up and running it was pretty smooth. Each station had 2 monitors and ran a different workspace one each monitor. 2 apps running on each station, plus what ever background services was assigned to that station.

I do know that GPS and other devices providing NMEA strings could give me head aches at times. I don't know if the software you'll be running has an auto-detect feature. But I had to do a lot of setup to get the software, OS, and GPS to all talk to each other in a friendly fashion.

The biggest help I had was being able to open a terminal hat monitors the COM port. Knowing if the sentences are actually coming in correctly and that they contain good data is almost a must in troubleshooting GPS.

-E

---

### Post by nikoPSK on 2008-01-15
there is also feather. which is nice on old systems. :)

---

### Post by JamesAG on 2008-01-16
> **EmoDx said:**
> On the computers I had on the ship, they were all a Linux derivitive. They were a Dual processor set up with either 128 or 256 megs of ram. The processor was a 100mhz off brand. We used them for sat tty, had gps going intoi, and to issue basic controll commands to other gear. They ran decently. It took a little while to bring up different apps, but once they were up and running it was pretty smooth. Each station had 2 monitors and ran a different workspace one each monitor. 2 apps running on each station, plus what ever background services was assigned to that station.

I do know that GPS and other devices providing NMEA strings could give me head aches at times. I don't know if the software you'll be running has an auto-detect feature. But I had to do a lot of setup to get the software, OS, and GPS to all talk to each other in a friendly fashion.

The biggest help I had was being able to open a terminal hat monitors the COM port. Knowing if the sentences are actually coming in correctly and that they contain good data is almost a must in troubleshooting GPS.

-E

I feel this computer is similar to what you are talking about, as this is for emergency vehicles and cop cars. The Gps should be giving out NMEA. I've been talking to one of my friends, he run's wifimaps.com we're trying to work on some ideas. First is using GPSd to use for the Daemon of the GPS, for multiple apps. Including Kismet, and GPSDrive. 
My current obstacle  is getting an antenna. I think it's SMA, as I've been told. So good luck to me, I almost had one from best buy but it was the wrong size, stupid garmin gps systems =(
My first task is still installation, then getting the touch screen to be recognized. And then the GPS, which should be simple.
I'd also like to get to load the command line and install via command line instead of booting to the gui, with xubuntu or whatever flavor I use. 
Any tips is going to be great.

---

### Post by JamesAG on 2008-01-31
So here's an update.
I got the GPS working, needed to run TSIP tools. Fun. I wont get into it here.

I dont remember if i mentioned, the computer is P3 and 500mhz. So I am a little happier.
I have GPSdrive working, and installed kismet. Both work great!

My concern is still the touch screen. Nothing I try works. even using the drivers ubuntu downloaded on its own. It sometimes gets the point information, and throws the cursor way off to the lower right corner. And sometimes, does nothing. Of course driver issue, or settings issue, will work on it when it's fully mounted.

I have a wifi card in it, and a 5dbi external ant. Working beautifully. Except takes for ever in ubuntu to clear the found list when clicking on the wifi signal in the topbar, in order to see what ssid's it hears and what i want to connect to. 

I have also bought a gps antenna, working also great! Unfortunatly GPSdrive does not show my satelite info, nor direction... anyone with GPS ideas? It is spitting out NMEA data now. =)

The interface is still a little on the slow side. I am looking to slim it down, and also try to stop some services from starting up, see if things speed up. I also found Ubuntu Satanic Edition, which I am going to install for the high contrast it gives (I dont like the defaults)...  also it'll keep a theme between my laptop, carpc, and media desktop (attached to TV, next project).

Anyone with ideas on the statements above, please help! =) Love to hear suggestions, also if anyone wants to give a verbal walkthrough or is wiling to talk to me over the phone about it, please PM me, I would love assistance. =)

---

### Post by pave-low on 2008-03-05
Another one for your list might be the function buttons around the screen. Is there a way to "log" the ascii codes from custom keyboards like that?
(newest newbie on the forum)

---

