---
title: "Modem problem"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by TonyRobson on 2005-07-17
Hi,
Ubuntu seesm to think I am connected without dialling in?  Where do I dial in and how can I tell the browser and e-mail I am not connected and that they should dial in?
Tony Robson
[email]tonyrobson@absamail.co.za[/email]

---

### Post by damonw5 on 2005-07-17
Hi Tony,

You will need to enable your modem in the Network setup under the "System" menu. Does that work? Post back here to let us know if you need more help.

---

### Post by TonyRobson on 2005-07-23
Hi
Thanks so much for your reply.
If we can correspond directly via e-mail I would really appreciate it.
My address is [email]TonyRobson@absamail.co.za[/email]

This is what I do...
I go to System, Administration, Device Manager.
Here I see a device Smartlink Smart PCI 561 56K Modem - ALi Corporation
My modem is actually an internal LG LM-I56N but I understand it uses a chipset from someone else?

I then go to System, Administration, Networking where I see Modem Connection and Ethernet Connection
I select Modem Connection and then click Properties.
The tick box "This device id configured" is NOT ticked.
I tick it and set up my ISP Data and Account Data
I then click the modem tab.  If I click the Auto Detect button it just goes walk-about for ever.  In Windows my modem is seen as COM3 so I select port TTYS2.
I go back to the Device screen and click Activate.  The Modem entry gets colour but there is absolutely no modem activity?
Firefox still thinks it is "on line".  How can I tell it that it needs to dial up first?

Regards,

Tony Robson.

---

### Post by az on 2005-07-23
You need to install the proprietary drivers for your modem:

[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

The reason your machine thinks you are connected could be that you have an ethernet card that is configured with a static address?

---

### Post by TonyRobson on 2005-07-27
Nope - no fixed IP address.  No network cable either.  This is a stand alone home pc.

---

