---
title: "Linux Users Groups etc"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-03
I am a recent linux "convert" or what not and switched because of the open-source programming/modding uses as I am reading on items like this, I really need to talk to anyone really experienced in linux and programming and "hacking", especially programming in python as this is the language I am learning. I am also interested in finding a LUG around where I live which is near Bloomington Normal, Illinois, any help in both of these subjects is definitely thanked especially as I see how it could be a "burdon" to anyone who helped, but contrary I am a fast learner and will make every attempt at being faster, thanks in advance.

---

### Post by Sarteck on 2007-12-03
Heh, welcome to Linux, Phiber.  What have you done with Python?  You coming over from Windows?  How long have you been on Linux?

---

### Post by mellowd on 2007-12-03
You can talk here or are you asking for face to face contact with someone?

---

### Post by Phiber_tek on 2007-12-03
> **Sarteck said:**
> Heh, welcome to Linux, Phiber.  What have you done with Python?  You coming over from Windows?  How long have you been on Linux?

With Python I'm still just starting, I haven't done anything substantial yet but I'm working really on comprehending programming still, coming from Vista there isn't much hacking or modding that is possible software wise which is why linux appealed to me.

Yes coming from windows, the main machine I use is still running XP because I need it for steam and Counter Strike and such, unless there is a substitute that makes those possible on Ubuntu, in which case I'll go pure Ubuntu; but the machine I am installing Ubuntu on used to run Vista so that's where that one is coming from.

Umm, I've been on Linux for not quite a half hour now lol.


And, in response to you mellowD I think just talking here is good for now but if I can find a LUG or someone experienced in my area that would be fantastic too as I do learn more by interaction with the target software or hardware better than I do reading about it, which is why Python is proving to be simple as the tutorial is "hands-on"

---

### Post by mellowd on 2007-12-03
As far as I know you can run Counter Strike through wine

---

