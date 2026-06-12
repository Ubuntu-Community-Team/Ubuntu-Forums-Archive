---
title: "Anyone able to get the nbcolympics.com live streaming to work?"
date: 2012-07-28
forum: Any Other OS
---

### Post by legoman666 on 2012-07-28
I've tried with my Mint 13 Laptop using Chrome dev. I log in using my Comcast credentials just fine. When I try to view a stream, the video box is just blank.

I've tried on my Mint 11 HTPC using Chrome dev, same result as above. I've also tried Firefox 14 & 15 on this machine. It logs in fine, and then keeps asking me to pick my cable provider again. And again. And again.

Same login credentials are working fine on my wife's Win7 laptop with Chrome so I'm stumped as to why it won't work on mine.

---

### Post by EricCFlem on 2012-07-28
As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.

---

### Post by mscout2004 on 2012-07-28
Using what EricCFlem posted I was able to view the live feed just fine this morning. I was having the same problem legoman666 was earlier with it just stuck in a loop asking for login credintials.

Congrats Eric for finding this fix.

---

### Post by Perfect Storm on 2012-07-29
Moved to Other OS/Distro Talk.

---

### Post by xjohnthomasx on 2012-07-29
I second - this fix cured the issue as described. Cox, nbcolympics.com, hal, google chrome/chromium, xubuntu.

---

### Post by legoman666 on 2012-07-29
> **EricCFlem said:**
> As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.


Worked for me in Firefox, awesome. To get Chrome to work, I had to disable the built in Pepper Flash player and use the older 11.2 release that was on my system.

Thanks!

---

### Post by Dubbayoo on 2012-07-30
> **EricCFlem said:**
> As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.
Worked for me; thanks. You must close the browser before step 3.

---

### Post by gfe on 2012-07-31
It worked for me too. The same fix allows me to watch CNN live.

---

