---
title: "How to install a wireless network card?"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by StephanW on 2005-08-27
Hey,

I just installed ubuntu on my laptop yesterday to fool around with.  I looked in the starter guide and throughout these forums and I can't seem to find anything on how to install a wireless card.

I have a wireless card from dell.  The only product type that I can get off of the card is it's a Dell Wireless 1350 802.11 b/g PC Card.

If anyone could help me out it would be greatly appreciated.

Thanks,

-Stephan

Oh and I have the ethernet hooked up on my laptop and the internet is working and everything, I just can't seem to install my wireless card.

---

### Post by SqdnGuns on 2005-08-27
Have you searched the forums?? There are a TON of post That will assist you.

---

### Post by sigma2805 on 2005-08-27
hi,
before we get started, have you done anything so far in regards to adding backports?  If not, follow this section of the Ubuntu Guide. 

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

after that, first step is to get the drivers for the card. usually those can be found on dell's support site. try to find the most up to date drivers. next thing you want to do is making a list of your wireless networks settings, this includes your ssid, encryption method, passphrase(if your using it) channel and other important stuff. After that, you need to get ndiswrapper. go to system -> administration -> synaptic package manager on the top menu.  enter YOUR password. then search for ndiswrapper. If you are using a wpa encryption, get wpa_supplicant as well. once you are done, reply back and we will continue.

---

### Post by sigma2805 on 2005-08-27
basically you need ndiswrapper here are some links 

[http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper)

[https://wiki.ubuntu.com//?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://wiki.ubuntu.com//?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)

---

### Post by StephanW on 2005-08-27
I'm working with all the information you gave me sigma, I'll get back with you by tomorrow or sunday.

---

### Post by StephanW on 2005-08-27
[QUOTE=StephanW]I'm working with all the information you gave me sigma, I'll get back with you by tomorrow or sunday.[/QUOTE]
 Got it workin sigma, thanks a bunch!

---

### Post by sigma2805 on 2005-08-28
i'm glad it works!

---

