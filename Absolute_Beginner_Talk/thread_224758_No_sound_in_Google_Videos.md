---
title: "No sound in Google Videos"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-28
Hi
After just 4 days, I'm finding that I really like Ubuntu. However, still a few rough edges to smooth out.
Although I can play CDswith sound, when I try to run a Google video using MacroMedia Flash Player, the video plays but without sound.
Can't seem to locate a fix for this problem.
Can anybody help?

Thanks
Paul

---

### Post by franute on 2006-07-28
I've posted it three times today :D
[http://www.ubuntuforums.org/showthread.php?t=219365](http://www.ubuntuforums.org/showthread.php?t=219365)

---

### Post by PaulFXH on 2006-07-28
Hi Franute
Thanks for your reply.
Although I have tried your suggestions (made in your other thread), my sound problem has not been resolved. Indeed, my situation is actually worse!

Here's what happened:
1) I installed alsa-oss and then did the FIREFOX_DSP="aoss" thing as you describe. After this, not only was there no sound in Google videos, but the videos themselves only played for 1-2 seconds before freezing. However, after shutting down the video, I could not restart FireFox without rebooting my machine.

2) Then I installed libflash-mozplugin as is mentioned in the Macromedia troubleshooting page.
After this, there was still no sound and even the video did not play at all. However, on the positive side, Firefox could be shut down and restarted without rebooting.

I though about uninstalling the FlashPlayer but cannot find it in Synaptic.

I do hope you or somebody else may be able to offer some suggestions as to where to go next.

Thanks 
Paul

---

### Post by franute on 2006-07-29
Flash gives lots of problems in linux, it's a shame that solutions like this works only for some people :( I did the same thing in another laptop yesterday and it works fine, but we cannot think it will work allways in every computer. With pentium M seems to be no problem, but for example in amd64 there are lots of them.

I found that FIREFOX_DSP="esd" or FIREFOX_DSP="auto" must be also ok, but I don't know...

---

### Post by TomParker on 2006-07-29
Well I like how ubuntu refuses to get anything YOU want to work (too much to list) then next time it works flawlessy and stays that way lol

examples:
- Webcam
- Media Controls on keyboard
- Sound on Youtube Videos

:)

---

