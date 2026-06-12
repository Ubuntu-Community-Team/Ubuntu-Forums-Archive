---
title: "yea yea another &quot;can't connect to the net&quot; =)"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by aquaeyed on 2007-04-07
hi to all. it's second day i am with ubuntu (my first linux =) ) and i can't to connect to the net too, i undestand it's very often problem to newbie. i tried to find the answers but failed, so i ask for help.
my cable usb modem is working fine at windows xp, it's also connect well in ubuntu 6.10 (i think so) i can to connect to internet supllyer compuny (bad bad english =( ) to downloading the connector for windows and skrypts for linux ( 212.143.205.211) i tried to do what is wrote to do in install text file but it don't work well, something it don't open it says something denied i don't know... so it is all i think, i'm from israel and if someone is too so please help with netvision linux skrypt, if u not, plz help too =)

and one strange thing, when i turn off from ubuntu and start with xp at first time (and sometimes at second too) my mouse(ps/2) and usb webcam don't working at all, so i must to turn off (reset did't help) the computer and turn on again for working propertly, why it is?
sank u again.

---

### Post by mikeyphi on 2007-04-07
> **aquaeyed said:**
> hi to all. it's second day i am with ubuntu (my first linux =) ) and i can't to connect to the net too, i undestand it's very often problem to newbie. i tried to find the answers but failed, so i ask for help.
my cable usb modem is working fine at windows xp, it's also connect well in ubuntu 6.10 (i think so) i can to connect to internet supllyer compuny (bad bad english =( ) to downloading the connector for windows and skrypts for linux ( 212.143.205.211) i tried to do what is wrote to do in install text file but it don't work well, something it don't open it says something denied i don't know...

Depends on how you are installing...the "denied" might be that you didn't use 'sudo' before the install command?
Can't help further without more details....

---

### Post by aquaeyed on 2007-04-07
ok i will check it now, or i tiered to swap between xp to ubuntu =). sanks anyway.

---

### Post by aquaeyed on 2007-04-07
and..... i tried and of course it didn't work 
:( 
i copied my work so check it plz, if i shared something security important plz tell me =)
and by the way the strnge mouse thing happend again : first windows running usbcamera and ps/2 mouse didn't work, after shout downing and turn on again everything work fine, ideas? =)

---

### Post by aquaeyed on 2007-04-07
guys, i really want to study ubuntu but i can't do it without internet in it, i can't swap every time, so please, if someone can help me, don't be lazy, look at this post for 5 min. thank you very much. =):)

---

### Post by Maestro23 on 2007-04-07
> **aquaeyed said:**
> guys, i really want to study ubuntu but i can't do it without internet in it, i can't swap every time, so please, if someone can help me, don't be lazy, look at this post for 5 min. thank you very much. =):)

.

---

### Post by aquaeyed on 2007-04-08
?

---

### Post by aquaeyed on 2007-04-08
it is my progress :confused: 
ok forget about usb cable modem i link it with ethernet. i did again what install file says to do it in attach file here and now what? where is link for connect or i need to write command in terminal for connecting? and it is from first downloading link (see the picture). thank u.

---

### Post by mikeyphi on 2007-04-08
Hi again!

From the picture it looks that you are trying to install a Red Hat file - these are not directly compatible with Ubuntu. If you have downloaded the Red Hat package and successfully opened it you should have a file ending with .rpm
If true then use Synaptic to download and install the package 'alien' - then open a terminal and type
sudo alien -d (name of file).rpm

If you do not have a .rpm file - say what you got from that website.

---

### Post by oilchangeguy on 2007-04-08
does your computer have an ethernet connection? if so use that instead of usb. if not ethernet cards are cheap. get one. and the ethernet connection is faster than using usb.

---

### Post by lpmurder on 2007-04-08
How about using the code:
[COLOR="Red"]sudo pppoeconf[/COLOR]

---

### Post by aquaeyed on 2007-04-08
guys, thanks for responding.

may be i don't undestanding what about you talking or we speak about two different things. 

i have cable ethernet modem now. it's working ok on xp and i can connect to internet supplier  site for downloading scripts for linux. this is a link cables.netvision.net.il (212.143.205.211) . 
in the windows i had downloaded dialer file and each time i connect to net i must first to run it. i don't know if in linux is similar way for lunching internet connection or it totally different way. i understand that there is no such thing install dialer file  and there is script that i must open/create/something else for creation dialer shortcut. i tried to do exactly what was said in install.txt file in t2lp script - the first one - not for red hat, and my progress was said in previous threads. and look at attached  files, i was copied the terminal text too.

so my question is not how to connect modem or if it is working but how to create the similar windows dialer and to write in it my supplier  ip, my username and password for connecting.

thank u for helping. :)

---

### Post by aquaeyed on 2007-04-09
ghk ghk ....

---

### Post by kahrytan on 2007-04-09
Just plug the cable modem into a Router. Router makes connecting to the internet whole lot easier. Just set it up and forget it. Most major brand routers have step by step setup wizard that is browser based.

---

### Post by aquaeyed on 2007-04-09
yea, but i have a little problem , i have no any router. just pc and cable modem.

---

### Post by aquaeyed on 2007-04-09
](*,)

---

