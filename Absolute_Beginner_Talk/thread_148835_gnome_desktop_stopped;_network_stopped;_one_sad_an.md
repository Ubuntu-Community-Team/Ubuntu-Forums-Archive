---
title: "gnome desktop stopped; network stopped; one sad and confused noob"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by jal on 2006-03-22
I need some !HELP!/suggestions/comment/direction here folks, please?

First, tell me what did I did wrong.
Second, help me to fix my network.
Third, if that's buggered, how can I find out what else is buggered that I can't see (yet)? 

First, the event, what went wrong?

I'm running 5.10, gnome, been running happily for a week now, got all my bits installed. This morning I launched Gimp from the applications menu and the desktop locked up instead, just stopped doing anything. No response to keyboard or mouse clicks. I couldn't change virtual screens, pull down menus, or activate application tabs (those at the bottom). No disk activity lights.

As it happened I had a terminal going when I (attempted to) launch the gimp. The terminal took focus and was responding to commands at the prompt, but nothing was getting through to the gui (although the mouse cursor was moving). I stupidly closed the terminal and then sat there for a while looking t a useless computer :(

So I pressed the (time delayed, soft) power button, which immediately stopped the gui and displayed a 'terminal' type screen with a login prompt. While I was trying to login the machine rebooted. 

The first attempt to restart, selecting 'recovery', stopped in the terminal screen (kernel panic?). After 3 restarts I finally got the gui to come up  but now I don't have DNS (and who know what else). Presumably I've done some damage to the fs.

Is there something else I could or should have done instead?

I wanted to run fsck but the last time I did that it competely destroyed the fs ('course it did warn me first small comfort) and I had to do a complete re-install.

What is best practice then? Say the system crashes, fs is in question, I want to run fsck. When I boot from grub I end up in the gui with everything mounted. How do I get into a single user, minimal setup so that I can run fsck safely against the various partitions? If I can run fsck succesfully, can I then trust the system? Will broken files be flagged?

The Network problem. 
Ethernet is up, and I can ping my router on the internal network, but am not able to connect out to the internet. nslookup can't find the DNS servers.

The DNS servers are on the "other" side (ISP, internet side) of my router which is connected to a cable modem. resolv.conf lists the correct ip addresses. I note that 'route -n' shows only localhost/local network entries. Should it have entries pointing to the DNS servers networks too? (I'm at work now and so can't show you the exact entries.)

What else should/could I be looking for? 

tia for any comment.

---

### Post by Egmontman on 2006-03-22
I am totally new here so i can't be much help. I can do this though:

BUMP!

---

### Post by Mustard on 2006-03-22
To run fsck on the root partition you would need to boot with a live CD, you can use either the live CD for Ubuntu, or download a smaller live CD like System Rescue CD.  Using a live CD, you can run fsck without the partition being mounted.  It does sound like there could well be a hardware problem going on with regards to your lock up, so its worthwile investigating whether your hard drive is flaky.

---

### Post by jal on 2006-03-23
Thanks Egmontman.
Thanks Mustard.

I have the Ubuntu Live CD, and so was able to fsck the partitions, showed absolutely no problems at all.

So I booted up off the disk, and it ran up perfectly. No network problems, everything works fine. 

Being masochistic, I thought I'd just try that one more time, so I shut down cleanly, asking for a restart. That failed. Sigh.](*,) 

After the BIOS found the disks, and before going to the MBR, grub loader, the BIOS printed this: "Updating ESCD. Updated". I saw this happen this morning, but never before that. Does anybody have any idea what it might mean?

The failed boot up started running and then hung for a long time before stating that the disks (all three) were not ready. 

I'm thinking I have a deeper problem than disks failing. Expletive. Expletive Expletive.

I am running now, rebooting worked this time. I guess though, that I'll be seeing more problems. 

Anyway's, thanks guys for trying to help.

---

