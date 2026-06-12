---
title: "Tryingto get my cingular aircard to work!!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Kendrick_mark on 2008-02-28
I posted a thread in the wireless section here....
[http://ubuntuforums.org/showthread.php?t=708510](http://ubuntuforums.org/showthread.php?t=708510)

it's a Cingular/AT&T Broadband Card Option GT Max 3.6

Anybody have a clue as to how to make it work.  I've tried several different ways. theconfig filesare on the other thread.

Any help would be greatly appreciated.

Thanks,
Mark

---

### Post by wolfen69 on 2008-02-28
i found this: [http://centerclick.org/aircard555/](http://centerclick.org/aircard555/)

and this from the att message boards (looks promising) [http://forums.wireless.att.com/cng/search?submitted=true&q=linux+aircard](http://forums.wireless.att.com/cng/search?submitted=true&q=linux+aircard)

---

### Post by Kendrick_mark on 2008-02-28
I followed those links which led me to others and other searches until I found....
[http://www.uluga.ubuntuforums.org/showthread.php?t=407768](http://www.uluga.ubuntuforums.org/showthread.php?t=407768)

I found this command on the page... gcom -d /dev/ttyUSB0 

Ran it got this (best glimmer of hope so far)
mkendrick@mkendrick-laptop:~$ gcom -d /dev/ttyUSB0
SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "Cingular",2
Signal Quality: 15,99

If I disable my wifi card  I cannot connect to the internet.  Evdently the card is available and functional.  I just have to figure out how to use it.

---

### Post by Kendrick_mark on 2008-02-28
any idea on how to get ubuntu to connect via the modem or see it as a network device?

---

### Post by Kendrick_mark on 2008-03-06
I got it to work using the 'vodafone mobile connect card driver'

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

After downloading and installing ( I followed the reame file in the download) it auto detected my modem.

I was able to connect using these settings( I am posting this from it now!!!):

user [email]ISP@CINGULARGPRS.COM[/email]
pwd CINGULAR1
apn name: isp.cingular

---

