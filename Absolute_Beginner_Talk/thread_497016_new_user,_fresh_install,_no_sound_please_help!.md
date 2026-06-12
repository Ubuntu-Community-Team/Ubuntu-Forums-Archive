---
title: "new user, fresh install, no sound please help!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Painton on 2007-07-09
I have a fresh install and cannot get sound to work for the life of me. Please help! :)

---

### Post by bodhi.zazen on 2007-07-09
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Othewise, sound card ? what have you tried ? What are you trying to play ?

---

### Post by Painton on 2007-07-09
That link was extensive, but couldnt help me. The card I have is Realtek ALC885 . I can get to the alsamixer, and find that I can change the volume levels just fine, nothing is muted..but I cannot get sound at all.

---

### Post by bodhi.zazen on 2007-07-09
I do no tknow if this will help or not :

[http://ubuntuforums.org/showthread.php?t=418681&page=4](http://ubuntuforums.org/showthread.php?t=418681&page=4)

---

### Post by Painton on 2007-07-09
this seems to be a mac help, Im on an everex amd duel core. I dont know if that makes much difference but it seems that that particular issue likes with macs. What I do know is that my computer def knows that the card is in there, the problem is the drivers I think.  Just trying to play music.

---

### Post by bodhi.zazen on 2007-07-09
Well, usually I look here : [http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

But I do not see your card listed, so you may want to contact Realtek and ask for the linux drivers.

---

### Post by Painton on 2007-07-09
well see im confused now. when i typed sudo asoundconf list I got Nvidia. so...am I wrong now? In the mixer it says

card HDA nvidia
chip: Realtek ALC885

---

### Post by bodhi.zazen on 2007-07-09
You need to first identify your sound card then find and install the drivers.

I can not find any information on your sound card meaning it may not be supported.

---

### Post by Painton on 2007-07-09
how can I best identify it? what cmd would give me a solid awnser? on the computer mfg site it tells me what card I have as a  Realtek , they have drivers on that site but I dont know if they are what I want..they are found at this link, can you please review it?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

---

### Post by bodhi.zazen on 2007-07-10
There you go. 

Download "Others 	4.06a	2007/6/8"

Then extract the archive and read the README

```
sudo apt-get install build-essential

cd realtek-linux-audiopack-4.06a
./configure
make
sudo make install
```

The follow the rest of the readme.

Step 3 ...
You may need to :
sudo ./snddevices


Step 4 Ubuntu uses /etc/modules
Back up the original file first.
gksudo gedit /etc/modules

paste that stuff at the bottom ...

save the file ..

Reboot

Should be good to go at that point. You may need to fiddle with alsamixer

Post any error messages ;)

---

### Post by frodon on 2007-07-23
@Painton, did this worked ?

I have a friend with the same sound card and she have no sound so could you tell us if this worked for you ?

---

