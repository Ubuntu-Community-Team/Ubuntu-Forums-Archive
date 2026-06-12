---
title: "Asus K52F can't hibernate nor suspend"
date: 2012-03-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pog12156 on 2012-03-05
im running ubuntu 11.10 and when i try to suspend the computer it just gets stuck in a black screen until i turn it off through the power button. 
When i tell it to hibernate it enters a black screen with this msg
[FONT=Arial]
[  724.280084] irq 17: nobody cared (try booting with the "irqpoll" option)
[  724.280237] handlers:
[  724.280264] [<ffffffffa02d00a0>] ath_isr
[  724.280293] Disabling IRQ #17[/FONT]

[FONT=Verdana]to be honest i have no idea what any of this means nor do i know how to boot with irqpoll. After i manually shut off my computer though when it restarts it behaves as if it hibernated, brought up all the programs i had on and everything.[/FONT]

i looked around trying to solve this and some suggested updating the BIOS and making sure theres enough swap space. my BIOS is updated and with 3gigs of ram my swap space is 6.35 gigs

p.s. im dual-booting with windows 8 consumer preview if thats relevent

---

### Post by jfever311 on 2012-03-05
[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

---

### Post by pog12156 on 2012-03-05
thank you so much!!! fixed it perfectly, so is there something i should do like make the title say [solved]?

---

### Post by hubertofliege on 2012-03-06
I don't understand where in that link it solves this issue.  It offers a package, but it doesn't say what it does.  There is a notice about fixing the wireless disabling after the computer suspends, but I don't understand what to do to awaken my computer once I open the lid.

---

### Post by pog12156 on 2012-03-08
> **hubertofliege said:**
> I don't understand where in that link it solves this issue.  It offers a package, but it doesn't say what it does.  There is a notice about fixing the wireless disabling after the computer suspends, but I don't understand what to do to awaken my computer once I open the lid.


for me installing that package fixed the problem. all i have to do is open the lid and the login screen will pop up

---

