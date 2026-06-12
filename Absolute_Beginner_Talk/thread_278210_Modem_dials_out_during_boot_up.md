---
title: "Modem dials out during boot up"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by rufousfelix on 2006-10-15
My 56K external Zoom modem dials out successfully when I boot up in xubuntu (installed from ubuntu server 6.06, but now pure xfce).  The problem is it's the only way the modem connects to the Internet.  

I tried using wvdial and setup wvdialconf per instructions, but I only see the init string in the log and get silence--no "talking."

I also tried using Gnome-ppp, but while I get dial tones, the connection goes nowhere and dies.

What I'd like is the modem not dialling out during boot, but don't know where to look to disable this default behavior.  That done, I think I probably can get wvdial working.  

By the way, I have a wi-fi PCMCIA card that works perfectly (at least there I can use WiFi-Radar in the xfce environment to turn it on during sessions).

---

### Post by _duncan_ on 2006-10-16
try this:

1. System > Administration > Networking
2. click on 'Modem Connection', 'Properties' button and finally the 'Options' tab.
3. Make sure the 'Set modem as default route to internet' checkbox is NOT checked.

---

### Post by rufousfelix on 2006-10-16
Thanks, Duncan.  Yes, I'd seen that was the likely culprit in searching through posts.  Unfortunately, I can't do anything as direct as System>Administration>Networking>Options because I don't have that menu with a pure XFCE install.  That's not strictly true, however, because one does have the option under XFCE of launching Gnome services, an option I'll try.

But first, I was wondering if someone knowledgeable about relevant file settings could point to where System>Aministration>Networking>Options writes its value.

I might mention the /user/.wvdialconf and /etc/wvdialconf files appear okay.  The /etc/network/interface file, however, has the following two entries at bottom:

iface ppp0 inet ppp
provider ppp0

auto ppp0

Is that last line a culprit?

Lastly, some of the quirky behavior of wvdial might be due to an erratic serial cable, which I will replace today.  Still, serial cable functionality is a side issue to the long-standing dial out on boot problem.

---

### Post by rufousfelix on 2006-10-16
Okay, the modem works perfectly now in pure xfce xubuntu.

To deal with the dial-out problem on boot, I went into /etc/network/interfaces and changed "auto ppp0" to "noauto ppp0."

I still had a problem with wvdial hanging with a "no carrier" msg and changed wvdial.conf as follows:

      add X3 to Init2 (means dial without waiting)

      add Carrier Check = no as a new line (useful for Smartlink modems)

      add Stupid mode = on as a new line (will start pppd immediately--required by some ISPs)

Things work fine now & if anybody else goes 100% xfce, they lose the System/Administration/Networking menu & would be advised to look at the two files above & a few others :) 

Lastly, the modem cable was not a problem, but the replacement only cost $4.99 @ Frye's (no tax or Oregon buyers!).

---

