---
title: "Mac Mini - Ethernet port and wireless won't work"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by jncash on 2008-06-01
Has anyone had this problem?  I have a mac min, (intel), I have Windows XP and it runs just fine, I also have Lepoard as the Mac OS and it runs great too.  How ever with Unbuntu 8.4 I cannot get it to recognize the Wireless and wired Network interface cards.  Has anyone had this problem and if you did, how did you solve it.  I am new to Mac and Linux, just testing different operating systems.  For me, Windows so far is the easiest to use and to solve problems.  Any help with getting on the internet with the Linux Virtual Machine (Using Parallels) would be greatly appreciated. 

Thanks JNCASH

---

### Post by cyberdork33 on 2008-06-01
> **jncash said:**
> Has anyone had this problem?  I have a mac min, (intel), I have Windows XP and it runs just fine, I also have Lepoard as the Mac OS and it runs great too.  How ever with Unbuntu 8.4 I cannot get it to recognize the Wireless and wired Network interface cards.  Has anyone had this problem and if you did, how did you solve it.  I am new to Mac and Linux, just testing different operating systems.  For me, Windows so far is the easiest to use and to solve problems.  Any help with getting on the internet with the Linux Virtual Machine (Using Parallels) would be greatly appreciated.
Just to clarify, Are you running Ubuntu in a VM or are you running it natively on the actual Mac hardware? If you are just running it in a VM, then you have to configure the networking device in the VM configuration, your problem is not with Ubuntu. (also, for WiFi, you don't use it in Ubuntu... you connect in OSX (or Windows whatever you are using) and the VM uses that connection to get internet access.

---

### Post by jncash on 2008-06-02
hello thanks for responding:  I am running Unbuntu in a VM using parallels.  I can use the Wireless in the Windows VM, but it doesn't work for the Unbuntu VM.  I will look closer at the Networking Device in the VM.  I may have missed something, but as for the wireless, I can click outside of the VM to get back to the MAC OS and wireless works just fine. It just doesn't want to in Unbuntu VM.  Thanks again for the response. 

Jncash

---

### Post by jncash on 2008-06-02
Your the man Cyber, I was able to remove the default setting I had and go with the shared connection.  I had to delete the old default setting,that was where I was messing up.  I would click to change and when I opened the vm it didn't get the new selection.  I also had to tinker with "System" "administration" "network" "network settings" so Unbuntu could see the wireless.  Thanks for setting me straight.  I was just about ready to whine about how hard it is to get linux to work. ](*,)

Peace:

---

### Post by mfox on 2008-06-02
For what it's worth, I have Ubuntu 7.10 running on my Intel iMac through Parallels and both 7.10 and 8.04 running on my Intel mini through VMware Fusion.  I haven't had to play with any Ubuntu settings to get my ethernet working on the iMac and AirPort on the mini.  In both cases I just accepted whatever options the Ubuntu installer provided.  The biggest problem I've had with the later versions on each system was installing the Parallels/VMware tools packages, which are what provide much of the dual OS functionality.  Neither program focuses on Linux and their stated compatibilities are for earlier versions (7.04 on Parallels).  In both cases it took a bit of tweaking to get the tools installed on the versions I'm using.  In the case of Parallels, there are multiple posts in various forums that state that Parallels Tools cannot be installed on 8.04, yet, and no timeline has been given by Parallels for when that will be fixed.

One other thought.  Parallels did come out with an update in the last month or two.  Make sure to get that update.

---

### Post by jncash on 2008-06-02
to Mfox:  I do my update checks every time I log on, I think I have the latest update.  When I first installed Unbuntu, I had the Ethernet cable plugged in.  I think the install didn't consider the wireless (if that makes sense).  I never saw or heard about a tools package for Linux either, it's (parallels) more interested in making windows work on a Mac.  Well this is the first time using Linux that every thing seems to work, sound, video, internet, etc.  Usually there would be one or two things that just won't work.  So now I can seriously check out linux and see what ever one is raving about.  

Peace

---

### Post by mfox on 2008-06-02
The tools package I meant was Parallels Tools, not Linux tools.  If everything is working, including instantaneous windows resizing, then you must have the tools already installed.

---

### Post by cyberdork33 on 2008-06-02
> **jncash said:**
> to Mfox:  I do my update checks every time I log on, I think I have the latest update.  When I first installed Unbuntu, I had the Ethernet cable plugged in.  I think the install didn't consider the wireless (if that makes sense).  I never saw or heard about a tools package for Linux either, it's (parallels) more interested in making windows work on a Mac.  Well this is the first time using Linux that every thing seems to work, sound, video, internet, etc.  Usually there would be one or two things that just won't work.  So now I can seriously check out linux and see what ever one is raving about.  

Peace

Most vitural hardware is pretty well supported in Linux. You need to separate the concept of your VM and your Mac though. running Ubuntu in a VM is ***not*** running Ubuntu on a Mac. In a VM, the OS doesn't see the "real" hardware, it sees virtual hardware. Because of this, there is really no reason to "get your wireless working in the VM". Your wireless card is managed by the Host OS, the VM uses it's virtual ethernet card to use the Hosts connection as it's own.

---