### Post by franute on 2006-07-29
Problems with flash are not really ubuntu people problems, if flash was open source, there would be no problem, but problems with shutting down on laptops for example are not fixed yet even in Edgy beta. I think maybe they are not thinking too much in users now, I wish it will change soon :(

---

### Post by PaulFXH on 2006-07-29
Hi Franute
I still haven't made any progress with the FlashPlayer but I noticed something interesting that you might want to comment on.

In /etc/firefox I have the firefoxrc file which contains the line FIREFOX_DSP="aoss" as you had recommended.

However, in /etc/mozilla-firefox there is another file called mozilla-firefoxrc which contains the line FIREFOX_DSP="auto".
The "auto" thing is stated as being "buggy" in the comments contained in the firefoxrc file.

Does you think that this has any significance to my problem?

Thanks
Paul

---

### Post by franute on 2006-07-29
I don't know if that's the problem, change it with "aoss" and try :D do you have alsa selected as the main output for gnome? In system/preferences or in system/administration, but maybe it's hidden, so edit the menus to make it visible and try, sorry I can't tell you any more idea :neutral:

---

### Post by PaulFXH on 2006-07-30
Hi Franute

Well, I finally got the FlashPlayer working.
What I did was to re-install Ubuntu 6.06 so that I was starting from a clean sheet.
Then, besides downloading the MacroMedia FlashPlayer, I installed Alsa Oss and then followed the reasonably simple instructions here:

[https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

After this, FlashPlayer worked perfectly.

Interestingly, in /etc/firefox the file firefoxrc file now contains the line FIREFOX_DSP="none" rather than "aoss" as you had suggested.

In addition, this time there is no confusing /etc/mozilla-firefox folder which had confused me before.

Thanks for your help and suggestions
Paul

---

### Post by durableapostle on 2006-07-30
Hace you tried easy ubuntu?

[http://easyubuntu.freecontrib.org/get.html]("http:http://easyubuntu.freecontrib.org/get.html//")

I found it the easiest way to handle multimedia issues.

---

### Post by PaulFXH on 2006-07-30
Hi
Well, I don't actually HAVE any MultiMedia problems right now after I got the FlashPlayer to work.

Also, having struggled for the past week to get some limited understanding of Ubuntu 6.06, I think it would be unwise to take a step back and content myself with what sounds like a toned-down version of the real thing.

But, I've never used Easy Ubuntu. What advantages does it have, in your opinion, over Dapper Drake?

Paul

---

### Post by franute on 2006-07-30
Basically, Easy Ubuntu is a program which downloads and installs codecs, plugins... But really, it only uses apt-get the same way you can use it selecting the packages with synaptic. Easy Ubuntu is a good way to do it faster, but it doesn't really do anything you couldn't do with apt-get and a good sources.list :D

---

### Post by durableapostle on 2006-07-30
> **PaulFXH said:**
> 

...I think it would be unwise to take a step back and content myself with what sounds like a toned-down version of the real thing.

It's not a step back....  It may be a more simple method than doing a zillion apt-get's, but--it no step back... and it IS "the real thing."  It simply installs everything that you need to see and hear audio/video, flash, java, fonts, etc.

> **PaulFXH said:**
> What advantages does it have, in your opinion, over Dapper Drake?

It's not an alternative to Dapper--it's a program (that works IN Dapper) that installs all of the plugins and codecs that will more than likely fix your problem.

Maybe it's not a complex "hack into the pentagon" level operation--but it's a fix nonetheless.  Install it, you'll see your problems end.
[http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html")

---

### Post by Rich3077 on 2006-07-31
I get the same problem at times. Google video will work great for days on end and then the sound will stop working, it happened to me tonight. I am sure there is a better answer than mine as I am a newb but when this happens what I do is open atomatix and reinstall the codecs, and on completion sound works again. I dont think that this is a random event in my case as I am always screwing around with the system in some way. Yesterday I installed Compiz and I think thats what messed up the sound in Google video.

---

### Post by klytu on 2006-07-31
> **Rich3077 said:**
> I get the same problem at times. Google video will work great for days on end and then the sound will stop working, it happened to me tonight...

This happens to me from time to time as well. Also (this may or may not be a related issue) mplayer will play embedded video flawlessly for days and then it will stop doing so. In my case these anomalies are not connected to updating anything or changing any of the system configuration. As far as I can tell, I can always restore fully functionality by rebooting! This means that the root cause is probably some process running in the background that under certain conditions either doesn't terminate as it should and/or prevents accessing the sound daemon the way Google Video trys to access it. 

One of these days when I understand more, I'll troubleshoot this by killing and restarting background processes one by one until I isolate the problem one. It's difficult to do because I haven't been able to consistently reproduce the behaviour.

---

### Post by klytu on 2006-08-01
> **klytu said:**
> This happens to me from time to time as well. Also (this may or may not be a related issue) mplayer will play embedded video flawlessly for days and then it will stop doing so. In my case these anomalies are not connected to updating anything or changing any of the system configuration. As far as I can tell, I can always restore fully functionality by rebooting! This means that the root cause is probably some process running in the background that under certain conditions either doesn't terminate as it should and/or prevents accessing the sound daemon the way Google Video trys to access it. 

One of these days when I understand more, I'll troubleshoot this by killing and restarting background processes one by one until I isolate the problem one. It's difficult to do because I haven't been able to consistently reproduce the behaviour.

OK. I stumbled upon a situation that consistently kills the sound in Google Video on my system. I use the gnome desktop environment that installs by default on a fresh Dapper install. I also run a couple of KDE apps and games from time to time within that environment. Yesterday, after solving a layout in KMahjonng, I happened to try to watch a Google video and got no sound! Earlier in the day the sound had worked in Google video so at that time I did:

```
ps -ef > working_sound
```

to get a snapshot of all the processes that were running when the sound worked in Google video. When the sound stopped working I did:

```
ps -ef > no-working_sound
```

I compared the two files and noticed that when Google video sound wasn't working these extra processes were running:

/usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -l 3 -f
dcopserver [kdeinit] --nosid --suicide
/usr/lib/gamin/gam_server

I tried:

```
killall /usr/bin/artsd
```

then loaded a Google video and sound played normally again! I reproduced the situation three times in a row (now I'm tired of playing KMahjonng :) ) and I was able to correct it the same way each time.


I did a little bit of research and found out that artsd is the sound server used in KDE. Evidently under some circumstances artsd kills the sound in Google video when it runs in the background in a gnome environment. There are probably other similar situations that do the same thing. It may take a lot of time and patience to find more of them.

---

### Post by PaulFXH on 2006-08-01
Hi klytu
After my euphoria of a few days ago on finally getting the sound to work in the FlashPlayer, I now find as you do that the sound disappears every now and again.
In my case at least, I can get the sound back in seconds just by entering the following two lines in terminal:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd [/PHP]
```

The Ubuntu Desktop Guide refers to this code as setting the ESD environment (whatever that is).
Interestingly, I don't have any artsd file/folder in the location you mentioned so it appears it's not just one thing that can cause this annoying sound loss.

At least, there's a couple of simple quick-fixes.
Paul

---

