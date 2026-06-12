---
title: "Dial-Up help..."
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Patrick-Ruff on 2006-01-28
hey all I just installed ubuntu yesterday..  WHOLE new operating system for me.  hell I knew windows xp like the back of my hand.  anyways, I downloaded that ltmodem thing and I haven't a clue how to get it to work.  can anyone here use dummy terms and walk me through it? I only have dialup internet.

---

### Post by Patrick-Ruff on 2006-01-28
omg... nobody knows or... nobody even thought a question such as this was even worth they're time I need the internet to learn the operating system. please  helP!

---

### Post by Stereotypical Rage on 2006-01-28
It's the weekend dude, settle down. Many people have lives on the weekends. I'm sure someone will help you if you're wait long enough.

---

### Post by erikpiper on 2006-01-28
You cant expect people to answer in 5 mins..... And not many here use dialup. I would help, but I am on a LAN with dsl instead of dialup.

---

### Post by stanz on 2006-01-28
[quote=Patrick-Ruff]omg... nobody knows or... nobody even thought a question such as this was even worth they're time I need the internet to learn the operating system. please  helP![/quote] 
:rolleyes: Yeah.. When we ask for help~ { one newbie, to another } we need to be searching around, for answers ~ while we wait.
Did ya spend time here: [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")
Have ya been here: [http://www.linmodems.org/]("http://www.linmodems.org/")
Have ya done it ALL over ~ 5x ?
Where are ya gettin' stuck?
Are ya having fun yet?

Can you supply more info~ what kind of modem ya got? ~ Little things like that! 
I've been trying, for a few days- myself...:-k... and also, - have left, the lazy 'point & click' world, behind...well, kinda. :-#
The training wheels are off...figuring how to find, our balance~ is up to us..
I'm glad, these folks offer their time & help...to us newbie's!  
Don't give up!!   \\:D/

---

### Post by Patrick-Ruff on 2006-01-28
ok yeah I suppose I was being a bit vegue... but those first 2 replys were absolutly no help at all. in any way whatsoever.  anyways, the modem I have is...*waits as windows boots up* Conexant D110 MDC V.9x Modem.  I'm running on Ubuntu Hoary Hedgehog 5.04. I need to know a few things, I've tried applications like LTModem but I couldn't get it to work (major noobie here)  and I also tried installing some drivers but thats a pain.  whats also PRETTY messed up is... my ONLY source of internet is dialup, and the installer wants to access the internet to get the packages (this is the free one that goes into the full) if I were to download the full version that would work right out of the pack it would slow my connection (the free one) the one that costs money is the full one... pertty fucked up eh?  I'm sure theres some other alternatives. perhaps someone could walk me through the usage of LTModem.  also, on the modem I can't ever autodetect it.  I think this may have something to do with the drivers. because when I run the driver install it detects the modem but then it wants to go online to install it.  also, on the Networking,the modem thing it has a button that says "activate" is that supposed to attempt to dial the modem or something?  and YES I have spent alot of time at those 2 sites.  the wiki and linuxant.  I tried getting the drivers from there and I think I got a full version but it limits me.  there MUST be a way for me to get online to install these drivers or something.  via dialup. please help.



specific enough?

-Patrick

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=Patrick-Ruff]when I run the driver install it detects the modem but then it wants to go online to install it. [/QUOTE]
I am not sure whether that driver needs to be compiled, so (just to make sure you don't get stuck bc you don't have a compiler) insert the install cd and ```
sudo apt-get update
sudo apt-get install build-essential linux-headers-'uname -r'
``` 

I used that ltmodem thing once, for five minutes, on an unsupported winmodem (just to try). I remember that it uses a browser to get the modem working, but the browser does not connect to the internet. it connects to  the local host (your own computer, 127.0.0.1) to some port. have no idea why and how. did you try going all the way with that? if you did, what was the result? any error messages (detailed)? 

for dial up, configure and use wvdial (at the end of the dialup wiki you mentioned -in my signature). the networking thingy doesn't work for my winmodem either. 

attach your modemdata.txt here as well.

---

### Post by Patrick-Ruff on 2006-01-29
again...major noob. also, I do NOT have a cd for my modem.  this is a dell computer so all the drivers were pre-installed.  and the drivers that are on the CD are EXE's and are specially configured by Dell. also, I couldn't ever figure out how to run LTModem.  instructions please? also, I don't know where the modemdata.txt is

-Patrick

---

### Post by Patrick-Ruff on 2006-01-29
be back in 30 mins.

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=Patrick-Ruff]again...major noob. also, I do NOT have a cd for my modem.  this is a dell computer so all the drivers were pre-installed.  and the drivers that are on the CD are EXE's and are specially configured by Dell. also, I couldn't ever figure out how to run LTModem.  instructions please? also, I don't know where the modemdata.txt is
[/QUOTE]
At this point, I've got to refer you back to the wiki. the second link in my signature. In the wiki, follow the instructions on how to use scanModem tool. it will create a modemdata.txt. Read it, compare it with what the wiki says, and if does not make sense, attach modemdata.txt (as a file) in here.

PS. forget about the windows drivers of winmodem. they won't work in linux, sorry. but don't throw out the cd either ;)
PS2. Out of curiousity, if you don't know where modemdata.txt is, how did you figure out you have an ltmodem? this is just me being curious, no offense intended.

---

### Post by blud on 2006-01-29
I have only just gotten over this problem myself as I have dialup and installed Ubuntu yesterday and trust me it's alot of effort to get dialup working nothing like windows alot harder (ok for me it is I've used windows all my life). first up I really recomend buying an external modem downloading drivers for internal modems with dialup isn't alot of fun I tried. Make sure the modem has a serial port connection the first one I bought connected via a USB port there just the same as internal modems apperantly so after a few mistakes I ended up with a modem from Office Works for a mere 100 bucks (Australian Dollars not US) 
Once you've got your modem connected to your computer right click on a panel go to add new icon there should be a dial up modem option in there somewhere   add it to your panel click on the icon and go to properties mark the checkbox this device is configured fill out your service provider details then go to the modem menu and autodetect your modem click ok and your done. Now to connect to the Internet click the icon and go to activate. Internet and the settings are always there when i did it some other way that someone else told me each time i wanted to connect I had to fill out all the details at that annoyed me. 
Hope it helps.

---

### Post by Patrick-Ruff on 2006-01-29
I downloaded LT modem from a certain site. (I forgot where exactly.) also, one of the installers from linmodems.org works BUT!!! they are cheap bastards and they want money for a license key.  any way to crack it or get it for free?  since this is REALLY not cool of them to do that.

---

### Post by Patrick-Ruff on 2006-01-29
nah, I know enough to the point where I wont waste money on a modem. I CAN get my modem to work the drivers are just a pain in the *** to get. the full version wants money.  the regular ver wants internet... I mean SERIOUSLY this is bull lol.  and yeah I'm a windows expert but I wanted to try something new.

I installed it yesterday as well.

---

### Post by Patrick-Ruff on 2006-01-29
Anyone?

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=Patrick-Ruff]Anyone?[/QUOTE]
Referring to my post #10 in this thread, did you do it (scanmodem) and get the modem to work and connect. if not, attach modemdata.txt only if you couldn't make sense of it. 

if the modem is now working, no one in here can give you advice on illegal issues (hacking a driver that has to be paid for). you will have to:
-buy the driver
-keep the limited driver
-buy a hard modem (has serial connection to computer)
-switch to broadband and use router...

---

