---
title: "Internet/modem problem.."
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2006-11-25
well.. this is kinda weird.. cuz.. i had ubuntu64bit edition, n.. my ethernet modem worked without any problem.. 
due to compatibility issues.. i kinda removed it and installed the 32bit edition.. now.. it does not seem to work.. i cant go online :confused: 

whats gone wrong?

modem : UT-300R2U

---

### Post by tommcd on 2006-11-25
I found this in the archives:
[http://www.ubuntuforums.org/archive/index.php/t-159039.html](http://www.ubuntuforums.org/archive/index.php/t-159039.html)
Do you connect by usb port or ethernet? Usb modems can be a problem. If you use DSL over PPPoE I suppose you could try 'sudo pppoeconf' in terminal, even though the link I gave said it is not required. Hope this helps.

---

### Post by nightwolf2k5 on 2006-11-25
its connectd via the ethernet port.. its kinda like already configured.. when i ran the ubuntu 64bit os, the internet worked right away, i.e. i went to firefox and could surf w/o any problem

now.. i cant even go to the modem page i.e the 192.168.1.1 page.. it says page cannot be displayed.. :(

---

### Post by tommcd on 2006-11-25
Are you running firestarter or another software firewall? If so turn it off. Make sure eth0 is enabled under system>administration>networking, and it is set to DHCP. Also try:
ifconfig -a
sudo ifdown eth0
sudo ifup eth0
Then to obtain IP address do:
sudo dhclient eth0
There was an ethernet troubleshooting guide in the forums. can't seem to find it atm. hope this helps.

---

### Post by nightwolf2k5 on 2006-11-26
i dont have any firewall.. but.. somehow.. the internet seems to work :)
its like.. i go to system->aminstration->networking
and deavtivae and activate the eth0, then.. it works.. but.. what i dont get is.. why should i do this? also.. i'm not really sure if thats the way i went abt to activate it  :P
anyhow.. i'll copy the stuff u gave.. i'll be really greateful if u could send me that link man..

thanks a lot :)

---

### Post by tommcd on 2006-11-27
For some reason, stopping and then starting eth0 can get internet connected sometimes. This is what you are doing with 'ifdown eth0' and 'ifup eth0'. I guess it restarts your modem or the linux driver.
I can't find the troubleshooting guide itself, but here is a link to a discussion thread about it:

[http://ubuntuforums.org/showthread.php?p=476494](http://ubuntuforums.org/showthread.php?p=476494)
Hope this helps you stay connected.

---

