---
title: "[SOLVED] Cant connect to internet,Need programs only have terminal access"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by gumpontheweb on 2008-02-01
Please understand that I am a total newbie but have tried for loits of hours now to fix this...
When I enter if config it finds a ethernet connection I have hooked up.
I only have a failsafe terminal access with a messed up system! jaytek was having me go through and check stuff but I think that is useless at this point!
If I have my source file correct AND I have something being detected in eth0(with 20 intterrupts)...I tried running lynx but I don't have it, Or MANY OTHER important programs
What should I do next to get wireless internet working...
If you want to read my prior thread it is :here[http://ubuntuforums.org/showthread.php?p=4246911#post4246911]("http://ubuntuforums.org/showthread.php?p=4246911#post4246911")
The thread says I don't have anything working

---

### Post by oedha on 2008-02-01
can you login from your terminal.....
what installation do you have ? or where did you install from ? 


~E~

---

### Post by gumpontheweb on 2008-02-01
when I log in I get put into a failsafe terminal. I have tried apt-get and tons of other stuff...
It has boiled down to  the output of ifconfig eth0.
I did that and see that it detects my hardware. Do I need to type it out. I type slowly!

---

### Post by gumpontheweb on 2008-02-01
Xserver doesn't work either.
It came up yesterday and didn't work, NOw it doesn't come up at all...

---

### Post by deadmnky on 2008-02-01
i dont know if this helps but i had a simliar problem. it was solved by resetting my modem. i have yet to read your other post but that is worth a try maybe. it may be a dumb suggestion but it worked in my case and that is the only knowledge i have as i am new to linux as well

---

### Post by gumpontheweb on 2008-02-01
i just did```
sudo ifup eth0
```
I got back no errors.
I got an ipadress? How can I download my entire ubuntu??

---

### Post by gumpontheweb on 2008-02-01
> **deadmnky said:**
> i dont know if this helps but i had a simliar problem. it was solved by resetting my modem. i have yet to read your other post but that is worth a try maybe. it may be a dumb suggestion but it worked in my case and that is the only knowledge i have as i am new to linux as well
It's much worse than that!!!!
My modem works and all that stuff! It is the mai operating system having files and stuff moved and taken out! that is the easiest way to tell you.
synaptic was used to put in adept. Then.. manually move around files...
I need to download stuff like the desktop but wont get anything


I think I got synaptic to work after doing ifup!!!!!!!
NOPE it looked like it was downloading but froze my computer!!!! What should I do????

---

### Post by jan quark on 2008-02-01
some input pls
and delete the exclamation marks from you active vocabulary pls:)

pls post the results of the following terminal commands
```

iwconfig
```
```
ifconfig
```
```
lspci
```
```
sudo iwlist scan
```

---

### Post by gumpontheweb on 2008-02-01
> **jan quark said:**
> some input pls
and delete the exclamation marks from you active vocabulary pls:)
Sorry, just frustrated.
> **jan quark said:**
> 
pls post the results of the following terminal commands
```

iwconfig
```
lo    no wireless extensions

etho   no wireless extensions

eth1   IEEE 802.11g   SEEDI:off/any
           Mode managed....& MORE,say if needed
Cted   power amanagement: off
       link quality:0 Signal leve: noise level:0 
       Rxinvalid nwid:0...& more


> **jan quark said:**
> 
```
ifconfig
```
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:11234 errors:0 dropped:0 overruns:0 frame:0
TX packets:5714  errors:0 dropped:0 overruns:0 frame:0
collisions:0 txquelene:1000
Rx Bytes:15803510 (15.0MB) Tx bytes 409659 (400KB)


eth1 Link encap

> **jan quark said:**
> 
```
lspci
```

up running
> **jan quark said:**
> 
```
sudo iwlist scan
```
IS taht what you needed to know???
IT sees them there. the files are messed up so it doesn't work?

---

### Post by gumpontheweb on 2008-02-01
I jst tried to get stuff again and I think i am getting ubuntu-desktop
Notice no exclamations

---

### Post by gumpontheweb on 2008-02-01
GOT BACK MY DESKTOP!
ifup eth0 thenthe commonads you gave me got smoething to let me
sudo apt-get install ubuntu-desktop.
now I need to get anything else I need. Is there a way to do that?
If I don't ghet an answer I will start a new thread tomorrow.

---

