---
title: "Still no 5.1..Dont know what else to do"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by pablo_max on 2007-07-07
Hello, 

I switched to Linux about 2 months ago and so far really like. One problem though..I can't get 5.1 sound to work at all. Not in movies of anything else. 
I have a asus p5nsli MB and it for sure works on my windows partition but not in linux. I tried to create the file in my home directory and that didnt do anything at all. 
I am also using the alsa drivers. 
When I go to the properties there are no sliders at all for center, sub and surround speakers.  This is for sure something really sucky about linux..thats is so hard to make something work all the way. At least for someone new to it. 
Can someone point me in the right direction? Its such a pain to have to boot to windows every time I want to watch a DVD in 5.1.
Thanks a lot. 
Patrick

---

### Post by Daveth on 2007-07-07
you need to fire up the alsamixergui from Synaptic. It has more sliders than you can shake a stick at, and certainly will give you 5.1 sound.

---

### Post by annda on 2007-07-07
> **Daveth said:**
> and certainly will give you 5.1 sound.

...assuming the manufacturer of the card created linux drivers or was user-friendly enough to release their specs so other user-friendly people could write linux drivers and save them some development work and money.

---

### Post by pablo_max on 2007-07-07
I tried the alsamixergui and it for sure does not give me any option for 5.1 sound. I tried all the normal stuff, but not sure what else to do. THere are drivers on the asus' webpage, but I am not sure if I should try them,.

---

### Post by pablo_max on 2007-07-08
oh man....
I put is this "options snd-hda-intel position_fix=1 model=3stack" into the alsa-base file and now it's all messed up! 
I dont know the hell is going on with the computer now. I cant play music anymore. The volume dial on my keyboard does nothing at all. I cant play anything with movie player..how can this one line **** it up so bad? 
Its like those programs are looking for a device thats not there. 
How can I check that? Its totally useless to have a PC with no sound. Any ideas..I really dont want to go back to windows..

---

### Post by Daveth on 2007-07-15
so edit the alsa-base file and remove the line you inserted- that should put you back where you were at least.
This
[http://forums.suselinuxsupport.de/index.php?showtopic=50985&pid=224267&mode=threaded&show=&st=&](http://forums.suselinuxsupport.de/index.php?showtopic=50985&pid=224267&mode=threaded&show=&st=&)

might help a bit, though one cannot vouch for the status of the fix.

---

