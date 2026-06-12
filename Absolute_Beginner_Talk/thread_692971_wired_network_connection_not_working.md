---
title: "wired network connection not working"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-10
I trying to get my laptop to work with a wired ethernet connection.
It works wired at my house but at another house I can't get it to work.
It displays " wired connection established"  but I can't make any connections to the internet.

I'm on another computer so I can't paste my results but ifconfig shows an inet address that is completely different from anything that shows up on windows ipconfig on a Windows maching using the same router & chord. 
route - shows only a genmask # & nothing at all under default.
I chaned the settings - system>administration>network... to enable roaming but it did'nt make any difference at all.

---

### Post by eggdeng on 2008-02-10
I'm afraid your post is a little difficult to follow so perhaps you have already checked the following but just in case,
First see if you can ping the router. If you can, the connection is working and you will just need to configure DNS.
If not, check whether the router in the house where you are trying to connect is configured to use dynamic or static IPs.
In System->Administration->Networking, configure your wired card accordingly.

---

### Post by garyed on 2008-02-10
WelI I just left the house I was at so I can't test anything to see if it will work.
In my first post I meant to say "machine" instead of "maching".
I was typing my questions on a Windows computer plugged in to the cable co. router  accessing 
the internet fine. I just unplugged the ethernet cable from that computer & plugged it into my laptop running feisty & it wouldn't connect to the internet even though the icon at the top of my screen showed my wired connection was connected.

I'm home now & my wired connection works fine now.
I don't know why it wouldn't work the other place.
I'll fight the battle another day.
Thanks for the help anyways.

---

### Post by ugm6hr on 2008-02-10
If "roaming" wasn't enabled before you turned your laptop on, it might not have worked.

Without roaming, you need to switch the computer on with the ethernet already connected.

---

### Post by garyed on 2008-02-10
> **ugm6hr said:**
> If "roaming" wasn't enabled before you turned your laptop on, it might not have worked.

Without roaming, you need to switch the computer on with the ethernet already connected.

I'll try that next time.
roaming was not enabled when I first turned the computer on but I did enable it afterwards.
I did reboot once while I was there but I can't remember if it was before or after enabling roaming.

---

### Post by texasjim on 2008-02-27
You didn't say if the ISP you are using permits more than one MAC address to be connected.  I am on Time-Warner cable and if it is necessary to move the cable from one computer to another the cable modem must be reset each time the cable is moved. If this is too cumbersome (it is), then install a wired router (not a workgroup hub)with the modem cable plugged to the WAN socket on the router.  I got one at my local Goodwill for $%US.  Good luck.

That's $5US.

---

