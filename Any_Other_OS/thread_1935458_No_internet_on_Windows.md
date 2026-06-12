---
title: "No internet on Windows"
date: 2012-03-04
forum: Any Other OS
---

### Post by beceraful on 2012-03-04
2-3 months i do not have internet. The failure of the entire city was shut down. When the failure got back , i do not have internet on windows.. Everything is working , IP , and everythink else. I see one thing on Services/ DNS Client was shuting off.I turned on but again no internet. Tell me what to do people if i got internet there. I won't need to fix the sound problem here (on linux).

I am on windows 7 ultimate,  please help.

I know this is a ubuntu forum but i can't find a forum where could i post this , or if i could find there are not people there. Please help and thanks :S :P

---

### Post by CharlesA on 2012-03-04
Try here:
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by 0011235813 on 2012-03-04
> **beceraful said:**
> 2-3 months i do not have internet. The failure of the entire city was shut down. When the failure got back , i do not have internet on windows.. Everything is working , IP , and everythink else. I see one thing on Services/ DNS Client was shuting off.I turned on but again no internet. Tell me what to do people if i got internet there. I won't need to fix the sound problem here (on linux).

I am on windows 7 ultimate,  please help.

I know this is a ubuntu forum but i can't find a forum where could i post this , or if i could find there are not people there. Please help and thanks :S :P

The first thing to consider is where do you live? It sounds like your ISP has a failure, is it working in Linux?

One of the common problems is DNS; if you've enabled a **D**omain **N**ame **S**ervice, you would have had to set your system to use automatic DHCP addresses only, but if you no longer use DNS, you must make it automatic DHCP addresses. 

Another potential issues might be drivers, you could try doing a system restore and see if that resolves the problem.

---

### Post by wolfen69 on 2012-03-05
Press F8 to get into safe mode, insert windows disc and run **sfc /scannow** in a command prompt.

---

### Post by afhx on 2012-03-07
If you have a dongle then search for Sakis  on line to find a script which reliably connect you to the internet. The problem which might arise  is because you have windows you might not have the requisite programs installed. It won't harm your system to try([www.sakis3gord/versions/latest/i386](www.sakis3gord/versions/latest/i386))

---

