---
title: "Audio On 5,1 Aluminum Macbook NOT WORKING"
date: 2009-04-03
forum: Apple Hardware Users
---

### Post by emilebrahimi on 2009-04-03
OK, I'm very new to Ubuntu and Linux. I've installed it on my new Aluminum MacBook 5,1. I can't get the sound to work. I've tried every terminal command listed on the Ubuntu forums, and it still won't work. Then, right as I started posting this thread my the sound button hat the mute symbol over it. Now, every time I try to open "Volume Control" it says "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I'm stuck and I don't have clue what to do. When I COULD access "Volume Control" it recognized my NVIDIA graphics card as a ALSA sound card, and wouldn't play any sound. I've been told that a MacBook uses SigmaTel.
Any Help?

---

### Post by emilebrahimi on 2009-04-03
P.S. everyone I also noticed (before my audio had the mute sign on it) that my headphone jack had a glowing bright red light coming out of it!

---

### Post by cyberdork33 on 2009-04-03
Find documentation for you Mac here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

> **emilebrahimi said:**
> P.S. everyone I also noticed (before my audio had the mute sign on it) that my headphone jack had a glowing bright red light coming out of it!
that is normal. That is the digital output. You should able to disable it once you get the sound card recognized properly.

---

### Post by emilebrahimi on 2009-04-03
I also tried fixing up my trackpad with all those terminal commands, but I got nowhere, fast!

---

### Post by cyberdork33 on 2009-04-03
> **emilebrahimi said:**
> I also tried fixing up my trackpad with all those terminal commands, but I got nowhere, fast!
Are you trying to use Jaunty? If so, that is a known issue that will hopefully be corrected before the final release. There is information about it here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

### Post by emilebrahimi on 2009-04-03
No, I'm using 8.10 Intrepid Ibex.

---

### Post by cyberdork33 on 2009-04-03
> **emilebrahimi said:**
> No, I'm using 8.10 Intrepid Ibex.
ok well it should work with the packages from the mactel ppa as shown in the wiki page.

touchpad entries in your xorg.conf will conflict, so make sure to remove them.

---

### Post by emilebrahimi on 2009-04-03
[UPDATE] I got the sound coming out of the headphones;), but still no sound from the speakers!:mad:

---

### Post by emilebrahimi on 2009-04-04
[UPDATE] I got the sound to come out of the right speaker, thats good enough for me!:guitar:

---

### Post by emilebrahimi on 2009-04-04
Ok, the speakers stopped working again:mad:! Why is it freaking out on me???

---

