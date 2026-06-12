---
title: "[SOLVED] Access concentrator issues with COX Cable"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by funkshun on 2007-07-22
I just installed ubuntu 6.06.1 and I'm trying to get my laptop connected to the ADSL connection (cox cable) at work. I read the guide 

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-pppoe](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-pppoe)


I did the pppoeconf command. It stated if **found 1 ethernet device "eth0**". I proceed and an error comes up **"Sorry, I scanned 1 infterace, but the Access Concentrator of your providor did not respond. Please check your network and modem cables. Antoehr reason for the scan failure may also be anthother running pppoe process which controls the modem."**.

Can someone recomend what else I should  try. I thought I might need to update the driver on the ethernet card. I went to the gateway site but it does not say what type of ethernet card I have. I just know it's an intergrated one.

[http://support.gateway.com/s/Mobile/2007/Oasis/1014129R/1014129Rmv.shtml](http://support.gateway.com/s/Mobile/2007/Oasis/1014129R/1014129Rmv.shtml). Im spanking new to ubuntu so any advice would be much appriciated. Thanks

---

### Post by w4ett on 2007-07-22
Are you sure about this...I had Cox Cable in Florida...it was just a normal DOCSS Cable Broadband.  Then it's split off at your work location via a Router/Switch..  ADSL connections are provided by the telephone company over the old style 2 wire phone line.  

Ubuntu should work out of the box on a cable connection via direct wired ethernet connection.

---

### Post by overdrank on 2007-07-22
> **w4ett said:**
> Are you sure about this...I had Cox Cable in Florida...it was just a normal DOCSS Cable Broadband.  Then it's split off at your work location via a Router/Switch..  ADSL connections are provided by the telephone company over the old style 2 wire phone line.  

Ubuntu should work out of the box on a cable connection via direct wired ethernet connection.

I agree  I have cox and just installed wireless on  a second laptop no problem. :(

---

### Post by funkshun on 2007-07-22
I'm  on the windose computer right now next to the laptop I'm trying to get a connection on.

In windose i went to command promt and typed  ipconfig /all
"lv.cox.net" ...I'm in Las Vegas and all we have out here is cox cable. I thought I would be able to connect by pluging the cable into my ethernet connection. I have had no such luck. My real goal is wireless. But I have to get a cable connection so I can download and update files so I can run mdsiwrapper for my broadcom 802.11 wirless adapter.

---

### Post by funkshun on 2007-07-22
Bumb!   I fixed the problem. After an hour or so of searching on the fourms. I found out I had to turn off the cable router and turn off my laptop for 5 mins. Then I restarted the cable router and my laptop and now I have internet "funkshuning". This fourm is really a blessing. Thanks

---

### Post by overdrank on 2007-07-22
> **funkshun said:**
> Bumb!   I fixed the problem. After an hour or so of searching on the fourms. I found out I had to turn off the cable router and turn off my laptop for 5 mins. Then I restarted the cable router and my laptop and now I have internet "funkshuning". This fourm is really a blessing. Thanks

:guitar:
Glad too hear and good surfing!!!!!!!!!!!!!!

---

### Post by overdrank on 2007-07-22
Oh and can you mark this thread as solved please! 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks Overdrank

---

