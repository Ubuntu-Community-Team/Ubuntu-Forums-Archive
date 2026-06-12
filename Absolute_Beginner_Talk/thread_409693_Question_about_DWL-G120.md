---
title: "Question about DWL-G120"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by nar57981 on 2007-04-14
Hey I've been admiring Ubuntu for a while and I've finally decided to dual boot my computer with (hopefully) v6.10 Edgy. I've been scanning the forums and hardware support pages to see if the D-Link DWL-G120 wireless card works with Edgy and what I need to do to install it; but I haven't been able to find anything. I saw something about "prisma02" and I googled it but there weren't any real straight answers, and if it was straight, there was a bunch of technical jargin thrown in that I don't understand. This is the only thing holding me back from installing Linux on my computer, so could someone please tell me:

1) Will/Should this work with Ubuntu v6.10?

2) What drivers do I need to get/what do I need to do to install this card on the system?

Thanks for the help!

(P.S. sorry if this seems pretty remidial to you linux gods out there :) )

---

### Post by N Clement on 2007-04-14
One of our rival forums (shhhhh) has a hardware compatibility section for linux compatibility in general.  I found [your card]("http://www.linuxquestions.org/hcl/showproduct.php?product=2117&cat=all") there.

---

### Post by nar57981 on 2007-04-14
Alright, thanks for the help.

On the site you gave me, it says:
"I run "/sbin/modprobe ndiswrapper" then "dhclient wlan0" after every reboot then it works great!"

Could you tell me what exactly that does? I'm guessing that I'm going to have to do this every time I reboot to enable the card? because the install tutorial says to just enter "sudo ndiswrapper -m" and it will work on boot.

One more thing, on the intall instructions [here]("http://members.driverguide.com/driver/detail.php?driverid=189755") it has in the .zip file:
1) g120.inf
2) PRISMA02.cab
3) PRISMA02.sys
4) PRISMIOC.vxd

and in the instructions it says only to unzip .inf and .sys files into my Ubuntu directory, should I just unzip everything? (btw the person who wrote the page listed ubove has a generic account: u:driver2, pw:all)

Also the install site I was looking at is different what the person says, which is [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Install")

Thanks for all the help again!

---

### Post by Maestro23 on 2007-04-14
Ndiswrapper Doc: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Might be of some help.  Good luck.

---

### Post by Linux_oid on 2007-04-14
I've had DWL-G510 about two yers in a row. At the time I was trying several distros. *Ubuntu* was one of a few that just recognized it (no additional driver neded) and had simple utility to set it up. 

WDA-1320 (second box): it's just worked with *Ubuntu*. I tried some Linksys and e-Home card with no luck.

WDA-1320 costs about $60.00 now (I spent $35.00 at the end of last year). So my third box has DWL-G510 as well ($29.95 on newegg.com). 

Small problem: DI-524 (wireless router) had run DHCP server. When one box was online, second one couldn't go online. So I had to turn DHCP server off and manually set IP adress.

---

### Post by nar57981 on 2007-04-14
Alright, after reading it for about half an hour (at least) I think I understand. But I have one questions. I'm planning on DLing everything I need and then putting it on a flash drive. And theres two things telling how to install the drivers. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy") and on step 8.1 that confused me for a while, am I supposed to follow the link and just skip 8.1?

---

### Post by N Clement on 2007-04-15
I'm not really sure I'm clear on what part of the procedure is causing you problems.  Which steps of that main ndiswrapper page have you completed?

---

### Post by nar57981 on 2007-04-15
I haven't done anything yet, I'm still working on installing it. But I think I understand what I need to do. I'll check back in if something happens.

Thanks again for the help!

---

### Post by nar57981 on 2007-04-15
Hey I still haven't loaded Ubuntu on my PC or tried the ndiswrapper, but I asked d-link customer support and they game me a link to [here]("http://support.dlink.com/faq/view.asp?prod_id=357"). Would the driver that is under my card work with Ubuntu, or would I still need ndiswrapper?

[Edit] - Sorry I forgot to tell you which version I have. I have vB1 of the adapter, so they tell me to use [this]("http://sourceforge.net/project/showfiles.php?group_id=59001&release_id=128821")

---

