---
title: "Problem Duel Booting"
date: 2010-12-19
forum: Apple Hardware Users
---

### Post by Hursty1 on 2010-12-19
Hi guys i'm new and wanted to try duel booting Ubuntu on my mac book.

So i downloaded the 64bit edition of ubuntu burned it to a cd as an ISO then installed.
After i updated ubuntu this morning my system wouldn't boot at all either ubuntu or OSX 10.6 (snow leopard). I tried the live CD for ubuntu wouldn't boot, i tried the mac OSX cd and it wouldn't boot. I tried opening disk utilities by holding C when booting, i tried forcing a boot by holding x and still no luck. Finally i had to remove the disk and using my spare enclosure for 2.5 stata drives, i removed the hard drive and had to manually format it on my GF's mac using it as a external drive.

This has solved my problem i was able to reinstall mac OSX and then upgraded to 10.6 again and finally migrate all my files from a back up along with settings over. 

My question is how might i prevent this from happening in the future. Also i don't know what happened i assume something over written the EFI boot loader or something like that. I'm trying to learn so any info into what happened would help me out or pointers on what i did wrong or if there was a alternative method to fixing what happened.

So if i was going to try to  reinstall ubuntu how might i go differently to prevent complications? Also i do mapping work and use GIS software so i'd like to also have windows on my laptop, is there a way i can tri-boot with out having to load an additional boot loader to the bootcamp one?

Thanks Hurst.

---

### Post by yugnip on 2010-12-19
Hi. Have a look at the community tutorial here: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

That should get you up to speed. If you have further questions, post again. 

BTW, if something ever happens again, instead of removing the HD, try using another mac as a Host and booting your mac into Target Disc mode. You can do this by connecting your mac to the Host machine via firewire, then booting your mac while depressing the T key. Your mac will show up on the Host mac as a HD and you should be able to run Disk Utility from there.

Hope this helps.

---

