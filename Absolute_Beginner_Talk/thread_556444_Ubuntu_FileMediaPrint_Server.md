---
title: "Ubuntu File/Media/Print Server"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Mayur on 2007-09-21
Hello.  Sometime later this year I plan on turning one of my spare boxes into a Ubuntu home server.  I am a college student and I will be using it as a media server mostly but as well as a print server and probably a file server.  The server will need to stream music and videos to laptops that have Vista via a wireless network.  Now my question is that will it be fast enough to stream a movie?  I understand that we can always download the file to the laptop and then later delete it but that takes a little bit longer.

I did some searching here and I read something about samba.  No problem but I read that with samba there are slow transfer rates.

Computer Specs:
AMD Duron 1200+ (892mhz)
496mb ram

Network Specs:
10/100 mbps NIC card connected to 108mbps Wireless G Router

---

### Post by hyper_ch on 2007-09-21
Hmmm, for streaming audio I use gnump3d. I guess you can also stream video with it - although I never tried it.

---

### Post by Mayur on 2007-09-21
So does gnump3d put up like a webpage type thing?  I would want it so that all the files can be played through windows media player.  Hopefully even have all the music files in the windows media library but files located on the server.

---

### Post by hyper_ch on 2007-09-21
yes, you can then access it by a browser and create your playlist that will then be streamed (you can also select files for download)...

but as said, I dunno if it works for videos also - although I think that should not be a problem. The playlist is then handed over to your media player which requests the actual files diretly from the server... so if your media player can play the videos they should be fine...

---

### Post by Mayur on 2007-09-21
Excellent.  So it makes like .m3u playlists or something and then I use that file with windows media palyer?  If it can play with a media player then thats all I need.

Now for the case of a print server and a file server.  File server probably will be rarely used.  A print server is deff needed though.

---

### Post by dfreer on 2007-09-21
gnump3d does put up a webpage, port 8888 by default. there is problems with gnump3d 

When using firefox or IE in windows, if you click on a video file it will attempt to download the whole file, and THEN start playing it. This obviously defeats the purpose of streaming. One option is to install vlc, and then click on the **[Info]** link next to the filename, and then click **[Play]**. This generates a playlist for the video file (.m3u I believe), which you can download and then open with VLC. The video should stream from there. Really, this should be the default behavior (it is with the music files, so why not video as well?)
In linux, with the firefox mplayer plugin, the files just stream correctly.

The music files stream pretty well in both windows and linux, so kudos for that.

For some reason, music files have all spaces properly displayed in file names, so your subfolders and track names are readable. Video files will have an %20 at every space, making folders/filenames hardly readable.

Anyways, IMO gnump3d works great for music, but I wouldn't use it to stream video unless you figure out how to modify it. I haven't found a server that handles video yet, I've been working on creating my own but it's a slow process.

I'm currently using samba on my LAN, with wireless. I've had problems in the past with network speeds slowing to a crawl, but that was due to an issue with my network card and linux, not samba. Videos should stream fine, as long as you have a good connection. Which goes to say you probably won't be able to stream video from across the dorm, but in your dorm room and your neighbors dorm room you should be fine. I'd mount the samba share as a network drive, and then you can access the files as if they were local files, with fast-forward/rewind options and everything.

---

### Post by Mayur on 2007-09-21
Excellent.  I have heard of vlc before and I have used it once or twice.  Ill just play around with everything and see how I like it and what not.  I dont really need it setup right away so no rush.

Also I live in an apartment so distance should not be an issue because only the people that have permission within the LAN will be able to access the files.

---

### Post by hyper_ch on 2007-09-21
vlc is a fantastic player... its FOSS and available for windows and linux... it plays almost any  media format out of the box...

dfeer: I cannot replicate your issue with gnump3d... when I clicke the file it downloads it -> thats good... otherwise I mark it for playlist generation and then it will stream...

What kind of file server do you need exactely? Different logins for different people?

---

### Post by vladk2k on 2007-09-21
> **Mayur said:**
> I did some searching here and I read something about samba.  No problem but I read that with samba there are slow transfer rates.

Computer Specs:
AMD Duron 1200+ (892mhz)
496mb ram

Network Specs:
10/100 mbps NIC card connected to 108mbps Wireless G Router

I've been using ubuntu 6.10 server, 7.04 server and recently 7.04 desktop as home file/media/print server. It works flawless, even on an AMD Duron 900MHz (socket 462, pre xxx+ ratings) with 256 megs of SDRAM and stupid Sis 900 NIC.

Speeds? ~10MB/s from another ubuntu, 8-10MB/s from Windows XP, vista is almost always >10MB/s (that is on a 100mbps full duplex network).

So don't worry about specs, it works fine

---

### Post by LowSky on 2007-09-21
I would love to make a print server.. We only have one good printer in the house and I would be so much easier to store all my media files onto one box that could stream to others...

I think I found my next project!!! time to buy a new case and hard drive and use some spare parts...lol

---

### Post by Mayur on 2007-09-21
> **vladk2k said:**
> I've been using ubuntu 6.10 server, 7.04 server and recently 7.04 desktop as home file/media/print server. It works flawless, even on an AMD Duron 900MHz (socket 462, pre xxx+ ratings) with 256 megs of SDRAM and stupid Sis 900 NIC.

Speeds? ~10MB/s from another ubuntu, 8-10MB/s from Windows XP, vista is almost always >10MB/s (that is on a 100mbps full duplex network).

So don't worry about specs, it works fine

Interesting...Ill just install it and play around with it.  Ill still probably upgrade to a Ahtlon 3200+ because I cant stand the slow cpu speed.  Plus I can then get a mobo that can utilize sata drives :)

---

### Post by dfreer on 2007-09-22
@hyper_ch

hmmm, are you in windows using firefox or IE? basically, it downloads the entire file when you click on the video filename itself (it's not the .m3u file), so for a ~1 GB movie file I end up having to wait for approximately 7 minutes before the movie even begins playing. Whereas in linux, using mplayer plugin it'll start playing pretty much instantly, caching the video in the background.

if you can't replicate it, can you post what you are doing exactly? maybe I am doing something wrong, or using a wrong version of gnump3d (I'm using v2.9final).

---

### Post by hyper_ch on 2007-09-22
dfeer: I have to test that again...

---

