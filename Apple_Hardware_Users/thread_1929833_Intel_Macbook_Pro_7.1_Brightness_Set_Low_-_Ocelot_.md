---
title: "Intel Macbook Pro 7.1 Brightness Set Low - Ocelot Xubuntu"
date: 2012-02-22
forum: Apple Hardware Users
---

### Post by Bry6n on 2012-02-22
I've recently made the switch from Mac OSX 10.6 to Xubuntu. So far, I am loving it and everything has run exceptionally well. Except for a few minor issues. The first, and largest of these, is my screen brightness. Out of Grub, my brightness is set at maximum. Which is great. But if I close my laptop lid, go inactive for a short period of time, or change the brightness.. I become limited to about 1/3 brightness. I would appreciate some pointers on getting the MBP screen to be able to work at it's full brightness. Thanks,

---

### Post by dakos on 2012-02-24
You wrote that the problem is solved but didn'tt write what the solution was... I'm having the same problem on Ubuntu 11.10 on MBP 7.1 so may be you can elaborate about how you solved it?

---

### Post by Bry6n on 2012-02-29
Sorry for the lateness on this, what you have to go do is add the MacTel repository with a "sudo add-apt-repository ppa:mactel-support && sudo apt-get update". The next step is to also grab pommed. "sudo apt-get install pommed". Pommed will add functionality to your F# buttons, and will allow you to change the screen brightness. at /etc/pommed.conf, you can edit the increments of brightness, the default settings are basically the same as Apple's. The final step is to get the nvidia-bl-dkms package, "sudo apt-get install nvidia-bl-dkms". Using all these steps, what you should be able to do is have functioning F1 and F2 keys. As of now, I have a fully funtioning MBP7.1 with oneric Xubuntu/DWM. Absolutely loving it.

---

### Post by naggu on 2012-02-29
Mine is same system first installation had this issues. After a week I re-installed Ubuntu again and updated on first logon and never had this issue.

---

