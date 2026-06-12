---
title: "my silent nightmare"
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by niteblind on 2008-09-08
Hi ALl,

Can anyone assist me? I have a Macbook (black) which was bought at the beginning of the year. I have just installed Hardy 8.04 and I cannot get the sound to work on it. From reading about this appears to be a common problem so does anone have the anwer?

After following the macbook wiki and getting no where fast I found a post which suggested downloading the latest alsa drivers 1,0,17 which i did and tried to follow the posts instructions which were:

cd to the alsa folder
./configure
make
sudo make install

all this went fine but then it said :
sudo /etc/init.d/alsasound stop

which is where I am now stuc as this file does not appear to exist! Anyone know where I went wrong?

niteblind

---

### Post by cyberdork33 on 2008-09-08
> **niteblind said:**
> Hi ALl,

Can anyone assist me? I have a Macbook (black) which was bought at the beginning of the year. I have just installed Hardy 8.04 and I cannot get the sound to work on it. From reading about this appears to be a common problem so does anone have the anwer?

After following the macbook wiki and getting no where fast I found a post which suggested downloading the latest alsa drivers 1,0,17 which i did and tried to follow the posts instructions which were:

cd to the alsa folder
./configure
make
sudo make install

all this went fine but then it said :
sudo /etc/init.d/alsasound stop

which is where I am now stuc as this file does not appear to exist! Anyone know where I went wrong?

niteblind

I believe that all you need to do is restart ALSA... This can also be accomplished by restarting you machine.

---

### Post by niteblind on 2008-09-08
that does not work I amafraid. It also does not explain where the file has gone that I suppose should be there.

any other ideas|

niteblind

---

### Post by cyberdork33 on 2008-09-08
> **niteblind said:**
> that does not work I amafraid. It also does not explain where the file has gone that I suppose should be there.

any other ideas|

niteblindThere is no alsasound initscript anymore.

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by niteblind on 2008-09-09
okay thanks for letting me know. I think though it would be more helpful if you could tell mw what I should be stopping instead maybe?

niteblind

---

### Post by cyberdork33 on 2008-09-09
> **niteblind said:**
> okay thanks for letting me know. I think though it would be more helpful if you could tell mw what I should be stopping instead maybe?

niteblind
I actually don't know. Since ubuntu has moved to using pulseaudio things have changed a bit. There is a pulseaudio initscript, but I don't know if it restarts ALSA.

---

### Post by niteblind on 2008-09-09
okay. thanks. Can I ask a really stypid question then? One of the fixes for this issue is to ensure that all the platback channels are unmuted.

Should I be using alsa-mixer to do this? Also is a muted channel where the M at the bottom is hightlighted (as i assume that is correct) or is it the other way round?

niteblind

---

### Post by cyberdork33 on 2008-09-09
> **niteblind said:**
> okay. thanks. Can I ask a really stypid question then? One of the fixes for this issue is to ensure that all the platback channels are unmuted.

Should I be using alsa-mixer to do this? Also is a muted channel where the M at the bottom is hightlighted (as i assume that is correct) or is it the other way round?

niteblind
Yes, alsamixer should still work for the most part. (you can actually disable pulseaudio if it is giving you problems). The M means it is muted. use the M key to unmute.

---

### Post by BenAshton24 on 2008-09-09
Randomly plucking something out of the air, i've never had a mac book or any apple product in my life :S anyways, why not give this a shot. type this in terminal:
> sudo asoundconf list
you should get a list of available soundcards, if there is more than one then try them all individually by typing:
> sudo asoundconf set-default-card nameOfSoundCard
obviously don't forget to replace nameOfSoundCard with one of the names from the previous list. as i said before I've never had a mac so I'm not sure if this will work but its worth a shot. hope this helps :D

Ben.

---

### Post by niteblind on 2008-09-09
Hi,

Did that still no noise nothing actually happened after the last command it just came back with the prompt again.

God how I miss Gutsy! Can anyone who has a Macbook that had this no sound issue let me know if they managed to fix it or not?

Cheers
niteblind

---

### Post by niteblind on 2008-09-09
c'mon everybody surely one of you geniuses sorted this out?

---

### Post by niteblind on 2008-09-10
bump

---

### Post by cyberdork33 on 2008-09-10
I am not sure what Macbook version you have, but there is a bug report on this here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/162347](https://bugs.edge.launchpad.net/mactel-support/+bug/162347)

There might be some helpful info there.

---

### Post by niteblind on 2008-09-12
Hi cyberdork33,

THANK YOU!!! for putting me out of my misery. It would appear from the posts on the page you linked that there may be a vital line missing from the setup wiki. Does anyone know how I go about asking for this to be updated?

cheers to all the others for their assistance as well

niteblind

---

### Post by cyberdork33 on 2008-09-12
> **niteblind said:**
> Hi cyberdork33,

THANK YOU!!! for putting me out of my misery. It would appear from the posts on the page you linked that there may be a vital line missing from the setup wiki. Does anyone know how I go about asking for this to be updated?

cheers to all the others for their assistance as well

niteblind

you can quite easily update it yourself. (It is a wiki afterall). Or you can post what needs to change and I can update it.

---

