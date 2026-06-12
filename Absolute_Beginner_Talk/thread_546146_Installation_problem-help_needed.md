---
title: "Installation problem-help needed"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by karuppaiah.al on 2007-09-08
Hi,

I tried installing ubuntu in my laptop. the hard disk type is Hitachi HTS541616J9SA00 and the laptop model is acer Aspire 4720. But i receive a error tty not found. I also got some info that i need drivers for instllaing any Os in my laptop.
Cna any one of you suggest me some idea to install ubuntu in my laptop.


-Regards
Karups

---

### Post by Tyke91 on 2007-09-08
how exactly are you trying to do this?

installation should be as easy as burning the ubuntu live cd, putting it in your computer, and restarting the entire thing.

(at least that's how it's been every time i've installed ubuntu)

---

### Post by mojomojo on 2007-09-28
Cheers Tyke.
I also get the same error trying to instal using the live CD on an acer 4720.  My hard drive is a seagate SATA ST980811AS. I'll look round some more places and report what I find here.

---

### Post by mojomojo on 2007-09-28
OK this thread gives the solution
[http://ubuntuforums.org/showthread.php?t=421588]("http://ubuntuforums.org/showthread.php?t=421588")

I booted the live CD hit F6 and entered **break=top** at the start of the boot option line.
Ubuntu kicked me out to a prompt
[B]modprobe piix
exit[/B]
The live CD then booted up fine.
That thread mentions about needing to do some things to install the system right so I think it covers everything.

---

