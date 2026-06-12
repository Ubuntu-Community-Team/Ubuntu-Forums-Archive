---
title: "Wireless drivers"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mc.7winkie on 2007-01-06
I got Ubuntu up and working this morning and its like nothing I have ever used.  I guess that can be both good and bad but I'm up for anything, pretty much.  I use a desktop with one of those Belkin Wireless G USB thumb sticks.  But I can't seem to connect to the internet.  I tried some stuff with ndiswrapper but I don't really know what I'm doing with the terminal and what not.  Could some one please help me?

---

### Post by rbhigday on 2007-01-06
Do you have anything showing under network?

What errors are you getting?

what does iwconfig show

---

### Post by mc.7winkie on 2007-01-06
I don't have any networks showing.  And whenever I type into the command line  to install the inf file it says it was installed incorrectly.  What should I do?

---

### Post by riven0 on 2007-01-06
It's best to post the error message here. 

And also post the output of the command rbhigday gave you: **iwconfig**

---

### Post by mc.7winkie on 2007-01-06
When I type in iwconfig it says;
l0        no wireless connections

eth0    no wireless connections

sit0      no wireless connections

I typed in ndiswrapper -l and it says;

installed drivers:
bkwgu   invalid driver!

But when I go to uninstall it by typing "ndiswrapper -e bkwgu.inf"
it replies "driver bkwgu is not installed"  I then go and type in "ndiswrapper -i bkwgu.inf" and it replies "bkgwu is already installed"  WTF?!?!?
Is that better? ](*,)

---

### Post by teaker1s on 2007-01-06
find the driver on the windows hardware driver cd-you may need to use either cabextract or unzip to get it out of .exe file

---

### Post by mc.7winkie on 2007-01-06
is cabextract on the live cd???

---

### Post by riven0 on 2007-01-06
> **mc.7winkie said:**
> is cabextract on the live cd???

I'm not sure but you can try downloading it [from here ]("http://packages.ubuntu.com/edgy/utils/cabextract")and transfer it with a pen drive or something to Ubuntu. Then to install just double-click on it.

---

