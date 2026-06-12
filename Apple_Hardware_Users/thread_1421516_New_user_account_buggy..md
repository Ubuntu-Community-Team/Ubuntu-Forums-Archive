---
title: "New user account buggy."
date: 2010-03-04
forum: Apple Hardware Users
---

### Post by CallsignBaron on 2010-03-04
I hope someone here can help and I hope I have chosen the correct place to post. Just installed Ubuntu 9.10 (32-bit) on Intel C2D iMac, 2.16Ghz, 3GB RAM. Ubuntu owns this iMac, no OS X partition. Everything going pretty well so far until I created a user account for my son. He has desktop user privileges. After logging into his account we immediately noticed that everything is very buggy. Moving windows around is herky-jerky (sorry for the less than technical terms her LOL), Internet is slow and flash is problematic. There is also a bit of a delay from when you click on something and its response, like if you click on the applications menu there will be a slight delay before the menu opens. Everything on my account, the one I created when I installed works well, its more fluid if that makes sense. So, I don't understand why his account is also not fluid. Any help would be greatly appreciated and if you need more information please let me know.

---

### Post by linuxopjemac on 2010-03-04
I have no idea but I would post it in the "General Help" forum as well. Does the newly created user have enough privileges?

---

### Post by Rasa1111 on 2010-03-04
I had a similar problem after installing 9.10 on a friends machine..

 after 2 hours of trying to figure out why the "buggyness" and "freeezes" were happening, 
I decided to turn off (switch to "none") the special effects in appearance menu...
and everything smoothed our perfectly. 

Maybe give that a try?

System>preferences>appearance> visual effects> select top option (none)

Sorry if that doesnt help. .. but hopefully it does. 
Good luck bro.

---

### Post by CallsignBaron on 2010-03-04
I think I have narrowed it down. A reboot fixed the overall buggyness and I think my problems lie with flash. He is young and the first site he went to was nickelodeon and nickjr. When I attempted to go to those sites on my desktop I experienced the same issues. Seems my problem is with flash, Any suggestions?

---

### Post by linuxopjemac on 2010-03-04
I have the Adobe flash plugin installer, which installs Adobe's Flash from the net.

```
sudo apt-get flashplugin-installer
```

You might consider more flash plugins, see the synaptic package manager.

---

### Post by CallsignBaron on 2010-03-06
Thanks for your help guys! I did need that flash plugin installer and ATI x1600 drivers. All fixed now, thanks again! :)

---

