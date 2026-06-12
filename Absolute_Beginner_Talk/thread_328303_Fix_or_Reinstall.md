---
title: "Fix or Reinstall?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ponyspreso on 2006-12-30
I'm a brand new Linux user who has recently installed Ubuntu.  The installation was flawless and the dual boot system has been fault free.  

Unfortunatly, I have just spent the last two weeks (!) trying to get my USB Speedtouch 330 modem to work in Ubuntu, still with no success.  I have decided to just spend some money and get an ASDL modem with ethernet connection.  Seems everyone says that's the best way to go anyway.

However, in my quest to get my USB modem to work I have fumbled about and goofed around alot with installing various drivers and bootscripts and the like.  Now Ubuntu loads really, really slow, and all the applictations load even slower.  It takes between 30 seconds and a full minute for Termial, or Open Office to load up.  Once they load, they work fine, but its the wait.....

My question is, is there a way to try to undo the damage I've obviously done to the system, or should I just try to reinstall Ubuntu and start with a clean slate?

And, if reinstallation is the answer, do I have to uninstall before I reinstall?

Lastly, for whatever answers people give, because I'm very new at this and obviously I've messed this up once, lol, if you could give any clear and percise instructions with your suggestions, it would be greatly appreciated.

Many thanks in advance for all your help!

---

### Post by Frak on 2006-12-30
I've reinstalled countless times, but if you can find a way to fix the damage done, that'd be best, but you don't have to uninstall Ubuntu, just write over its partition, but be sure to be carefull, like backup and what not, if you need any specific instructions just ask.

---

### Post by riven0 on 2006-12-30
Did you try installing the adsl modem first? Usually long load times are related to a badly configured network. The ethernet modem may fix it. 

If not, re-installing may be the best option. Don't worry about uninstalling. Just reformat the entire drive with gparted.

---

### Post by teaker1s on 2006-12-30
join the club on the speedtouch issue-I got as far as connecting and then had ARP issue which is pppd bug and seems unresolvable at the moment. 
you can remove the init.d file and  firmware look [here]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") and just remove from the locations.

as long as you haven't had sudo host problems as I did terminal
sudo nautilus
which will give root file access to alter and delete

---

### Post by louieb on 2006-12-30
> **Frak said:**
> I've reinstalled countless times
ME TOO. But thats OK. I have learned a little more each time about what works and what doesn't. It took a couple of months of twisting, tweaking, and  trying  out different desktops and other stuff. But now I have a system that I am comfortable with and easy to use and maintain.

---

### Post by ponyspreso on 2007-01-01
Cheers, I'll give the reinstall a try

Many thanks for getting back to me!

---

### Post by Frak on 2007-01-01
Reinstallation, the GLORY of Linux, you don't have to reactivate it over the phone.

---

