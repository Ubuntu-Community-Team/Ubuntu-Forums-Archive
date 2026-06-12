---
title: "Ubuntu Clock In Virtualbox Runs Fast"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by esaym on 2007-03-24
I have ubuntu 6.06 installed on virtualbox that I use for development.  My operating system is also 6.06.  For some reason the clock on the virtual 6.06 runs very fast.  Anyone have any idea why?


Thanks

---

### Post by esaym on 2007-03-24
anyone?

---

### Post by lamalex on 2007-03-24
try installing ntpclient and setting to get time from a time server. it could be running fast due to the hardware abstraction and it not having direct contact with the system clock. Possibly some kind of impedance between your guest operating system and the host passing on the data to it.

---

### Post by esaym on 2007-03-24
> **Iamalex said:**
> try installing ntpclient and setting to get time from a time server. it could be running fast due to the hardware abstraction and it not having direct contact with the system clock. Possibly some kind of impedance between your guest operating system and the host passing on the data to it.

Yes I can set the clock to automatically update but it is kind of impractical.  It gains about 1 hour every hour so when the clock gets set to the right time all my dev programs start complaining about a package being built in the future.

---

### Post by esaym on 2007-03-25
well I guess I will bump this thread one more time and see if anyone knows anything....

---

### Post by ericdegen on 2007-06-08
esaym, did you every resolve this?  I'm seeing the same thing on a newly built Intel quad-core running 6.06 server and VMware Server 1.03.

Pretty darn strange!

---

### Post by zekopeko on 2007-06-08
try searching the forums. i know i've seen it somewhere.
 i have a similar problem with my feisty install (non virtual machine) but it's not so sever. i gain in 1 day 30m.

---

### Post by TheFuzz4 on 2007-06-11
I also am having this problem with my Windows XP VM running in Fiesty.

---

### Post by TheFuzz4 on 2007-06-13
I think that I might have found the cure for this.  When you install the VM tools there is a setting with the tools that allows you to synch the clock with the system clock.  Since doing that it now stays in synch with no problems whatsoever.  Hope that helps out.  If you need the tools let me know.

---

### Post by RedRover1 on 2007-06-13
Try this link for a possible solution.

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1420](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1420)

This one is also from VMware but may give hints on why Virtual Box can have issues if the hardware has Intel's SpeedStep or AMD's PowerNow or Cool'n'Quiet.

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591)

---

