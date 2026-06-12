---
title: "Watching TV from laptop"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-04-25
To be able to watch TV on your computer, you need a TV cable going into your laptop. Now that seems VERY... restricting.

Is there someway I could plug the TV cable into something like a... wireless signal? To where I can walk anywhere around the house and still watch TV without having it be plugged in (but still accessing the cable signal from a router or something?)

---

### Post by annda on 2007-04-25
sure, there are some transmitters on sale, but i doubt they have linux drivers. look around and see if you can get anything with with a bluetooth adapter.

---

### Post by jamiehd on 2007-04-25
> **annda said:**
> sure, there are some transmitters on sale, but i doubt they have linux drivers. look around and see if you can get anything with with a bluetooth adapter.


Would bluetooth be fast enough to watch TV?

---

### Post by chris062689 on 2007-04-25
I saw Slingbox.  It looks pretty promising, but would I be able to use it on Linux? :(

---

### Post by Austin_KW on 2007-04-25
You can have a ubuntu PC re-broadcast the TV program on you home LAN and then just pick it up on your laptop using its wireless connection. I know kaffeine allows this and I am sure that other players can also do it.

---

### Post by chris062689 on 2007-04-25
Just found a great alternative.
[http://www.sagetv.com/sagetv.html?sageSub=tv](http://www.sagetv.com/sagetv.html?sageSub=tv)

---

### Post by Austin_KW on 2007-04-25
Yes but, you do know that you can do all all of that (and more) for free on linux. Look at solutions like mythtv which is basically a linux media center.

---

### Post by chris062689 on 2007-04-25
...
You can do this wireless ly on Linux? How? :/

---

### Post by Austin_KW on 2007-04-25
> **chris062689 said:**
> ...
You can do this wireless ly on Linux? How? :/

Your media pc (with the tv card) broadcasts the program on your LAN. It is best if this media pc is using a wired connection but it can be wireless ethernet.

Any PC on you home network can listen in to the broadcast and display it using your favourite media player.
Assuming that you have a wireless router or access point on your network, then you Laptop can use its wireless ethernet to listen in. It can also use its wireless connection to control the media PC.

---

### Post by stmiller on 2007-04-26
There are lots of good usb hdtv tuners out there. You'd have to plug one in and see how reception is. Otherwise, you'll need a cable/antenna connected to that tuner.

Bluetooth is horribly slow.

---

### Post by sstickeler on 2007-04-26
Check out [http://www.silicondust.com/wiki/products/hdhomerun](http://www.silicondust.com/wiki/products/hdhomerun)

It has gotten good reviews. Can stream to MythTV and VLC. Both of which run on Linux.

---

### Post by Beezleblub on 2007-04-26
It depends on what you want to watch. 

If you want Free to air program receiption, get a digital Usb receiver (DVB or atsc, depends on where you are... )
If you want to see TV programs receieved via your set top box or cable network, then your best bet is indeed to have a media server converting your receievd program into a transport stream on your network. 
Myth TV should be able to do that. only need to install mythTV frontend on your laptop. 

don't have much good experience with streaming live video wireless though... might have to reduce quelity to get acceptable bandwith over your network, I guess you should be able to get an acceptable trade off there.

---

### Post by Beezleblub on 2007-04-26
Alternatively have a look at VLC.
Comes standard with Ubuntu (for Sure Feisty is using it for remote desktop control)

you should be able to use a tv capture card, and have VLC transmitting the TVcard input into a stream on your network. 
All your Laptop needs is vlc viewer to watch the file. :popcorn: 

Cheers!

---

### Post by chris062689 on 2007-04-26
Well, I use roadrunner (cable) so I would have to get a "media server" (such as [http://www.silicondust.com/wiki/products/hdhomerun?](http://www.silicondust.com/wiki/products/hdhomerun?))

What's the cheapest one, with "good" quality?

---

### Post by Beezleblub on 2007-04-26
I don't know about the fixed Media servers. 

I checked out the VLC program yesterday. It works like a charm. 

Install VLC, then use the wizard in VLC to open your source (Either File or TV-device), 
and indicate you want to stream the source over your network. 
you need to indicate IP address of  the PC you want to stream to. 

On my Laptop only needed to have VLC player opening a network stream. 
I Had smooth video even over my wireless connection. 

I got it all working in less then 30 minutes. 

You could consider to use a small pc to do this, instead of a dedicated Media Server device. 
if you use a card with hardwre Mpeg encoding (like PVR150) then you will not need a very heavy PC with huge harddrive. very basic system will do the job.

---

### Post by chris062689 on 2007-04-27
what dedicated media server did you use?

---

