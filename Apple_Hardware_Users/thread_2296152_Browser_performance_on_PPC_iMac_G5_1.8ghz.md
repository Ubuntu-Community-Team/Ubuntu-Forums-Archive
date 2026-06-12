---
title: "Browser performance on PPC iMac G5 1.8ghz"
date: 2015-09-23
forum: Apple Hardware Users
---

### Post by Saml01 on 2015-09-23
I am running Lubuntu Trusty 14.04 on a PPC iMac G5. In order to get video I have to run it with* yaboot parameter "nouveau.config=NvMSI=0*". The issue I am having is that whenever I load a site like last.fm or even CNN the browser grinds forever it seemingly never loads. The task manager indicates the CPU is bouncing arond 80 - 100 percent and it is all being used by the browser. Even just typing in the browser as I post this kicks ups the cpu usage to 50% or more. The condition exists whether I am using firefox or midori. I tried looking into the cpu throttling and with cpufrequtils I was able to confirm and configure that the system to using ondemand governor. I tried setting it to performance but that had no affect on the browser even though I can see the cpu was running at 1.8ghz. In an attempt to fruther improve performance I looked into the swap settings. So I knocked swappiness down to 10 from 60 and it seemed to improve the system performance but the browser is still slow whenever its open.

The only thing that I have not tested was going back to Mac OSX and seeing if the browsers and the pages react the same way.

But before I do that, I am starting to wonder if this has to do with nouveau running the way it is OR could something else that I am not familiar with. Any suggestions would be greatly appreciated. I dont want to believe that this system is that slow that I can't even use it for basic web browsing.

---

