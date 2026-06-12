---
title: "PowerPC Install Troubles"
date: 2009-09-03
forum: Apple Hardware Users
---

### Post by bug67 on 2009-09-03
OK,

First of all, I'm writing this post from a Live CD session on my Mac.  So I know that I can boot from a live CD.  It's an old Hardy Alternate CD and I have to tab 'live-nosplash-powerpc64' to get it to boot.  I'm doing this from Hardy because it's the only Live CD my G5 will even boot.  I'm hoping that if I'm able to at least get Hardy installed, I can update from there.  **_EDIT_**:  I have successfully installed and run Hardy on this system before.  Don't know why I'm having problems now.  [http://ubuntuforums.org/showthread.php?t=980519](http://ubuntuforums.org/showthread.php?t=980519)

Mac is a dual 2.7 GB PowerPC G5 

When the boot screen starts to load, I get the following errors:

> [6.933039] hub 1-2:1.1: hub_port_status failed (err 62)
[6.936032] hub 1-2:1.1: hub_port_status failed (err 62)
[6.939020] hub 1-2:1.1: hub_port_status failed (err 62)

Then, all other status are 'OK' Except:

ERROR: The object '/dev/adb' doesn't exist

There's some other stuff but, honestly, these where the ones I could catch.

Anyhow, I get through 98% of the install process and I get a pop-up stating the following:

> FAILED TO INSTALL BOOT LOADER

The installation if the yaboot boot loader failed.
Check /var/log/syslog or see virtual console 4 for the details
Warning:  Your system may be unbootable!

Now, I know I probably don't need to post the whole syslog but, I have no idea what I'm looking for so:

---

### Post by llamabr on 2009-09-04
Sorry to say so on an ubuntu forum, but I always had trouble.  Ubuntu is no longer supporting ppc.

To fix, I now run debian lenny on my ppc.  Installs fine, finds the airport card, etc.  I did have to do something funny to fix the sound, but it was quick.

---

### Post by tiresia on 2009-09-04
You should try to install Ubuntu Jaunty (9.04) because Hardy has problems when installing the bootloader on powerpc64. See this thread [http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882) (Number 6. about Hardy)

---

### Post by bug67 on 2009-09-05
Ok,

Yesterday, I was finally able to get the *Jaunty* Live-CD to boot using Tab, live-nosplash-powerpc64.  Right away, however, I got a bunch of "Fatal Errors."  Then, It went ahead and booted the live-cd and I was able to complete an install.  However, when I re-booted as prompted to do so, my machine started in OS X and the HD I had installed Jaunty on was "unreadable."

So, I really have no idea what I need to do or what I could post (file, syslog, etc?) on here that would help you guys help me.  Having actually gotten Jaunty to boot at all is extremely promising though.  Standing by...

---

### Post by tiresia on 2009-09-06
When you restarted after installing, did you get any yaboot prompt?

---

### Post by bug67 on 2009-09-06
> **tiresia said:**
> When you restarted after installing, did you get any yaboot prompt?

No, it just started up to OS X like I hadn't done anything.  After that. I restarted while holing the option key to see if it would see the ubuntu OS.  No go.  Nothing but OS X.

---

### Post by bug67 on 2009-09-06
I wanted to give you guys some more info on what's going on during install.  I have no idea what any of this stuff means but, apparently, it all seems that my Mac winds up not able to see my Jaunty install.

Bunch of fatal errors about something called "windfarm" which is something I've never heard of.  Also the 'deb/adb' thing I talked about in my OP.  I am able to boot to Live-CD and I am able to install.  However, when I reboot, my Mac is unable to see the Jaunty install.  Wait, I said that already.  :P

Anyhow, they say pictures are worth a thousand words so...

---

### Post by bug67 on 2009-09-06
I think I figured out what the problem is but, I have no idea how to fix it.  If you guys can help please do so with extremely elementary language.

I just ran a Debian installer and got all the way through when I got the "yaboot installer failed."  So, apparently, yaboot is not installing.

I'm not trying to put this on the same hard drive as OS X.  I have a separate internal hard drive I am installing to.  I've gotten all the way through several Jaunty installs and now a Debian install but, I'm having yaboot install issues I guess.  

Now, I'm back up in OS X and I've got a flag that says "this drive is un-readable. What do I want to do?"  I'm pressing ignore because I don't want to have to take the time to install all over again.  I'm assuming if I can get the yaboot thing sorted, I can boot from the Live-CD and use the "rescue" option.

Please help a n00b out.  :popcorn:

P.S.  If I can get the yaboot thing sorted I may just go ahead and re-install Jaunty although, I'm kinda intrigued by Debian now.

---

### Post by tiresia on 2009-09-07
> **bug67 said:**
> 
I'm not trying to put this on the same hard drive as OS X.  I have a separate internal hard drive I am installing to.
How is this second HD connected? Those models have two SATA connection, is the HD where you are installing Linux just one of them?

---

### Post by bug67 on 2009-09-07
I have 5 hard drives in this computer. 2 are on the factory bus and 3 are on an extra serial card I have added. The one I am trying to install Linux on is on the 3rd party serial card bus.

---

### Post by tiresia on 2009-09-07
Ok, that must be the problem. If you want to solve that problem the easy way, you should just install Linux on the second HD on the factory bus or move the HD.

---

### Post by bug67 on 2009-09-07
Ok, I'll give that a shot when I get home.

---

### Post by bug67 on 2009-09-08
That was it.  Needed to have the hard drive I was installing Linux on on the factory serial bus.  Got it installed and running.

Couple of things right off the bat:

1.  Audio only comes out of the built in internal speaker.  I'm not hearing anything out of the built in fiber optic out.

2.  I can't change any of the visual effects settings.  I am only able to select "basic" visual effects.  I get a flag that says I don't sufficient drivers installed.  I can't remember off the top of my head if I have an ATI card or nVidea.  Must investigate further.  :confused:

Thanks for your patients.  I'm running Ubuntu 9.04 as of now.  I had Debian Lenny running but decided to see if I could get Ubuntu running cause it's what I'm used to and, I couldn't figure out how to make Debian not mirror my dual monitor set up.  I haven't really made up my mind yet.  Maybe I'll start posting over at ppclinux.com.

---

### Post by darrenalex on 2009-09-08
Hi... As per i read your comment and from that i would suggest you that just update your ubuntu version so it may help you to solve your problem for power pc installer and also you can check your set up when you installing it just do not forgot to restart or re boot your PC..... Thanks for sharing the post...

---

