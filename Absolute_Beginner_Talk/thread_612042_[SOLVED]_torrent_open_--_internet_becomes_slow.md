---
title: "[SOLVED] torrent open -- internet becomes slow"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-11-13
When ever I have a torrent downloading, my internet is slower than a crawl. Even if I have just one torrent downloading at about 35 Kbps, it takes the browser 7-8 minutes  to open Google's webpage. So basically my internet surfing comes to a standstill while downloading torrents. That's the reason I have to keep torrents alive only when I am not around the computer.

Has anyone else seen this? I use Deluge btw.

Is there a fix?

---

### Post by ddrichardson on 2007-11-13
What is your upload speed set to, I think by default its maximum available? Restrict it to approx 25% of your download speed. You need to be able to send packets as well as receive when surfing.

---

### Post by Inxsible on 2007-11-13
> **ddrichardson said:**
> What is your upload speed set to, I think by default its maximum available? Restrict it to approx 25% of your download speed. You need to be able to send packets as well as receive when surfing.
I know...but thats the problem. My upload speed is restricted to 35Kbps.

Download speed is set to unlimited.

---

### Post by ddrichardson on 2007-11-13
35 kbps is a fairly high upload rate (depending on your connection of course) most ISP connections have an upload rate a quarter of the download rate.

---

### Post by Inxsible on 2007-11-13
> **ddrichardson said:**
> 35 kbps is a fairly high upload rate (depending on your connection of course) most ISP connections have an upload rate a quarter of the download rate.
Well, I have cable internet with 6 Mbps download speed and 384Kbps upload speed. (as listed by my ISP - of course)

I shall try and lower the upload speed and check it out.

---

### Post by ddrichardson on 2007-11-13
Torrents are a bit of an oddity. I have 1Mbs down and 128Kps up, I have to set the torrents to 111 down and 26 up to get stable download speeds and any kind of response in Firefox.

---

### Post by Inxsible on 2007-11-13
> **ddrichardson said:**
> Torrents are a bit of an oddity. I have 1Mbs down and 128Kps up, I have to set the torrents to 111 down and 26 up to get stable download speeds and any kind of response in Firefox.

111 -- that would suck for me, because I have been able to download stuff at 140 -150 kbps. Just last night, I downloaded @ 450 kbps average. I saw speeds as high as 538 kbps. I wouldn't want to restrict my download speed. Maybe I will ocntinue using torrents only when I am not home or sleeping ;)

---

### Post by ddrichardson on 2007-11-13
Rub it in - anything higher than 1 Mb is still a luxury in rural areas in the UK. Unfortunately air bases are always in the middle of nowhere.

---

### Post by Inxsible on 2007-11-14
> **ddrichardson said:**
> Rub it in - anything higher than 1 Mb is still a luxury in rural areas in the UK. Unfortunately air bases are always in the middle of nowhere.Whoops!! Sorry, I didn't mean to rub it in :D.....or did I ? ;)

---

### Post by carlosjuero on 2007-11-14
There is always the option that the ISP is throttling the connection while Bittorrent is running as well; they could have it set up to automatically reduce bandwidth speeds to users who are detected using Bittorrent (without blocking them outright, or doing what Comcast does and sending bad packets).

---

### Post by ddrichardson on 2007-11-14
If they're throttling the connection they don't usually throttle port 80 where http requests come through.

---

### Post by carlosjuero on 2007-11-14
> **ddrichardson said:**
> If they're throttling the connection they don't usually throttle port 80 where http requests come through.
True, usually. Hmm, maybe the # of connections? I don't know - I rarely see a slow down using torrents and browsing at the same time, even with huge files like game updates.

---

### Post by Inxsible on 2007-11-14
I dont remember if I use a non-standard port on Deluge. Lemme check. If its a non-standard port, the ISP throttling the connection should not be a problem right ?

---

### Post by doomster on 2007-11-14
> **Inxsible said:**
> When ever I have a torrent downloading, my internet is slower than a crawl. Even if I have just one torrent downloading at about 35 Kbps, it takes the browser 7-8 minutes  to open Google's webpage. So basically my internet surfing comes to a standstill while downloading torrents. That's the reason I have to keep torrents alive only when I am not around the computer.

