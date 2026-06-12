---
title: "Headphones not working after Ubuntu 12.04 installation"
date: 2012-07-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by shalashasks on 2012-07-10
Hey there,

I installed Ubuntu 12.04 on my Asus k55vd laptop this morning. Laptop is now dual booting, with Windows 7 on the other partition. When running Ubuntu, sound plays out the speakers, but when I plug in my headphones, the speakers turn off (as they should) but nothing is played through the headphones.

This does not happen on the windows side of the partition. I've ran the information test with Alsa. The results can be found here:

[http://www.alsa-project.org/db/?f=8ee7c8440470360b51afebdf398678676219f010](http://www.alsa-project.org/db/?f=8ee7c8440470360b51afebdf398678676219f010)

Any help at all would be very much appreciated.

---

### Post by shalashasks on 2012-07-11
This issue magically solved itself after the third reboot, without changing any settings. If I ever figure out what happened, i'll post here incase someone runs into the same problem.

---

### Post by Tudor4 on 2012-07-16
> **shalashasks said:**
> This issue magically solved itself after the third reboot, without changing any settings. If I ever figure out what happened, i'll post here incase someone runs into the same problem.

I have the same problem with this notebook, I came from italian forum of ubuntu, please can you make a post for fix this fastidious problem?

Thanks.

---

### Post by Tudor4 on 2012-07-17
I have solved the issue, it is very bizarre. So if I reboot the system, sounds in the headphones not working, but if shut down and I start the system with the button of notebook, sounds magically it's active in the headphones. Incredible but it's true. What do you mean?

Thanks.

---

### Post by ash_kpi on 2012-09-07
Same problem. Sound appears after I shutdown and then start laptop and disappears after reboot/suspend system.

---

### Post by jaithehulk on 2012-09-08
All of you people... are having this problem with the same laptop model?

---

### Post by ash_kpi on 2012-09-10
I have Asus k55vd

---

### Post by jncneo on 2012-09-14
Same issue also on Asus K55VD, running Kubuntu 12.04 with latest updates. Only shutdown solves the issue.

---

### Post by olamina on 2012-09-29
I have a Lenovo Thinkpad. I have to suspend and then log back in. SUPER annoying. I did find that I don't seem to have this problem with USB headphones...

---

### Post by kenweill on 2013-01-24
I have the same model and I'm having the same problem, using Ubuntu 12.10.
Installed updates, restarted laptop with external deviced plugged in or not, sound still not working on external device. Sound is only working on internal speakers.

Anyone care to share how to fix this? 

This problem is so common even on other distros. The only distro that I have tested without this problem is Fuduntu.
But on Ubuntu, Linux Mint, Fedora, openSUSE, problem is the same on these 4 distros.

~update~
Got it fixed with
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
then reboot system.

Found the solution on [http://ubuntuforums.org/showpost.php?p=11418413&postcount=3](http://ubuntuforums.org/showpost.php?p=11418413&postcount=3)

---

