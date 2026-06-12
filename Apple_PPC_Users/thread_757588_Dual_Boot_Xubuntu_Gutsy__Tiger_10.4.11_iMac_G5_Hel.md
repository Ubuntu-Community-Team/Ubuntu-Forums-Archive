---
title: "Dual Boot Xubuntu Gutsy / Tiger 10.4.11 iMac G5 Help?"
date: 2008-04-17
forum: Apple PPC Users
---

### Post by dai_vernon on 2008-04-17
Hello, I'm interested in setting up a Dual Boot on my iMac G5 PPC.  I am currently running OS X 10.4.11 and would like to Dual Boot with Xubuntu Gutsy.

I have not taken any steps to partition my drive to allow for this dual boot because I don't know / don't trust myself to do it properly.  I have looked at some threads previously on partitioning an OS X PPC drive, but I would like further help.  I have backed up essentially what is irreplaceable on my drive; pretty much all of my applications are either redownloadable or reinstallable.  That said, I would very much like to non-destructively repartition this drive as I don't have the install CDs for Tiger with me.

Could someone walk me through non-destructively repartitioning my drive and installing onto this repartition?

---

### Post by oswaldkelso on 2008-04-17
[http://forums.debian.net/viewtopic.php?t=18193&highlight=](http://forums.debian.net/viewtopic.php?t=18193&highlight=)

and

[http://ubuntuforums.org/showthread.php?t=89960&highlight=ccc](http://ubuntuforums.org/showthread.php?t=89960&highlight=ccc)

---

### Post by stream303 on 2008-04-17
With Hardy release so close, you may want to wait a week or so instead of using Gutsy.

I don't know which version of G5 iMac you have (early, ALS, or isight), but on my early model with Gutsy or Hardy, there is a bug with the nvidia driver that shifts the screen about a half-inch or so to the right and it wraps back around to the left.  Slightly annoying, but can be ignored with all that screen real-estate.  The video bug is coming from freedesktop.org and has been submitted and verified by them.

If this drives you crazy, you can install Gutsy, and back the nv video driver (nv_drv.so) down to the one in Feisty, which doesn't have this problem.  This is how I run Gutsy on my iMac right now, and am just hoping that someday the bug will be fixed for Hardy (or for Debian Lenny for that matter)

Also note that on my early G5 iMac, with Ubuntu, the fans absolutely scream during installation, and calm down after the first reboot.  Thus you may not want to install late at night with the family sleeping. In addition, some G5 iMacs have had some power-supply / motherboard capacitor issues, and I'm not sure how much current those screaming fans pull during installation.  I have abused my iMac by installing Ubuntu countless times with the fans screaming and so far no problems - but it is a risk to be aware of.  Note that Debian installs are nice and silent.

There is also a commercial product called iPartition, which has worked for me in the past to non-destructively resize my OSX partition, but not sure if you'd want to go that route with the other options mentioned in those good links above.

---

### Post by ih8vtec13 on 2008-05-03
I wanna know the same thing, I am a total n00b at Ubuntu, its been on my PC laptop for like a week and I want to put in on my Mac too.

---

