---
title: "Wireless Help on a Compaq Presario, Broadcom Wireless Card"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ispy on 2008-02-24
So, my friend here has a Broadcom Wireless Card, and i managed to get the firmware working, but it still won't connect to the internet. I have internet on my laptop here (i have intel =]), but he doesn't, and we're withing a foot of each other, so connectivity isn't an issue... i think it's an ndiswrapper issue, but i can't find a decent, understandable guide to follow in order to install ndiswrapper. if anyone has some insight as to my problem, it would be much appreciated...

:guitar:

---

### Post by Lysander10 on 2008-02-24
Can you connect to the Internet via ethernet cable? If so, follow these instructions:

1) Make sure you have all repositories enabled. Go to System > Administration > Software Sources and make sure all the boxes are checked.

2) Go to Synaptic Package Manager. System > Administration > Synaptic Package Manager. Click "Reload", and then "Mark All Upgrades", and then "Apply". 

Hopefully, that will give you the driver you need for your wireless card. If not, let me know and I'll guide you through installing ndiswrapper.

---

### Post by ispy on 2008-02-24
thanks, i will try that when he has enough power to do it... he's out of battery right now... meanwhile, maybe you could tell me how to do the ndiswrapper in case it doesn't work, and in case someone has the same problem...

thanks... useful post though...

---

### Post by Lysander10 on 2008-02-24
Sure. You're going to need the Windows driver for this, though. Can you get that by yourself, or will you need help with that, too?

---

### Post by Lysander10 on 2008-02-25
I actually just had to use Ndiswrapper to install a USB wireless network adapter. The wifi at my university sucks, and I thought it might help if I had something faster than the stock wireless card in my laptop. Here are the steps to using ndiswrapper:

1) Obtain the Windows drivers for your wireless card(or USB adapter). Mine came on a CD with the product, but you can usually download drivers from the manufacturer's website on the Internet.

2) Make sure you have all the repositories enabled. Go to System > Administration > Software Sources and make sure the box is checked next to every repository.

3) Now it's time to actually install Ndiswrapper. Go to System > Administration > Synaptic Package Manager. Click "Reload", and then "Search". Enter "ndiswrapper" in the box, and press enter. You should be presented with three software packages. Install all of them by right clicking and selecting "Mark for Installation", and then clicking "Apply". 

4) Now, with ndiswrapper installed, go to System > Administration > Windows Wireless Drivers. Select "Install New Driver", and point it to the correct wireless driver.

Alright, I think that's it. You're Internet should be working for you now. If you have any problems, let me know. Good luck!

---

### Post by wormser on 2008-02-25
I did not see which model number the Broadcom card is. 

```
lspci
```

I have a BCM43xx card and used Restricted Drivers Manager to install it.  This was really easy to do.  System> Administration> Restricted Drivers Manager.  Select the firmware and follow the wizard.  You will need to be online to download the firmware.

---

### Post by Sordelka on 2008-02-25
There is a guide for broadcom installation in ubuntu forums (check wireless section). It helped most of the people I know.

---

