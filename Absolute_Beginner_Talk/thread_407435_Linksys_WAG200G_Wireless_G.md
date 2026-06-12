---
title: "Linksys WAG200G Wireless G"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by travsraven on 2007-04-12
I have been given a Linksys WAG200g Wireless Router as a thankyou gift from a friend of mine today. I have searched the forums about how to install the router in ubuntu and am feeling rather lost.

How do I go about installing that specific router and what do I need to do, because all I see are posts for other router versions and not the WAG200g. I have even done a google search and most links are for foreign sites which is off no use to me.

Can anyone please direct me or help me in directing where I need to go and install this router. Be easy on me as I have only been using Ubuntu for just about a month now so the clearer the instructions the better.

Thanks in advance.

---

### Post by mohjlir on 2007-04-12
You don't have to install any software to use your router. Do you have a ethernet connection to the router from your computer? If so, you can set it up using its web interface.

sudo ifdown eth0
sudo ifconfig eth0 up 192.168.0.10

Then open your browser and put in 192.168.0.1 as the address.

User: admin
Password: admin

Let me know if you get this far.

---

### Post by travsraven on 2007-04-13
mohjlir,

Sorry for the late reply, as I was on work call out and haven't been able to sort all this out until two hours ago. Thankyou for your help as it is appreciated.

I still am having a problem of sorts.

First I followed the instructions on linksys settings and put in my name and login code etc etc etc. That didn't work at first and I couldn't understand why, so went to another site and decided to try something that was totally irrelevant and changed one setting.

I went back into Optional Settings in basic setup and changed the MTU settings from Automatic - 1500 to manual - 1300. That seemed to have done the trick a little bit but still one issue needs to be resolved.

I am currently on Edgy and am with BT Broadband in the uk. My previous modem was a Alcatel USB modem, and once I set it up it ran fine and everytime when ubuntu loaded up. However it's not doing this with the Linksys Wag200g and I cannot figure out why this is the case.

Here is what happens, when the computer loads up, the linksys router dsl light flicks on and flicks off whilst ubuntu loads up. After I sign in the dsl light flickers again( sometimes it stays on and sometimes it doesn't ). At this point once the desktop is loaded the Internet light should be on too. However this is not the case, it doesn't show up at all. 

So I have to reboot the computer again and again and again until it decides to light up. I thought it was the wires, nope, checked that, thought it could be the linksys modem, but it can't be that as I am using it right now and it's all working fine.

I'm at a loss figuring out why this is happening ( checked with my old modem - all is well and loads up and runs everytime ) Has anyone experienced this and if so how did you resolved the problem? My other thought would the current router be fighting against the old file I installed for the alcatel usb modem? 

Any answers to this problem would be appreciated before I think about what to do next ie send it back.
So I am at a loss at to why this is happening

---

