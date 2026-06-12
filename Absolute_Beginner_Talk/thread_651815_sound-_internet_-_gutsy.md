---
title: "sound- internet - gutsy"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by tanyac on 2007-12-28
I am using Mozilla.

I installed Gutsy Gibbon over a month ago, and have been without internet sound since.

If I download items and play them outside of the internet sound is fine, it seems to only be on the internet.

I have tried several different things in many posts, and i really do not know what to do at this point.

any help would be much appreciated.

---

### Post by toddward on 2007-12-28
tanyac, when you're trying to listen to sound through Firefox (the Internet) are you listening to other audio like things outside of it?

If you are, try closing down all of the running applications and start up Firefox.  See if the sound works and get back to me on the thread.

---

### Post by tanyac on 2007-12-28
I have tried to listen to internet with and without other audio playing, there is no difference.

---

### Post by toddward on 2007-12-28
Sorry for more questions, is this flash that isn't producing sound?

---

### Post by tanyac on 2007-12-28
don't mind the questions, ask away!

I am unable to hear sound on things like youtube/myspace, which i guess is flash.

I am also unable to hear music on pandora... I am not sure if that is flash.  If you have something else I can try to see if I get sound through non-flash let me know.

i am able to see video on flash though, its only the sound that is a problem. 

thanks for the help.

---

### Post by tanyac on 2007-12-28
also... i have the same problem with opera and mozilla.

---

### Post by tanyac on 2007-12-28
yes its flash that seems to be the problem. i tried watching a trailer on apple.com and the mplayer launched for quicktime. 

too bad so much stuff is in flash.

I have tried a lot of things in other posts.... not sure what to do at this point. any help would be very appreciated.

thanks again!

---

### Post by mmb1 on 2007-12-28
tanyac, in your firefox preferences, go to the content tab, at the bottom you should see a file type association button, push it.  Now find the "spl" and "swf" file extensions and see if they're set to open with shockwave flash.

---

### Post by tanyac on 2007-12-28
yes they are

---

### Post by mmb1 on 2007-12-28
Okay, now go into synaptic and make sure the "ubuntu-restricted-extras" package is installed.

---

### Post by buckykat on 2007-12-28
that sounds like a flash problem. check what version of flash you have. type "about:plugins" (no quotes) in the address bar and see what version of flash you have. if you have flash 7 (no flash 8 for linux ever existed), you should download the .tar.gz from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN)
unzip it, then put the libflashplayer.so into /usr/lib/firefox/plugins. you need to be root to do this, so do  "sudo nautilus" in terminal, then navigate to /usr/lib/firefox/plugins and drag the new libflashplayer.so there. you also need to delete the old libflashplayer.so. then restart firefox and see if youtube works. hope this helps.

---

### Post by tanyac on 2007-12-28
yes i have that

---

### Post by tanyac on 2007-12-28
is this the correct version? this is what i have:

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by tanyac on 2007-12-28
yes, i have that package of ubuntu restricted access

---

### Post by DarkN00b on 2007-12-29
This sounds like a problem I get sometimes. It just happens without warning. You should be able to fix your problem by following the instructions [here]("http://www.arsgeek.com/?p=2966").

I have no idea why this happens, but this always fixes it.

EDIT: As a matter of fact, I just now fixed it again. That's how I found your post. I was looking for people with the same problem so I could tell them how I fixed it. :D

---

### Post by tanyac on 2007-12-29
it worked! thank you so much.  you have no idea how much time i have spent trying to fix this!

---

