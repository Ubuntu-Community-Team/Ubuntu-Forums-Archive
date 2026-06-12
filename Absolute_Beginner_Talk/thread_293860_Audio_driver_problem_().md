---
title: "Audio driver problem (?)"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2006-11-05
Ok, so i just installed ubuntu edgy, and everything works fine. Not that I understand how it works, seeing as I don't know anything about linux, programming or any other "geeky" stuff :). 

 Now, I've run into a couple of problems, like playing media files, getting ATI graphics up and running and stuff, and I've found nice how-to's and guides and stuff that helped me out. However, I still can't convince it to play any sound for me. I know I have the codecs, so I assume it must be some kind of driver problem. I've tried to find a guide, but I just doesn't seem to be able to.

I have an onboard soundcard on my Intel motherboard, and the device manager identifies it like this one:

82801EB/ER (ICH5/ICH5R) AC'97 Audio

 Can anyone help me out here? Either by telling me how to do, or pointing me in the direction of a guide :) Thanks in advance.

Regards
Bjarke Jensen
Roskilde, Denmark.

---

### Post by ReaderRat on 2006-11-05
Sound Solutions - Comprehensive Guide
         **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by azkehmm on 2006-11-05
Thanks a bunch... I'll look into and post again if I'm too much of a newbie to understand it :)

---

### Post by azkehmm on 2006-11-06
Ok... now I've tried everything in the Sound guide. 
I've switched from edgy to dapper, to see if that'd make it work (it didn't)
As far as I can see, everything is as it should be. My soundcard is identified, the driver is there, I have the right codecs and stuff. The only thing that's worng, is that the sound doesn't get from the card and to my speakers (and yes, I have checked cables and connections :))

 Right now, I'm running Dapper, since that should be the best supported version right now. Can anyone please help me figure this problem out? Thanks in advance.

Regards
Bjarke Jensen
Roskilde, Denmark

---

### Post by ReaderRat on 2006-11-06
I found this -> **[http://www.linuxforums.org/forum/debian-linux-help/47853-intel-sound-driver-needed.html](http://www.linuxforums.org/forum/debian-linux-help/47853-intel-sound-driver-needed.html)**
I don't know if this applies to your situation.

---

### Post by ReaderRat on 2006-11-06
This one is better -> **[http://www.flaterco.com/kb/audio.html](http://www.flaterco.com/kb/audio.html)**

---

### Post by rdxdude on 2006-11-06
I have the same problem as azkehmm and used your links turned up the sound on the alsamixer and all. Still having no sound.  I am using edgy and it recognizes the card and i loaded the sound driver and all and still no sound.  Mine is an intel ich4 ac 97 and loaded the driver snd-intel8x0.  I am on a laptop and i know the sound works cause it works in windows so any ideas would be helpful.  thanks.

---

### Post by azkehmm on 2006-12-10
It turned out this isn't a driver problem or anything, but merely a simple question about turning the right switches in Alsamixer. 

 I needed to turn on "Master Sorround" and crank the volume up there, and then turn on "Float to front" almost at the end of the row of switches.

---

