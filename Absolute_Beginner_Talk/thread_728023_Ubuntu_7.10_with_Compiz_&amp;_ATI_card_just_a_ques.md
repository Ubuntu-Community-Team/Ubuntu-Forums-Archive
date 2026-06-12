---
title: "Ubuntu 7.10 with Compiz &amp; ATI card just a question..."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2008-03-18
Hi all,
I have the ATI X1950PRO 512MB graphics card and I have just installed Ubuntu 7.10. I keep going off and on Ubuntu. The ATI card is killing me....

anyway I have managed to install Compiz and it works. I also have the Avant Window Manager installed. 

Now I seem to be having some problems every now and then with some Desktop Effects and I have to restart them in order to work the way I want. 
The other thing I notice is that videos don't play normally with Compiz enabled (they used to play fine with Beryl and my other ATI X800XT card.)

So this is all to do with my ATI card right? Is there another dock like Avant to use without Compiz?

What do others use who have similar card to mine?

Thanks!

---

### Post by forrestcupp on 2008-03-18
It's a bear to run Compiz on an ATI with proprietary drivers.  Videos and OpenGL apps will flicker unless you turn Compiz off, and if you turn Compiz off, AWN disappears.  So will any dock because they rely on compositing.  ATI compositing just doesn't work well with openGL apps.

Honestly, I ended up buying a cheap nvidia card, and I couldn't be happier.

But do [this](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) to at least fix flickering with videos in vlc.

---

### Post by emshains on 2008-03-18
ATI has never been a good choice for linux, even worse if you want to run compiz. 

When I encounter video/audio playback problems I just press CTRL+ALT+Backspace, that resets my xorg and now it all works. 
Try this:
[http://ubuntuforums.org/showthread.php?t=726938&highlight=ati+with+compiz]("http://ubuntuforums.org/showthread.php?t=726938&highlight=ati+with+compiz")
[http://ubuntuforums.org/showthread.php?t=717010&highlight=ati+with+compiz]("http://ubuntuforums.org/showthread.php?t=717010&highlight=ati+with+compiz")


I am sorry for your bad expierience with ubuntu, but the only thing i could suggest is to think before you buy a video card.

---

### Post by ROUBOS on 2008-03-18
yeah you're right. this has really turned me off ATI cards. Problem is that I only have ATI cards. 
Funny that in Ubuntu 7.04 I had Beryl running, and video played normaly with my ATI X800XT card. Even while Desktop Cube was rotating video played fine. Luck I guess of the particular model card. 
I was so stupid to upgrade with another ATI card. :(

---

### Post by ROUBOS on 2008-03-18
emshains is right. now i remembered how I fixed it with my X800XT card. Using VLC and the output module set to X11, it displays the video correctly.... ;)

thanks guys... 

In bad need of a new card. NVIDIA !!! ;)

---

### Post by billgoldberg on 2008-03-18
> **forrestcupp said:**
> It's a bear to run Compiz on an ATI with proprietary drivers.  Videos and OpenGL apps will flicker unless you turn Compiz off, and if you turn Compiz off, AWN disappears.  So will any dock because they rely on compositing.  ATI compositing just doesn't work well with openGL apps.

Honestly, I ended up buying a cheap nvidia card, and I couldn't be happier.

But do [this](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) to at least fix flickering with videos in vlc.

I never have any flicker on my videos, but gaming is impossible.

Compiz fusion works perfectly.

You could try envy to install your ati card, it uses the latest 8.3 ati catalyst, it could help.

---

### Post by emshains on 2008-03-18
> **billgoldberg said:**
> I never have any flicker on my videos, but gaming is impossible.

Compiz fusion works perfectly.

You could try envy to install your ati card, it uses the latest 8.3 ati catalyst, it could help.

Hmmm its a divided opinion. Im not putting ATI down, but  I have seen ATI working and ATI making you want to buy a NVIDIA. Its like 1/5, 1= worker, 5= s&cker.

It really depends on the model and linux you are using.


And Robous if you liked my help, please "thank" me by clicking on the star next to the "quote" and other post options and then go to the thread options and if you got all you wanted from this thread  go to the thread options and  mark thread as solved

---

