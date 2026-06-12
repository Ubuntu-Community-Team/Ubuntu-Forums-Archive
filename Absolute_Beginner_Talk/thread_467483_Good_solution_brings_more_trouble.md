---
title: "Good solution brings more trouble"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Zero Ziat on 2007-06-07
I need help, I did what it says here since my wireless didn't work ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)) but it removed my wireless device, as in, not shown, like if I had none.

Everything matched accordingly, that lspci grep check.

So, uhh.

How do I retrieve my wireless device back?

How do I make my wireless device work?

---

I installed Ubuntu from the Feisty Fawn BETA Live CD (7.04), dual-booting with Windows XP Professional, where I do have access to internet, not in Ubuntu.

If more information is needed, I'll be pleased to give it.

---

### Post by Hendrixski on 2007-06-07
> **Zero Ziat said:**
> 

I installed Ubuntu from the Feisty Fawn BETA Live CD (7.04), dual-booting with Windows XP Professional, where I do have access to internet, not in Ubuntu.

I would gander to say that this is the reason for your problems.  That BETA disc may have had some experimental configurations that did not make it into the final version so the directions would work differently.

I would recommend that you try to go to IRC to get an answer for this.  If you install XChat (it's in the list of programs in Add/Remove) then you can go to the channel #ubuntu and have a conversation with a live person. They can have you try a few things, then you tell them the results and figure out the problem in a matter of minutes.

Sorry, wish I could help more, but like I said, IRC would give you the best help for this.

---

### Post by Zero Ziat on 2007-06-07
Done so, IRC told me to check in forums.

---

### Post by Zero Ziat on 2007-06-07
Hello? I need a solution!

---

### Post by Zero Ziat on 2007-06-08
I thought you guys were helpful and stuff, but you are just ignoring me, does it mean that Ubuntu doesn't work?
Shame.

---

### Post by Zero Ziat on 2007-06-13
It's been 4 ******* days, ANYONE ANSWERING!?

---

### Post by ugm6hr on 2007-06-13
This chipset appears to be a bit of a nightmare, and there a few different variations on solutions to get them to work.

How does your wireless not get detected?

Try *lspci* in Terminal - it will still be there.

Have you tried the link:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

Specifically:
sudo rmmod bcm43xx

Blacklisting bcm43xx in /etc/modprbe.d/blacklist is something else that might be required.

---

