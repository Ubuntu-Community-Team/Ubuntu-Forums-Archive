---
title: "pppoe help please"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-22
for the past 3 months i have been posting here 
that i cannot connect to internet in ubuntu thru pppoe
neither sudo ppoeconf works
neither rp-pppoe works
infact it does n't even get installed
nor does i have any oher client that can actually find all access concentrators and list it the way raspppoe does FOR windows.
every time i do a **sudo pppoeconf** i get an error saying
cannot find access concentrator
i feel this is a hight time
n i shud forma my ubuntu partition
coz without inTernet i cannot do anything
n i feel 3 months r MORE THAN ENOUGH
I DONT EVEN EXPECT A REPLY
I JUST CAN'T UNDERSTAND Y I CANNOT RUN MY ADSL CONNECTION IN UBUNTU THE WAY I RN IT WINDOWS
Y IT ISN'T THAT SIMPLE IN UBUNTU?
Y UBUNTU IS NOT ABLE TO TO FIND THOSE ACCESS CONCENTRATORS ???

---

### Post by jualin on 2008-02-22
what internet provider do you have?
I have a ADSL connection as well and the PPPOE session is made directly through the modem therefore the Operating System has nothing to do with it. I have heard of a program called Roaring Penguin for PPPoE connections, maybe you should try it. Also check if you are putting the username correctly. Sometimes it makes a difference if you write jualin instead of [email]jualin@bellsouth.net[/email]. I hope this helps.

---

### Post by jualin on 2008-02-22
in my case, when i try to run the sudo pppoeconf i get the same message that you get, however my modem web based setup manages their own pppoe protocol so I dont need Ubuntu or Windows to do it for me. Are you behind a router?, How about accessing your modem's web based setup through the web browser, maybe that will help.

---

### Post by coolnik6 on 2008-02-23
i cant even access my modem's web based configuratio page
when i type [http://192.168.1.1](http://192.168.1.1)
it says cannot find  the requested server....
but the same thing works in windows like a cham
really i have given up now
i have tried everything
from pppoe to bridge mode to static ip to dynamic ip
but nothing works im my ubuntu distro

---

### Post by spiderbatdad on 2008-02-23
pppoe is not that great. Why haven't you tried kppp or gnome-ppp, or even wvdial?

---

### Post by zvacet on 2008-02-23
Upper right>network applet>manual config>select your modem(don´ tick it just click on it)>properties>select your connection(dhcp or static)>close>DNS tab>delete address you find there and put your name servers>connection tab>tick your modem and window will pop up with  a message configuring network interfaces.When it is finish go to the terminal and type 

```
pppoeconf
```

---

### Post by Shakeysteve on 2008-02-29
To Zvacet
This post is in the Absolute Beginner Talk, could you give more detailed information, as in "upper right" what? Which network applet?
I have the same problem. Ubuntu 6.06 works perfectly. Ubuntu 7.10 just won't connect, though at one stage I could ping any internet address, but browsers would just time out. That is with DNS IP addresses set properly. There is definitely something screwy with later versions of Ubuntu!

Coolnic6 what version of Ubuntu are you trying to use?

---

### Post by zvacet on 2008-02-29
> "upper right" what? 

O.K. maybe my English is little bit broken but I´&#314;l try again.On your upper panel on the right side you have icon(it look like monitors) and that is network applet.Left click on it and you will see message **manual configuration.** Select that and window will pop up with modems.Select your modem.....and do the rest I posted you.If I still don´t explaining well just post and tell me.

---

### Post by Shakeysteve on 2008-02-29
Now I understand it thanks!
OK, now I think I am up to the same stage as coolnic6.
I can ping any internet ip address, and even ping say [www.newscientist.com](www.newscientist.com) and get replies. Yet I still can't get anything through firefox or even synaptic package manager!

Where do we go from here?
Thanks for any help.

---

### Post by suterman on 2008-05-18
Having been a Linux user for all of 10 minutes, I found myself facing exactly the same PPPoE access provider problem. Drove to the office and looked through the forums, thought updating my network card drivers might be the issue...but no, according to Realtek they're included in the kernel. Damn.

But then, back home, wandering through the menus came across system>administration>hardware testing. Ah, what the hell....and believe it or not as soon as the testing of my RTL8139 was complete, the internet lights came on on my modem, and I had internet!!!

Don't know if this will work for you too, but I know you're probably tearing your hair out, I certainly was, I wish you luck

---

