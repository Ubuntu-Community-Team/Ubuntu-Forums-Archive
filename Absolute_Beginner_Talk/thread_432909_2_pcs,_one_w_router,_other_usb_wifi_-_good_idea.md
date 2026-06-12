---
title: "2 pcs, one w/ router, other usb wifi - good idea?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by pedro.wicker.man on 2007-05-04
Hi all,

Fisrt off, thank you in advance for any suggestions you might have for me.
Second, apologies in advance if this has already been discussed somewhere else on the forum. I searched, to no apparent avail.

That said, here's the scenario.
On a room of the house I've got a Pentium IV 2.80 w/ 1GB RAM. On it i've got XP and Ubuntu 6.10. 
Connected to it i've got a WAG354G v2 that gives me access to the internet on both OS flawlessly.

On the living room i've got a Pentium III 700 something with 512 MB ram with xubuntu (latest one) installed. It is connected to the TV and stereo system, so as to function as a avi/xvid/mp3/ogg/jpeg/tiff/younameit player.

I would like to have, on this 2nd computer, wireless connection to the internet and to the ***other *** computer, and it's hardrives (internal and usb) so that i can see a movie file (avi) that's on a hardrive 2 rooms away from the TV. Plus, with the internet connection, i can listen to my favorite radio stations (wfmu and soma, for the curious ones :) )

That said, i was thinking of buying a linksys usb card and plug it into my xubuntu box. I've seen the compatibility list and there seems to be a couple of them that would work.

Will i be able, as a newbie that can follow directions, and paste stuff on a terminal, be able to have wireless internet on the living room and see (and play) the files i've got on the other computer? Is there any guide somewhere and did i missed it, thus making this thread useless?

Again, thanks in advance,
pedro

---

### Post by nanotube on 2007-05-04
once you are connected to the router wirelessly, your xubuntu comp will be automatically connectable to the other computers on the same subnet. 
if you just want file access, the simplest way would be to install an ssh server on the other computer, and then you can connect to it with ssh from xubuntu and see all the files.

it can even be mounted as a drive if you use nautilus's "connect to server" - probably there is something similar in xubuntu.

you could also go the NFS route, instead of ssh

but at any rate, since both comps are on the same local network, yes, definitely you can connect between the two.

---

### Post by pedro.wicker.man on 2007-05-04
Oooooooooooook....

i didn't quite undestood how to do all that, but i'll google and ubuntuforum it.  8)

Thanks for the reply!

---

### Post by xpod on 2007-05-04
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

Thats how i got nfs set up and ssh.....

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

nfs is better for pc`s on the same network i think.....no waiting for stuff to copy 
I dont know about wireless as i just use a second nic and a crossover wire to connect the second Ubuntu machine.

---

### Post by pedro.wicker.man on 2007-05-05
Great, thanks, i'll look into it :D

---

### Post by Mr.Beast on 2007-05-05
> **pedro.wicker.man said:**
> Hi all,

Fisrt off, thank you in advance for any suggestions you might have for me.
Second, apologies in advance if this has already been discussed somewhere else on the forum. I searched, to no apparent avail.

That said, here's the scenario.
On a room of the house I've got a Pentium IV 2.80 w/ 1GB RAM. On it i've got XP and Ubuntu 6.10. 
Connected to it i've got a WAG354G v2 that gives me access to the internet on both OS flawlessly.

On the living room i've got a Pentium III 700 something with 512 MB ram with xubuntu (latest one) installed. It is connected to the TV and stereo system, so as to function as a avi/xvid/mp3/ogg/jpeg/tiff/younameit player.

I would like to have, on this 2nd computer, wireless connection to the internet and to the ***other *** computer, and it's hardrives (internal and usb) so that i can see a movie file (avi) that's on a hardrive 2 rooms away from the TV. Plus, with the internet connection, i can listen to my favorite radio stations (wfmu and soma, for the curious ones :) )

That said, i was thinking of buying a linksys usb card and plug it into my xubuntu box. I've seen the compatibility list and there seems to be a couple of them that would work.

Will i be able, as a newbie that can follow directions, and paste stuff on a terminal, be able to have wireless internet on the living room and see (and play) the files i've got on the other computer? Is there any guide somewhere and did i missed it, thus making this thread useless?

Again, thanks in advance,
pedro

Hi Pedro, 
Are you happy with the distances and wireless performance you will be getting from the machine that is connected to the TV?  How many walls is it going through? 
Assuming you are, the other machine is dual boot, so I'm curious where your music and movies are going to be, and your choice of file system for this area (Fat32, NTFS, EXT?) Is your collection visible to both Ubuntu when booted, and XP when booted?
The files that are on USB, again, will it matter which O/S you are booted into for this. (If your movie files are on this external source, you would probably find it much quicker to walk into the other room, unplug the disk,  and plug it and mount the volume and play the film that way, than over the wireless LAN. :) 


I think it may be worth doing some tests on the environmentals in your scenario before you go setting up file shares everywhere and spending weeks getting something setup under windows, and ubuntu that may not perform as you expect it to.

---

### Post by DSn0wMan on 2007-05-05
I am not sure I read your question right, but if you are purchasing a new USB Wi-fi adapter it will make things much easier if you select one from this compatibility list.

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by sailor2001 on 2007-05-05
an interesting note........if you go with an eXternal usb antenna, you an purChese an amplified usb eXtender  Cable for about $16 that works wonders for bringing in signals from great distanes or through a lot of walls.......As far as I know, Hawkings usb antenas are not reogoniZed for linuX

---

### Post by pedro.wicker.man on 2007-05-06
Hi all,

I've been looking at my walls and doors and distance, and i'm getting excited with  the old-fashioned idea of cabling the distance... all in all it would be, with all the twists and turns so as to have the cable as conspicous as possible, we're alking about 30-35 meters, and this way i can have internet and intranet (so to speak) with little to no fuss. No compatiibilty problems, no fuss... simple and eficient. 

On the other hand, the "grab an external HD and take a copy of the film/episode to the living room" seems ok as well :)

Thanks all, i'll probably nag you lot a little more by the time i'll setup the network between both pcs. 

:KS

---

### Post by pedro.wicker.man on 2007-05-06
:mad: 

The doors won't close properly... :confused: 
Decisions, decisions....

I'm gonna have to sleep on it, thanks again all

---

### Post by pedro.wicker.man on 2007-05-06
> **Mr.Beast said:**
> Hi Pedro, 
Are you happy with the distances and wireless performance you will be getting from the machine that is connected to the TV?  How many walls is it going through? 

I've got a Nintendo Wii right next to the xubuntu box and can surf the web at ease, no problem with speed.

---

### Post by DSn0wMan on 2007-05-06
In my experience wireless works best, especially if you are renting. I dont like drilling holes in other people's walls. 

As long as you have supported hardware... wireless with Ubuntu is super easy to set up.

---

### Post by pedro.wicker.man on 2007-05-07
It wouldn't really be a case of drilling, or let's say the idea was to not drill, period, but yeah, i guess i'll buy the wireless thingy. It'll have to be next month, though, darn bills took me by surprise today!

---

