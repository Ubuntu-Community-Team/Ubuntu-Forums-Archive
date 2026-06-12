---
title: "Network card disabled at install"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by cdenk on 2007-12-29
I have a P4 motherboard with Realtek RTL8139 network card. When installing V7.1 (either Ubuntu or Kubuntu) the LED's at the network cable ends are "off", and stay off during and after the install, and not able to use the network. The other end of the CAT-5 goes to a Zoom X6 ADSL + 4 port router (one othe computer here) + Wireless (disabled). The system is dual boot XP Pro, and network works fine when using the XP. Per Realtek's site, the cards drivers are included in Linux. The automatic DHCP config fails, and I enter the gateway of 10.0.0.2, and then later the other 3 ports addresses.  The install is particularly slow at the apt-get stage, probably since the network is not available.

Seem strange that the install would shut off the network card to the point that no lights are active. Any help would be appreciated.

---

### Post by rustutzman on 2007-12-29
Is network manager running? If you right click on it is your network enabled? Is the card listed under System/Preferences/Hardware Info?

Russ

---

### Post by p_quarles on 2007-12-29
Use this command to find info on your available networking hardware:
```
ifconfig -a
```
This may show the problem, or at least point in the right direction.

---

### Post by cdenk on 2007-12-29
Problem solved, I think!

Previously during the install the Network activity led's were off, and stayed off. I aborted a Windows ZP Pro install early on. The activity led's were on from the beginning of the install, and remaining on when the Kubuntu install was started, and staying on continuously, except for some periods of traffic while install configured the net, or downloaded material. The DHCP install went through automatically.

Only thought I can see, is the install does not try to activate the network card if it happened to been disabled. :)

---

### Post by cdenk on 2007-12-31
Problem solved, well, kind of! Switched the network cards in the 2 computers and no problem. Here is the current configuration, note that the issue is with the Network cards switched:
Motherboard: Intel W845-WN, 1.6 Gig P4, Network Card: Accton Technology Corporation SMC2-1211TX, Win XP SP2

Compaq Presario 5310US, NetworkCard: Realtek RTL8139, Win XP Home SP2

In searching for a solution, I found numerous people having problems with Realtek card over many releases, including where the bug was closed as a bios problem. This card has worked for several years in the first computer with both Win 98, ME, and XP Pro. The fact is that if the card is disabled on Linux boot, it is never turned on. Windows DOES TURN ON the card about the time the splash screen appears. This sort of thing WASTES all sorts of time, and is a big negative for Linux. :-({|=

---

### Post by p_quarles on 2007-12-31
I understand the feeling, but there really is very little Linux developers can do about a BIOS problem. The real waste, imho, is that so many hardware manufacturers are shipping such limited and inflexible BIOSes. There are settings I would very much like to change on all of my comps, but the firmware just doesn't have the option.

In any case, some developers are working on an open source firmware replacement. It's slow going, but it already works well with a number of motherboards. The point being simply that open source developers are well aware of and concerned by these kinds of issues.

---

### Post by cdenk on 2008-01-01
It seems to me that the Object of the Linux movement is to provide an alternative to the Windows environment, which I welcome, and object is to operate functionally on the majority of hardware that Windows functions on. The fact is that the hardware in question is widely used and produced by noted manufacturers. In this case Linux claims to be compatible with the Realtek RTL8139 and includes the appropriate drivers, which is not the case, and this hardware should be removed from the list! 

Well, maybe if that motherboard had been made by a less famous manufacturer than Intel, and the network card by someone famous like Belkin the story would be different! In fact the Belkin F5D5000 card requires a Realtek RTL8139 driver in XP, see: [http://belkin.httpsvc.vitalstreamcdn.com/belkin_vitalstream_com/support/dl/f5d5000_xp.pdf](http://belkin.httpsvc.vitalstreamcdn.com/belkin_vitalstream_com/support/dl/f5d5000_xp.pdf)

Then that lead me to Realtek, where I found the last revision of their driver is dated 11/20/2007  see: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Conn=4&DownTypeID=3&GetDown=false&Langid=1&Level=5&PFid=6&PNid=6](http://www.realtek.com.tw/downloads/downloadsView.aspx?Conn=4&DownTypeID=3&GetDown=false&Langid=1&Level=5&PFid=6&PNid=6)

Then which network card should I buy, that will work without question?

and if you look at the release notes for date 10/20/2007 you will find there was an issue that "can't wake up in some platforms'

Again my issue is, it is claimed that Linux has drivers for hardware, but in fact they don't work on a large population of hardware. Google for this issue will find many forum articles, essentially all end with no resolution.

As a little off topic, The PC architecture is long overdue for replacement, the backward compatibility to 1980 structure is terrible. It's been patch on patch, and work arounds where things are so intertwined, it's impossible to add something without messing up something else. 

If you have drivers that  need Beta test, let me know, but I warn you, I'm new to the Linux area, but not afraid of terminal, would need instructions to load. :)

---

### Post by cdenk on 2008-01-01
A further thought, it appears (by looking at dates in release notes)  that Realtek is active with revising drivers for both Windows, Linux, and other OS, but appears they have stopped some of the Linux work, possibly thinking that the Linux community has taken over the work. Prehaps a conversation with Realtek would prod them to take the issue on, either wholes or as part of a team effort. They may be happy to take on the activity. :)

---