Has anyone else seen this? I use Deluge btw.

Is there a fix?

The way torrents work, force the system to use many different connections. most ISP , have a limit of connections per user. even if you have set highest upload limit to 10, if these 10kbps are consumed, by many more than 80-100 different  ip's(connections) then the connection itself, lags
.Try to set maximum connections in deluge preferences to maximum 80-100 to see if this fixes your
problem :D

---

### Post by Inxsible on 2007-11-14
Snap !!!

I am using the standard ports 6881-6889. That could be an issue.

---

### Post by Inxsible on 2007-11-14
> **doomster said:**
> The way torrents work, force the system to use many different connections. most ISP , have a limit of connections per user. even if you have set highest upload limit to 10, if these 10kbps are consumed, by many more than 80-100 different  ip's(connections) then the connection itself, lags
.Try to set maximum connections in deluge preferences to maximum 80-100 to see if this fixes your
problem :DThat makes sense too. Let me try that.

EDIT: My Max Connections are set to 200. Now if i reduce these, it will also reduce my download speed correct? assuming of course that the IP which would have given me 300kbps could be the 101st connection (which it will never connect to if i reduce max connections to 100)

---

### Post by Whiffle on 2007-11-14
You might check into your router as well, some routers choke up with bittorrent without a few modifications.

---

### Post by Inxsible on 2007-11-14
Also I cannot for the life of me, find a way to selectively download something in Deluge.

Does Deluge support this yet? I had stopped using deluge and started using qBittorrent for this very reason in Feisty. I read somewhere that it started this feature, but I can't find it

---

### Post by doomster on 2007-11-14
> **Inxsible said:**
> That makes sense too. Let me try that.

EDIT: My Max Connections are set to 200. Now if i reduce these, it will also reduce my download speed correct? assuming of course that the IP which would have given me 300kbps could be the 101st connection (which it will never connect to if i reduce max connections to 100)

heh , the fast connection might also be the 201 th , the one thats has been already denied :D
just limit it to 100 m8, and dont worry..  after all  its a broadband connection, not a dial up... you pay the same if the downoad ends in 12secs or in 15 secs:D .

---

### Post by Inxsible on 2007-11-14
> **Whiffle said:**
> You might check into your router as well, some routers choke up with bittorrent without a few modifications. I use random ports in Deluge now (just changed the setting in fact).

Do you mean that I have to forward the port that Deluge uses? If yes, how would I do that while using random ports?

---

### Post by Inxsible on 2007-11-14
> **doomster said:**
> heh , the fast connection might also be the 201 th , the one thats has been already denied :D
just limit it to 100 m8, and dont worry..  after all  its a broadband connection, not a dial up... you pay the same if the downoad ends in 12secs or in 15 secs:D .True :D. I should stop being greedy  ;)

---

### Post by doomster on 2007-11-14
> **Inxsible said:**
> I use random ports in Deluge now (just changed the setting in fact).

Do you mean that I have to forward the port that Deluge uses? If yes, how would I do that while using random ports?

to do this using random ports you should  check if your router supports the "Range of Ports" forwarding, to fw multiple ports  :)

---

### Post by Inxsible on 2007-11-14
I set it to 100 max connections and guess what !!

I can surf the internet...without noticeable lag :D

Thanks a bunch everyone !!!

---

### Post by Inxsible on 2007-11-14
> **doomster said:**
> to do this using random ports you should  check if your router supports the "Range of Ports" forwarding, to fw multiple ports  :) But the random is only from a given range ?

In any case, I don't think my router is blocking any bittorrent data since I normally get 150-200kbps download speed. and even if it is...I couldnt care less since the speed is god enough for me :D

---

### Post by doomster on 2007-11-14
> **Inxsible said:**
> I set it to 100 max connections and guess what !!

I can surf the internet...without noticeable lag :D

Thanks a bunch everyone !!!

 i m glad it worked:)  i used to have the same problem and HAD to search for the solution alone:P:P

mark it as solved plz:)

---

### Post by Inxsible on 2007-11-14
> **doomster said:**
> i m glad it worked:)  i used to have the same problem and HAD to search for the solution alone:P:P

