---
title: "No Sound while downloading Torrent"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-10-14
Hi Guys, 

Ubuntu is clearly the best OS i have ever seen. I came across a bug that i wanted to discuss with you guys and get your feedback on the same. Everytime, i while i am downloading a torrent using the inbuilt ubuntu bittorrent client, i notice that the sound soon stops. For example, if i am using Rhythm box, i see that the song is being played but i hear nothing. Even if i increase the volume to full, i hear nothing. Eventually, when i log out and log in again, the sound comes back.  But again if a torrent is being downloaded i run into similar problems. Also skype does not work, I mean i cannot make skype calls, since it says some audio device error.

Have any one of you experienced something like this? Any advice, suggestions and feedback is most welcome. 

Thanks a lot in advance.

Cheers,
Harry

---

### Post by mindtrick on 2007-10-14
You can use other torrent clients 
Deluge is one of the best torrent clients I've ever seen
[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by 001100 on 2007-10-14
personally I don't like the default bittorrent clent, for thoes same reasons I would try Azureus [http://azureus.com/]("http://azureus.com/")

---

### Post by hyper_ch on 2007-10-14
rTorrent ist really nice also...

---

### Post by Beggar on 2007-10-14
rather then continue to add useless information about which torrent client is superior to the default version (everyone knows deluge is the best anyways).

When you have this problem again, run 

```

lsof | grep /dev/dsp
lsof | grep /dev/snd/

```

It might take a second, but it will tell you what is using your sound device, it will give you output something along the lines of

```

firefox-b 28632     darren  mem       CHR      116,4               14340 /dev/snd/pcmC0D0p
firefox-b 28632     darren   47u      CHR      116,4               14340 /dev/snd/pcmC0D0p

```

This does two things for you, it tells you what process is using your sound driver (firefox-bin in my case) and it gives you a pid for that process.

So if firefox grabs my sound device and doesnt give it up, I can run those commands and then 

```
 sudo kill -9 28632
```

Watch out though, this immediatly terminates that process, so make sure you dont have anything unsaved when you do this. Now your sound should be in working order again. 

Thats the short term fix, long  term depends on what process it is you need to kill, let us know and maybe someone here knows your answer :)

---

### Post by cool_penguin on 2007-10-14
Well guys. I  thank you all for you help. I am running Deluge and is by far the best torrent client i have even seen till date. With Deluge, i don't seem to be running in to sound issues. But as Beggar rightly said, we need to find a long term fix to this bug. 

mindtrick, thanks a million for recommending such a wonderful torrent client.

keep up the good work guys.

Cheers,
Harry

---

### Post by hyper_ch on 2007-10-14
well, deluge has one huge problem: you can't operate it from the comand line...

---

### Post by Beggar on 2007-10-14
Why cant you run it from the command line hyper? Apart from it displaying debuging type information, I have no problems...

---

### Post by hyper_ch on 2007-10-14
well, I rather meant running in the cli :)

You know, starting up SCREEN and then loading different programs into the terminal multiplexer... so that I can connect from everywhere to it through ssh ;)

---

### Post by Beggar on 2007-10-15
Dont see that as a problem, from their site,

"Deluge was created because of the lack of a good, native, GTK based torrent solution for Linux"

They arent looking to make a CLI based torrent program, your talking about a very different program. Besides, the OP is looking to get sound working, unless he really likes messing with people (and who here hasnt ssh'd into there computer and messed with sound levels just to mess with someone?), I dont think that he cares if it has a cli. 

Please stop trying to start a fight, over a problem which has been resolved.

---

### Post by hyper_ch on 2007-10-15
well, since rtorrent is cli only there's only a very slim chance that it would interfere with sound ;) so I did give an appropriate solution.
Furthermore the a cli client offers options that he might not have thought about before ;)

---

