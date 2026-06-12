---
title: "I can't do ping or traceroute"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-01-28
I have a problem i can't ping traceroute any address they are automatically blocked from firestarter firewall

I have reviewsly enabled from firestarter preferences the ICMP filtering option

and i haven't ticked any of the options below the **Allow the following ICMP packet types**

that must means that any of these will be blocked right ???

So after i understood that i ticked the ping,traceroute and MS traceroute but i still can't ping or traceroute any address

Anyone nows where is the problem please help!!!

---

### Post by OffHand on 2007-01-28
```
sudo apt-get install traceroute
```

---

### Post by bscbrit on 2007-01-28
Which firewall are you using?

But, first things first, switch of the firewall, and make sure that you can ping and traceroute the way you expect to.  You may be surprised to learn that some folks have claimed to have a blocking problem but have subsequently discovered that they were using the commands incorrectly!

Then, tell us which firewall you are using and how you have configured it - I'm sure that we can solve the problem.  What kind of connection do you have to the internet - it might be that you do not need the firewall anyway, although if you have recently come from a Windows background then I can understand your reluctance to continue without one, and using one will not hurt your system anyway.  But, if you are connected via a commercial modem/router or using some specific hardware (LiveBox etc) then it might be that you simply do not need the firewall or that the hardware is causing the problem.

---

### Post by fasoulas on 2007-01-28
> **OffHand said:**
> ```
sudo apt-get install traceroute
```

I have already done that

I forgot to say that if i disable the ICMP fitering option ping and traceroute work normaly

---

### Post by fasoulas on 2007-01-28
> **bscbrit said:**
> Which firewall are you using?

But, first things first, switch of the firewall, and make sure that you can ping and traceroute the way you expect to.  You may be surprised to learn that some folks have claimed to have a blocking problem but have subsequently discovered that they were using the commands incorrectly!

Then, tell us which firewall you are using and how you have configured it - I'm sure that we can solve the problem.  What kind of connection do you have to the internet - it might be that you do not need the firewall anyway, although if you have recently come from a Windows background then I can understand your reluctance to continue without one, and using one will not hurt your system anyway.  But, if you are connected via a commercial modem/router or using some specific hardware (LiveBox etc) then it might be that you simply do not need the firewall or that the hardware is causing the problem.

I already said that i use firestarter 
I have 512 Kbits/s ADsl connection

AND if i disable the Icmp filter the commands work perfectly

AND i know how to use these commands i use them every day

---

### Post by bscbrit on 2007-01-28
Sorry, my mistake - you are using firestarter!  I'm just installing it now to check.

---

### Post by bscbrit on 2007-01-28
Didn't mean to cause offence - and I've already apologised for missing the 'firestarter' clue!

---

### Post by kosmic on 2007-01-28
Yes your firewall is blocking that, in a terminal type this :

sudo iptables -L

and post the results here

---

### Post by fasoulas on 2007-01-28
> **bscbrit said:**
> Didn't mean to cause offence - and I've already apologised for missing the 'firestarter' clue!

Ow sorry if i sounded a little angry 

and thnx a lot for trying to help...do u really installed firestarter just fo me

thnx agian and i hope we can find a solution

---

### Post by fasoulas on 2007-01-28
> **kosmic said:**
> Yes your firewall is blocking that, in a terminal type this :

sudo iptables -L

and post the results here

to big to post it here 

Any other suggestions?

---

### Post by bscbrit on 2007-01-28
OK, I've installed firestarter (and sudo apt-get installed traceroute) and the ONLY settings that I have made in the firewall are in the Preferences, I have selected the same ICMP filtering that you have given.  I can ping and traceroute with no problems - have you any other policies or event filtering in place?


EDIT - Corrected typo errors

---

### Post by OffHand on 2007-01-28
> **fasoulas said:**
> I have already done that

I forgot to say that if i disable the ICMP fitering option ping and traceroute work normaly

That's how it's supposed to work.

---

### Post by OffHand on 2007-01-28
Read

---

### Post by fasoulas on 2007-01-28
> **OffHand said:**
> Read

Thats what mine looks like 2

And i can't do ping or traceroute

---

### Post by fasoulas on 2007-01-28
> **bscbrit said:**
> OK, I've installed firestarter (and sudo apt-get installed traceroute) and the ONLY settings that I have made in the firewall are in the Preferences, I have selected the same ICMP filtering that you have given.  I can ping and traceroute with no problems - have you any other policies or event filtering in place?


EDIT - Corrected typo errors

Have u made it like this pic?

