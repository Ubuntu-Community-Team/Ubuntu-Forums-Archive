---
title: "Reinstallation of ubuntu"
date: 2013-01-07
forum: Any Other OS
---

### Post by bijupp on 2013-01-07
Hai everyone

I have tried ubuntu and linux os multi boot with windows.. but after a change in the partition table or windows installation the linux os goes out of order and need to reinstall every time. each time after the installation i find that the my downloaded and installed programes and data are lost. This problem keeps me away from the linux. I love the linux based OSs  but windows I feel much simpler to operate and install. in windows I can easily reinstall without losing the installed programmes and data. It detect and repair the existing installation everything goes fine.. as earlier. why this facility is not included (??) in ubuntu installation. 

I would like see the following changes in the installation...
It should detect the existing installation and repair without losing data
It should be customized installation as what apps are to be installed 



I'm not an expert in linux because the above problems I have lost many GB of data from my computer even though I love the OS and I would like to get more trained about the linux  Please tell me whether there is any solution for my problems..

---

### Post by Cheesemill on 2013-01-07
There's absolutely no need to reinstall Ubuntu every time you reinstall Windows.

When you reinstall Windows, all that happens is that the boot menu gets overwritten. This is because Windows always assumes that it is the only OS on the disk. Your Ubuntu installation is still intact, all you need to do is repair the boot loader.

You can use the Boot-Repair tool to do this, the easiest way is to download the Ubuntu Secure Remix CD and burn it to a disc. Then if you ever need to repair the bootloader just boot from this CD and run the boot repair tool and you will be able to choose to boot Ubuntu again when you restart your computer.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

