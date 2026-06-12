---
title: "Networking not working in Ubuntu install in VMWare Workstation"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-28
I've installed Ubuntu 6.10 in VMWare Workstation and I can't get the network to run.  Interestingly I installed Kubuntu 6.10 in VMWare Workstation and it worked without a hitch.  The VMWare Tools have been installed.  Can someone help me?

---

### Post by yellowband on 2007-03-28
hmmm

i'm by no means a network specialist, but i have ubuntu working within vmware in windows XP.  When i installed the virtual guest i chose bridged networking, is that what you chose?  

within ubuntu, i have IP addresses assigned via DHCP, the same as in windows.  

other than that, i didn't make any other changes.

---

### Post by Thrasonic on 2007-03-29
That's interesting because it sounds like you have yours setup just like I have mine, and as I said when I did the same exact setup with Kubuntu it worked without a hitch.  Very strange.  I installed the VMWare Tools last night and that didn't help, unfortunately.  I was hoping that would be the silver bullet, but apparently it's not so I'm still stuck.  What command do I run to see what IP the interface has?  Maybe that will help y'all to help me.

---

### Post by hyper_ch on 2007-03-29
If you have a wifi card use NAT and not bridged networking.

---

### Post by HereInOz on 2007-03-29
run ifconfig to see what IP address your ubuntu VM has been given.

Are you able to ping an IP address at all?

---

### Post by Thrasonic on 2007-03-29
Okay, running ifconfig tells me that the nic does have an IP address that is correct, however I can't ping anything.  I tried pinging google.com and got 100% packet loss.  I can ping google.com just fine from the host operating system, though.  Any thoughts?  Again, the Kubuntu virutal machine can hit the Internet just fine.  I'm not sure if that info helps.

---

### Post by HereInOz on 2007-03-29
Try pinging 64.233.161.147

If you get a response from that but not [www.google.com](www.google.com), it is a DNS issue.  If so, set a fixed IP, gateway and DNS addresses (from your ISP) and that may help.

---

### Post by Thrasonic on 2007-03-29
I tried by IP and that didn't work either.  I still got 100% packet loss.  Any other ideas?

---

### Post by Thrasonic on 2007-03-29
bump

---

### Post by Exodus00FF on 2007-03-29
I am encountering this same problem I would indeed like to have some resolution with it.  I would like to make a note though that when I was installing ubutu I was able to browse the interweb no problem.  This problem only occured once I was no longer running off of the cd and running in the Virtual Machine only.

---

### Post by Exodus00FF on 2007-03-30
bump

---

### Post by neogenesis213 on 2007-04-01
I am having a pretty similar problem. 

I can ping my vmware guest XP ip from the host ubuntu 7.04 but I can't ping anything from the XP guest aside from 127.0.0.1. Internet doesn't work on the guest.

Is there a solution?

---

### Post by QuietTheVoices on 2007-04-04
> **hyper_ch said:**
> If you have a wifi card use NAT and not bridged networking.

Not sure if it was that setting (above) alone that helped but I also went to VMWare Edit>Virtual Network Settings: Automatic Bridging (tab). Check "Automatically choose an available network adapter to bridge to VMNet0" and added my wireless card.

---