[http://ubuntuforums.org/attachment.php?attachmentid=24059&d=1170015880](http://ubuntuforums.org/attachment.php?attachmentid=24059&d=1170015880)

---

### Post by OffHand on 2007-01-28
Dude, you gotta check the ping, pong and traceroute checkbox for it to work with your firewall.

---

### Post by bscbrit on 2007-01-28
OK, put ticks in the boxes for ping, pong and traceroute and all should be sweetness and light again!  :D

---

### Post by fasoulas on 2007-01-28
I ticked ping.pong,traceroute and MS traceroute

The ping works but the traceroute doesn't work

---

### Post by fasoulas on 2007-01-28
:~$ traceroute [www.yahoo.com](www.yahoo.com)
traceroute to [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (69.147.114.210), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *

And keep going

---

### Post by bscbrit on 2007-01-28
OK, at a command line or terminal (Applications->Accessories->Terminal) type:

traceroute [www.ubuntuforums.org](www.ubuntuforums.org)

and let me know what happens...

---

### Post by bscbrit on 2007-01-28
According to your post at 0946 (at least that the time showing on my screen, about 3 minutes ago!) then traceroute is conducting its analysis.  Leave it to run, and it will complete.

---

### Post by fasoulas on 2007-01-28
~$ traceroute [www.ubuntuforums.org](www.ubuntuforums.org)
traceroute to [www.ubuntuforums.org](www.ubuntuforums.org) (82.211.81.186), 30 hops max, 40 byte packets 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  *
 the same thing

---

### Post by bscbrit on 2007-01-28
From the 'man traceroute' page, you will find the following information: 
```


       A more interesting example is:

              [yak 72]% traceroute allspice.lcs.mit.edu.
              traceroute to allspice.lcs.mit.edu (18.26.0.115), 30 hops max
               1  helios.ee.lbl.gov (128.3.112.1)  0 ms  0 ms  0 ms
               2  lilac-dmc.Berkeley.EDU (128.32.216.1)  19 ms  19 ms  19 ms
               3  lilac-dmc.Berkeley.EDU (128.32.216.1)  39 ms  19 ms  19 ms
               4  ccngw-ner-cc.Berkeley.EDU (128.32.136.23)  19 ms  39 ms  39 ms
               5  ccn-nerif22.Berkeley.EDU (128.32.168.22)  20 ms  39 ms  39 ms
               6  128.32.197.4 (128.32.197.4)  59 ms  119 ms  39 ms
               7  131.119.2.5 (131.119.2.5)  59 ms  59 ms  39 ms
               8  129.140.70.13 (129.140.70.13)  80 ms  79 ms  99 ms
               9  129.140.71.6 (129.140.71.6)  139 ms  139 ms  159 ms
              10  129.140.81.7 (129.140.81.7)  199 ms  180 ms  300 ms
              11  129.140.72.17 (129.140.72.17)  300 ms  239 ms  239 ms
              12  * * *
              13  128.121.54.72 (128.121.54.72)  259 ms  499 ms  279 ms
              14  * * *
              15  * * *
              16  * * *
              17  * * *
              18  ALLSPICE.LCS.MIT.EDU (18.26.0.115)  339 ms  279 ms  279 ms

       Note  that the gateways 12, 14, 15, 16 & 17 hops away either don’t send ICMP "time exceeded" messages or send
       them with a ttl too small to reach us.  14 - 17 are running the MIT C Gateway code that  doesn’t  send  "time
       exceeded"s.  God only knows what’s going on with 12.

```

Does that explain the '*' for you?

---

### Post by fasoulas on 2007-01-28
i don't understand what do u mean i was doing that without the ICMP filter the traceroute would work

in firestarter >events tab i have a whole list of blocked packets indicated as traceroute packets

---

### Post by bscbrit on 2007-01-28
OK, we have a communication problem here - in both senses of the word.  

If you turn the firewall off, then traceroute [www.ubuntuforums.org](www.ubuntuforums.org), do you see something different than if you repeat the exercise with the firewall on?

---

### Post by fasoulas on 2007-01-29
> **bscbrit said:**
> OK, we have a communication problem here - in both senses of the word.  

If you turn the firewall off, then traceroute [www.ubuntuforums.org]("http://www.ubuntuforums.org"), do you see something different than if you repeat the exercise with the firewall on?

Yes as i said the traceroute works

---

### Post by bscbrit on 2007-01-29
In post 17 you told us that ping works, and in your last post that traceroute now works.  So, if I have understood everything, you have now got everything working and your firewall installed.  Finished!?

Come back if you have any more problems.

---

### Post by fasoulas on 2007-01-29
> **bscbrit said:**
> In post 17 you told us that ping works, and in your last post that traceroute now works.  So, if I have understood everything, you have now got everything working and your firewall installed.  Finished!?

Come back if you have any more problems.

No u asked if i turn of the firewall the traceroute works and i answered yes nut i still have that problem when i turn it back on

---

### Post by bscbrit on 2007-01-29
Sorry, I misunderstood.

So, before you installed firestarter and you used traceroute it gave you a full read out of each of the hops between yourself and the target URL, but since you have installed firestarter you see what exactly.  Do you see traceroute displaying * * * or do you get nothing at all?

I'm just re-installing firestarter again so I can compare what I get with whatever you are seeing.

---

### Post by fasoulas on 2007-01-29
> **bscbrit said:**
> Sorry, I misunderstood.

So, before you installed firestarter and you used traceroute it gave you a full read out of each of the hops between yourself and the target URL, but since you have installed firestarter you see what exactly.  Do you see traceroute displaying * * * or do you get nothing at all?

I'm just re-installing firestarter again so I can compare what I get with whatever you are seeing.

it only displays  * * *

---

### Post by bscbrit on 2007-01-29
It seems that others have discovered the same problem.

Firstly - it is a known limitation of firestarter.

Secondly, the easy fix is to disable firestarter whenever you want to carry out traceroute, and then switch it back on again once you are finished.  Firestarter is simply doing what it thinks it should.

I'm going to look at a few other firewalls and see if I can identify one that will let you do what you are trying to do.  I'll be back in a while.

---

### Post by fasoulas on 2007-01-29
> **bscbrit said:**
> It seems that others have discovered the same problem.

Firstly - it is a known limitation of firestarter.

Secondly, the easy fix is to disable firestarter whenever you want to carry out traceroute, and then switch it back on again once you are finished.  Firestarter is simply doing what it thinks it should.

I'm going to look at a few other firewalls and see if I can identify one that will let you do what you are trying to do.  I'll be back in a while.

ok thnx for the information

---

### Post by bscbrit on 2007-01-29
I've tried a couple of others but they exhibit similar effects.  Smoothwall seems promising but it is too complex for me to just set it up to test for you.  You might consider giving it a try though....  Good Luck

---

### Post by fasoulas on 2007-01-30
> **bscbrit said:**
> I've tried a couple of others but they exhibit similar effects.  Smoothwall seems promising but it is too complex for me to just set it up to test for you.  You might consider giving it a try though....  Good Luck

OK my freind thnx a lot for trying to help.

I will try it but one last thing... i wonna ask  how can i reinstalll the firestarter maybe the problem will be fixed after that?

or maybe it's bug of firestarter and will be fixxed after the next version comes out

thnx a lot again

---

### Post by bscbrit on 2007-01-30
Firestarter can be easily removed and re-installed using either Synaptic (System->Administration->Synaptic Package Manager) or from the command line:

sudo apt-get remove firestarter
sudo apt-get install firestarter

However, I do not think that it will make much of a difference.  Others have experienced the same 'problem' - in fact, some are quite adamant that this is **exactly** what a firewall should do!  And the solution is fairly simple.  Switch it off for the few occassions that you must use traceroute, and then switch it back on again when you 'need' it.  As I suggested very early on in this thread, if you are already behind a hardware modem/router you are unlikely to see the benefit of the firewall unless you are attacked from within your own local network.  But using one will do no harm other than to interfere with programs such as traceroute from time to time!

---

### Post by fasoulas on 2007-01-30
1 last question 
Will ICMP filtering help protect from something or should i disable it?
I am currenly behind an adsl modem that doesn't have enabled the firewall but it uses a NAT translation

---

### Post by bscbrit on 2007-01-30
I would suggest that you are safe behind your your modem/NAT translation.

ICMP doesn't pose a direct risk.  It can indicate that your computer exists (as opposed to being stealthy) but, assuming that someone then decides to target you, they have to crack your modem and then your linux box first.  I wouldn't even worry about it - in fact I don't.  I have a network of 6 computers all behind NAT/ADSL router.  I am far more concerned about someone breaking in a stealing them than someone cracking their way in from the internet.

Finally, one of the many reasons that people switch to linux is because Windows machines are far more likely to be targetted than a linux box.  For Windows, there are far more people trying to become crackers, they have far more tools available to them (or should I say have far more user-friendly tools available to them!) and Windows is very susceptible to running their bots or trojans if they ever do get in.  Linux is far more difficult to utilise in this regard and, so far, we have seen much less effort in trying to exploit linux boxes.  It may happen one day - but it is very unlikely in the short to medium term.  

If you plan to use your box as a web or mail server with access from the internet then a firewall is essential but, for normal domestic use, it is probably as safe as it needs to be behind your ADSL modem. :D

---

### Post by fasoulas on 2007-01-30
I use my ubuntu box for home use so i don't need that much protection but i like to feel that i have everything under control :D 

What about DOS attacks using ICMP packets?

---

### Post by bscbrit on 2007-01-30
Denial of Service attacks are **usually** conducted against big names either as a way applying pressure (perhaps for extortion etc) or simply to demonstrate to the world that somebody or some group can conduct such an attack.  Although you could theoretically be subjected to such an attack it is most unlikely.  However, your existing firewall was providing perfect protection against such attacks but it is likely that you would still be unable to operate on the internet in any event.  Your available bandwidth would still be significantly reduced

Do you really think that you might be the target of such an attack?  I suspect that your ISP would also be interested if you thought that you might be a target!

But, in real terms, ignore it for the time being.  If you do not advertise your presence on the internet it is unlikely that anyone will pick your IP at random and subject you to a DOS attack.  However, this thread is straying far from my area of expertise and, if you feel that you need more competent advice, either start a thread specifically asking for help in preventing a DOS or pay for professional advice.  I am qualified to provide neither!

---

### Post by fasoulas on 2007-01-31
i made that question just because i am taking a Cisco CCNA course and that day we were disusing about DOS attacks so i wrote that question 

Thnx anyway about your response

---

