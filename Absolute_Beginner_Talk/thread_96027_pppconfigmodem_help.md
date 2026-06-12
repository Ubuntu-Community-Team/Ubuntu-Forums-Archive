---
title: "pppconfig/modem help"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by defubar on 2005-11-27
I recently installed Ubuntu and eventually got the driver for my modem installed.  I then followed a tutorial from the Ubuntu Wiki for setting up pppconfig.  I don't know if I inadvertantly set my modem to dial itself upon loading Ubuntu or it automatically does this.  I would like to turn this feature off but I don't know what file I need to edit to turn this autodial feature off.

Also, another question related to my modem (Intel 536EP) and my ethernet (3com 3C940).  In order for me to use my Internet connection when I am on dialup, I am forced to disable my NIC.  Is there some way to change this?  If I go to "System > Administration > Networking" under the "Default Gateway" option I can only select my NIC or if I disable that, nothing.

---

### Post by defubar on 2005-11-28
bump

---

### Post by Mustard on 2005-11-28
are you using gnome-ppp to connect?

If you are I would be looking in the setup options for that to see if you have chosen for the modem to dial out on demand.

---

### Post by defubar on 2005-11-28
I don't have it installed but maybe I will install it and see if it is somehow enabled.  Thanks.

---

### Post by defubar on 2005-11-28
Hmmf, I did not see an option to dial out on demand in gnome-ppp.  Also, it dials as Ubuntu as loading, before I even log in.

---

### Post by Mustard on 2005-11-28
[QUOTE=defubar]Hmmf, I did not see an option to dial out on demand in gnome-ppp.  Also, it dials as Ubuntu as loading, before I even log in.[/QUOTE]

Hmm..sorry about that bit of misinformation then.  I had gnome-ppp running at the time, but I can't see the settings when I am actually connected.

I can recall this happening to me when I was using the System>>Administrations>>Network to configure my modem and then activating the connection through that menu.  Currently I have no configuration settings shown in that menu, as its all done by pppd.  At the time I was thinking it might be related to the attempt that ubuntu makes to synchronise the clock with an ntp server.  I have disabled this service in the System>>Admin>>Services menu.

---

