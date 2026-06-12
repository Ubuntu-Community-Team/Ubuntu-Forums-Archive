---
title: "Desktop CD fails to boot on ibook G4 while loading kernel"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by keyshawn on 2006-06-03
Hi,

I tried to boot the newly released 6.06 (LTS) Dapper 'desktop' on my ibook g4, 
(1.42 GHz, relatively newer model, bought in August 2005). 
The CD was recognized, but when after I hit enter (at the first text screen) to run the cd on default, the message 'kernel is loading....' came up and froze. 
I also tried to do the option "live video=ofonly" (iirc, the option may be a bit different, i forget, I'll change next time around.) that was suggested on that first text screen as well. 

Just to note, I was able to successfully boot the 6.06 live beta CD without any significant problems. 

I looked at malone and found a bug report that might apply to my situation - [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)
but I'm not sure if it's the same situation. 

(Does the new Dapper use the [2.6.15] same kernel that is in the bug report ?)

Regards,
keyshawn

---

### Post by nkbj on 2006-06-07
Yes, dapper was released with the buggy kernel. A fix has been commited and will be released with the next kernel update.

Regards,
Niels Kristian

---

