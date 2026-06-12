---
title: "Wired/wireless - not yet there(?)"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by boomerian on 2005-12-31
Okay, a definite newbie but not as dumb as I'm beginning to feel.
Maybe jumped the gun on installing (or trying to install) ndiswrapper in order to get wireless access for linksys WMP54G version 2 with Broadcom chipset.
Quite frustrated at the many instructions which assume internet connectivity (i.e., use apt) for installing necessary stuff to obtain wireless connection.
Have hooked up cable to old NIC, which Ubuntu recognizes but the wireless card does not show up in the 'Network settings' window.
Can someone walk me through the Terminal entries to get access?
I am currently using XP machine, but have moved my beloved old box (now with Ubuntu) upstairs/alongside for this very purpose. I am prepared to setup wired access if it will help me eventually get wireless, but so far cannot get either. Is it possible, in my haste, I've got a wireless driver installed for the wireless adapter (that is apparently not configured)? 
- Trying, learning, but with limited early success...:confused:

---

### Post by Lambert on 2005-12-31
Broadcom chipsets can be tricky. No there isn't a driver in breezy for this device so you do need ndiswrapper and a windows driver.

There are a lot of threads and it can be confusing. There is a link in my signature for ndiswrapper. Read through this. There is also links at the bottom of that page that take you to the ndiswrapper wiki with troubleshooting and tips.

Two things to make sure of.

1. You're using the correct driver which you find in the the instructions in the link in my signature. (you may already be but it's important as not all released drivers work for the device.)

2. Make sure you have both .inf and .sys files in the folder on your drive

---

### Post by boomerian on 2005-12-31
Two things to make sure of.

1. You're using the correct driver which you find in the the instructions in the link in my signature. (you may already be but it's important as not all released drivers work for the device.)

2. Make sure you have both .inf and .sys files in the folder on your drive

I'm quite sure of the right driver, and both .inf and .sys files - but does it matter what folder I copy them to? (I'm trying /drivers)
I'm really not sure even where the ndiswrapper file should be...
Thanks for your help (and I do have a printed copy of your thread, which has been very helpful to this point).

---

### Post by boomerian on 2006-01-02
Trying to get someone's attention with this while I stumble on trying to figure it out.

In Terminal, $sudo iwconfig  results in:
lo         no wireless extensions.

eth0     no wireless extensions.

sit0       no wireless extensions.

>System>Admin>Networking  results in Network settings that show the Ethernet connection (the interface eth0 is active) through which I have cabled access to the internet (thus this note) and a "Modem connection" (the interface ppp0 is not connected).  I don't understand this, since I have physically removed the old modem long before I installed Ubuntu.  There is no mention of my Linksys WMP54G v.2 adapter in the Network settings window.

However, if I enter $lshw, the wireless adapter shows up under *-network: 0 UNCLAIMED, with details, after which *-network: 1 is followed by the description of the Ethernet interface.

How can I get the system to recognize the wireless adapter so that I can configure it.  All the other stuff (ndiswrapper, drivers, wpasupplicant) is loaded and waiting...

---

### Post by boomerian on 2006-01-03
Have made some progress, but would like someone to help with questions in last post - Ubuntu not recognizing adapter (shows 'phantom' modem???)
Please help if you can. Thanks,

---

### Post by carlosqueso on 2006-01-03
Try this.  Open a terminal and navigate to wherever you have your windows driver at the moment.  Then type ```
sudo ndiswrapper -i <.inf file>
modprobe ndiswrapper
```  Where <.inf file> is the .inf file of your driver.  Make sure to pay attention to capitalization, that gave me problems.  Then you should be able to see your wireless card.   Please post back your results.

---

### Post by boomerian on 2006-01-03
Gracias, Carlos. I will try what you have suggested.
(At work right now...later today)
Cheers, and thanks for helping!

---

### Post by boomerian on 2006-01-04
Tried to (and thought i had) posted the results yesterday.
Made the entries per Carlos' instructions, and response was
#FATAL: (then some text and file location for ndiswrapper that I can't recall) 
Once again, trying to piece this together from work...sigh.
Will try later...
Cheers,

---

