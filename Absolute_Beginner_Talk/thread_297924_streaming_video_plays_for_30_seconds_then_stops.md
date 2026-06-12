---
title: "streaming video plays for 30 seconds then stops"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by PrairieShaman on 2006-11-11
hey ive been trying to get my video stuff working on ubuntu for a while now and the progress has been slow. Ive run automatix2 a few times now and it doesnt seem to do anything new. 

I installed all my packages in synaptic that I thought I needed. 

didnt work

I downloaded and installed automatix2 updated my source list and ran automatix. 

didnt work

SOME videos play such as the ones hosted on youtube. The ones that DO play only play for 20-60 seconds before the sound cuts out and the video goes all choppy. Im thinking it has something to do with cache/buffering but I really don't know.. 

Im running edgy, fully updated. Firefox 2.0 browser..

any suggestions?](*,)

---

### Post by PrairieShaman on 2006-11-12
bump.

---

### Post by Sef on 2006-11-12
Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by junglepeanut on 2006-11-12
It sounds like they actually play so I am just guessing here but is your internet connection up to steam? I have a huge connection at the university but still when everyone comes online occasionally even a 14kb radio stream cuts in and out.

Sorry if this doesn't help.

---

### Post by PrairieShaman on 2006-11-12
Ive read the restricted formats page about a thousand times, unless I dont understand it or something?

My connection is plenty fast enough to play these videos. I dual boot with xp and they play just fine in firefox while running winblows.

---

### Post by junglepeanut on 2006-11-14
Have you tried doing it without Automatix(1or2)?  As I have heard some complaints about it.

I have used version 1 along time ago and it did not work for me, but following the wiki has always worked...

Hope you can resolve your issue.

---

### Post by sunexplodes on 2006-11-14
Quick question: You mentioned YouTube. Are these problems occurring only within flash-based media files?

If so, this is a documented problem. Automatix installs Flash 7, which has some serious problems with streaming video. Search these forums for Flash 9 upgrade instructions. It's a really easy upgrade, and it might solve your issue.

---

### Post by sunexplodes on 2006-11-14
nevermind, here's [the link]("http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin"). Grab that file, should be a tar with a single file included. 

Navigate to your firefox plugins folder (likely /usr/bin/firefox/plugins or some variation thereof) and replace the file there with the one in the zip. restart firefox. problem SHOULD be solved.

---

### Post by sappman2 on 2006-11-22
Thanks sunexplodes. That fixed my flash issue. now to work on the m-player and totem plugins not working with *.wmv streams and real player not working with *.ram streams. (sound, but no videa.)

---

### Post by PrairieShaman on 2006-11-23
Hey there. Thank you for the information and link to the updated flash files. I will give this a try.

The problem has continued, I installed the packages via terminal like recommended in the restricted formats thread, and the problem was not solved. I installed automatix 2 which also did not work to solve this problem. It DOES appear to be a flash based problem now that I think about it. I will install this update and post back here later in the day with the results. Thanks for helping out this nooblet!

---

### Post by sunexplodes on 2006-11-24
No problem, good luck. Let us know if it works.

---

### Post by PrairieShaman on 2006-11-24
From what I can tell, this has solved my problem!

Thank you very much Sunexplodes! :)  Streaming videos seem to play properly now, except for the odd "skip" which is not nearly as bad as it stopping completely or losing audio! :D  Awesome! All of my ubuntu/linux problems have been easily solved by asking questions and browsing these forums! Thanks Ubuntu for having all of this so easily available!

---

### Post by PrairieShaman on 2006-11-24
yes this has definitely solved the problem. thanks again.

I just watched 3 hours of straight streaming video with no problem! 8) :KS :KS :KS :KS :KS

---

