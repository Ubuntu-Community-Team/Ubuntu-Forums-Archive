---
title: "Xubuntu 6.10 Install Problems"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Jebster69 on 2007-03-12
[SIZE="4"] First, I'm an experienced Windows user but I'm a newbie to this Ubuntu/Xubuntu stuff, so please be patient with me. :)  I first got an old PC from a friend of mine, that contained the following hardware:

amd k63 450
256 ram
voodoo 3 3000 agp video
asus motherboard model is: k5a (i think)

And he recommeded that I download the Xubuntu 6.10 (Edgy) OS software ... so I downloaded the burner file and I burned it onto a CD ... then I put it into the old PC and I tried installing it. Eventually, it got to a point of the install, where it makes 3 (click) attempts to check my monitor (it's an AcerView 77e monitor) and once the 3 attempts are made, it eventually brings up a hollow white "+" sign in the middle of a black screen ... and stays like that. Eventually the drives stop too and it just stays like that till I eventually reset it and restart the install again. I tried this install about 3 times before giving up.
Then, my friend recommended that I download/install the Xubuntu 6.10 (Edgy EFT) Alternate install and install it in Graphic mode. So that's exactly what I did and (after burning this new version installing it) ... the install did exactly the same thing as described above (remaining at the hollow "+" sign on the black background).  So, my friend then said to try it in text mode, so I did that and low'n behold, it seemed to load in properly. But, when I restarted the PC, it started up but again, it ended at that hollow white "+" sign on the black background again and staying like that. So I just shut it down and my friend said to post a message here to see if anyone can help me.
Please, if anyone can help with this, I'd greatly appreciate it.
Thanks
Jebster69
[/SIZE]

---

### Post by overdrank on 2007-03-12
> **Jebster69 said:**
> [SIZE="4"] First, I'm an experienced Windows user but I'm a newbie to this Ubuntu/Xubuntu stuff, so please be patient with me. :)  I first got an old PC from a friend of mine, that contained the following hardware:

amd k63 450
256 ram
voodoo 3 3000 agp video
asus motherboard model is: k5a (i think)

And he recommeded that I download the Xubuntu 6.10 (Edgy) OS software ... so I downloaded the burner file and I burned it onto a CD ... then I put it into the old PC and I tried installing it. Eventually, it got to a point of the install, where it makes 3 (click) attempts to check my monitor (it's an AcerView 77e monitor) and once the 3 attempts are made, it eventually brings up a hollow white "+" sign in the middle of a black screen ... and stays like that. Eventually the drives stop too and it just stays like that till I eventually reset it and restart the install again. I tried this install about 3 times before giving up.
Then, my friend recommended that I download/install the Xubuntu 6.10 (Edgy EFT) Alternate install and install it in Graphic mode. So that's exactly what I did and (after burning this new version installing it) ... the install did exactly the same thing as described above (remaining at the hollow "+" sign on the black background).  So, my friend then said to try it in text mode, so I did that and low'n behold, it seemed to load in properly. But, when I restarted the PC, it started up but again, it ended at that hollow white "+" sign on the black background again and staying like that. So I just shut it down and my friend said to post a message here to see if anyone can help me.
Please, if anyone can help with this, I'd greatly appreciate it.
Thanks
Jebster69
[/SIZE]

Hi and welcome. Can you try and boot to the recovery mode in the grub and there you can enter  *sudo dpkg-reconfigure xserver-xorg* follow the instruction and this should get you to xubuntu and then maybe find your drivers for the old video card. Good luck!

---

### Post by Jebster69 on 2007-03-12
[SIZE="4"]Thanks Paul for the info and the welcome too! I'll give that a try. Jebster69
[/SIZE]

---

### Post by arron on 2007-03-17
I am trying to help him out. the install process never rebooted and finished, so grub is not installed form what i figure with all the options.  I'm thinking maybe a server install, then the xubuntu-desktop package?

anyone help out?

---

### Post by halitech on 2007-03-17
when you downloaded and burned the file, what speed did you burn it at? almost sounds like a possible corrupt cd

---

### Post by Jebster69 on 2007-03-17
> **paul capps said:**
> Hi and welcome. Can you try and boot to the recovery mode in the grub and there you can enter  *sudo dpkg-reconfigure xserver-xorg* follow the instruction and this should get you to xubuntu and then maybe find your drivers for the old video card. Good luck!

Paul:

[SIZE="3"]My friend Arron and I tried your suggestion and with that, and some of Arrons help, we finally managed to get the desktop to work! Thanks for the suggestion Paul. I appreciate the help!
Jebster69 :) [/SIZE]

---

### Post by Jebster69 on 2007-03-17
> **halitech said:**
> when you downloaded and burned the file, what speed did you burn it at? almost sounds like a possible corrupt cd

[SIZE="3"]Haltech ... I burned the CD at a slow speed ...  I think it was at X4 so that part worked fine because I tried running it on my laptop and it came up no problem. By the way, thanks for the post and we did manage to finally get it up and running!
Thanks again,

Jebster69  [/SIZE]

---

