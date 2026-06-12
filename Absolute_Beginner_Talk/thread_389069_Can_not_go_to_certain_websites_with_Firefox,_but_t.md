---
title: "Can not go to certain websites with Firefox, but they work in ELinks and IE on reboot"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by bobsacks on 2007-03-20
I am having an odd problem. Up to a few days ago I could go to any website I wanted. Now I can not go to a few sites - cdw.com, dell.com, amerisave.com, the customization pages on hp.com, and a few others.

I can not get these sites to open using Firefox on Ubuntu. If I reboot to Windows on the same box I can get there from IE7. If I load Firefox in safe mode I get the same result. I ran the Ubuntu Live CD and got the same result. I installed Opera and get the same result. I put the live CD in another box and got the same result.

I started up a Windows XP Virtual machine inside Ubuntu and tried to go to the sites using IE and it did not work.


The guy sitting next to me using Gentoo does not have this issue and the other guy sitting next to me does not have this issue with windows.

I have ran Wireshark and have found what appears to be the issue. Using ELinks I do not get the following packets - 
Ethernet II, Src: Dell_71:b7:4a (00:15:c5:71:b7:4a), Dst: IETF-VRRP-virtual-router-VRID_03 (00:00:5e:00:01:03)

Does anyone have any idea on what it might be?

---

### Post by crispy_420 on 2007-03-21
Do you have java runtime installed as a plugin for your browser?

I went to hp.com to test and had no luck via firefox with java blocked. Once I unblocked/allowed java it worked just fine.

---

