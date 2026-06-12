---
title: "Broadcom BCM4312 Wireless not working"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by rkb9572 on 2007-11-28
Hello all,

I am a Ubuntu and Linux newbie. So far, I love my Ubuntu. I do have an issue that appears to not be an uncommon one. I installed the BCM driver per instructions in another post. It appears it is connecting because I get a valid IP from my DHCP server. However, when I try to go to a web page or navigate my network I get nothing. Then I tried installing the ndiswrapper version via another post and now I don't even show a wireless adapter. Does anybody have any ideas? I am happy to supply any additional information you may need. Here is my set-up:

Dell Latitude D630
Intel Core 2 Duo 2.00 GHz
1GB RAM
lspci = Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Thank you in advance and I apologize for my inexperience on this subject.

Best regards,

Ryan

---

### Post by csharpy on 2007-11-28
I had similar issues with my Dell. I found the following link useful in returning to my condition prior to messing with ndiswrapper.

[thread]("http://ubuntuforums.org/showpost.php?p=2533847&postcount=67")

I've since parted ways with the laptop; So, I can't be of much more help. I can say that wifi was working without ndiswrapper. I did have to run "modprobe bcm43xx" after each reboot...annoying.

---

