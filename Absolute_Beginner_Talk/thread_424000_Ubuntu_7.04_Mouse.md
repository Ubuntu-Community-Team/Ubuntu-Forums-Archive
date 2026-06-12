---
title: "Ubuntu 7.04 Mouse"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by mjmjohn on 2007-04-26
OK I admit it-- I'm a complete noob when it comes to Linux. I installed VPC 2007 on my computer and tried to install 6.1 on it, but the screen was garbled and the help that I looked up told me to hit CTRL+ALT+F1 to go to text mode, but that was totally unreadable......Sooooo I also found where someone said to that 7.04 did not have that issue. I downloaded the alternate.iso and installed it. Although the screen was garbled, going to text worked great. I was able to set the color depth back to 16 from 24 and the GUI looks wonderful. Now I can't get the mouse to work!!! I've tried everything I can think of, and I haven't been able to find what the problem might be. Can anybody help me???? I really want to try Linux but I've spent hours trying to get it to run.

---

### Post by igknighted on 2007-04-26
> **mjmjohn said:**
> OK I admit it-- I'm a complete noob when it comes to Linux. I installed VPC 2007 on my computer and tried to install 6.1 on it, but the screen was garbled and the help that I looked up told me to hit CTRL+ALT+F1 to go to text mode, but that was totally unreadable......Sooooo I also found where someone said to that 7.04 did not have that issue. I downloaded the alternate.iso and installed it. Although the screen was garbled, going to text worked great. I was able to set the color depth back to 16 from 24 and the GUI looks wonderful. Now I can't get the mouse to work!!! I've tried everything I can think of, and I haven't been able to find what the problem might be. Can anybody help me???? I really want to try Linux but I've spent hours trying to get it to run.

I'd just run the liveCD to test on your machine... runs on your true hardware so you can see what it would do if you actually installed, but doesn't touch your HD's at all.  I feel like this is a VPC issue.  I would steer you towards VMWare server (its free) or VirtualBox (i think it has a windows version).  In the very least with these two there will be people here who understand them.

As for your issue, are you using a USB mouse?  In other virtualization software, you need to explicitly enable what USB devices to show to the virtual machine in the program setup, you might need to set up a USB device for the VM for the mouse.

---

### Post by mjmjohn on 2007-04-26
Thanks for the quick reply...I have run the live CD and was impressed. But I wanted to see the speed of the OS from an install. Run apps from CD can be quite slow.
I'll try to ge a copy of VMWare server and try it there.

---

### Post by wittelw on 2007-04-29
Sorry if this is a dupe. Didn't see my quick reply so am trying again...

[http://blogs.technet.com/seanearp/archive/2007/04/28/ubuntu-7-04-feisty-fawn-in-virtual-pc-2007.aspx](http://blogs.technet.com/seanearp/archive/2007/04/28/ubuntu-7-04-feisty-fawn-in-virtual-pc-2007.aspx) has some links that sound like blocking issues (kernel bugs in 7.04) when running in Virtual PC.



OTOH [http://linux.slashdot.org/linux/07/04/27/1337246.shtml](http://linux.slashdot.org/linux/07/04/27/1337246.shtml) points to a review that claims to have installed on Virtual PC 2007 ([http://www.informationweek.com/news/showArticle.jhtml;jsessionid=W25M4BPNXYZPUQSNDLPSKHSCJUNN2JVN?articleID=199201179&pgno=2&queryText=)](http://www.informationweek.com/news/showArticle.jhtml;jsessionid=W25M4BPNXYZPUQSNDLPSKHSCJUNN2JVN?articleID=199201179&pgno=2&queryText=)).



For now I decided to stick with 6.06 which was the only version I've been able to get running in Virtual PC, but if someone has had a successful experience running 7.04 under Virtual PC it would be great to hear about it.

---

