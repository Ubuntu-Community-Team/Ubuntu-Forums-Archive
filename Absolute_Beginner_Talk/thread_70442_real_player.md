---
title: "real player"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-09-29
i installed the linux version but it is not working:
"unable to execute child process"

---

### Post by aysiu on 2005-09-29
How did you install it?

---

### Post by jasonpeinko on 2005-09-29
a bin file, i did what it told me

---

### Post by Perfect Storm on 2005-09-30
Here's how you do it: [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)


.:=The AI Dude=:.

---

### Post by netwench on 2005-09-30
please please please will someone who knows what they're doing actually follow the directions on [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer) and tell us newbies if they're still valid? 

i have read on the forums that realplayer has been removed. when i tried following the exact directions above, the file names have changed and so the instructions didn't match. one is looking for rp8, but real.com now has rp10 out.

also,since the w32codecs have been moved, those directions don't work also. could someone please point me in the direction of simple directions to install the w32codecs?

thank you all very much for your help

---

### Post by Qrk on 2005-09-30
The ubuntuguide instructions are wrong. You have to go to real's website and follow their instructions.

cd into the directory you downloaded it into and run

chmod a+x RealPlayer10GOLD.bin

Then 

sudo RealPlayer10GOLD.bin

---

### Post by nitricacid on 2005-09-30
ignore this post

---

### Post by netwench on 2005-09-30
nitricacid, that's what my point was. :) the synaptic package manager says this is the installer for real player, go to real.com and download the player. then, the player you download from real.com and the only one i can find is RealPlayer10 GOLD. the installer points to a real player 8 file and completely different file name. the synapitc one is outdated.

qrk, thank you for checking on this for me!! so i'm not nuts! :) i have followed real.com's instructions, but it still doesn't work so i figured i was doing something wrong. i see realplayer 10 and realplayer 8 in sound and video, but nothing happens when i click on them. i tried looking for the w32codecs, thinking that's what i'm missing, but now i'm reading that they're moved.  i'm a little too new to know where to go looking for them... :) i don't know how to compile yet either...

maybe i'm going about this the wrong way- *all* i'm trying to do is to be able to play video's from websites.... i really appreciate all the advice posted on these forums, but i'm finding it outdated since stuff has been moved.

do you know of the latest-as-of-this-week- place to get this newbie to just play video off the web? :) i have sound! i can play cd's all day long- just no video.

much appreciated! :)

---

### Post by nitricacid on 2005-09-30
Mybad..... isht happens.
Sorry if i sounded like an ass. i didn't mean to.

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=nitricacid]or search the synaptic package manager for REALPLAYER and install it that way....
This isn't windows anymore, you don't have to search the web,download and install what you need when there is a program that does all that for you.

Don't be suprosed that in the future MicroCracker doesn't implement something like this into their own system and then some how sue the people that made synaptic just so that WindBlows can be the only program to have a selfsearch,self-installer program.[/QUOTE]

this is wrong. For realplayer you must install it how the post two up says to do. It works great for me then!

---

### Post by Qrk on 2005-09-30
Realplayer also doesn't like esd.
Try typing 

killall esd 

into a terminal before running it.

---

### Post by hvignesh on 2005-10-01
hello pals... 

         i am new to ubuntu.. pls guide me how to install xmms or realplayer .. iam not able to play mp3 files... i tried jus the way instructed in guide.. but it is not working...

---

