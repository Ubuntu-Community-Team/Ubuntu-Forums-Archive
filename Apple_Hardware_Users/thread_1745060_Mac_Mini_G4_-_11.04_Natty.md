---
title: "Mac Mini G4 - 11.04 Natty"
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by xtr3m3 on 2011-04-30
Hi, I'm hoping someone can help out here.

Before upgrading from 10.10, there was nothing coming up in monitors, (i.e. blank, and no resolutions to pick) and the resolution was set at 1024x768 by default, but I chose to ignore this as I was only using the machine through SSH. 

After upgrading, the machine crashed at restart/shutdown and my monitor gave an out of sync error. At first I thought it was probably due to the upgrade, so I downloaded the Natty powerpc image and reinstalled. I am now having the same problem.

I've been using Linux (Ubuntu and Arch) over the past few years and have gotten very familiar with how it all works, but this is beyond me. I've got a feeling that this is a xorg.conf problem, (this file doesn't exist at present) but I have no clue how to go about setting this up.

I've also noticed that if I CTRL+ALT+F1, there is a blank screen and the system crashes.

I'm unable to use my small monitor, a Compaq TFT5005, as it is constantly out of range, and I am currently using a LG L226WTQ, where I get the out of sync error on restart/shutdown.

The Mac Mini is M9686. It was originally 1.25GHz, but I used a hardware hack (cannot remember the site) to remove some very tiny pins to boost it to around 1.4GHz, and has been fine ever since. It also has 1GB RAM, and as you know it has an ATI Radeon 9200.

Any help would be greatly appreciated, as I have no clue how to set up xorg. On my main PC I usually let the restricted drivers do their job. :)

---

### Post by teachop on 2011-04-30
Are you able to SSH into the machine when the desired monitor is attached, or is it completely dead?  I was wondering what xrandr would show, and if you could get thing set up correctly for that small monitor with xrandr.  You might even try that with the undesired monitor is attached, if that is what it takes to get it running enough to hack on it.

---

### Post by xtr3m3 on 2011-04-30
Hi, haven't set up SSH yet, but when I had 10.10 running, SSH without a monitor attached worked fine. Actually, I could even use remote desktop.

By xrandr, do you mean this?

[IMG]http://i.imgur.com/85ddZ.png[/IMG]

This is what I get with my LG L226WTQ. I can't use my Compaq TFT5005, as it just gets an 'out of range' error.

Thanks for your reply.

[EDIT] I just solved the xrandr/monitor problem by using a DVI Cable with my LG L226WTQ. It now detects the monitor and I can change resolutions. The restart/shutdown crash is still there. The LG now says that it is going into power saving mode, and the machine doesn't restart/shutdown.

So it seems that I can't use a VGA cable for my monitor (which I'm not bothered about, as I only want SSH access) and the only problem I'm left with is the crashing/freezing.

---

### Post by teachop on 2011-05-01
There is some non-Apple hardware discussion of a problem that sounds similar to your remaining issues, it doesn't look like they are to the bottom of it yet:
[http://ubuntuforums.org/showthread.php?t=1741668]("http://ubuntuforums.org/showthread.php?t=1741668")

---

### Post by xtr3m3 on 2011-05-01
Hmm.. Thanks for the link! I will keep an eye on this.

I need to use the machine for ampache, tiny tiny rss and irssi, so will probably reinstall 10.10 powerpc tonight.

Or.. I could set all of the above up on 11.04 and not restart the machine.. 

Decisions, decisions..

---

