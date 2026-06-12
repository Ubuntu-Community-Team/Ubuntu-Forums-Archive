---
title: "still got trouble with slow internet"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-23
i'll try and give as much info as i can.

the problem :  i can connect to the internet without any problems but when i am on its so slow it makes the connection unuseable, it takes 5 mins to load a web page.

The setup: i have a dual boot of windows xp and ubuntu warty( i hope to upgrade to hoary when the cd's arrive)

The system: i have a p4 celeron 1.7, 512mb ram, 160 gig hard drive, dvd burner, gejore 4 video card. 56 kbs cirrus modem(external)on com port 1


my settings for the internet:ppp configuration utility settings
provider name:provider
name servers dns: dynamic dns
ip number for primary nameserver: i left this blank
ip number for secondary nameserver: i left this blank
authentication:pap (i have tried the others they just disconect straight after dialing)
user name ***********
password************
modem port settings 115200
tone or pulse:tone
dial up number:**************
select modem port: /dev/ttyso(does not automatically detect my modem i entered correct value)
advanced settings: add user:my login name
return to previos screen
finished and write files
exit
in system configuration>networking
modem is detected
account is set with my user name password and dial up number
advanced:start ppp as soon as modem connects is ticked
set modem as default route to the internet is ticked.
set dns servers manually is unticked.
hope i can sort this out so i can update my system

---

### Post by twoseids on 2005-07-23
Did you get your driver through [www.linuxant.com?](www.linuxant.com?)  Cuz if you did, the max speed you can connect at is 14.4Kbps unless you fork over some cash.  Could that be the problem?

---

### Post by porsher_puddles on 2005-07-23
i haven't downloaded any drivers as it would take forever at this speed it is just running on the basic driver that ubuntu loaded, i have however tried a different modem but its still the same. when i switch to windows connection speed is fine so i know the hardware is all good

---

### Post by twoseids on 2005-07-23
[QUOTE=porsher_puddles]i haven't downloaded any drivers as it would take forever at this speed it is just running on the basic driver that ubuntu loaded, i have however tried a different modem but its still the same. when i switch to windows connection speed is fine so i know the hardware is all good[/QUOTE]
 Hmm...well ya got me there - I hope some more experienced users can help.  The only other thing I know of is here:

[http://ubuntuguide.org/#loadwebsitefasterfirefox](http://ubuntuguide.org/#loadwebsitefasterfirefox)

But it sounds like this won't improve your situation greatly...sorry couldn't help more!

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=twoseids]Hmm...well ya got me there - I hope some more experienced users can help.  The only other thing I know of is here:

[http://ubuntuguide.org/#loadwebsitefasterfirefox](http://ubuntuguide.org/#loadwebsitefasterfirefox)

But it sounds like this won't improve your situation greatly...sorry couldn't help more![/QUOTE]

I second that firefox guide.

---

### Post by porsher_puddles on 2005-07-23
its not just firefox that is painfully slow, i went to upgrade something and the file was only small about 1.2 mb and it took 5 hrs to download, it seems to do nothing for a few minutes then download a few kb then stop, then a few more minutes, then a few more kb. i have even load ubuntu on another computer tried different modems and its still the same its really spoiling using it as i can't get drivers upgrade or anything.

is there anything in my internet setup which is wrong?

---

### Post by porsher_puddles on 2005-07-24
i now believe this is caused by the modem driver

How i arrived at this conclusion : i have tried 2 different external modems, one which i use regularly and one which i just bought second hand. The second hand one is the modem i intended to use on this system, it is a cirrus logic 56kbs(ambient technologies chip) i have tried it in windows on this machine with the standard windows drivers and it only connects at 9600 even though i set port settings to 111500. my other modem i use runs fine on the standard windows drivers, but it is still running very slow on ubuntu.

My question: how do i identify the correct driver i need for ubuntu and how do i install it?


Another question: how can i see what my connection speed is in ubuntu?

---

### Post by beamo on 2005-07-24
> the problem : i can connect to the internet without any problems but when i am on its so slow it makes the connection unuseable, it takes 5 mins to load a web page.

I have had a similar problem. For me, sometimes the connection is fine, sometimes the connection is ridiculously slow and sometimes the connection doesn't work at all. However, I finally found a way to fix it. I open System>Administration>Networking and click on Ethernet Connection. Then I deactivate it and reactivate it. It works every time and my connection is as fast as it was on windows. I don't know why I have to do this but it is what works. Before this I tried everything, but nothing else worked. Would love to know why I have to do this, though.

---

### Post by mingus on 2005-08-13
[QUOTE=beamo]Would love to know why I have to do this, though.[/QUOTE]

If Ethernet is active then that can impact the DNS resolution, slowing the connection or in some cases preventing DNS from working at all.

---

