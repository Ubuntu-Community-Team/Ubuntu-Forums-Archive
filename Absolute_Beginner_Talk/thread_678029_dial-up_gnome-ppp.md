---
title: "dial-up gnome-ppp"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2008-01-25
Dial-up woes continue, as I have been unable to connect with gnome-ppp. Running the program does cause the line to be in use. I can hear analog transmission sounds if I lift the receiver, but eventually the maximum numbers of attempts is reached and the program times out.
I am using slmodemd.

What I have done is to follow a script in the screenshot below.
Currently I get two errors from wvdial or gnome-ppp. The first is "Cannot get information for serial port," but then modem initialization continues...everything checks out ok...modem is initialized...dialing goes through. Then "waiting for carrier" comes up, though I have tried everyway to disable carrier check. Anyway, finally gnome-ppp time out with the error: "NO CARRIER."
scanmodem looks good. I have found a link to an init script for gnome-ppp and wvdial.conf  AT&F E0 V1 &A3 &D2 &C1 S0=0  this script should allow V92 modulation and LAPM compression. I will try it next.
Any help would be greatly appreciated.

---

### Post by nowshining on 2008-01-26
it's prob. ur phone line - when we first moved from apt. 1 to 3 it was staticy so much static that one could not dialup, but even then the phone was not too much staticy - fixed now :)

is ur phone staticy, the modem u use can affect how much static it can accept when trying to dialin.

if there is a bit of static on ur phone - call ur phone carrier to come out and check the line - ours was old on the telephone pole and rusty, so they put a new one in and it's better now :)

---

