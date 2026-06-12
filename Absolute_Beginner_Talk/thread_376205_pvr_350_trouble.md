---
title: "pvr 350 trouble"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by dennis m king on 2007-03-04
so i spent all week in the bacement and i am running a shuttle an35 ultro nforce2 with xp3200 and a fx 5200 ultra vid card and i installed the stuff for ivtv for my pvr 350 card. as far as ivtv is conserned it works. when i do a cat /dev/video0 > /tmp/test_capture.mpg 
and play it back with the mplayer it has good video and sound SO IT WORKS>>>
why will none of the software work at all. i tried tvtime xawtv kdetv and mythtv though myth seems real involved and it gives errors something about connecting with data but that to me is not real important since simple pvr tv programs do not work. 
the frustrating thing is it seems i can adjust things in v4l-conf but i can not figure it out. i want to change to 16 bit high color to try thinga and no info i found.
i have the generic nvidia drivers in also i ge the splash screen on startup. i am a trouper trying things and when this works (i think it does just s software or settings glitch i am thinking) windows is not needed.
i am greatfull for any help i am thinking it is settings or so but i do not know enough about linux as of yet.

  dennis

---

### Post by dennis m king on 2007-03-04
ok i typed in the string for the mplayer and i got video and sound way cool. does it change channels? and why nothing else working? can i record with a video input with mplayer though i am thinking not though i will ask.

---

### Post by dennis m king on 2007-03-04
just trying to keep it active since this is a very active forum.

---

### Post by superm1 on 2007-03-04
Mplayer can't change channels AFAIK.

Xawtv > v4 supports ivtv - but i don't think its even in feisty.

tvtime doesn't support ivtv.

there are some python scripts floating around that will handle channel changing for you if you use mplayer or VLC, but I don't know of one off hand.

As for mythtv, sorry to say that its not a "simple" setup because it can be used so diversely.  If you want some help setting up mythtv, its definitely a very redeeming process.  Once you start doing all your tv stuff with it, you don't really want to go back.
take a look at the wiki for some info about it: [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

That's about the options I can say.

---

### Post by dennis m king on 2007-03-04
i was afraid it would be mythtv. i tried it once and lots of things i did not understand how to get by happened (i only been at this for a week) i am thinking i will be beating myself through this. if they want techies to go to linux someone should make eaiser. if it was as simple as deciding to install it then doing it and bam it works i am betting lots would move from windows. so here it goes.

 thanks

---

### Post by panch0 on 2007-03-05
For a nice interface you can try KPlayer. It should detect your TV device and let you choose a list of channels. Then you can make a playlist with the channels you want and switch between them at will.

---

### Post by dennis m king on 2007-03-05
i will try kplayer but if it will not record from the card i am guessing it will be mythtv. sofar it is the only thing i came across that is a pvr un less others have more info.

---

### Post by dennis m king on 2007-03-10
ok get this i installed mythtv and it will not use the card. i installed a fresh op system and this time the ivtv does not give me the card when looking in dmesg or dmesg |grep initialized i get no pvr 350 in it. in dmesg it says ivtv started buts does not give it a dev/video0.
but i can do a mplayer  /dev/video0 and watch tv. anyguess anyone
also the online install instructions give me ivtv 0.7.0 i think it is correct. it has a 7 in it only and the new one is 0.10.0 i think. do i need a upgrade? 
it sort of works. why is this so hard. if you type it like the ubuntu says not everything works. it is not cut and dry.

---

### Post by superm1 on 2007-03-10
> **dennis m king said:**
> ok get this i installed mythtv and it will not use the card. i installed a fresh op system and this time the ivtv does not give me the card when looking in dmesg or dmesg |grep initialized i get no pvr 350 in it. in dmesg it says ivtv started buts does not give it a dev/video0.
but i can do a mplayer  /dev/video0 and watch tv. anyguess anyone
also the online install instructions give me ivtv 0.7.0 i think it is correct. it has a 7 in it only and the new one is 0.10.0 i think. do i need a upgrade? 
it sort of works. why is this so hard. if you type it like the ubuntu says not everything works. it is not cut and dry.

If you are getting a /dev/video0, then you will be able to use this same device in the mythtv configuration (Be sure to choose PVR-XXX series card in mythtv-setup).  The 0.10.0 is only for the newer kernels, so it is not relevant here.

---

### Post by dennis m king on 2007-03-11
i will go down stairs and see if i can find a place in setup where to choose the card. i can tell you the it scans the channels but when you go to watch tv it will not show anything.
and it does not have a line in dmesg that says it is dev/video0

---

### Post by dennis m king on 2007-03-11
just trying to keep it on top.
also i tried to run 7.04 alp 5 and it gives the warning about not giving it a dev video0 number. it works in XP and i did unplug the board for a bit. as a computer ubuntu is great. trying to do other stuff is intresting.

---

### Post by dennis m king on 2007-03-11
just keeping it on top

---

