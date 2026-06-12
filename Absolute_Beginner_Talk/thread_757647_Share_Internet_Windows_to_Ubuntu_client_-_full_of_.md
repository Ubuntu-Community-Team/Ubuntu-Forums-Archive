---
title: "Share Internet: Windows to Ubuntu client - full of fail :("
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by rawry89 on 2008-04-17
Good day,

For months I have lived merrily with my Ubuntu computer connecting to the Internet through a Windows computer in another room. However, recently something mystical happened and the connection has dropped as well as any folder sharing from Ubuntu to Windows.

My computer: Ubuntu Gutsy

Other computer: Windows XP

Internet: ADSL (connected to my computer through Windows computer with a cable)

There is a communication between the computers - just..not much. Mayhap it is the cable but the cable seems to be in top order.
I have tried experimenting with the connection settings for weeks, but alas no avail :( I reformatted the Ubuntu computer to see if that would help and it naturally did not. I do not know what to do! I have deleted the connection on the Windows computer and attempted to 'redo' a connection. I have searched on the internet for solutions but nothing is working for me. I am at a loss!
This has happened once before when I had Windows instead of Ubuntu and I fiddled with the local area connection and somehow fixed it (IP address fiddling), but I have not been lucky this time.

I am not sure what other information to add. Networks are ever so fickle.

Any recommendations will be greatly appreciated :) I need my connection back to my Ubuntu machine as this will greatly help with University readings and general study!

---

### Post by northern lights on 2008-04-17
Do I get you right when I understand you've set up a gateway on you XP system and the XP machine's got two ethernet devices, one connected to the ADSL modem and one connecting to your Ubuntu machine?

--> A simple hardware solution would be to invest in a router. You should get one for less than 40 USD / 30 EUR / 20 Pounds.

In order for us to help, can you post the outputs of ```
lshw -C network
``` and ```
route -n
``` and maybe also ```
cat /etc/network/interfaces
``` from your Ubuntu machine?

P.S. the net on the XP comp works fine, right?

---

### Post by hyper_ch on 2008-04-17
doesn't the adsl modem have router capabilites and two plugins for ethernet?

---

### Post by northern lights on 2008-04-17
> **hyper_ch said:**
> doesn't the adsl modem have router capabilites and two plugins for ethernet?
That would indeed be the easiest. And pretty funny if it was overseen...

;-)

---

### Post by hyper_ch on 2008-04-17
even if it does not, then buying a seperate router would solve a lot of issues... they aren't that expensive anymore... not even wifi routers...

---

### Post by northern lights on 2008-04-17
I concur. +1 for a router.

---

