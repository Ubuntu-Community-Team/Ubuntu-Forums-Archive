---
title: "Offset screen, unclear font?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by bigaLOL on 2008-01-09
hey guys..so FINALLY after about the ..3rd time attempting to install linux..i finally installed ubuntu 7.10 gutsy on my PC. :) i tried to fully switch..but some things are holding me back. i have a Netgear WG111T wireless adapter and ive read a LOT of threads and this was kind of hard to set up but thanks to a fellow friend who uses Ubuntu, he helped me out with ndiswrapper and such utilites. Well ..im going to say my PC specs now just to clear up some questions that might come up:

Intel pentium 4 2.4 GHz, 512 RAM, Intel(R) 82845G/GL/GE/PE/GV (integrated graphics lol)..and W1900 Dell LCD TV [19 inch widescreen] for my monitor. it's native resolution on XP is 1280x768 :lolflag: :p ahahah

okay so ..so far. i wanna thank you all for reading all that and hopefully somebody will help me out :P ima list my problems now.

OKAY SO when i run 1280x768 reso. on Gutsy, it's randomly offset..like veritcally. the top part is cut off by a LITTLE tiny bit. i took pics of my monitor in a few different resolutions..here's the 1280x768:

[http://img266.imageshack.us/img266/6351/7681je0.jpg](http://img266.imageshack.us/img266/6351/7681je0.jpg)

[sorry i took these pics in 3M mode in my camera..so they'll be big :P]

yea notice that cut off? lol .. if i do auto adjust from my monitor, it makes it into like 1024x768 but not stretched out..just 4:3 i think and i gotta switch back to XP, and auto adjust it again for it to go back to normal 16:9.

okay btw to everybody ive ran sudo dpkg-reconfigure xserver-xorg approx. 3 times but it hasnt done anything to me..

here is my monitor in 1280x800 mode..in this resolution..the font i dont know why looks REALLY clear..clearer than in 768..but the bottom of the screen doesnt show my lower panel..so i deleted the bottom panel and added the stuff to the top panel, but still..id prefer my monitor to show everything, you know?

[http://img101.imageshack.us/img101/7484/8002tr2.jpg](http://img101.imageshack.us/img101/7484/8002tr2.jpg)


and finally here is 1280x720 reoslution..it goes off to the right too much and black bar on the left:

[http://img266.imageshack.us/img266/4328/7201ad2.jpg](http://img266.imageshack.us/img266/4328/7201ad2.jpg)

&

[http://img266.imageshack.us/img266/3250/7202lf8.jpg](http://img266.imageshack.us/img266/3250/7202lf8.jpg) [notice the iGoogle that's cutoff]

ahhhhh yea.

im pretty sure ive said everything that there is to be said . . . 

I was already planning to switch full time to linux but keep my XP partition for school work and printing out documents and other things cause i dont feel like installing my printer driver onto linux lol..but this resolution thing is kind of annoying :( although my internet sometimes when i boot up..says it wont connect..after a restart X or just normal restart, its back to normal, so that's not bugging me at all.

i read a lot of threads from the offset monitor and followed their guides but they wont help me. also i read this one where it said that this person had an LCD monitor and it was offset but when they turn it off and back on, it gets set back to normal. tried that...didn't work. lol

anyways if anybody can help..and if anybody has read all of this. i greatly appreciate it. im really looking forward to a reply..until then..going to stick to XP. Thank you very much.

- Arvin

---

### Post by frup on 2008-01-09
Does the monitor have any configuration options? On a standard computer screen (not TV) you can change the width and position a little which generally fixes these kinds of problems.

---

### Post by bigaLOL on 2008-01-09
yeah it lets me manually change the position..but like..everytime i boot, it goes back to being offset..but when i manually move the vertical a little down ..it works out i guess

---

### Post by bigaLOL on 2008-01-09
:lolflag: :(

---

### Post by rexxxlo on 2008-01-09
try to reconfigure xorg from the recovery mode that has worked for me in the past 

to enter recovery mode press esc when you are prompted during the boot sequence
wait for all of the text to stop you will be at a prompt then type 

sudo dpkg-reconfigure xserver-xorg

then type your password and follow the settings 

dont for get that when it asks: low, medium, advanced, choose advanced.
to choose what screen resolution you want press the spacebar to put a star in that box click the resolutions that your monitor can do  
when your are finished and bback to the prompt type 
sudo reboot 
 you should be better from there 

dont forget to tell us how it works for you im a newb and i could be wrong but it hs worked for me

---

### Post by bigaLOL on 2008-01-09
Thanks Rex...i just booted in recovery mode and did what you told me..i just when with the defaults that it gave me..and i only checked MY resolution that i wanted and i did sudo reboot..as i rebooted..like idk if its usual or not but my screen is completely black until the login screen..and at the login screen im like whoa. ok this is gonna work...cause the resolution looked normal..and i did it so i dont have to enter pass to login ..so as my desktop started up..i noticed that the top part of the panel was still cut off..and the small black bar on the bottom of the screen...

:(

---

### Post by bigaLOL on 2008-01-10
lawl :| ):P

---

### Post by bigaLOL on 2008-01-11
MAYBE I just need a new monitor?! :o HM LOL but i wanna keep it i dont want a new one. owned.

---

### Post by bigaLOL on 2008-01-13
:lolflag:

---

