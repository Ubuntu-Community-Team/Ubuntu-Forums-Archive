---
title: "Ubuntu 10.10 wont recognize my built in iSight."
date: 2010-10-03
forum: Apple Hardware Users
---

### Post by sean.simpson on 2010-10-03
Hello, 
i'm new to the ubuntu os and am having trouble with my isight built in webcam in my imac 5,2.  i followed the instructions at this url:  [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)
after following the instructions i shut down completely and rebooted, and neither cheese or skype are finding my camera. I confirmed that the isight.fw file was located in /lib/firewire/isight.fw.  i appreciate any feedback on this issue, and thankyou in adbvance for being patient with a "newb".

---

### Post by davim on 2010-10-09
Same problem here... :(

---

### Post by sean.simpson on 2010-10-09
> **davim said:**
> Same problem here... :(

well if you find anything out please let me know.  if you would emial me at [EMAIL="simpson.sean.h@gmail.com"]simpson.sean.h@gmail.com[/EMAIL]
and if i find anything.  i'll be sure to post it here

---

### Post by Technoviking on 2010-10-10
Interesting, the iSight is one of the few things working for me under Ubuntu 10.10.

T-V

---

### Post by linuxopjemac on 2010-10-11
I think the firmware extraction only works until OSX Leopard, not with Snow Leopard.

---

### Post by hobleydd on 2010-10-27
Me too. I was running 10.04 and all was working well. After I upgraded to 10.10 it stopped. The isight.fw firmware is still in /lib/firmware.  Anyone any ideas?

---

### Post by linuxopjemac on 2010-10-27
Just copy that file (AppleUSBVideoSupport)to some place. Purge isight-firmware-tools and reinstall pointing the location of the driver to the place you copied AppleUSBVideoSupport to. 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)

---

### Post by nortish on 2010-10-28
I have the same problem! Sometimes it works tho, and sometimes not. Its like it doesnt load the isight.fw at boot. Tried to shut down and boot again a couple of times now but nothing. 

I've made the script and all, and its worked for a while, the today...dead!  Any chance it has something to do with me installing ndiswrapper yesterday? Could i have ****ed something up? =)

Help is greatly appreciated!

/nort

---

### Post by hobleydd on 2010-10-29
I reinstalled the isight tools as per the instructions above and rebooted, but still no joy.

---

### Post by rajashraful on 2010-11-13
isight was working normaly in 10.04. After a fresh install of 10.10 I had done everything found in net. From all directions. And failure. I am confused how to solve it.

---

### Post by paulinchen on 2010-11-13
Same here.
Sometimes it works, sometimes not.
 Tried with the AppleUSBSupportVideo from Leopard and Snow Leopard, tried also with the Script. Compiled isight-firmware-tools by myself.

NOTHING. Don't know what else to try ...



By the way with the sight-firmware-tools in the mactel ppa, its now possible with Snow Leopard.

---

### Post by CyberShadow on 2010-11-26
I'm also experiencing this problem with a MacBook1,1 after upgrading from 10.04 to 10.10.

/lib/firmware/isight.fw is in place, but cheese and gstreamer can't find the video device (/dev/video* does not exist).

EDIT: This solution helped me:

> **redmac68 said:**
> For me the solution to this problem was to install isight-firmware-tools-1.5.92 from here 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/%7Emactel-support/+archive/ppa/+packages").

I had an old version of isight-firmware-tools, (re-?)adding the PPA and updating fixed it.

---

### Post by JerkyChew on 2010-11-29
CyberShadow, that fixed my issue, thanks. I came from an upgrade of 10.04 and already had isight-firmware-tools installed, but not that PPA. Here's what I did in case anybody needs some handholding:

sudo add-apt-repository ppa:mactel-support/ppa
sudo apt-get update
sudo apt-get upgrade

Power down and back up, and everything is gravy. Mmmm... gravy....

---

### Post by paulinchen on 2010-12-12
Does not work on macbookpro 5.5 don't know why.

Anyone ideas?

---

### Post by platz on 2010-12-18
I'm subscribing to this thread, MacBook Pro 2,1, Ubuntu 10.10. No iSight after isight-firmware-tools.

---

### Post by izzaboo on 2011-01-10
I do believe I'll subscribe too.

iMac Ubuntu 10.10 (dual boot Mac OS X 10.5)

iSight device not found after following firmware extraction instructions.  Leaving the .fw file in /lib/firmware I was able to boot just fine. But the iSight not detected by anything.

Anybody have any news on this front?

---

### Post by ronbirrell on 2011-01-11
Hi all, I have a macbook pro 5.5 running Ubuntu 10.10 and osx 10.6.6[FONT=monospace].  [/FONT]I experienced the same problems mentioned in other posts and resolved it by doing the following.[FONT=monospace]

[/FONT]Locate the following file in the osx filesystem and copy it to a pen drive. 

System/Library/Extensions/IOUSBFamily.kext/Contents/PlugInsL/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport  

**Step 1.**

Reboot and start Ubuntu.
Copy the file from the pen drive to your home directory
Start synaptic package manager, mark isight-firmware-tools for installation, mark cheese for installation if not already installed
Select apply

**Step 2.**

Go to [https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/%7Emactel-support/+archive/ppa/+packages") and select the folder [isight-firmware-tools - 1.5.92-0ubuntu1~mactel2]("http://ubuntuforums.org/isight-firmware-tools%20-%201.5.92-0ubuntu1%7Emactel2"), within that folder I selected the  AMD folder.  Download the built file and allow install manager to upgrade your previous version of isight-firmware-tools.

[B]Step 3.
[/B]
Reboot and re-login to Ubuntu.
Start Cheese and iSight should now be working
If like me you need skype , download and install

Hope this helps.

Ron

---

### Post by fotis1983 on 2011-02-19
Hello evrybody.I have the same problem here too...Im runing ONLY ubuntu 10.10 on my macbook( CPU: 2x Intel Core2 CPU     T7400 2.16GHz &#8214; RAM 970 MiB &#8214; Apple Inc. Mac-F4208CAA - Apple Inc. MacBook2,1)and my camera does not work att all(cheese,skype,MSN).Wired is that after i installed 10.10(before i had tiger 10.4.11)the earphones does not work as well(you can see a red light into the input).
I dont know if that will help you [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages").
cha cha!

---

### Post by alexmoon on 2011-03-09
JerkyChew's solution worked for me: many thanks!

---

