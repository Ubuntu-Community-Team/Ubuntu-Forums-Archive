---
title: "ntp"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by chrislynch8 on 2007-10-26
Hi,

When I right click on the clock and want to update it with an internet time server. I get a message saying 

"NTP Support is not available"
Please install and enable NTP support in the system.

I haven't use Linux in a while so now I'm a bit out of touch.

how can I solve this?


Chris

---

### Post by adza on 2007-10-26
try searching in synaptic for NTP and install any packages...

---

### Post by ajdm326 on 2007-10-26
Install ntp in your synaptic package manager.  System>Administration>Synaptic

---

### Post by chrislynch8 on 2007-10-26
Hi I have ntpdate installed and thats all thats there. I have no package called ntp.


Any advise

Chris

---

### Post by nick_h on 2007-10-26
When you right-click on the clock and select "Adjust Date & Time" then select "Keep Synchronised with Internet Servers" it prompts you to download ntp.  You just have to say yes and allow it to do it.

---

### Post by chrislynch8 on 2007-10-26
> **nick_h said:**
> When you right-click on the clock and select "Adjust Date & Time" then select "Keep Synchronised with Internet Servers" it prompts you to download ntp.  You just have to say yes and allow it to do it.

It says install NTP, I press install it give the busy icon for the mouse then thats it nothing else. I don't think its downloading it!!! It doesn't give anymore message after I press install and everytime I select "Keep Syn......" it asks me to install


Chris

---

### Post by nick_h on 2007-10-26
For me, after I hit the install button it installed it quickly.  You could always try installing it manually from a terminal by typing:
```
sudo apt-get install ntp
```

---

### Post by chrislynch8 on 2007-10-26
It froze and not it says manually run "dpkg --configure -a". When I type this in it says I need to be a super user, I'm the admin, is that nit a super user?


Chri8s

---

### Post by nick_h on 2007-10-26
To run a command as super user use sudo.  In this case:
```
sudo dpkg --configure -a
```

---

### Post by chrislynch8 on 2007-10-27
Thanks, Thats working now

---

### Post by rseiler on 2007-10-29
> **nick_h said:**
> For me, after I hit the install button it installed it quickly.  You could always try installing it manually from a terminal by typing:
```
sudo apt-get install ntp
```
I saw the same thing as the OP with v7.10. I, too, have only ntpdate installed, according to Synaptic.

However, when I enter the command you recommended, I'm told that "Packge ntp is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package ntp has no installation candidate."

Any ideas?

---

### Post by nick_h on 2007-10-30
Check to see that you have the universe repository enabled.

---

### Post by rseiler on 2007-10-30
Thanks, that did the trick.

I'm not sure why universal wouldn't be enabled by default though (nor the main one located above it).

Also, why wouldn't ntpdate itself be enough?  After all, it is installed by default and described as a "client for setting system time from NTP servers," so it should be able to do the job.

---

### Post by nick_h on 2007-10-31
ntpdate is just the front-end.

Universe is not enabled by default because it contains software that is not available under a free licence.

---

