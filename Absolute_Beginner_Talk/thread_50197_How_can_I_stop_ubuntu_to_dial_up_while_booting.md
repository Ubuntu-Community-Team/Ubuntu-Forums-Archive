---
title: "How can I stop ubuntu to dial up while booting?"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by signtist on 2005-07-19
Hi,

I've just installed ubuntu and I love it!!!!
However, I don't like that it dials up to the internet while it's booting.
How can I stop doing it?
Many thanx

Torsten

---

### Post by Juergen on 2005-07-19
Ubuntu tries to sync time with a NTP-server.

To stop this it should AFAIK be enough to remove the X-ecutable flag from '/etc/init.de/ntpdate'

---

### Post by JayCnrs on 2005-07-19
You will need to possibly edit a file, I'm not sure on how dial-up is but you can check **/etc/network/interfaces**  if you see in this file **auto ppp0**  then remove this line or comment out the line with #. Try a reboot and see if it tries to dial.  The other way of stopping it from dialing is to go to **/etc/rcS.d**  and then look for the link that says S20networking, if this is in there you will want to use the following command:

**mv S20networking  K20networking** 

If this causes any issues or causes the dial up not to work you can re-enable the networking by using

**mv K20networking S20networking** 

Let us know if you are succesful  ;-)

---

### Post by JayCnrs on 2005-07-19
I was just thinking before getting into editing files you could try going to :

System --> Admin --> Networking

Highlight the ppp0 interface and look through the options and see if there is a checkbox for start at bootup, if so make sure there is no check in this box.

---

### Post by signtist on 2005-07-21
Hi,

the problem is solved. it solved itself to be precise. I installed gnome-ppp, which uses wvdial, to solve my internet speed problem and I deleted the entry in System Admin Networking tool.
Now it does not dial up anymore.

But thanks a lot for your help!!!

---

