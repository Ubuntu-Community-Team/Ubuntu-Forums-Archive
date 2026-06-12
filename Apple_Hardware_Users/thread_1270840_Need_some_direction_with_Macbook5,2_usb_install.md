---
title: "Need some direction with Macbook5,2 usb install"
date: 2009-09-20
forum: Apple Hardware Users
---

### Post by wildman will22 on 2009-09-20
Hello all. I have a Macbook5,2 that I'm trying to run ubuntu on through an external flash drive. It took me a couple weeks of google searches and fiddling around but I've already succeeded in installing Karmic Alpha 5 to the flash drive and booting using a rEFIt boot disk :)

Now, most would say "Just install rEFIt to the HD!!!", and I would, except this is a school computer. 110 new computers and they had to use macs. eh.... Anyhow, today I managed to create a (temporary) Administrators account so as to load rEFIt on a seperate flash drive (for test purposes). Well, it worked (of course lol) which instantly made me want to install it to my karmic flash drive. 

Using GParted on my own ubuntu pc, I reformatted the drive to have one HFS+ partition at the start to install rEFIt on. Except for the resize, I didn't touch my karmic install partition. Well, as it turns out, I forgot to format the drive to GPT before the karmic install. So it would not mount in OS X and I definitely could not install rEFIt. Next, I used Partimage to create an image of the karmic install partition, and created a new partition map as GPT with one HFS+ part at the start and the rest being Ext4. (tell me if I generally bungled on the partition section as I have a feeling I did) I plugged the drive back into the macbook, installed rEFIt onto the HFS+ part through the command line shell script (same thing I did with my other flash drive) and rebooted. I held down alt/option and presto! rEFIt comes up right next to "Macintosh HD". However, the legacy OS boot option in rEFIt is missing.

EDIT: The legacy os option is also missing if I boot from the rEFIt cd that I used before.

Any suggestions as to where my next step should be?? I was thinking just scrap the install and begin a new and maybe that would fix things as when I booted rEFIt from flash drive #2 it had the option to boot Legacy OS. 

Thanks in advance for any help, this has been a long, hard, uphill battle against Steve Jobs and his merry band. :/ Or intel, whoever you want to blame for this mess.

---

### Post by wildman will22 on 2009-09-20
Never mind folks. Just did a clean install on the flash drive with karmic into the ext4 partition, not touching the hfs+. Works fine now. 

Now I gotta remember how I got x to start... -_- (sigh)

---

