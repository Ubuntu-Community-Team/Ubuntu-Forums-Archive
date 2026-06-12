---
title: "XVID video is garbled in Gutsy"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by randalotto on 2007-10-24
I'm trying to watch an XVID video on Gutsy, and the video is completely garbled. The image is static. The audio comes through just fine. 

I was under the impression that Gutsy could play XVID without any additional work. I also looked through Synaptic and it appeared that the XVID codec was installed. Any suggestions?

Thanks!

(and i couldn't get the image to post in the thread, so go here: [http://bayimg.com/HahlHaaBl](http://bayimg.com/HahlHaaBl) )

---

### Post by Vansinnesvisan on 2007-10-24
I've had issue with Totem before, as well. I think "Totem-xine" works better.

---

### Post by earobinson on 2007-10-24
this is a bug with nvida, you need to reboot to fix this as far as I know.

---

### Post by randalotto on 2007-10-24
Well that's just odd. I wonder what triggered it?

Restarting was all it took.

I've been using Gutsy since the release, and have restarted 10 times at least, just hadn't played a video until now; something between the last restart and me wanting to watch caused some trouble I guess.

Thanks!
(and it was an nvidia card)

---

### Post by nykobing on 2007-10-25
It isn't just xvid for me, it is anything that is played in any player, like mpg. Happens in both  kaffeine and vlc. Logging  out and back in fixes the problem for a few hours only and then it happens again. Any more permanent fix? 

Thanks.

My screen looks like the screenshot the original poster supplied, but is green instead of yellow.

---

### Post by longinus on 2007-10-25
Same thing here....
I also noticed that the screen flashes (black flashes) when the video thing happens... I have compiz enabled..

I don't know exactly what triggers it, but I've seen it quite a few times already.... a more permanent solution would be nice.

---

### Post by rsambuca on 2007-10-25
I'm thinking it is something to do with the nvidia-glx-new driver.  I never had this happen until that was installed.  I think I will roll back the driver.  It doesn't happen often, but certainly enough to become an annoyance.

---

### Post by jdfreshwater on 2007-10-25
I have also been experiencing this problem since upgrading from gusty beta.  did a clean install from release iso.  I am hoping that this fixes it.  Especially since I'm using it as a mythtv frontend.  Hope that a fix is coming soon.

---

### Post by randalotto on 2007-10-27
Yeah... so this problem keeps happening again and again. I really don't want to have to restart every time I want to watch a video.

---

### Post by longinus on 2007-10-27
> **randalotto said:**
> Yeah... so this problem keeps happening again and again. I really don't want to have to restart every time I want to watch a video.

I don't think you have to restart. Just log-off and then back in... works for me.
It is still very annoying... but a bit faster..

---

### Post by whomever21 on 2007-10-29
Same problem, and you're right. The screen flashes black just before we're all done playing videos for a while. Then I restart X and we're good to go.

Does everyone else here have the nvidia-glx-new driver installed?

---

### Post by smd0665 on 2007-10-29
Well, I just started (as of this morning) getting an error message. Totem tells me, "video code XviD is not handled." These were the same files I was playing yesterday without any problems. I have a nVidia card too, but I'm using the legacy driver. The only thing I can think of that changed is there was a new version of Automatix that became available, but I didn't actually install anything before I got the error. I've tried reinstalling codecs with Automatix, but it doesn't help.

---

### Post by longinus on 2007-10-29
> **smd0665 said:**
> Well, I just started (as of this morning) getting an error message. Totem tells me, "video code XviD is not handled." These were the same files I was playing yesterday without any problems. I have a nVidia card too, but I'm using the legacy driver. The only thing I can think of that changed is there was a new version of Automatix that became available, but I didn't actually install anything before I got the error. I've tried reinstalling codecs with Automatix, but it doesn't help.

I think it's probably a different error. Were you getting the green screen before (once in a while)?
About the missing codec, Totem seems to find the required codecs now, and ask to install them.. Is it not asking for it?

---

### Post by smd0665 on 2007-10-29
Actually, now that I think about it, the picture did cut out a couple of times on Saturday, but the screen was black. And, the error message just says that Xvid is not handled and I might need to install additional plugins.

---

### Post by whomever21 on 2007-11-02
I reinstalled nvidia-glx-new 3 days ago and haven't had this problem since.

---

### Post by Giggity on 2007-12-01
I just reinstalled nvidia-glx-new, and it did not solve the problem.  Does anyone else know how this problem can be fixed?

---

### Post by Gone fishing on 2007-12-01
I use mplayer or Gxine and the nvidia driver enabled from restricted drivers manager and I've not got this problem infact my Xvid and DivX playback is better than in Windows.

---

### Post by whomever21 on 2007-12-02
Think I spoke too soon. My videos still occasionally won't play. I get sound, by the video is just a yellow and purple interlacing mess.

---

### Post by lvleph on 2007-12-02
I have a Radeon Xpress 200 and have the same problem, so I don't think it has to do with nvidia.

---

### Post by rollps on 2007-12-03
well same here, my video screen is most of the time pink though :(

fresh install of gutsy + nvidia + compiz + emerald

it happens with all the video readers (mplayer, vlc, smplayer)

---

### Post by arigram on 2007-12-12
Yep, same here, with all video players.
It started happening a few days ago, so its not due the fresh Gutsy install but some update or setting that did it. It happens on every session too, just not necessary the first video I play.

---

### Post by QwertyManiac on 2007-12-12
Me too, on nvidia-glx-new and a GeForce 7600 GT. An XV issue?

---

### Post by rsambuca on 2007-12-12
Have you guys filed bug reports on launchpad?

---

### Post by QwertyManiac on 2007-12-12
I rolled back to nvidia-glx and it seems to have gone. Will post here if it still garbles up on this driver. Until then, my issue's resolved.

---

### Post by emwine on 2007-12-20
I'm now convinced this is a problem with wine.  I can reproduce it using uTorrent under wine (hit and miss-- certainly I don't see this every time), and I can correct the issue by shutting down all wine processes.  Someone said that killing wineserver won't fix the issue-- I can't confirm or deny that assertion.  But I do believe wine is the trigger because I can now resolve the issue without restarting X or rebooting.  I finish all wine processes, wait up to a minute, and try the video again.

Here are some other links relating to this issue:
[http://bugs.winehq.org/show_bug.cgi?id=10637]("http://bugs.winehq.org/show_bug.cgi?id=10637")

and:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343")

---

### Post by QwertyManiac on 2007-12-30
But I still run Wine after switching back to just nvidia-glx (from nvidia-glx-new) and I haven't experienced it anymore!

---

### Post by ashdezign on 2007-12-30
Happens with all video players
Happens in kde and gnome
Screen flashes Black for a quick second before it happens
Has nothing to do with Wine (at least in my case as I am not running anything under wine)
Once it happens it is only solved by logging out and then logging in, or rebooting.
Started happening about 4 weeks ago (maybe longer?)
Video is garbled, Audio is fine

---

### Post by scott14277 on 2008-02-01
I have the same problem. Green garbled screen after freezing on a pink a screen for a short period of time. I am running an nvidia card with the nvidia-glx-new drivers. I have noticed a way to replicate the problem on a consistent basis. If a recording finishes, all recordings and my live TV stream garbles. on occasion, the live TV component won't even load. The screen will go black and then return to the main menu. I have been able to watch TV or watch recordings before or during recording, and back-to-back recordings seem to work, but once it all stops, the playback is ruined.

---

### Post by huntercj on 2008-02-05
I still have a similar problem, quite probably two. I found on another forum (sorry forgotten which) that the inability to display video (on a GeForce 6200 in my case) is intermittent and once it happens the only way out is to reboot, sometimes more than once. I have now had my Mythbuntu install running Kaffeine for about two months non-stop. I leave the box running and turn off the TV and surround sound receiver. I change channels reasonably frequently across NZ Freeview DVB-S TV and radio channels. I have found that if I exit Kaffeine it is a lottery as to whether I can start it again successfully without a reboot - hence I haven't stopped it for ages. Sometimes it hangs on start and I can kill the process and run again successfully, but if it displays a garbage display, a reboot is the only answer (that I'm aware of).

I'm using Kaffeine because I can't get Myth to display DVB-S. Just get a black screen and no sound. Any assistance would be welcome. Otherwise I will hang on for DVB-T in a few months, but that opens a whole new barrel of eels - NZ Freeview will use H.264 (MPEG4-10) and I don't know if Myth can cope with that. Again any help most welcome. Finally, I'd like to use a dual DVB-T tuner, possibly hybrid with analogue (needs VHF and UHF tuning for NZ), and preferably PCIe for a bit of future proofing and better performance. If anyone can point me in the direction of such cards that would be great. It would be ideal if they are already compatible with Ubuntu/Myth, otherwise I'll watch and wait.

Cheers,

Colin.

---

### Post by stfu on 2008-04-17
I get this error occasionally too, well I used Wine today with some overlay window installer thingie. Now I use compiz and didn't even have to log out, just alt+f2 and metacity --replace and again with compiz --replace, seems to work ok and is a bit faster than logging out or killing X.

---

