---
title: "Ubuntu crashing"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by davetheravexxxx on 2006-01-28
I installed Ubuntu on my Inspiron 9100 yesterday and I have been trying to use in today.  It appeared to pick up and configure evrything except my USB headset and Wireless card. So far it has crahed 17 times.  Anyone any idea what might be wrong,

My Spec is

Inspiron 9100
ATI Radeon 9800 256 Mb Graphics Card
1024 Mb Ram
80Gb Hdd, 44GB of which is an XP Partition 28.5 Gb Linux Partition.  1.5 Gb Swap Partition
P4 3.4Ghz with HT
8x Sony DVD RW
On Board Usb
On board ieee1394

The only thing that fails on startup is synchronisation with the time server.
I am relatively new to Linux so any help would be greatley appreciated

---

### Post by agapito on 2006-01-28
Does it crash when you are doing something or it just crashes whenever it wants?

---

### Post by davetheravexxxx on 2006-01-28
Its random for example it might crash when I open evolution, or when i try to change desktop backround or if i try to run something

---

### Post by agapito on 2006-01-28
If it was specific it would be easier to solve... You could try installing a kernel for a 686 processor (like you P4). In Synaptic search for linux-image. I think the latest is 2.6.12-10-686. If it still crashes, you can look in the system logs to see what went wrong. They are located in /var/log  or you can use the Graphical Interface in the System Tools menu. Additionally you have an error log in your home directory. It's a file called .xsession-errors, where the error with X are reported. Synchronisation with the time server failing may be an indication of the network not working...

---

### Post by moephan on 2006-01-28
If by "crash" you mean that the GUI freeze's or "hangs" and you can't do anything, then may be experiencing an issue with powernowd. 

You could check out this thread:
[http://ubuntuforums.org/showthread.php?t=76288&highlight=powernowd+hang](http://ubuntuforums.org/showthread.php?t=76288&highlight=powernowd+hang)

and see if you think that might be related to your issue.

Cheers, Rick

---

### Post by davetheravexxxx on 2006-01-28
Thanks guys I will try these and get back to you

---

### Post by davetheravexxxx on 2006-01-28
Ok I have now tried both your solutions and they appear to have slowed down the problem but the machine is still freezing every five to ten minutes or so.  In addittion to the solutions above I have also tried removing the linux-image 386 and have tried turning off the hyper threading on the bios but with no sucess.  Has anyone any other ideas.  Would reinstalling Ubuntu help?  Are there any similar distos to Ubuntu that I could use instead.  I am a college student doing law so my experience in Linux is limited

The time server synchronisation problem has disappeared though

---

