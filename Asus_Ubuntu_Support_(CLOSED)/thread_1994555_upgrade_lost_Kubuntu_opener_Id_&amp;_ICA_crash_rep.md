---
title: "upgrade lost Kubuntu opener Id &amp; ICA crash report detected; &amp; HP printer craps out"
date: 2012-06-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ken78724 on 2012-06-02
Now have a Slower OS on my asustek PC. this happened after Upgrade from 11.10 to 12.04 LTS
Since the upgrade I see a "crash report detected" notice that has stayed with me two weeks. Also get a wragged pre login skin. The wragged skin won't correct itself evem with multiple updates. Actually I am not even sure if I have retained kubuntu as that skin no longer shows up when I boot up. 

To facilitate getting your help I analyzed my network on Terminal as of 6-2-12 9:30 PM. That is reported below.

ken@kenpc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:8234]
Kernel driver in use: forcedeth


if I cannot overcome these problems, I plan to do a back up to ubuntu one cloud. Then I can do a new install to 12.04 LTS. 
__________________
Mirus P5GC-MX with 750 giB HD; Linux User 470205 since 2002; Get a Linux User # @ [http://counter.li.org](http://counter.li.org)

---

### Post by ken78724 on 2012-08-10
Today I fired up this PC first time in two months. 368 updates awaited. Practically all are kde related. all failed to update. Leaves me disenchanted enough to find an alternative. :(

meanwhile, here's a problem analysis with the same NVIDIA output as I reported before setting this PC aside June 2, 2012. hmmm. 
ken@kenpc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8234]
	Kernel driver in use: forcedeth
ken@kenpc:~$ 


Intent is to back up all files so I can do a new install, possibly PC-BSD 9.1 Beta.

---

### Post by BigCityCat on 2012-08-11
You should try a clean install.

---

### Post by ken78724 on 2012-08-11
Many thanks BigCityCat. That's been my plan but files backup function repeatedly failed.

---

