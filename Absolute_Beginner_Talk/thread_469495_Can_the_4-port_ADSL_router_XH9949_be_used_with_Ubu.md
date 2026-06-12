---
title: "Can the 4-port ADSL router XH9949 be used with Ubuntu"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Kiwilad on 2007-06-09
Hello,

As someone who has never used ubuntu in any other form other than on the live CD (and I can't get internet to work) my first question is.... will I be able to access the internet whilst using Ubuntu via the XH9949 DSE ADSL router? I currently have XP Pro and that can access internet OK. More details of router at following link.

[http://www.dse.co.nz/cgi-bin/dse.storefront/466b723e0103ca142740c0a87f330668/Product/View/XH9949](http://www.dse.co.nz/cgi-bin/dse.storefront/466b723e0103ca142740c0a87f330668/Product/View/XH9949)

Many thanks

Stu

---

### Post by ronocdh on 2007-06-09
DHCP-enabled ethernet should work out of the box in Ubuntu. Wireless might take some configuration, depending on your hardware, but ethernet should be effortless. Judging by the link you sent, this seems like a 2-in-1 modem and router, is this correct? If this is the case, you might want to get a brand name router and connect that to the modem. This would not interfere with your connectivity in WinXP.

---

### Post by Kiwilad on 2007-06-10
Thanks ronocdh,

*Judging by the link you sent, this seems like a 2-in-1 modem and router, is this correct? If this is the case, you might want to get a brand name router and connect that to the modem. This would not interfere with your connectivity in WinXP.*

Ahhhh, not sure! I have one line coming from the filter that gets plugged into the back of the router. I then have two network cables from the back that go to two seperate computers, one of which I would like to try Linux on.

So, what you're saying is that I need to get another router which would be the first in line from the filter. The xh9949 would then be connected to that, and the two computers left connected to the xh9949 as they are now.... is that right?

Thanks again

---

### Post by ramjet_1953 on 2007-06-10
Ubuntu will just see this as a switch and should just connect automatically.

I have used two different ADSL routers:cool: and both were recognised straight-up by Ubuntu.

Regards,
Roger

---

### Post by Kiwilad on 2007-06-10
Yeah, I'm not too good with this stuff....which is kinda why I thought it would be good to take a wild leap out of my comfort zone, lol. The box that the router came supplied in does have the Windows logo, a Mac logo, and a Penguin logo, so I assumed it would work.  Sorry to be a pain, but....

I can not get it to work. I've tried using terminal and typing "sudo pppoeconf". 

It tells me that...
"I found 1 ethernet device: 
eth0
Are all your ethernet interactions listed above? (If No, modconf will be started so you can load the card drivers manually). 
Or press esc to abort here"

Pressing "No" simply does not work and results in a message in the terminal window "/usr/sbin/pppoeconf: 468: modconf: not found"

Pressing "Yes" starts it looking for PPPoE Access concentrator on eth0...(multi-modem mode)" and then ends up with the message "Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem".

The network and modem cables are fine. I've tried unplugging the other computer from the router, but same result. I've tried rebooting computer with router switched on and switched off, but same result. 

I really have no idea what I'm doing, so any help would be very much appreciated. 

Thanks heaps

---

### Post by drowner on 2007-06-10
It should work just fine.... what is the problem? No internet?

I know its obvious, but if you have a network monitor in your panel, right click it and make sure it says 'Enable networking' or whatever.

---

### Post by Kiwilad on 2007-06-10
Well, I'll be damned!! :p

I had actually checked that before and right clicked it and set it so that the networking was enabled. What I hadn't done was left clicked it and ticked the "wired network" option. Now that I've ticked the "wired network" option (left click menu) as well as the "enable networking" option (right click menu), it works fine.

You guys ROCK !!!!

Thanks heaps for your help, now I can work at becoming a linux convert.

---

### Post by drowner on 2007-06-10
As they teach medical students 'When you hear  thundering hooves on the plain, think of horses, not zebras'

;)

---

