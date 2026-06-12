---
title: "Problems with Gnome ppp &amp; Kppp"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-11-22
Ubuntu 6.06LTS, Dapper
I can't get gnome ppp or kppp to recognize modem, keep getting msg that: "No modem was found on your system".  Modem is ext. serial modem @/dev/ttyS0[com port 1]  Am presently using "Network settings" to institute dial-up connection, it was autodetected immediately & interface properties/general tab shows "device: ppp0".  Can someone help me out of this quamire? ](*,)

---

### Post by PennYanPete on 2006-11-22
Hi Randy

I get that same message but am able to connect. The only distro that detects my modem (TRENDnet tfm-560x) so far has been Xandros. 

Are you able to connect, or are you just concerened about that message? I am new to Ubuntu,but i'll help if I can

PYP

---

### Post by randiroo76073 on 2006-11-22
Hi PennYanPete, thanks for reply. Question, did you sneak in and copy my modem, thats what I run too.LOL!  Haven't tried yet, will give it a go.  Puppy linux[live cd] recognizes it too, but DSL won't.  Some others that won't: Kanotix,Kubuntu,Mephis,PC linux & Freespire.  Unbuntu does, but only from "Network settings".  If I can get 1 of the ppp configs to recognize the others should be easy to get :)

---

### Post by PennYanPete on 2006-11-22
randiroo...

Up to this point the only distro that detected my modem was Xandros. I just configure and away we go.

Ubuntu...PCLOS...FC4...Mepis...Mandriva...Xandros...Red Hat Have all worked for me. The only bump I had was on my GF's Compaq,it has onboard eth0. Seems to me there was some sort of conflict so I just disabled eth0 in bios. (Ubuntu install)

PYP

---

### Post by randiroo76073 on 2006-11-22
I'll try that next, I tried to connect from gnomeppp, got error msg : Unable to open modem. Got that msg in other distros too.

---

### Post by PennYanPete on 2006-11-22
I believe a lot of people think if the modem is not detected it just will not work. I have found that to not be true. As I said, just configure and enjoy.

---

### Post by randiroo76073 on 2006-11-22
Well that kinda worked, in that autodetect finds modem now, but when I connect thru gnomeppp I can't get it to stick, it keeps losing the connection after about 1 min & I have to fall back to "Network settings", get 1 solved and another crops up LOL!  Gonna boot into other distro's and see what happens there :)

---

### Post by PennYanPete on 2006-11-22
Is there anything other than modem displayed in Network settings? As I stated above about eth0, I think the system detects eth0 and configures it, creating a conflict. I had the same problem dropping the connection until I disabled it.

---

### Post by eriefisher on 2006-11-22
I too have the trendnet 560. It's hooked to a compaq desktop. If I query the modem I get "modem busy" or "cannot find modem". If I try to connect providing everthing else is configured (kppp) everthing is good. One thing I found was in /kppp/peers you have to uncomment noauth. As for the conflict with eth0, I have also encountered this but overcame it buy setting eth0 to static. Hope some of this helps.

eriefisher

---

### Post by PennYanPete on 2006-11-22
Hmm...set eth0 to static. I'll remember that, thanks for the tip.

PYP

---

### Post by randiroo76073 on 2006-11-22
Okay, I finally got some screenshots of stuff, may help.
Log file from gnome-ppp #1, 2-5 are Kubuntu[Kanotix,Mephis are same] shots of modem config.  I'm really lost now, any/all suggestions welcome :)  I did go into bios and disable my onboard ethernet, only thing that shows is modem.

---

### Post by randiroo76073 on 2006-11-23
Still having same problem, have checked everything I can think of, need some help.

---

### Post by eddie57 on 2006-11-23
HI I had the same problem with my external modem. I have an actiontec which has a serial and a usb port. gnome ppp would detected it through the usb port but not the serial port, even though the pppconfig utility would detect it through the serial port but not the usb port. Go figure. I don't know if your modem has a usb port, but if it does give it a try

---

### Post by randiroo76073 on 2006-11-24
Waaa, mines only serial, I'm still muckin around & reading, got to be an answer somewhere :)

---

### Post by eriefisher on 2006-11-25
For KPPP try this:

kdesu kate /etc/ppp/peers/kppp-options

you should see  #noauth

remove the # and save and close and dial

---

