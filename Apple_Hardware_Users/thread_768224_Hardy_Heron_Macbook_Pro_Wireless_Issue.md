---
title: "Hardy Heron Macbook Pro Wireless Issue"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by ritz on 2008-04-26
hi i just installed ubuntu 8.04 on my macbook pro (3,1) as a triple boot using refit etc. it is all working my graphics, keyboard layout, sound except my wirless...this annoys me, i tried to install it using the ubuntu wiki with the madwifi drivers but it doesnt work...it can see my network but when i try to connect it just asks me for my key again and again i am using madwifi 3403 and also i ran this command "lshw -C network" in terminal and it says that my wireless cars logical name is wifi0... help please

---

### Post by ditsch on 2008-04-26
I am currently using SVN r3402 and it is working. My device is ath0. Could you ensure the module ath_pci is loaded and iwconfig shows you both wifi0 and ath0?

---

### Post by ritz on 2008-04-26
when i ran iwconfig it showed that ath0 was my wireless card and wifi0 had no extensions so i guess i was wrong...but i still cant get it to connect to a network it still keeps trying to connect and then asks me for the network password again...is there a way i can uninstall my current madwifi 3403 and try 3402?? and also i dont know how to ensure the module ath_pci is loaded, how can i do that?maybe there is a way i can get my comp to manually connect

---

### Post by ritz on 2008-04-26
i got it to work!!! i typed the passphrase for my network wrong..thank you for your help anyway

---

