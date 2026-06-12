---
title: "Post Update Disconnected Wired Network Connection"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Tahi_Kiwi on 2007-12-20
I've searched an read through somewhat similar problems that others have reported, but none are quite the same as my situation.

I am running virtualized Ubuntu session (guest) running on an XP host. VMware Player 2.02 is the virtualization software.

Have been running 7.04 and then 7.10 guests for many many months without any wired network connection problems. Two days ago (18 Dec 2007) after having received and installed the standard Updates and after having restarted the PC, my Ubuntu 7.10 session suddenly failed to connect to the Internet. 

My VMnet virtual ethernet drivers are connected to the Internet. To try to isolate whether the problem lie with VMware software, I removed and reinstalled VMPlayer--latest version, which was the same that I have been using. (By the way, all this time, my XP host connects without fail.)

RESULT: Ubuntu 7.10 cannot connect. 

Next, I reverted to an early Ubuntu 7.10 clone that I had made shortly after 7.10 came out. 

RESULT: Connection works!! No problems after a few hours on the Web.

Before I went to bed, I then proceeded to run the Ubuntu update--139 had to be downloaded and installed. Upon completion of "successful" updating, I shut down the Ubuntu, XP, and the PC.

This morning I booted up XP, VMPlayer, and the newly updated Ubuntu 7.10 (from the saved clone). 

RESULT: Ubuntu cannot connect!!!!! :confused::(  What's common? Ubuntu Update in both situations.

This repeatable situation suggests that something in the Update process trashed my session of Ubuntu's ability to connect to the wired network.

I'm on another PC at this moment, with the same type of setup (Windows host, Ubuntu guest) but I am NOT going to run the Update just yet. 

Whom do we contact to explore or resolve this, please? It's clear to me that something in the updates--not my ISP, not Windows, not the firewall, not VMPlayer (all of which work)--caused the failure.

Thank you

---

### Post by vek on 2007-12-21
I had this happen too - it shows it as having no ethernet card when in guest mode. I updated recently and had the exact same thing happen.  But there is a workaround for now...

You can manually make it work by using the following in the console:

sudo ifconfig eth0 up
sudo dhclient &

I'm not a pro at this, so I have no idea why this might be the case, but its like the desktop half of things doesnt 'see' the adapter and auto-enable it at startup.  I'm guessing that they're working on fixing this.  The network manager icon will still say you're disconnected, but the internet will work (I'm using it right now)

---

### Post by Tahi_Kiwi on 2007-12-21
Thank you , vec. I will give it a go after I restart Ubuntu on the other Ubuntu VM. (I'm running from the old cloned copy at this moment.)

---

### Post by Tahi_Kiwi on 2007-12-25
I have tried a fresh installation of Ubuntu 7.10, but this time using NAT instead of Bridged networking. Installation ran fine and network connections were automatic and seamless, that is, until after I allowed the updates to run!!!

Same thing happened after rebooting: Ubunut cannot detect Wired connection at all!

The two-liner that vek provide works well, but that's just a workaround.

Whom do we notify, please, about Updates breaking recognition of network adapters????

This has happened three times with me. Fortunately, I have backups that I can revert to, but that doesn't solve the problem.

---

### Post by metoor30 on 2007-12-28
You might want to try to look through your logs.  Try the to run 'dmesg | grep eth' from the command line and see what pops up.  I  know that you are probably frustrated, but if you want someone to help you we will need more information.  Can you post the output of the above?

If the commands 'sudo ifconfig eth0 up' and 'sudo dhclient &' work as a work around, you might want to look in the /etc/network/interfaces file to make sure that the interface is set to bring it up on boot.

---