### Post by Dr Small on 2007-12-03
I found these two LUGs in Illinois:
[http://www.luni.org/](http://www.luni.org/)
[http://www.silug.org/](http://www.silug.org/)

---

### Post by Phiber_tek on 2007-12-03
> **mellowd said:**
> As far as I know you can run Counter Strike through wine



Sweet, thanks, I'll have to look into that after I get a feel for the GUI.


Thanks for the LUG info, their a little to far from home but i did join both so maybe if there are some meeting movements or anything like that I'll have to attend, but thanks again.

Also a question:  Once I start completely figuring out Linux and Python, as I develop programs will I actually be able to complete that program or modification or whatever I make and run it on the computer, I know thats a really noobish question but I really find that interesting, thanks.

---

### Post by mellowd on 2007-12-03
> **Phiber_tek said:**
> 
Also a question:  Once I start completely figuring out Linux and Python, as I develop programs will I actually be able to complete that program or modification or whatever I make and run it on the computer, I know thats a really noobish question but I really find that interesting, thanks.

You sure can.

---

### Post by teryowen on 2007-12-03
how do you go about finding LUGs?

---

### Post by Dr Small on 2007-12-03
> **teryowen said:**
> how do you go about finding LUGs?
I just googled it.

---

### Post by teryowen on 2007-12-03
> **Dr Small said:**
> I just googled it.

ah i forgot about google there for a second have to remind myself again that Google has almost everything if not everything.

---

### Post by Phiber_tek on 2007-12-03
Alright so I just came to first Login and I've never had a system that requires you remember the User Name and the Password, so I only remembered the password, is there a Password recovery or other tool available and is there a way to make it so that you only have to remember password?

---

### Post by teryowen on 2007-12-03
boot of a live cd and check this out on your ubuntu partition

/etc/passwd

view that file your user name should be somewhere in there.

then reboot without the live cd and login from there go to setting admin or preference and there will be an option for log on or log in and in there you can change how the login interface looks (one of them being you can see all the users)

EDIT: look for a line that looks like this
```

Joe:x:1000:1000:Joe,,,:/home/Joe:/bin/bash

```
and from that line you can see the username is Joe

---

### Post by Dr Small on 2007-12-03
Try looking somewhere on the login page. Your hostname (as it should say) should be the same as your username (or near it) unless you changed it at installation.

Also, you can boot up into recovery mode and run:
```
cat /etc/passwd
```

And find your username in there.

Dr Small

---

### Post by meierfra on 2007-12-03
Or  pick recovery mode at the grub menu. This will boot you into command line mode.  Type  "ls /home".

---

### Post by teryowen on 2007-12-03
> **meierfra said:**
> Or  pick recovery mode at the grub menu. This will boot you into command line mode.  Type  "ls /home".

Wow that solution is x1000 better than mine :lolflag:

how did i even think of my first idea :confused:

---

### Post by Dr Small on 2007-12-03
> **meierfra said:**
> Or  pick recovery mode at the grub menu. This will boot you into command line mode.  Type  "ls /home".
Yeah, that would probably do better than my solution too :D

---

### Post by Phiber_tek on 2007-12-03
Alright I suppose I'll use the second solution then because I cant seem to find it in the specified file that you guys mentioned earlier...so I'll give the other way a shot.

---

### Post by Phiber_tek on 2007-12-03
Alright I found it, lol, thanks for that help!  Now I was wondering if any of you have or knew how hard it is and how to install beryl on Ubuntu 7.10 I was looking into that this afternoon before I installed Ubuntu and couldn't find any links on the beryl website as to how to install it, well I did find one but it was a dead link so I'm not sure what to do about that.

---

### Post by Dr Small on 2007-12-03
You are supposed to use Compiz-Fusion on 7.10 because Beryl is no longer supported, nor is in in the repositories.

---

### Post by Phiber_tek on 2007-12-03
Alright, man this is a lot different from what I'm used to and I have one more question for the night here's the setup:  I have a cable modem hooked up to a netgear wireless router encrypted with 128-bit WEP and I click the neat little network button up in the status bar and it pops up the window asking for your wireless security type, pass phrase and Authentication, I chose WEP 128-bit pass phrase, enter the passphrase and leave it on open system in authentication and it just loads for a while then pops the screen back up...so what should I do, I'm left with no network connectivity at all.

---

### Post by mellowd on 2007-12-03
open a terminal and type 

```
ifconfig
```

paste your results, at least your IP and gateway

---

### Post by Phiber_tek on 2007-12-03
Hold on I need to find an ethernet cable to get my laptop wired into the router...

---

### Post by Phiber_tek on 2007-12-03
Is there any way to copy and paste what I see in terminal because I'm not sure what is what in the box of information it gives me so I'm going to attempt to copy+paste what it spits out to me.

---

### Post by Phiber_tek on 2007-12-03
tyler@Phiber-tek1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:89:30:E3  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe89:30e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1856038 (1.7 MB)  TX bytes:230301 (224.9 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:9E:DD:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5250 errors:177 dropped:177 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:11780 (11.5 KB)
          Interrupt:16 Base address:0xa000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17480 (17.0 KB)  TX bytes:17480 (17.0 KB)
alright I guess I figured it out so here you all go...

---

### Post by Phiber_tek on 2007-12-03
is that bad or how come no one is responding lol...

---

### Post by mellowd on 2007-12-03
RX packets:5250 errors:177 dropped:177 overruns:0 frame:0
a lot of errors here, not good.

Could you paste the contents of this file:

/etc/network/interfaces

---

### Post by Phiber_tek on 2007-12-03
All it says is exactly as follows:

Auto lo
iface lo inet loopback

---

### Post by mellowd on 2007-12-03
Unplug the lan cable, try and connect to the wireless and then do an ifconfig again. Save the results to a file, reconnect the lan cable and paste the results here.

---

### Post by nikoPSK on 2007-12-03
You can also help in LoCos...

---

### Post by rexxxlo on 2007-12-03
> **Dr Small said:**
> I found these two LUGs in Illinois:
[http://www.luni.org/](http://www.luni.org/)
[http://www.silug.org/](http://www.silug.org/)

wow thanks i didnt know such a thing existed i was reading thinking LUG what is that so i clicked the link and there is one near me thanks i joined and i  might see what it is all about

---

### Post by Phiber_tek on 2007-12-03
> **mellowd said:**
> Unplug the lan cable, try and connect to the wireless and then do an ifconfig again. Save the results to a file, reconnect the lan cable and paste the results here.

I can't do this right now as I'm short Ethernet cables because the 1 extra I did have seems to have shorted out or something (lights dont come on) but I'll pick a couple up at work tommorow and post the results first thing when I get home at about 4:45, sorry I can't do it now Ive got 3 cables, 1 run to a CS dedicated server, 1 run to my desktop which is downloading a whole bunch of stuff and 1 run to moms laptop which she is using and the 4th doesn't seem to enjoy working; so I'll post the results first thing when I get home. Thanks so much for the help thus far...

---

### Post by Phiber_tek on 2007-12-04
Alright I came to school this morning and am sitting here using their wifi which is unsecured in the Guest-Net, so I now know that it works if you just use un-secured but I would rather keep my network secure because I live in the city with a ton of people around me...

---

### Post by Phiber_tek on 2007-12-04
Alright well, I feel like a noob now, I came home and feeling rather experimental I switched 128-bit encryption to HEX 128 and now I'm posting this from the Linux machine so...problem solved, thanks for all the patience...now just to get compiz running nicely...

---

