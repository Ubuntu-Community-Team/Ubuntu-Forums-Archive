---
title: "New install on current system..."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by DNSBubba on 2008-01-11
With two new pieces of hardware, and having issues. I've installed Ubuntu on this machine several times, and was ready to make the move permanent, but I'm having a problem. The only new hardware I have from my last successful install is a Pioneer DVD burner (which is the only device on that IDE channel, and is set to master. Learned that little lesson from last time.) and a Envision 22' widescreen LCD that I got for Christmas. 

The issue seems to be display related, as I keep getting an error after a few minutes that state that the display server has been restarted several times. 

The card I'm using is an ATI Radeon X1600. It's worked in the past with Ubuntu, so I'm wondering if the monitor isn't the source of the issue.

Any thoughts? Thanks in advance.

Forgot to mention that I'm trying to install 7.10.

---

### Post by mikeyphi on 2008-01-11
ATI cards are still causing some issues - have you confirmed, after each install, that your card's driver is installed?
Also is your screen recognised under 'screens & graphics'?

---

### Post by DNSBubba on 2008-01-12
Thank you for your reply. I should have been more specific as to the nature of the problem. I can't even boot the live CD at this point without getting an error message about the display server. I've tried another distro (fedora live) and it booted without any problems. 

I had a good install running on this machine and vid card not too long ago, but now with the new monitor, it just doesn't seem to want to go.

---

### Post by DNSBubba on 2008-01-12
Okay, I got it to boot. I had to go through Windows and use Partition Magic to create a new partition. Using the alt install cd, I made sure to configure it for the native resolution of my new monitor, and that worked.

Of course, as soon as I enabled the restricted driver, it hosed it, but that I can work with. :)

Thanks again.

---

