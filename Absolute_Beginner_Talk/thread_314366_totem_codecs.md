---
title: "totem codecs"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-07
Can someone tell me where to start looking for audio codecs

Thanks

---

### Post by meng on 2006-12-07
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Hendrixski on 2006-12-07
There are also two good books you should look at: "Ubuntu Hacks", and "Linux Multimedia Hacks" that talk about getting codecs and other multimedia stuff up and running.  Stuff I'm sure you're not thinking about now, but that will make your Ubuntu experience better.

---

### Post by xpod on 2006-12-07
Theres is of course also Automatix2 that dosent require practically any reading.:D 
Gives you all your codecs,flash and java etc plus another couple of dozen useful things besides


[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

For the lazy reader:mrgreen:

---

### Post by squrl on 2006-12-07
Don't mind reading but after two days of reading and not a peep from the speakers makes me wonder if it's worth the effort. I went through the automatix install and got nothing. Amorok. Then audacity. Then Gnomoradio and on and on. 

Last week it was getting a printer to run. Finally got it to print by going through my wife's machine to the network printer. Not what I want but it is still better than windows. Maybe !!

Thanks for the help.

---

### Post by meng on 2006-12-07
Are you trying to play some weird file format? I can't understand why it's causing so much difficulty for you.

---

### Post by xpod on 2006-12-07
Sound issues are something a lot of us have endured at some point..

Have you tried right clicking your volume icon and checking all the settings...or type "alsamixer" in the terminal which will give you something to check.

---

### Post by squrl on 2006-12-07
The only format I would like to play is mp3. The sound card in this machine is a creative blaster. I am tempted to buy a new card.

---

### Post by meng on 2006-12-07
Okay, if the player (be it Totem, Amarok or whatever) isn't complaining about the file format and is recognizing the length of the track, etc, but you just aren't HEARING anything, then this is a soundcard configuration issue, not a codec issue. If your player throws an error dialog whenever you try to play an mp3 file, then it's a codec issue.

I think that most Creative soundcards should be able to be set up fairly easily. You should specify exactly which model you have though.

---

### Post by squrl on 2006-12-07
According to the best information I have it is known as creative blaster live. I don't have a model number and didn't find one on the card. Is there a specific place in the OS to identify or describe the card.

---

### Post by meng on 2006-12-07
Try in the terminal window:
lspci

You're implying that it's now a soundcard configuration issue, are you?

---

### Post by squrl on 2006-12-07
I GOT IT !!!!!!
This machine had the legacy sound turned on in the bios but uses a pci card. It worked either way in windows but when I shut off the legacy sound edgy now plays music.

Thanks to all for the help.

---

