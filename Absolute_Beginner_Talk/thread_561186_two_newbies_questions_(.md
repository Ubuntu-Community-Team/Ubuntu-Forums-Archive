---
title: "two newbies questions (:"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-09-27
1. lately I'm getting LOW ID on my aMule. this has started since the fall of the Donkeyserver No. # servers. all ports are open on my router
what could be the problem?
2. since i haven't managed to solve [this thread]("http://ubuntuforums.org/showthread.php?t=537101"), I'm thinking about buying a new sound card. 
the problem is that I'm quite sure that my sound card is onboard.
how can i check it out without taking my PC apart?

thx

---

### Post by PmDematagoda on 2007-09-27
What's the motherboard you have?

---

### Post by psmar on 2007-09-27
just a thought have looked on the back to see where your audio plugins are located? chances are if its not using the slots then its imbedded

---

### Post by madoracle on 2007-09-27
1) Stop using eMule and switch to Bittorrent :P

2)  If you are not getting sound from your rear-speakers but you ARE getting it from your front ones, most likely whatever you are listening too does not support surround sound. You have to enable to option. Also go into alsomixer and make sure the speakers aren't muted - I know I had to unmute my rear speakers and my sub.

---

### Post by asakurax on 2007-09-27
> **madoracle said:**
> 1) Stop using eMule and switch to Bittorrent :P

2)  If you are not getting sound from your rear-speakers but you ARE getting it from your front ones, most likely whatever you are listening too does not support surround sound. You have to enable to option. Also go into alsomixer and make sure the speakers aren't muted - I know I had to unmute my rear speakers and my sub.

1. i am using both (: but there are some stuff which are unavailable for bittorent
2. i believe i tried every alsamixer mix possible
my windows has no troubles playing all songs on 4 speakers
the only thing which affects my speakers volume is the PCM

---

### Post by madoracle on 2007-09-27
Ah, no idea on the emule then. I stopped using it.

As for the sound issue - if alll your speakers are unmuted the problem is most likely with the application itself. Most all audio and video you find on the net is set for stereo, so the programs to run them - like Xine - are configured for stereo only. You have to manually change it to surround 5.1. 

I can't tell you how at the moment because I'm not on my linux box, but if you google it you should find what you need.

---

### Post by Fixman on 2007-09-27
If you don't want to use BitTorrent,  ask you, do you have a private connection on your house?

If you don't know what Im talking about, go to the terminal, tell me your IP number.

---

### Post by asakurax on 2007-09-27
> **madoracle said:**
> Ah, no idea on the emule then. I stopped using it.

As for the sound issue - if alll your speakers are unmuted the problem is most likely with the application itself. Most all audio and video you find on the net is set for stereo, so the programs to run them - like Xine - are configured for stereo only. You have to manually change it to surround 5.1. 

I can't tell you how at the moment because I'm not on my linux box, but if you google it you should find what you need.

I wanna have surround sound on the Rhythmbox, since all my music is play via it. i could not find how to configure it for surround


> **Fixman said:**
> If you don't want to use BitTorrent,  ask you, do you have a private connection on your house?

If you don't know what Im talking about, go to the terminal, tell me your IP number.


i have a router. but as i said - on my windows it worked perfectly well

---

### Post by Hallvor on 2007-09-27
> **madoracle said:**
> Ah, no idea on the emule then. I stopped using it.


Your loss ;)

If you change your mind, try one of these. By the way, was Kad too firewalled?

[http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz)
[http://peerates.net/peerates/certifiedservers.met](http://peerates.net/peerates/certifiedservers.met)
[http://peerates.net/peerates/trueservers.met](http://peerates.net/peerates/trueservers.met)

Edit: Can`t notice any bad effects at all, even though the largest servers are down. Kad is working perfectly.

---

### Post by Shunketsu on 2007-09-27
I've heard of eMule but I don't use it

I'm new to ubuntu so I don't know how to help you if you have a driver problem... BUT! if you only need to play music/watch movies and desperate for surround sound you could use a stereo splitter as a temporary solution (would save you money buying a new sound card until the problem gets sorted).

---

