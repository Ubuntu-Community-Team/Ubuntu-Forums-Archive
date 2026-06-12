---
title: "help needed again."
date: 2005-02-08
forum: Apple PPC Users
---

### Post by redneckr1 on 2005-02-08
Thanks for last time i asked. i did sort it i didnt really clarify, but now ive got some more kinda serious issues which i need some help with, im not sure where to put this plea. literally it is a plea. right now my problems.

apparently window manager has crashed so i havent got the ability to minimize, maxamize or close my windows. also moving windows is impossible without the top navigation bars so im stuck. 

 also when i go into computer > Desktop Preferences > window it comes up with

[this](http://server3.uploadit.org/files/kingred7-WindowManagererror.jpg) im pretty sure its connected.


secondly synaptic is broken. im gradually getting more and more frustrated because i cant tinker whats running in the background (as its a 233 Mhz g3 imac with 64 meg of ram its pretty annoying)

[heres a screeny of whats its doing ](http://server3.uploadit.org/files/kingred7-Synapticerror.jpg)

Any help gratefully recieved.


Thanks for your time Red

---

### Post by t.rei on 2005-02-08
as synaptic is a wonderfull tool but consumes quite a bit of ressources i would suggest that - considering the machine you are using - you try to do the console thing:
  
   ```

 $> sudo apt-get update
 $> sudo apt-get upgrade
 
```
  
  that should give you alot more speed. and a bit less chance for errors.
  
  tell me if apt-get works that way. :)

---

### Post by landotter on 2005-02-08
Hey red, it's max from TF.

I didn't realize you were running Ubuntu under 64mb of ram--that must be rather painful.  :D 

In a terminal or hit alt+f2 to get a "run box"...

to kill your windowmanager (it should respawn after you kill it) type "killall metacity" and to start it up of course just type "metacity".

X is the thing that draws the GUI and sometimes it goes goofy so you need to kill it and let it restart--and unlike Windows, you don't have to restart the computer to do it, just "crl+alt+backspace", and login again and see if your problems are fixed.

Are you sure synaptic's broken? Make sure you don't have any broken packages installed--that will make synaptic mad. You can find broken packages by using the filter buttons on the left. Now make sure your repositories are correct--did you add any sketchy ones? Then refresh and see if the new header files are downloaded.

---

### Post by redneckr1 on 2005-02-10
[QUOTE=t.rei]as synaptic is a wonderfull tool but consumes quite a bit of ressources i would suggest that - considering the machine you are using - you try to do the console thing:
  
   ```

 $> sudo apt-get update
 $> sudo apt-get upgrade
 
```
  
  that should give you alot more speed. and a bit less chance for errors.
  
  tell me if apt-get works that way. :)[/QUOTE]
 i still have the synaptic problems, like i said i run an offline ppc warty install im wondering if i can get the update on my usb pendrive and direct the install to there. i tried it with the universe package and it didnt work (lol when i managed to do it i found it was about 100 meg to dl so my pendrive would have been useless)


any suggestions?

---

