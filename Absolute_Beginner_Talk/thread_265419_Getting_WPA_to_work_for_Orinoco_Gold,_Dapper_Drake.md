---
title: "Getting WPA to work for Orinoco Gold, Dapper Drake"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by moxie12 on 2006-09-25
Hello,

I just installed Ubuntu two days ago and since then have been desperately trying to set up WPA for my Orinoco Gold Classic.  I haven't had any luck following several tutorials, including:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://www.neowin.net/forum/lofiversion/index.php/t399787.htm](http://www.neowin.net/forum/lofiversion/index.php/t399787.htm)

I have also found the following tutorial but am not sure how to modify it if necessary for Ubuntu 6.06.
[http://www.ubuntuforums.org/showthread.php?t=90450&page=10&highlight=ORINOco+gold+wpa](http://www.ubuntuforums.org/showthread.php?t=90450&page=10&highlight=ORINOco+gold+wpa)

(1) As far as I can see, wpasupplicant does support my driver, which I believe is Hermes I. I went to the Agere Systems website and got the driver.
(2) Read the README file for the driver (wlags49). It asks to be extracted on top of the Linux pcmcia package.
(3) Went to pick up the pcmcia package at [http://pcmcia-cs.sourceforge.net](http://pcmcia-cs.sourceforge.net). Saw that this package is not for use with 2.6 kernels...went to the link for Kernel 2.6 PCMCIA support and did not see anything I could use with the Agere driver.

Any suggestions on what to do next? Has anybody been successful getting WPA to work for this card or driver in Ubuntu 6.06?

Whatever Linux experience I've had has been with Red Hat almost ten years ago, so I have some vague memory of modules and kernels but may not be completely on top of things. I was tempted to bull ahead and try to install the wlags/pcmcia-cs but am worried about screwing up other parts of my install, which are working well.

Thanks very much for any help you can give. Man, I've got a backache from being crammed in a corner for 2 days, attached to my router by a wire while I try to figure out my wireless network!

---

### Post by moxie12 on 2006-09-26
Should I try reposting in the Networking section?

---

