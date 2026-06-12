---
title: "DVD Burns failing (using LG 2166D external drive)"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by caleb01_99 on 2007-03-20
I'm very new to Linux and Ubuntu, and I'm trying to convert from Windows (home use). I'm currently set up as a dual boot system. I record internet radio shows and like to archive some of them for later listening. 

I just started using a L.G. 2166D external drive, and it appears to work fine in Windows (succeeded in burning a DVD with about 3 Gig on it...software was OEM version of Nero).

I've tried in Ubuntu 3 ways so far: Nautilus, K3b, and GnomeBaker. Each fails similarly. The burn starts and seems to proceed happily until about 50-60% done, at which point the application declares that the burn has failed. Also, in each case, near the time of failure, the system gets very sluggish (UI lags, mouse is very slow to respond..). This begins a few minutes prior to the burn failure, and persists even after shutting down the DVD burning application. In each case, I've had to restart to get the system to begin responding well. It's the only time Ubuntu has had what looks like a system-wide issue (something I'm used to in Windows, but thought wouldn't happen in Linux/Ubuntu).

I've probably left out technical details of interest, but I'm not sure what might be relevant. FWIW, I'm burning onto   4.7 G media (TDK). I'm asking for "Joliet" naming (though I don't really know what I'm doing), since I understand this is what will let Windows machines see the data on the DVDs.

I'd very much appreciate any pointers as to what might be the issue. Thanks in advance for any help you can provide.

---

### Post by caleb01_99 on 2007-03-20
Bumping this in hopes of being seen.

Also, I neglected to indicate this, but I my dual boot is XP/6.06.

Perhaps I entered this into the wrong forum, but I'm not sure how to move it (would Multimedia be more appropriate?).

Thanks for any help.

---

### Post by caleb01_99 on 2007-04-18
Guess this isn't as fun as talking about Feisty, but I'll try again...

I've since been able to burn many DVDs in Windows. I'd love to switch to Linux, though. Soon, I'll be looking for ways to burn DVDs of home videos taken with our camcorder. If I can't figure out how to do this on Linux, I think I'll get myself anchored on Windows for a while longer.

Anybody have any pointers?

Thanks

---

### Post by 3rdalbum on 2007-04-18
Put a burnt or commercial disc into your DVD burner, then run the command "sudo fdisk -l".

Your DVD burner will then be listed with a device name: /dev/sdf1 or something like that.

Then run the command "nano /etc/hdparm.conf".

You might see some text already in the file, you might not. In any case, go to the end of the file and insert the following:

```

/dev/sdf1 {
dma = on
}

```

(assuming that /dev/sdf1 is the device name of your burner).

Save changes by pressing Control-O and then the Return key. Then press Control-X to quit the program.

When you restart, your problem may be solved.

If it isn't, try running Gnomebaker or K3B as root - gksudo gnomebaker or gksudo k3b.

---

### Post by Jonam on 2007-04-18
If all else fails, the best way to find out the problem is to use the command line. I have successfully burnt DVDs from the command line using Ubuntu 6.06 (Pioneer 112d burner). I followed this howto (its for Gentoo linux but the commands are the same):

[http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn)

Or you can try the following howto in the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=363666](http://ubuntuforums.org/showthread.php?t=363666)

Or another similar tutorial:

[http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line](http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line)

You should get lots of output from running these commands and if there is something wrong then you will see it. Tools like k3b use the same commands anyway except they are hidden behind a nice GUI. See how you go and post back.

Jonam

---

### Post by ramjet_1953 on 2007-04-18
I'm successfully using an external LG GSA-5163D Super Multi, without any problems at all.

Initialyl there were problems, until I got permissions sorted out.

I created a group called burning and put myself into it.

I think that when you have a look at the docs for K3b it talks about that.

One other thing, I am using it as a USB device, as it has problems with the firewire port.

it is probably a permissions thing, again, but I haven't pursued it, as it is working fine on USB.

Regards,
Roger. :cool:

---

