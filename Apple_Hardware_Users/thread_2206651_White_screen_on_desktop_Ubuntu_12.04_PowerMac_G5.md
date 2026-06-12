---
title: "White screen on desktop Ubuntu 12.04 PowerMac G5"
date: 2014-02-20
forum: Apple Hardware Users
---

### Post by alexander21 on 2014-02-20
Okay, guys, I'm a rookie when it comes to Ubuntu. I recently installed it on a PowerMac G5. I am able to get it to fully boot in a functional manner when I long into Ubuntu 2D. However, when I try and log into the regular version I get a desktop that looks like the picture attached. I can mouse over where the icons are supposed to be, but the white screen the covers the desktop prevents me from further use. I have decreased the screen resolution and everything fits on the screen in 2D, but nothing seems to help the problem in the full-feature mode.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=250507&stc=1[/IMG]
I am at a loss of ideas on this. I assume it has to do with a dated graphics card since the computer itself is ancient, but this doesn't seem to be a very common problem. Any help, tips, comments, questions, concerns and short stories are welcome. I NEED HELP! 
System specs are as follows:
Memory: 481.5MiB
OS Type: 32-bit
Graphics: NO FREAKING IDEA (still has the Apple Display Adapter)
Disk: 158.4
Please also note that this machine has not been connected to the internet since the install as I am out of range of a decent internet connection - dial-up [insert laugh here].
I am a programmer and I can get to the terminal but I've never coded in this environment. Please go easy on the rookie. Thanks in advance!

---

### Post by Phil_Hite on 2014-03-01
Hello Alexander,

I had the same colours when running the 12.04 Live CD on my Powerbook G4.  The problem was caused by the nvidia drivers not being installed.

Have a look at csranu's excellent solution to install the nvidia drivers.

[http://ubuntuforums.org/showthread.php?t=1917328&page=2](http://ubuntuforums.org/showthread.php?t=1917328&page=2)

But be aware that that the repositories for natty universe are no longer active.  Changing them to the ones below worked for me.

deb [http://old-releases.ubuntu.com/ubuntu-ports/](http://old-releases.ubuntu.com/ubuntu-ports/) natty universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) natty universe
Also, at the end of his instructions, when you've made the change to yaboot.conf, you'll need to make it stick with

sudo ybin -v

before you reboot

Good luck!

Cheers,

Phil

---

