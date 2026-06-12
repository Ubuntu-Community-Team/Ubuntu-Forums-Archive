---
title: "black screen at start up"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by eaglehorse on 2008-02-21
:oops::oops: I have seen this question awskes several times nothing comes quite close to my issue.  I have a hp laptop(that is enough of an issue) it has an amd sempron cpu running at 995 mh an ati radeon xpress 200m graphics card ( I have enabled restrictive drivers) 1 gig ram. I am dual booting xp and  ubuntu 7.1 and am completely new to it. I have been using it for about three days. I love it but there is a hitch in my giddy up. Upon startup I have a black screen. I have found a work around I can press alt and f1 and it boots normally or I can press alt and f2 I think that is similar to safe mode in xp. I would like to  have it boot normally without having to do anything other than log in. That way my wife can get use to it so I can stick with one os for the most part.
Any suggestions are greatly appreciated. I have tries several command lines I have found here to no avail. 
This is the first of many questions.
):P :biggrin:

---

### Post by spiderbatdad on 2008-02-21
does the black screen occur before your login? There is  often a problem with the settings in /etc/usplash.conf

My solution to what may have been a similar problem was to edit usplash.conf thusly:```
gksu gedit /etc/usplash.conf
```

change values to 1024x768 respectively. Save. Reboot.

---

### Post by XxPoseidoNxX on 2008-02-21
[http://vntutor.blogspot.com/2007/10/blank-screenon-bootup-and-shutdown.html](http://vntutor.blogspot.com/2007/10/blank-screenon-bootup-and-shutdown.html)

hope this helps:)

---

### Post by eaglehorse on 2008-02-21
Thank you both. I will have to try it when the munchkin virus is removed from the computer  :mrgreen:. I will post back and let you know if it worked spiderbatdad.
XxPoseidoNxX there is alot of good info in that link.
I have some security questions but need to correct one thing at a time.

---

### Post by eaglehorse on 2008-02-22
:guitar: Sweet the boot screen now works. Thank You. :) :)but now Firestarter does not start at boot. I get a failed message. This concerns me because I am connected to broadband (cable). While on this subject do I need an AV or any other security software? I have read several posts but I tend to learn best by interacting with others.:D:mrgreen:
This is a great community.There are very few sites that provide this kind of help to newbies.

---

### Post by philinux on 2008-02-22
Firestarter is just a gui for editing the built in firewall iptables. I've never run it as I've got a router with it's hardware firewall. I've got no AV as it's not needed.

This may help you. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

