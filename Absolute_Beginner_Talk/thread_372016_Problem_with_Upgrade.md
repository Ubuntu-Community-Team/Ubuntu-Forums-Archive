---
title: "Problem with Upgrade"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by FotiX on 2007-02-27
Hi. I have Kubuntu Edgy (6.10). Recently I tried upgrading from 2.6.17-10 to 2.6.17-11 but Adept found some problems so it left the installation half-done. So now Grub says i have two kernels, but 2.6.17-11 doesn't work (it has problems mounting the root) and 2.6.17-10 doesn't work properly (ie it doesn't mount my external hard drive even though i tried to manually and can't use ueagle-atm and data). At least that's what i think is the case. Why did that happen? How can i restore the previous settings or solve the problem?

---

### Post by nyinge on 2007-02-28
Try issuing ```
 sudo apt-get -f install 
``` in the Terminal and post back the results please.  This is for the upgrade issues, but I'm not certain about the mounting issue.

---

### Post by FotiX on 2007-03-02
Thanks for the reply, but as I was kind of desperate that day and needed my comp, i reformatted the hard disk. Sorry about that. But the next time i tried upgrading, it went fine. Maybe the servers were busy or down and they couldn't supply the packets i asked for.

---

### Post by PartisanEntity on 2007-03-02
> **FotiX said:**
> Thanks for the reply, but as I was kind of desperate that day and needed my comp, i reformatted the hard disk. Sorry about that. But the next time i tried upgrading, it went fine. Maybe the servers were busy or down and they couldn't supply the packets i asked for.

Hehe I remember having done that a couple times when I was new to Ubuntu. I reinstalled Ubuntu on several occasions when x-server would crash until I learnt that I could edit xorg.conf :)

---

### Post by nyinge on 2007-03-02
Tell me about it.  I've been reformatting right and left for the past year whenever I feel bored.  I don't know why I enjoy installing fav apps individually and configuring the system to my taste.  I've seen scripts that'd do those stuff automatically for you, but I just love doing them by hand.  Not a very efficient method though.  :)  Ok, I'm way off topic.

---

