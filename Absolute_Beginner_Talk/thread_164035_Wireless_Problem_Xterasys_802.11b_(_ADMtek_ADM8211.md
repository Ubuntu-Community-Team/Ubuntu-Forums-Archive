---
title: "Wireless Problem Xterasys 802.11b ( ADMtek ADM8211)"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by AFJeremy on 2006-04-22
Hello Forum!

I am running a dual boot Win/Kubuntu.  I have a cheap xterasys 802.11b cardbus wireless adapter, which uses the  ADMtek ADM8211 chipset.  It was not detected on installation.  I have no clue how to initalize and utilize my wireless.  This is the main reason why I have stayed away from linux, every distribution I try to use, wireless doesn't work.  If anyone can help me get this working I would LOVE to learn how to use linux and expand my horizons so to speak.  I am using an entry level Dell Inspiron 1000 laptop.  Any help would be greatly appreciated!!!!


AFJeremy

---

### Post by Sandlst on 2006-04-22
Check out the wireless troubleshooting guide located [here]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide").  Also, since you are working with a cardbus card, be sure and read the bottom part if nothing seems to work-adding the line pci=assign-busses to your boot options(it describes how to do it in the guide) is the only way I can get wireless working.....the first dozen times I tried to get it working, I never read that part, seven months later I notice it.....:rolleyes: hopefully it will save you some headache.  Good luck! Post back if you have any problems.

---

### Post by mybootorg on 2006-04-22
I had a very similar problem earlier this morning with my wireless card not getting recognized.  I was a little worried because it was a Dell OEM laptop. But I found a nice tutorial on using a package called NDISWrapper to convert the Windows Driver on Dell's website to a driver that works with Ubuntu.

So in addition to resource pointed out above, check out:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")

---

