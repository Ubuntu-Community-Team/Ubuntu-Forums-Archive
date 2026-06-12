---
title: "remove ubuntustudio-audio"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-06-20
Help me, please
I just apt-got installed ubuntustudio-audio, when in the middle near the end of the installs, my pc tells me it is out of space on the file system. So i tried sudo apt-get remove ubuntustudio-audio and it gave me the following error msg:

darrell@darrell-laptop1:~$ sudo apt-get remove ubuntustudio-audio
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
darrell@darrell-laptop1:~$ 


i don't know how to do that and stuff is starting to fail on my pc (amsn keeps crashing on me)..
help please? Shouls i remove all the software 1 by 1 in add/remove? I don't think half of them are properly installed...
I can live without a working linux

---

### Post by quinnten83 on 2007-06-20
nevermind, 
After I calmed down from my initial panic, i checked the man pages and ran
darrell@darrell-laptop1:~$ sudo dpkg -r ubuntustudio-audio
(Reading database ... 171529 files and directories currently installed.)
Removing ubuntustudio-audio ...
darrell@darrell-laptop1:~$ 

Seems to be uninstalled now. Do I need to purge somehow?
or are the installation packages also removed?

---

### Post by quinnten83 on 2007-06-20
Oops, spoke too soon and back to panniciking.
I restarted and now get the message that gdm could not log me in, probably due to lack of space.
I thought i removed the ubuntustudio-audio, but I guess it is still there?
I'm unsure how tp proceed if anybody would care to point me in the right direction, since i can not log in to do anything.

I've just booted into windows 9
out of sheer desperation)

---

