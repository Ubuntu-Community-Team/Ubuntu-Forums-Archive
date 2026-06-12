---
title: "Linksys Wireless Adaptor with 7.04"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by peterjones on 2008-02-10
I've just installed Ubuntu 7.04 this evening and can't get it connected to the wireless network. I'm having to use someone else's laptop running XP to even ask for help.
I tried following some instructions on setting up ndiswrapper, not that I even knew what I was doing there and didn't seem to be getting anywhere.

The PCI adapter is a Linksys WMP54GS. Linksys own call centre tell me that all Linksys' wireless products work only with Windows, but I'm fairly certain that's not true at all.

I'm really really new to this, using the command line is pretty foreign to me and I'm yet to figure out what sudo means, so if someone could get me pointed in the right direction in as simple terms as possible it would be greatly appreciated.

---

### Post by neurostu on 2008-02-10
Try this:
[http://ubuntuforums.org/showthread.php?t=381594](http://ubuntuforums.org/showthread.php?t=381594)

---

### Post by peterjones on 2008-02-10
I'm trying that but I can't find WINE in the Synaptic Package Manager.

---

### Post by spiderbatdad on 2008-02-10
rut roh...your sources may be commented out, if you installed without a working internet connection...see this post:[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by rkd on 2008-02-11
If the only reason you are considering installing WINE is to unpack the driver files for the wireless card, you could avoid the effort needed to get WINE working by doing the unpacking on a Windows system then moving the driver files to your Ubuntu system. Of course, this assumes you have a Windows system you can use. If you don't, or if you want to use WINE for other things, go ahead and install it.

You asked about sudo. That is pretty simple. 

When you installed Ubuntu and set up your userid, it was set up as a nonprivileged user. This is a security precaution. 

If you need to do things such as install software, modify the computer configuration, etc., you cannot do that as a nonprivileged user. Putting sudo in front of a command causes the command to be run as a privileged user. It prompts you for your password to be sure that you actually are sitting at your computer and intended to do a privileged command.

There are ways to login to an Ubuntu system as the privileged user so you would not have to put sudo in front of the commands, but we recommend you not do that. The system is a little safer against intruders if you don't enable that possibility. 

The small hassle of typing the extra sudo in front of your commands is something that mostly will go away once you have your system set up properly. You don't need to use sudo for day-to-day use of the computer.

---

### Post by stalkingwolf on 2008-02-11
I am pretty sure that the Linksys support was blowing you off. I am running a linksys wireless
router and have since the beginning.  Never had a problem with it.

---