mark it as solved plz:)I did already !  BTW, Do you know how to selectively download in Deluge tho?

---

### Post by doomster on 2007-11-14
> **Inxsible said:**
> I did already !  BTW, Do you know how to selectively download in Deluge tho?

nope. to be honnest i am trying hard , to find a descent torrent client, with selective dl, torrent search engine, and build in bandwidth limiter/connection limiter. if you find one that has all of these, and a descent GUI, let me know:D

---

### Post by Inxsible on 2007-11-14
> **doomster said:**
> nope. to be honnest i am trying hard , to find a descent torrent client, with selective dl, torrent search engine, and build in bandwidth limiter/connection limiter. if you find one that has all of these, and a descent GUI, let me know:D

[qBittorrent]("http://qbittorrent.sourceforge.net/") comes quite close, but its GUI is too conflicting with the Human theme of Gnome. Probably because its been developed in QT

---

### Post by atomkarinca on 2007-11-14
> **doomster said:**
> nope. to be honnest i am trying hard , to find a descent torrent client, with selective dl, torrent search engine, and build in bandwidth limiter/connection limiter. if you find one that has all of these, and a descent GUI, let me know:D

ktorrent's got all of it.

---

### Post by Anthony M on 2007-11-14
> **doomster said:**
> nope. to be honnest i am trying hard , to find a descent torrent client, with selective dl, torrent search engine, and build in bandwidth limiter/connection limiter. if you find one that has all of these, and a descent GUI, let me know:D

Thats easy, just activate the Deluge plugin 'Torrent Files'. Once you have started dl'ing a torrent you can then choose the 'Files' tab and pick and choose which files you want. 

Edit: There is also a Deluge plugin called 'Torrent Search'. Guess what that does....

---

### Post by Inxsible on 2007-11-14
> **Anthony M said:**
> Thats easy, just activate the Deluge plugin 'Torrent Files'. Once you have started dl'ing a torrent you can then choose the 'Files' tab and pick and choose which files you want. 

Edit: There is also a Deluge plugin called 'Torrent Search'. Guess what that does....
How do you activate those plugins ?

---

### Post by barney385 on 2007-11-14
[http://deluge-torrent.org](http://deluge-torrent.org)

All official plugins are included in the packages/installers.

I'd check their site for new developements if you have an older version. They should have been included.

---

### Post by Inxsible on 2007-11-14
> **barney385 said:**
> [http://deluge-torrent.org](http://deluge-torrent.org)

All official plugins are included in the packages/installers.

I'd check their site for new developements if you have an older version. They should have been included.I have the version from the repos (0.5.4) but the latest is 0.5.6 will install the new one once my download finishes :)

wonder why Ubuntu doesn't have the latest

---

### Post by barney385 on 2007-11-14
> **Inxsible said:**
> wonder why Ubuntu doesn't have the latest
:confused:

Might need to be updated also. Please let us know how everything works out.

:)

---

### Post by Inxsible on 2007-11-14
> **barney385 said:**
> :confused:

Might need to be updated also. Please let us know how everything works out.

:)
I am currently downloading 5 seasons of Family guy ~ about 13 GB. It will be a while before I try out the new deluge version. Currently its done about 18 % and shows the ETA to be 1d and 1h.

Hopefully it will be done sooner. :)

---

### Post by doomster on 2007-11-15
> **atomkarinca said:**
> ktorrent's got all of it.

is there a way for us not using the Kubuntu, to install ktorrent without the whole Kapps package?

---

### Post by Inxsible on 2007-11-15
> **doomster said:**
> is there a way for us not using the Kubuntu, to install ktorrent without the whole Kapps package?any kde app that you install WILL bring with it the kde packages required for it to start up. having said that, i don't think its a huge issue.

I use Amarok, K3B and Kopete  all the time. 

I will try out KTorrent too. The benefit being that the updates will be automatically handled. If I install Deluge's deb file, I will have to keep track of the updates. And selective download is something that I really require. So kTorrent might be better in that regard, at least until Ubuntu's repos are updated with the latest Deluge which supports selective download.

---

