---
title: "Video Lag in Firefox"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Mushie on 2006-12-24
Just as the post says, I try watching stuff, e.g. youtube, and the video lags away from the sound. I press pause, the video then stops and then a second later the sound. Any patches or fixes out there. A link will do. Just don't understand why is only does it in firefox. Other videos that are on my hdd have no lag.

Thanks.

---

### Post by Shatrat on 2006-12-24
The videos on your hard drive arent flash video, youtube is.  The linux version of the flash player has lots of problems.  The latest flash 9 beta fixes the sync issue, although I still have crashing problems.

I'm sure if you do some searching on these forums you'll find instructions on how to install the latest flash 9 beta.  It basically involves downloading a file from the official site and extracting it and copying it to your firefox plugins directory.

---

### Post by Mushie on 2006-12-24
Thanks. I hope installing Flash isn't hard like it was to do JRE today. It took me about 3 hours to figure out, but I got it :) I'm so proud of myself. As I was once told, you only learn by doing and remember by making mistakes.

Thanks again.

---

### Post by tommcd on 2006-12-24
Get flash 9 here:
[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)
Extract it. If you already have flash 7 installed, just cd into /usr/lib/firefox/plugins and rename libflashplayer.so to libflashplayer.so.bak. Then copy the libflashplayer.so that you just downloaded to this directory (/usr/lib/firefox/plugins). Then do "gedit ~/.mozilla" and go to the end of the file and change "flash7.0" to "flash9.0". This is how I did it and it works perfectly. If you don't have flash 7 installed then just copy the libflashplayer.so to /usr/lib/firefox/plugins as above.

---

### Post by cw1925 on 2006-12-28
[LEFT]I tried that, but it says I don't have permission to write to the folder.  How do I get it?
[/LEFT]

---

### Post by tommcd on 2006-12-29
You have to use sudo. Just cd into  /usr/lib/firefox/plugins  and do 'sudo mv libflashplayer.so libflashplayer.so.bak' (This assumes you have flash 7 installed already). Then cd into the directory where you have the libflashplayer.so from flash 9 and do 'sudo cp libflashplayer.so /usr/lib/firefox/plugins'. 
Then do "gedit ~/.mozilla" and change the end of it where is says flash 7.0 to flash 9.0. No need to use sudo here cause it's your home folder. 
If you don't have flash 7 already then just copy libflashplayer.so to /usr/lib/firefox/plugins and it should just work. Restart FF after doing this.

---

### Post by bruenig on 2006-12-29
> **cw1925 said:**
> [LEFT]I tried that, but it says I don't have permission to write to the folder.  How do I get it?
[/LEFT]

There is a pretty easy howto in my signature.

---

### Post by cw1925 on 2006-12-30
> **bruenig said:**
> There is a pretty easy howto in my signature.Did that, it lets me see flash videos, but they are now studdering like never before.  Any way of undoing that?

---

### Post by tommcd on 2006-12-30
Did you try the way I suggested?

---

### Post by cw1925 on 2006-12-30
> **tommcd said:**
> Did you try the way I suggested?Yes I did.  And I just went to the Adobe site and reinstalled there Flash, and it works fine again.  Thanks.

---

