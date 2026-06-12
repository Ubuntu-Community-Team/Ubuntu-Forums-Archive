---
title: "youtube in ubuntu crashes"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-06
ubuntu crashes when watching youtube video. I didn't even had too many firefox tabs open. Just that Youtube video page was left so that it could finish off the buffer and so that i could watch the video continuously. but after it finished playing ubuntu stopped working. i tried pressing all the keys but it didn't respond. 

i rebooted and again went to youtube and the video just started playing and again ubuntu crashed.

i had been using ubuntu + youtube before but it never used to crash. two days back i updated from the bare bones minimum of ubuntu 6.10 edgy with all(180 updates)  from ubuntu repositories. 

now youtube makes the whole system crash. also this doesn't happen in windows. please suggest a solution.

sys config

p 4, 500 mhz ram. 20gb ubuntu + 60 gb winxp

Note : I installed flash from adobe site and not from ubuntu repositories.

---

### Post by daverich on 2007-09-06
there is no solution it's a bug with the flash player.

Kind regards

Dave Rich

---

### Post by arai on 2007-09-06
is there any other version of flash in the repositories that doesn't crash ubuntu ?

---

### Post by stchman on 2007-09-06
> **arai said:**
> ubuntu crashes when watching youtube video. I didn't even had too many firefox tabs open. Just that Youtube video page was left so that it could finish off the buffer and so that i could watch the video continuously. but after it finished playing ubuntu stopped working. i tried pressing all the keys but it didn't respond. 

i rebooted and again went to youtube and the video just started playing and again ubuntu crashed.

i had been using ubuntu + youtube before but it never used to crash. two days back i updated from the bare bones minimum of ubuntu 6.10 edgy with all(180 updates)  from ubuntu repositories. 

now youtube makes the whole system crash. also this doesn't happen in windows. please suggest a solution.

sys config

p 4, 500 mhz ram. 20gb ubuntu + 60 gb winxp

Note : I installed flash from adobe site and not from ubuntu repositories.

Does YouTube videos crash Firefox or Ubuntu.  I had a problem with YouTube crashing Firefox.  All I did was kill Firefox and it was over.  Here is a solution I have come up with.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

There is a bug in Flash for Linux.  Adobe won't fix it and they know about it.

---

### Post by zipperback on 2007-09-06
> **arai said:**
> ubuntu crashes when watching youtube video. I didn't even had too many firefox tabs open. Just that Youtube video page was left so that it could finish off the buffer and so that i could watch the video continuously. but after it finished playing ubuntu stopped working. i tried pressing all the keys but it didn't respond. 

i rebooted and again went to youtube and the video just started playing and again ubuntu crashed.

i had been using ubuntu + youtube before but it never used to crash. two days back i updated from the bare bones minimum of ubuntu 6.10 edgy with all(180 updates)  from ubuntu repositories. 

now youtube makes the whole system crash. also this doesn't happen in windows. please suggest a solution.

sys config

p 4, 500 mhz ram. 20gb ubuntu + 60 gb winxp

Note : I installed flash from adobe site and not from ubuntu repositories.




Uninstall Flash 9, and install Flash 7.

Flash 9 has some serious stability issues. [-X
Flash 7 will allow you to view YouTube videos. I use it almost everyday for exactly that. \\:D/

Here is the direct download link from the adobe site for flash 7.
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz)


- Jack 
- zipperback

---

### Post by jso2897 on 2007-09-06
Is this bug partly hardware - specific? I ask because I am running Fiesty on three different boxes right now, and flash9 runs flawlessly (in Firefox)on all of them. Two are P3 boxes, and one a PPC box. Sumpin' funny going on here.:confused:

---

### Post by syms on 2007-09-06
but in my ubuntu with firefox youtube never crashes. and i using 9 version.:)

---

### Post by arai on 2007-09-06
> Uninstall Flash 9, and install Flash 7.

Flash 9 has some serious stability issues.
Flash 7 will allow you to view YouTube videos. I use it almost everyday for exactly that.

Here is the direct download link from the adobe site for flash 7.
[http://fpdownload.macromedia.com/get...7_linux.tar.gz](http://fpdownload.macromedia.com/get...7_linux.tar.gz)


Now, how to uninstall flash 9? 

syms, jso2897, stchman yes it also depends on the hardware. my system is old. before i installed the updates system was stable. now when viewing videos in youtube the whole system crashes.

---

### Post by zipperback on 2008-01-01
> **jso2897 said:**
> Is this bug partly hardware - specific? I ask because I am running Fiesty on three different boxes right now, and flash9 runs flawlessly (in Firefox)on all of them. Two are P3 boxes, and one a PPC box. Sumpin' funny going on here.:confused:


Yes it's a known bug for Flash 9. For some people it works flawlessly. On a desktop computer I had, it worked and I never had a problem with it.

On this laptop, it always locks up firefox. Flash 7 doesn't. It's very strange.

- zipperback
:popcorn:

---

### Post by diafygi on 2008-01-01
> **jso2897 said:**
> Is this bug partly hardware - specific? I ask because I am running Fiesty on three different boxes right now, and flash9 runs flawlessly (in Firefox)on all of them. Two are P3 boxes, and one a PPC box. Sumpin' funny going on here.:confused:

This bug is hardware specific. It's been floating around launchpad.net (Ubuntu's bug tracker) for quite a while. It seems to be narrowed down to a problem between the snd-hda-intel audio driver and flash. I don't know that there is any debugging project going on. I've been pushing for one, but since I'm not a programmer, can do little but offer my machine as a testing environment.

Adobe has been unresponsive to this bug, but I would still recommend [emailing]("https://www.adobe.com/cfusion/mmform/index.cfm?name=wishform&product=17") them anyway. If enough people do, hopefully they'll get off their butts and fix it. I view this as a critical problem with Ubuntu that would prevent a lot of casual users from making the switch.

Some registered bugs in launchpad:
[#104470]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/104470")
[#114363]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114363")
[#84844]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/84844")

---

### Post by zipperback on 2008-01-01
Adobe knows about this bug but has done nothing to fix it.


- Jack
- zipperback

---

### Post by zipperback on 2008-01-01
> **arai said:**
> Now, how to uninstall flash 9? 

syms, jso2897, stchman yes it also depends on the hardware. my system is old. before i installed the updates system was stable. now when viewing videos in youtube the whole system crashes.


use your synaptic package manager to remove it.

- zipperback
:popcorn:

---

