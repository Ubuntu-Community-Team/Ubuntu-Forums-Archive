---
title: "Shutdown software for UPS"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-06-29
Is there any software that will give me a graceful Ubuntu Dapper Drake system shutdown after a specified period of AC power loss, that will work with APC and Belkin UPSs ?  

Yes, I did check with APC and Belkin & their answer is that they do not currently support Linux O/Ss.

Thanks.

---

### Post by x64Jimbo on 2006-06-29
You'd have to snoop the signal that the UPS sends to the computer when it loses power and when it gets it back. Then you could write a script that would listen for that signal, wait 20 minutes, or whatever, and then if it hasn't heard the "i've got power back" signal, it shuts down the system. I'm not sure how you would do that, but I'd start with seeing if the UPS gives the system a signal that would show up in xev. 
run xev in the terminal and then unplug the UPS and plug it back in. if you see two unique key events, then it's getting that input. For scripting that takes advantage of those signals, you'll have to google around a bit. If you find a solution, be sure to come back and post about it, or even create a how-to. I personally don't own a UPS so my testing is quite limited ;)

---

### Post by Kilz on 2006-06-29
[QUOTE=wpshooter]Is there any software that will give me a graceful Ubuntu Dapper Drake system shutdown after a specified period of AC power loss, that will work with APC and Belkin UPSs ?  

Yes, I did check with APC and Belkin & their answer is that they do not currently support Linux O/Ss.

Thanks.[/QUOTE]
I'm not to knowledgeable about UPS's. But a quick search of synaptic for UPS brought up quite a few replies.

genpower
apcd
apcupsd and apcupsd-cgi
nut
powstatd
upsd

[Here is a link]("http://linux.about.com/cs/linux101/g/genpower.htm") that talks about genpower and has links to nut and apcupsd articles.
You may also want to do a few searches for these applications to see if any of them will work for you.

:grin:  I hope this helps.

---

### Post by wpshooter on 2006-06-29
Thanks.

---

### Post by missmoondog on 2006-07-01
did this help you get anything figured out. i'm having the same dilemma. i've tried most of the ones, genpower, apcd, apcupsd and apcupsd-cgi, nut, powstatd
upsd mentioned and, NOTHING!!

i have the belkin 350va ser (F6H350-SER)

---

### Post by papangul on 2006-07-02
I just installed and tested apcupsd , works as expected.
I have usb connection, so the only entries I had to add to the /etc/apcupsd/apcupsd.conf file are - 'usb' twice for data cable type and ups type, % of charge remaining when shutdown will be triggered. Also the entry 'ISCONFIGURED' has to be turned to 'yes' from default 'no' in the /etc/default/apcupsd file. That's all.
Hope that helps.

---

### Post by cdeel77 on 2007-03-11
papangul, thank you for that ISCONFIGURED=yes tip. It appeared that the daemon wouldn't start up until I added that.

---

### Post by daller on 2007-08-13
I'm using powstatd, which seems nice and simple...

When using the test mode:

```
powstatd -t
```

It recognizes when I take the plug out of the wall :)
... and put it back in!

But it doesn't send any shutdown-signals to the system...

Can anyone help me here?

---

### Post by wpshooter on 2007-08-14
> **daller said:**
> I'm using powstatd, which seems nice and simple...

When using the test mode:

```
powstatd -t
```

It recognizes when I take the plug out of the wall :)
... and put it back in!

But it doesn't send any shutdown-signals to the system...

Can anyone help me here?

I have come to the conclusion that all of this is wasted effort until Belkins & APC decides to write some proper native shutdown software for Linux for their products !!!  Sorry for me and you and everyone else.

---

### Post by x64Jimbo on 2007-08-15
> **wpshooter said:**
> I have come to the conclusion that all of this is wasted effort until Belkins & APC decides to write some proper native shutdown software for Linux for their products !!!  Sorry for me and you and everyone else.
Well, good luck getting any large corporation to support Linux compatibility for hardware that already has a limited user base. I don't like being cynical about Linux support any more than the next guy, but this is one battle that is not worth fighting. A similar amount of time and effort could probably produce an open source, reverse engineered kernel driver and GUI front end. Then we would have control over the source and its uses, whereas closed source proprietary drivers are often restricted heavily (like being barred from distribution in a LiveCD, ala nVidia or ATI).
The call should not be for the manufacturer to make the drivers, because I can tell you from experience that they will not do so, and even if they did, the drivers would be buggy, closed source, and in all likelihood, not supported in any way whatsoever. Instead, the call should be for open source tinkerers out there to come together and do it themselves. Were I a programmer, I'd probably be working on it right now ;)

---

### Post by Mr. Brownstone on 2007-08-16
I have a Gentoo server and Ubuntu desktop sharing an APC Back-UPS RS 1000 and have successfully configured and tested them -- only 5 minutes ago -- as a master and slave for apcupsd using this excellent HOWTO:

[http://gentoo-wiki.com/HOWTO_APCUPSD](http://gentoo-wiki.com/HOWTO_APCUPSD)
(It's currently down for me, so [here is the Google-cache](http://64.233.183.104/search?q=cache:t7uHmSdIPWwJ:gentoo-wiki.com/HOWTO_APCUPSD+http://gentoo-wiki.com/HOWTO_APCUPSD&hl=en&ct=clnk&cd=1&gl=uk) version.)

Be sure to read it through to be aware of the gotchas, and use your common-sense when translating the Gentoo-specific stuff to Ubuntu. :)

---

### Post by xelasmada on 2007-08-18
There is a PowerChute Software from APC:  PowerChute Business Edition v7.0.1 Agent for Linux

[http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=2862&p_created=1052327264&p_sid=vPBhzvJi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQmcF9wcm9kcz0wJnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1](http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=2862&p_created=1052327264&p_sid=vPBhzvJi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQmcF9wcm9kcz0wJnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1)


You have to register to download it.

---

### Post by wpshooter on 2007-08-19
> **xelasmada said:**
> There is a PowerChute Software from APC:  PowerChute Business Edition v7.0.1 Agent for Linux

[http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=2862&p_created=1052327264&p_sid=vPBhzvJi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQmcF9wcm9kcz0wJnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1](http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=2862&p_created=1052327264&p_sid=vPBhzvJi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQmcF9wcm9kcz0wJnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1)


You have to register to download it.

I think I have talk to APC about this previously and if my memory serves me correctly, they fold me that this software is for only their top of the line UPSs that would generally be used on servers, i.e. I don't think that there is currently any software from APC for their lower end UPSs that would generally tend to be used by most Ubuntu home users.

Thanks.

---

### Post by lptr on 2008-05-09
> **daller said:**
> I'm using powstatd, which seems nice and simple...

When using the test mode:

```
powstatd -t
```It recognizes when I take the plug out of the wall :)
... and put it back in!

But it doesn't send any shutdown-signals to the system...

Can anyone help me here?

Maybe somewhat late - but better late than never :)

Found this: [http://ubuntuforums.org/showthread.php?t=362064&highlight=Powstatd](http://ubuntuforums.org/showthread.php?t=362064&highlight=Powstatd)

He describes exactly this. Seems as if the patch did not find his way into the repositories...

rob*

---

