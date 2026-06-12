---
title: "Madwifi and Kubuntu/knetworkmanager"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2008-02-13
Ok so I have Kubuntu 7.10 installed on my new laptop and everything other than my wireless card appears to be working... I see the restricted driver running however I am unable to see any wireless networks on my knetworkmanager.

Any ideas or suggestions to get this working? After XP kept freezing on me my choices are kubuntu or Vist-Aids and I would truly perfer kubuntu :)

~J3ff

---

### Post by beastrace91 on 2008-02-13
After reading my first post here is a bit more info on my laptop:

Asus F3Kseries
Atheros Wireless
M/B Version: F3KA

Not sure how to find the model number of the wifi card if someone will give me the command I will post that also.

~J3ff

---

### Post by Ex-windows on 2008-02-13
Check out this thread
[http://ubuntuforums.org/showthread.php?t=688641](http://ubuntuforums.org/showthread.php?t=688641)
 there may be an issue with the atheros driver if it is the 5700 or 5600

---

### Post by beastrace91 on 2008-02-13
Update:

Found my Card it is a Atheros AR5007EG

Ok so I checked out that thread you posted and basicly I have to install ndiswrapper? Ok so I am trying to follow [this guide.](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/#configure_interface) How ever when it gets to finding the windows driver for my card I am un-able to find the .inf file that matchs the .sys file... I have the card working on windows vista but I cannot find this .inf file it wants to install the driver using ndiswrapper... any ideas?

~J3ff

---

### Post by Ex-windows on 2008-02-15
I am really sorry Ihaven't been here. The 5007 is the one I meant (not 5700) Yes the ndis wrapper is the ticket or is supposed to be lol. I have not yet been successful due to lack of time But, I am followinf the instructions on the link I gave you.  Try this link 
[http://ubuntuforums.org/showthread.php?p=4259805#post4259805](http://ubuntuforums.org/showthread.php?p=4259805#post4259805)
and Check out the 3 Links provided there. I am trying the #3 Link

Otherwise, ndiswrapper appears to work: [http://ubuntuforums.org/showthread.php?t=649019](http://ubuntuforums.org/showthread.php?t=649019). Hopefully this will work I just haven't had the time to play and like you I can get the Vista side to work just fine.
Let me know your results, I'll have this thread sent to an emal box so I can stay on top of it. Good Luck

---

