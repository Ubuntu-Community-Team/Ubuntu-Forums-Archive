---
title: "How to 'repair' internet connection?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by markcorbyn on 2006-11-22
Hi,

I am a relatively new user to Ubuntu Breezy 5.10.
I am really happy with it but I have one thing which can be really annoying.

When I start-up it usually connects me to my wireless network fine, however sometimes it doesnt connect at all or the connection is EXTREMELY slow.

In windows XP I would usually resort to Right-clicking the monitors and choosing 'Repair' and this solves the problem.

Is there an Ubuntu equivalent?

At the moment i'm resorting to restarting the laptop and it works fine when it restarts but that just a pain.

Thanks for any help offered,

Mark

---

### Post by catanzag on 2006-11-22
I don't know if there is a linux equivalent for xp Repair feature, but, just a question, why don't you upgrade to a newer version, dapper (which will be long supported) or the recent edgy? software and drivers is for sure more updated, and maybe all the original problems are already be solved and you don't need a repair equivalent command.

regards

---

### Post by markcorbyn on 2006-11-22
I tried upgrading to Dapper but I had problems with the graphics drivers. Even the Vesa ones either wouldn't work or would crash after a few seconds (usually during the log-in screen although sometimes made it as far as the desktop). 

After the first crash, it wouldn't even manage to load all the modules etc, it just froze after the GRUB screen. I have tried re-installing several times with the same effect. (Although a Dapper live session worked for some reason)

Im not saying Breezy worked perfectly first time, I still had to initially re-configure it to use Vesa drivers and then upgrade to fglrx but at least It worked.

I recently tried Edgy but even the Live CD wouldnt boot up to I didnt risk actually going ahead with the install.

Anyone any suggestions?

---

### Post by markcorbyn on 2006-11-22
Anyone? 

Cant I simply stop the network process somehow and run the 'Configuring network interfaces' script somehow?

---

### Post by mcduck on 2006-11-22
you could try running 'sudo /etc/init.d/networking restart', that should do the job.

If that works, you can even make a launcher on your desktop or panel with that command, just replace 'sudo' with 'gksudo' so you don't need to open a terminal to do this :)

---

### Post by markcorbyn on 2006-11-22
This looks like exactly what I was looking for. I tested with a working connection and the connection still worked after restarting the process which is a good sign :)

I'll keep hold of this code and next time it 'messes up' i'll give it a go and post back here.

Thanks a bunch,
Mark

---

### Post by randytuggle on 2006-11-22
> **markcorbyn said:**
> I tried upgrading to Dapper but I had problems with the graphics drivers. Even the Vesa ones either wouldn't work or would crash after a few seconds (usually during the log-in screen although sometimes made it as far as the desktop). 

After the first crash, it wouldn't even manage to load all the modules etc, it just froze after the GRUB screen. I have tried re-installing several times with the same effect. (Although a Dapper live session worked for some reason)

Im not saying Breezy worked perfectly first time, I still had to initially re-configure it to use Vesa drivers and then upgrade to fglrx but at least It worked.

I recently tried Edgy but even the Live CD wouldnt boot up to I didnt risk actually going ahead with the install.

Anyone any suggestions?

Last weekend I found a completely new driver for my ATI Radeon Xpress 200 card. Since then, my video problems are history. If you run an ATI card, you should upgrade to Edgy and install the new ATI Driver. See [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") for complete directions. BTW: Method 2 of this page worked for me.

---

### Post by markcorbyn on 2006-11-22
Thanks, I may give this a go. I have an ATI Radeon X700 card in my laptop.

---

### Post by PrinceArithon on 2006-11-22
Another thing you can do is make sure your wireless card is on the proper setting.

Right click on your Icon that has to do with your wireless network.  A little menu will pop up.  You will see where it says connection.  If in the little box next to it, it says lo, change it to eth1.  It will work faster for you.

---

### Post by Metaljaz on 2006-11-24
I have had the same problems with my wireless however i only see lo, wlan and eth0. wlan and eth0 are active. I do not see eth1.
My internet and email was working fine for about 3 hours that i was using it. Shut it down, came back the next day..nothing..
I am using ubuntu 6.06LTS (dapper). I have tried DHCP and static address using my settings and still nothing.
lost

---

### Post by gent_k on 2006-12-01
I've been having to use the repair function in XP lately too, and didn't know if there is something similar in Ubuntu. (although i'm connected through cable modem)

I will try some of the suggestions next time.

---

### Post by MasterAslan on 2008-02-03
metaljaz:  I bet you have already sorted this by now but if anyone else comes across this thread then it might help.  If you are using ndiswrapper you need to modprobe ndiswrapper to get the network card to show up after restart.  The solution is to add ndiswrapper to the modules so it does this automatically on boot.

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
``` will do the trick.

---

### Post by dodgingspam on 2008-02-03
I've used the command you suggested but since I was not sure if it was done properly I've done it twice. Now I have two entries for ndiswrapper. How do I remove one?

---

