---
title: "Build from source or use wine for this program"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by BeatnikBandit on 2007-04-04
I would like to use this program called streamer which is a p2p internet radio like program most of the streams are ogg some wmv but those I'm not to worried about the site would give the best description of what this application does. [http://www.streamerp2p.com/?page=download.htm](http://www.streamerp2p.com/?page=download.htm) this page has downloads for both source (from an outdated version) and a windows exe. 

I have never been able to compile anything from source I've tried before but I am limited in my knowledge and I believe it is a fairly easy process when you get it but it takes a lot of hard drive space I kind of understand the build and make scripts. but I've never been able to work it out from source. Sorry for the long background information.

now for the question, img looking to either just use the newest version through wine if possible and I do not know how to use wine. I have it installed but I do not know the commands to run it nor do I have (if one exists) a GUI front end to make it a little easier for me to work out. to me that would be an easy solution?

Now on the other hand they have source posted and I don't know if it is a complicated program maybe someone could look over the source and find a way I can use another program to access the online streams? I don't know if the old version would work but also maybe someone could compile it for me?

I feel like I am asking a lot since I cannot do any that I ask but maybe there is someone out there that is willing to help me out and with superior knowledge in linux someone might be able to look at it to find the best or easiest way to use it.

---

### Post by phidia on 2007-04-04
Have you tried using vlc? You should be able to get it with synaptic.

[http://www.ubuntux.org/node/139](http://www.ubuntux.org/node/139)

---

### Post by BeatnikBandit on 2007-04-04
I cannot because you can only use the program "streamer to connect"  I was able to install streamer using wine thanks to this site [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine) but I am unable to get any audio out of it. It has an option to play the music on another player after you connect with streamer so of course I tried that and it told me I needed gekko it asked me if I would like to install it and I said yes and it just hung. so unless I can work it out the wine thing seems to be out unless someone knows what img talking about it is very small if someone is willing to try themselves. I used to use it with windows and used winamp to play the music so I was hoping to do the same but with xmms I have ogg and mp3 formats installed ( you need the program because its a p2p streamer with no central server so the company or program maker as it is freeware doesn't get in trouble I think. so that's why I need to get streamer to connect  I have vlc in case xmms doesn't work after I get gekko installed or figure out what the real problem is. I've managed to get it all set up with wine but now............ any help is appreciated thank you very much phidia for your quick try at helping me LoL I suck LoL :-({|=    < that makes me laugh the smallest smiley playing the smallest violin playing the saddest song LoL ha ha ha

---

### Post by BeatnikBandit on 2007-04-04
I just installed ie4linux and its working and all except activex on the site there is a download to use your browser and activex instead oif the program and i cannot get activex to work i followed a few different faqs to enable it and according to ie for linux it should be working i installed ver6 which i believe activex it bundled with i suppose activex wont work on linux no matter how hard i try i think ivew tried everything i know and all i can do now id hope someone who knows coding well to help me out maybe with that gekko thing or someone smart enough might be able to look at the source to see how it works and can figure a way for me to use it. i might be3 dreaming this is possible but i will think you are the nicest person in the world to figure this out for me hehehe and ill love anyone who posts just to try at least. TIA

---

### Post by BeatnikBandit on 2007-04-05
Since it doesn't play under wine is that because I don't have an ogg codec in the fake windows platform?  Maybe it's possible to install an ogg codec for windows through wine? If anyone can help me with this I would appreciate it maybe I should ask in a different area of the forum? If anyone can give me an idea answer any of my questions or plain help me fix it I would love your reply.
Thank you

---

### Post by david_kt on 2007-04-05
> **BeatnikBandit said:**
> Since it doesn't play under wine is that because I don't have an ogg codec in the fake windows platform?  Maybe it's possible to install an ogg codec for windows through wine? If anyone can help me with this I would appreciate it maybe I should ask in a different area of the forum? If anyone can give me an idea answer any of my questions or plain help me fix it I would love your reply.
Thank you

I to run under wine, it is ok although it reported some errors. I could listen to some radio channel.

```
wine installstreamer.exe
```

I am using wine 0.9.34

DK

---

### Post by BeatnikBandit on 2007-04-05
im a newb so im not sutre what version of wine apt-get says its the latest from the repositorys i have it installed fine it opens fine and it seems to connect but i cant get it to play could you play an ogg channel? or mp3? im trying to get ogg going i havent tried mp3 buffers then nothing i get no sound? i envy you that it seamed so easy for you install and go. mine gives no errors it told me to install gecko and it worked and is installed that was my only error and it didnt seam to help i was going to try and use winamp with wine to use the option "use external application" for ogg and mp3/ o really suck lol i want to play the server called "?the weak?" with the ? without the "'s lol can you compile thje sourcecode and see if the old version works still?

---

### Post by david_kt on 2007-04-05
> **BeatnikBandit said:**
>  i was going to try and use winamp with wine to use the option "use external application" for ogg and mp3/ o really suck lol i want to play the server called "?the weak?" with the ? without the "'s lol can you compile thje sourcecode and see if the old version works still?

I dont use any external aplication. It works just fine. But not all channel could play, sometime it even crashed. Maybe it was due to internet connection.  I saw "?the weak?" was the channel with the most user online. But I also could not connect to it. Why don't you try other channel first, to see if the problem with the channel or with your computer?

DK

---

