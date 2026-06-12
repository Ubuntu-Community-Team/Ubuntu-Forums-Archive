---
title: "Xbox not recognising ubuntu"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by droopyrow on 2007-02-21
Can anyone HELP Please....................................

I have bought an Xbox360 and want to stream music and videos ect from my computer  through my xbox that is conneced into my television.  The only problem is that the xbox is not recognising the ubuntu operating system at all.  When i use a computer with windows it steams from the computer through the xbox....... I dont want to have to buy a windows operating system so please can you help me make it work?!!!!!?

Regards

Droopyrow

---

### Post by ComplexNumber on 2007-02-21
i would have thought that microsoft make it deliberate that it only works with windows, but maybe someone with an xbox can help.

---

### Post by hannaman on 2007-02-21
Doesn't that only work with XP MCE or Vista?

---

### Post by droopyrow on 2007-02-21
Anyone own an xbox who can help me figure out how to stream programs from linux system through the xbox so i can watch films and play music on my television (use it as a media system)

cheers

---

### Post by ComplexNumber on 2007-02-21
this link may provide some clues:
[http://www.methylblue.com/blog/todo-xbox-360-streaming-from-amarok/](http://www.methylblue.com/blog/todo-xbox-360-streaming-from-amarok/)

---

### Post by droopyrow on 2007-02-21
STILL need help.....................bought a new xbox 360 replaced windows xp with linux software and now i want to stream my music ect through my xbox.  Unfortunately xbox will not recognise linux so i cannot stream.  I really dont want to buy a new windows operating system but really want the linux software to work for me.  Can anyone help.  There must be a program that can be downloaded to make the xbox recognise the linux system.

Cheers

Droopyrow:(

---

### Post by aberry5555 on 2007-02-21
if it recognises it as a network drive, (as in with windows where you would share a folder over a network) then it is possibe with a program called "samba". I do not know exactly how it is meant to stream though so if you could explain some more I can try and help, what did you have to set up in XP to make the Xbox see it?

---

### Post by droopyrow on 2007-02-21
The xbox 360 automatically detects another computer that is wired to the same router.  When i go into media file on xbox and select stream from computer, it searches for available computers.  It does not detect my main computer (linux system) at all.  I tryed the same with a windows xp laptop and it found it straight way.  

Help.............................

---

### Post by redman0570 on 2007-02-21
Unfortunately this will be very dificult.  You would have been in the same boat if you kept XP.  The XBOX360 only streams from MCE2005 SP2, maybe Vista but I have not checked.

Your only hope to stream from Linux to the 360 would be to install Wine and running one of the three available Homebrew streaming servers available for XP.  That's an adventure, because you got to configure Wine to work with them.

I have a 360 and I have not tried.  I do not have a MCE computer so I have never been able to stream to my XBOX, I tried one of the homebrew servers and it was choppy and unreliable.

You can find help and XBOX Homebrew software here.

[http://www.xboxscene.com/tools-xbox360.php](http://www.xboxscene.com/tools-xbox360.php)

Good luck.

---

### Post by aberry5555 on 2007-02-22
I did find something, apparently the way it works is via something called UPNP, which is an open source standard. there is a program for linux that uses this standard called GMediaServer which might work, give it a shot and see what happens

*edit*

apparently that doesnt really work but I did find another link that is meant to work pretty well, as it's designed to do so. Unfortunately it seems the site is down at the moment but Ill give you link to it anyway for when it comes back up

[http://x360mediaserve.sourceforge.net/](http://x360mediaserve.sourceforge.net/)

also here's a link to a mirror site with, supposedely, the working programs 

[http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/x/x3/x360mediaserve/](http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/x/x3/x360mediaserve/)

and heres some information to try and get it working

[http://ubuntuforums.org/archive/index.php/t-143016.html](http://ubuntuforums.org/archive/index.php/t-143016.html)

---

### Post by Eric B on 2007-03-05
> **redman0570 said:**
> Unfortunately this will be very dificult.  You would have been in the same boat if you kept XP.  The XBOX360 only streams from MCE2005 SP2, maybe Vista but I have not checked.

Your only hope to stream from Linux to the 360 would be to install Wine and running one of the three available Homebrew streaming servers available for XP.  That's an adventure, because you got to configure Wine to work with them.

I have a 360 and I have not tried.  I do not have a MCE computer so I have never been able to stream to my XBOX, I tried one of the homebrew servers and it was choppy and unreliable.

You can find help and XBOX Homebrew software here.

[http://www.xboxscene.com/tools-xbox360.php](http://www.xboxscene.com/tools-xbox360.php)

Good luck.

You do not need MCE to play music.

---

### Post by johnl on 2007-03-05
Hello,

I have tried some different software for linux with various success with my xbox360, so I thought I'd give you some advice.

The xbox360 communicates with media server using the uPnP protocol, which is a standard for media sharing.  Unfortunately, Microsoft's implementation has several differences from the standard which means a generic uPnP server will not work with the 360.  However, there are some projects out there which have added 360 support:

[TwonkyMedia](http://www.twonkyvision.com/Products/TwonkyMedia/index.html) is a commercial uPnP application that runs on Linux that supports streaming music to the 360.  There is a 30-day trial version available. 

[x360mediaserve](http://sourceforge.net/projects/x360mediaserve/) is a free, open source java program that supports streaming music to the 360.  I had mixed success with this -- songs would randomly cut off when playing, but the time would continue to count as if it were still playing.  Give it a try, see if it will work for you -- my problems may have had to do with slow network speed or network setup.

[UShare](http://ushare.geexbox.org/) claims to support the360.  I haven't tried this newest version (0.9.10) so I can't advise you on it.  I tried it back at version 0.9.7 when the support was still iffy, and it didn't work.  Thanks for posting this, I may actually go back now and try it again :) 


Good luck!

John

---

### Post by bitshifter1001 on 2007-12-06
For uShare check out the following links

A decent HowTo:
[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428)

Lost of questions and answers:
[http://ubuntuforums.org/showthread.php?t=631213](http://ubuntuforums.org/showthread.php?t=631213)

---

### Post by DragonKore on 2007-12-06
TwonkyVision works great for me, but it isn't free. Not sure what I'll do when the 30-day-trial is up...

---

### Post by Amstell on 2007-12-06
I would suggest setting up a samba server and it should see that as its a windows type server.  Should work fine.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by Hubris2 on 2007-12-11
The latest version (1.1a) of Ushare works quite well, and does support the Xbox360.  It's available from the Ushare repository.  Do a search on Ushare, there are a couple larger threads discussing how to install and configure it.

---

