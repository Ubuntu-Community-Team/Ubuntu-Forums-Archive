---
title: "Wireless troubleshooting, edgy--should I go fiesty?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-04-19
I have been with Edgy for about well 90+ days now.  I have NOT managed to get my home wireless working.  I have confirmed my wirless card works with an open network at another location, but I cannot get mine to work at home.  

I have WPA, but I turn that off, AND I broadcast my SSID.  I cannot get it too work. I have tried everything I know but that isnt' much.


I find the networking kind of a pain going back and forth from wireless and wired, not as easy as my previous experience with XP.  I am sure there are better ways to do so, but I don't know the tools.

Can anyone 1)suggest a troubleshooting program/fourm/place to start
and
2) do you think going to fiesty will fix the problem?  I have read that edgy doesn't have the best networking applications.......

Thanks!

---

### Post by cawill on 2007-04-19
My wireless on edgy didn't work but now it works out of the box on fiesty - you should give the live cd a try at least.

---

### Post by PartisanEntity on 2007-04-19
Definately give the live cd a try before installing.

Have you tried using Network Manager?

This has always worked for me (I connect to a wpa-psk encrypted network):
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by mkjarema on 2007-04-20
> **cawill said:**
> My wireless on edgy didn't work but now it works out of the box on fiesty - you should give the live cd a try at least.

Great idea, I hate it when I miss the obvious....LOL

I will 100% do that. Thanks!

---

### Post by mkjarema on 2007-04-20
Pending the Feisty Live CD works great, when I do the upgrade/reinstall, do I need to back up everything like my FF profile?  I am running my first round of buuntu so I am not sure exactually what i am doing

---

### Post by ColJep on 2007-04-20
I have an old Sony laptop using an SMC2835W (not V2) wireless card. This worked fine in Edgy but I am unable to get it to work with a fresh install of Feisty.

According to Feisty I have two wireless cards now. wmaster0 and wlan0. I just use a non broadcast SSID for security, I know this is wrong but I am miles away from anyone else. The option to use no security seems to be disabled now. Could this be the problem? The ease of connection using the Dapper live CD convinced me to change to Linux, 

Any ideas?

---

### Post by kaede on 2007-04-20
> **ColJep said:**
> I have an old Sony laptop using an SMC2835W (not V2) wireless card. This worked fine in Edgy but I am unable to get it to work with a fresh install of Feisty.

According to Feisty I have two wireless cards now. wmaster0 and wlan0. I just use a non broadcast SSID for security, I know this is wrong but I am miles away from anyone else. The option to use no security seems to be disabled now. Could this be the problem? The ease of connection using the Dapper live CD convinced me to change to Linux, 

Any ideas?
how actually you know the different for the version? 
cause i can't work it out my SMC2835W on my notebook.
sigh anybody could help me? im desperate now. 

running dmesg command shows many error message

---

### Post by ColJep on 2007-04-20
Good point about version of SMC card. Nowhere on the card has any version so I assumed it is a V1 type.

All I am sure of is it worked in Dapper and Edgy. I am now experimenting with an even older Netgear 104 card and the live CD.  No luck so far but only one wireless card is deteted.

Does anyone know how to control this new roaming feature? I cannot find any way to enter SSID and other data without going to manual configure.

---

### Post by cawill on 2007-04-20
You should be able to use the network manager and use the manual configuration option to enter SSID.

Or isnt that what you meant?

---

### Post by ColJep on 2007-04-21
> **ColJep said:**
> Good point about version of SMC card. Nowhere on the card has any version so I assumed it is a V1 type.

All I am sure of is it worked in Dapper and Edgy. I am now experimenting with an even older Netgear 104 card and the live CD.  No luck so far but only one wireless card is deteted.

Does anyone know how to control this new roaming feature? I cannot find any way to enter SSID and other data without going to manual configure.

Part number of SMC 2835W V2 card is 99-012084-295. The SMC website does not recognize this number if you enter it in the "I know my part number" box but if you follow the alternate route you come to this part number which is on the card. I therefor have a V2 card which should work according to the Ubuntu WIKI. Then again so should my Agfa Snapscan 1212u scanner :-)

---

### Post by mkjarema on 2007-04-23
> **mkjarema said:**
> I have been with Edgy for about well 90+ days now.  I have NOT managed to get my home wireless working.  I have confirmed my wirless card works with an open network at another location, but I cannot get mine to work at home.  

I have WPA, but I turn that off, AND I broadcast my SSID.  I cannot get it too work. I have tried everything I know but that isnt' much.


I find the networking kind of a pain going back and forth from wireless and wired, not as easy as my previous experience with XP.  I am sure there are better ways to do so, but I don't know the tools.

Can anyone 1)suggest a troubleshooting program/fourm/place to start
and
2) do you think going to fiesty will fix the problem?  I have read that edgy doesn't have the best networking applications.......

Thanks!
OK, so Feisty I went. When I did an upgrade from edgy I got nothing! I got a blank screen, not even a command line. I then reinstalled edgy, did all updates, and then upgraded to feisty again, and all is well.  AND my internet works!!  Wireless that is.  But I am using an externial PCI wireless card, I am just going to say that my internal broadcom isn't supported yet.  I have done all the tutorials for broadcoms, but I couldn't get it to work.  Feisty has much better network managing.  I don't have to manually do anything after the inital set up.

Very excited, thanks for the helkp, now all i need is a better video driver....

---

