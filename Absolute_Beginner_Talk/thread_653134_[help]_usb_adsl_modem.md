---
title: "[help] usb adsl modem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by agent pink on 2007-12-29
ok, so i just installed Gutsy Gibbon on my lappie and everything went perfect but one thing, internet... arggghh*$&(#<%&@!!!

know i shouldn't post here but i lost myself on that network and wireless forum, don't understand a bit of it. i don't even know how to connect using dialup :(

so, i have this zte zxdsl852 usb adsl modem. after googling, lurking here, ubudsl, and [[COLOR="DarkGreen"]here[/COLOR]]("https://help.ubuntu.com/community/UsbAdslModem/AccessRunner") i got it worked all right (green light blinking for a few second and then stop), but then what???

in my other legacy OS :p, after i got that green light stop blinking i just i went through standar dialup procedure, dialing 00000000 with username and password, that's it.

now what should I do in ubuntu?
pls...

---

### Post by ARhere on 2007-12-29
Sorry, but I don't have enough information to remotly help you.  You said...
> after i got that green light stop blinking i just i went through standar dialup procedure, dialing 00000000 with username and password, that's it.???
1.  What is the standard dial-up procedure in your old OS?
2.  The number you dialed was all 0's?  or was that some step after dialing an ISP's number?

If you have the hardware working, then goto apt-get or "Add/Remove" programs and install a dial-up manager.  There should be a bunch available.  After that, it is between you and your ISP.

-AR

---

### Post by agent pink on 2007-12-29
> **ARhere said:**
> 
1.  What is the standard dial-up procedure in your old OS?
2.  The number you dialed was all 0's?  or was that some step after dialing an ISP's number?
yeah, just like that, like the standard dialup and the number is 00000000.
> 
If you have the hardware working, then goto apt-get or "Add/Remove" programs and install a dial-up manager.  There should be a bunch available.  After that, it is between you and your ISP.

ok, and what/where is this dialup manager?
kidding :D
no, i really don't know but well, it doesn't sound that hard to find out.

ok i'll try and i'll report back here
thanks :)

---

### Post by agent pink on 2007-12-29
oh well...
i went mad installing god-knows-what ppp, pppoe, isdn, dial, blah blah
and yeah i got my fingers wet, terminal, editing files (nice to know that everyting in linux is human readable :)) and this and that (maybe i should reinstall ubuntu, gee...)

so i went back to [[COLOR="Blue"]ubudsl[/COLOR]]("http://ubudsl.ubuntu.pl/index_en.html"), that coolstuff made my hardware worked okay after all but my country wasn't on the list, becouse, after getting my fingers wet, i knew that that country list is just a typing away.
yup, it's on /opt/ubudsl/addressbook.xml and well...

YEAAAAAH WOOOOOOOHOOOO!!! i'm posting this one from ubuntu, first time i see the outside world from ubuntu :D

and **ARhere**, thx :)

ps: how do you mark this thread as [solved]? anyone?

---

### Post by ARhere on 2007-12-30
Hehe.. glad to help

On the top of this post you can click a "Thread Tools" drop down menu and select "Solved"

-AR

---

### Post by adrian5632 on 2008-01-01
Hi
I'm the UbuDSL developer. **agent pink**, could you tell me the name of your ISP (or service), country, protocol and VPI/VCI? So I could add it to the list and it'll be available in the next release by default.

---

