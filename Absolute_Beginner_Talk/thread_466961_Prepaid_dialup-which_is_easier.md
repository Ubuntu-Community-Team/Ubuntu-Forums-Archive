---
title: "Prepaid dialup-which is easier?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by mysexybluefeet on 2007-06-07
I'm trying to set up prepaid dialup for ubuntu and i'm having problem after problem. First tried bigpond and tried using bpalogin, got the modem a driver, used scanmodem, followed all the directions from the documentation, looked in the log files of bpalogin, and it told me it couldn't find the config file.  The dial tone hasn't sounded yet. 

Then in fustration I thought about using a different dialup prepaid, maybe optus.  Can any one give me advice on which is easier to set up (i'm a real noobie) or where i'm going wrong . Thankyou!!

---

### Post by HereInOz on 2007-06-07
Are you using an internal or external modem.  External serial modems are much easier to get working with Linux because they don't need the special PCI drivers that the internal ones do.

If it is an external modem, you should be able to install GnomePPP as your dialling utility, get it to find the modem and you ought to be there.

If you are using an internal modem, then it is probably a lucent win modem, or similar, and you are going to have to do some research on getting it working.  Apparently it can be done, just I have never done it.

Your choice of ISP should make no difference.

Cheers,

Alan

---

