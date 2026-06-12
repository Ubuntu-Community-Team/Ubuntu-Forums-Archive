---
title: "[SOLVED] Live Radio - web steaming content"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-11-22
I have Dapper Drake (6.06 LTS) and Firefox version (1.5.0.13pre) which came with Dapper Drake and updated a bit.

So far I can do everything with my Linux install that I could with any version of Window$ EXCEPT listen to streaming radio from a particular web site. That web site is: [http://www.kfi640.com/main.html](http://www.kfi640.com/main.html)

I have tried some plug-ins for Firefox, namely "Mplayer" and "streamtuner", neither work. They work with some sites, but not for the streaming content from this particular site. It is really Window$ Media Player centric.

I really would like to listen to this site on the weekends while working with my computer. Just go there and click the "listen live link" see if it works for you and tell me how I can get that streaming content, what plugin to down load, how and where to download it. I'm sure this is possible, it just takes knowledge I don't have.

Thanks in advanced. I'm sure we will get to the bottom of this situation and find a solution.

---

### Post by Dr Small on 2007-11-22
> **mister_lister said:**
> I have Dapper Drake (6.06 LTS) and Firefox version (1.5.0.13pre) which came with Dapper Drake and updated a bit.

So far I can do everything with my Linux install that I could with any version of Window$ EXCEPT listen to streaming radio from a particular web site. That web site is: [http://www.kfi640.com/main.html](http://www.kfi640.com/main.html)

I have tried some plug-ins for Firefox, namely "Mplayer" and "streamtuner", neither work. They work with some sites, but not for the streaming content from this particular site. It is really Window$ Media Player centric.

I really would like to listen to this site on the weekends while working with my computer. Just go there and click the "listen live link" see if it works for you and tell me how I can get that streaming content, what plugin to down load, how and where to download it. I'm sure this is possible, it just takes knowledge I don't have.

Thanks in advanced. I'm sure we will get to the bottom of this situation and find a solution.
Greetings,
Have you tried playing the streaming audio with VLC Player ?
VLC player can be downloaded via the repositories.

Dr Small

---

### Post by mister_lister on 2007-11-22
Are you talking about the Synaptic installer, I have access to all repositories, from previous installs I have done. Should I just do a search for "vlc" and install all dependencies?

---

### Post by Dr Small on 2007-11-22
Yes, or you can install vlc from the terminal using apt-get:
```
sudo apt-get install vlc
```

---

### Post by mister_lister on 2007-11-22
I used Synaptic. Installed the "VLC" plug in for mozilla and all it's dependencies. Didn't ask me to restart, so I started Firefox and went to that page, click on the link for "listen live" and a blank page loaded. After a few minutes it refreshed and had a link for the "player", clicked on that link and the page went blank. Over and over again, Same results. I guess that player is not being deteted.

By the way I tried the command prompt version of "apt" after synaptic and it said I had the newest version.

Any further thoughts by you guys?

---

### Post by Dr Small on 2007-11-22
Try going into VLC Player, click File > Open Network Stream > [Select HTTP/HTTPS/FTP/MMS] and paste the url of the streaming file in the URL. That should play the stream.

---

### Post by mister_lister on 2007-11-22
Did you try going to this "listen live" page. It is implemented with a java script and I was unable to find the actual source location of the streaming content. I searched through the source of the page, lots of code, and there is no definitive link to the source, the player must load and actuate a plugin, perhaps only a M$ Media Player.

I did insert the link to the player and VLC went through the code looking for a source but it was taking forever and never found anything to play.

Are you able to listen to live radio from this page? (refer to my earlier post for the link)?

---

### Post by dboyd13 on 2007-11-22
Point your player to the following URL:

mms://a465.l1977112464.c19771.g.lm.akamaistream.net/D/465/19771/v0001/reflector:12464?auth=caEa1b0cMcdbUd1aQdabPb9cSaDaAa6cgba-bhrIFM-4q-OMZX8_4orGDno4CBokwtAp&aifp=1234&CPROG=SIMULCAST&MARKET=LOSANGELES-CA&MNM=1&NG_FORMAT=talk&NG_ID=kfi640am&OR_NEWSFORMAT=&RVN_TZ=-8&SERVER_NAME=wwwkfi640com&SITE_ID=616&STATION_ID=KFI-AM

Seemed to work fine for me.

---

### Post by sstusick on 2007-11-22
I really hate sites that are as ignorant to only have Windows Media player supported players. Why can't they use something universal?

---

### Post by dboyd13 on 2007-11-22
Yeah I totally agree. Mister_lister, keep in mind that you can play this format on linux players... you just need to load the right codecs. I remember that I did this some time ago with mplayer... but I'm not at my machine to check what codecs I loaded.

---

### Post by mister_lister on 2007-11-22
OK. I tried that and still no luck. I copied the link you posted and pasted it into VLC>file>open network stream> MMS. NO SUCH LUCK.

I guess it just is not going to happen with this version of linux and firefox. Thanks for the input.

I will switch out to my Windows HD when I want to listen to streaming radio.

---

### Post by dboyd13 on 2007-11-22
Are you behind a proxy server at all? If so you need to specify your proxy server as a parameter when opening vlc:

e.g. vlc --http-proxy=myusername:mypassword@SERVERNAME:8080

Also, consider using MPLAYER instead, I had luck with M$ streams with that.

---

### Post by thiebaude on 2007-11-22
It probably is a Flash issue because the link you gave to the website uses flashplayer.

---

### Post by mister_lister on 2007-11-23
The flash ads on that player come up fine. 

As I wrote earlier, I tried "mplayer", no luck.

I am not behind a proxy server.

I tried turning off esd and just using the alsa sound, still no luck.

Could it possibly be the fact I have an old version of Firefox?

I agree with one of the previous posters, you would think a site would have something more universal, just a simple link  to a file instead of the bulky front end.

Sent a message to the webmaster of the site, trying to get some information from him\her and they have not replied, it has been weeks now.

I'm tried that link that was posted earlier, in "stream tuner" and it didn't work either, even after pasting in that link.

---

### Post by mister_lister on 2007-11-29
I found a partial solve. The main radio program I wanted to listen to on that radio station is, "Tech Guy with Leo Laporte". I found a link to a podcast\netcast of the show that is updated weekly, so I can now listen to the show, although still not able to with the live stream.

Thanks for all your suggestions. I'm gonna mark this thread as solved.

---

### Post by Steve R. on 2008-06-08
I am having the same problem trying to Listen to KFI-640. I have played around with trying to solve it and I have not gotten anywhere. So I wouldn't call this issue solved.

Anyway, we are using an **AMD-64** chip.  In searching the specifications, I did not see any reference to the streaming audio working on an **AMD-64** Platform.

Also I did find a link to KFI-640's ["Classic Player"]("http://www.kfi640.com/cc-common/streaming_new/index.html?refreshed=yes") that does work.

---

### Post by iosdaemon on 2008-07-03
This is a late post.... But just in case someone else with the problem finds this thread.

KFI now seems to require Windows Media Play 9, which of course minimally requires XP with service pack 2.  Not sure what the current Linux support for this is.

---

