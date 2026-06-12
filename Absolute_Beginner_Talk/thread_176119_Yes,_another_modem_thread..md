---
title: "Yes, another modem thread."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Sho™ on 2006-05-14
Hi.

I've just recently installed Breezy Badger and I'm having a few problems with getting the modem to work. It's a SoftV92 Data Fax Modem (according to Device Manager in Windows), LSPCI tells me: Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller.

At first I could't detect the modem at all, however in Windows it's situated on 'COM3'. I figure there is an alternative port for Linux (obviously not dev/modem) and found that it was there on dev/ttys2. All well and good, but whenever I try to query the modem or dial out, I get a busy response.

If anyone could help me with this, it would be much appreciated. :)

---

### Post by az on 2006-05-14
What windows is saying is COM3 is irrelevant.

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Maybe this:
[https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4)
or this:
[https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

---

