---
title: "Can't Start X &quot;no screens found&quot;"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by call3 on 2005-08-02
Hello. 
I've got a problem here. i have installed ubuntu but i don't get X to work on it.
the errorlog give me the the clue "no screens found" 
and i really haven't got a clue to witch drivers i need to use or how to change them
The grafik card is a 
ATI Technologies Inc Rage 128 RF/SG AGP
so i bet i need to use some ATI drivers, but how do i get in to the config / config it ? 

Thanks in advance
//calle

---

### Post by jasmuz on 2005-08-02
These are the directions you need to take:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28Binary%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28Binary%29)

---

### Post by call3 on 2005-08-02
will try. thx alot

---

### Post by call3 on 2005-08-02
Hmm Have used the guide. but still the same error... anyone got any other idee whats wrong?

---

### Post by Footer on 2005-08-02
Before you installed Ubuntu, did you try the live CD?  Did you have a display then?  If so, grab the appropriate X config files (xorg.conf) from there and load them onto your hd and you should be good to go!

---

### Post by call3 on 2005-08-02
GOOD idea... Haven't got the live cd but i worked with the whoopix live cd. but i'll donwload the cd now.. Thanks alot! :D

---

### Post by call3 on 2005-08-02
Noo, the live cd dosen't work... Weard ubuntu dosen't work but whooix and knoppix does :(

Whats the big differens in Knoppix VS ubuntu.. (in X case?)

---

### Post by Footer on 2005-08-02
I'm not sure what the X differences are between Knoppix and Ubuntu but ...

I did a quick search on your error message (no screens found) in the forums here and came across this post:

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=screens+found](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=screens+found)

Try running through that one and see if you can get it to work (it's long!).

Good luck and let us know how it goes.

 :)

---

### Post by super on 2005-08-02
open your xorg config:
[FONT=Courier New]sudo nano /etc/X11/xorg.conf[/FONT]

scroll down to the 'Monitor' section and under your 'Identifier' you should have a section that looks like this:
[FONT=Courier New]	HorizSync	31-96
	VertRefresh	55-160[/FONT]

if you don't have that you probably need to add it with your moniter's refresh rates and frequency values. add them and you should be good to go.

***do not use the above values*** you should be able to find the info on the back of your monitor

to save and exit press:
CTRL+X

---

### Post by call3 on 2005-08-02
Problem solved. The versa drivers worked :P

Thx alot everyone

---

