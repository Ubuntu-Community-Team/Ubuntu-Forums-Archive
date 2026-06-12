---
title: "Problems with Ndiswrapper and Broadcom 4318"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by SkipBlue on 2007-08-15
Hello all. I'm a newbie to Ubuntu and I have been having a heck of a time getting my Broadcom 4318 working under ndiswrapper. I can't seem to detect the wlan0 interface and it doesn't really work under eth1 (Sorry if that's not clear). I've followed tutorial after tutorial, and I believe I have the drivers installed. ```
 ndiswrapper -
``` gives me: 
[code]
bcmwl5 : invalid driver!
bcmwl5a: driver installed
                 device (14E4:4318) present (alternate driver: bcm43xx)
[/code[]

What do you think I should do? Are there any files or commands you need me to give the output of? I really need to get this working. Thanks.

---

### Post by SkipBlue on 2007-08-15
Not sure if anyone's watching this thread, but here's an update (over an ethernet cable).I did a 'sudo nautilus' and deleted every trace of ndiswrapper on my system. Now I guess I just need a good guide for ndiswrapper. Is ndiswrapper installation the same across chipsets except for the individual drivers, because my friend got wirelesss working on his Dell Inspiron 1501 easily. But that's not a Broadcom 3418; it's a Broadcom 43XX, not sure exactly what. I also tried this script: [http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+easy](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+easy) but t didn't work when I had already tried other guides and had leftover drivers and it was  a mess. Now that I've excised every trace of ndiswrapper, maybe I should try again. What do you think?

---

### Post by misfitpierce on 2007-08-15
Just terminal this command

sudo apt-get install bcm43xx-fwcutter

and extract and install and wireless is instant work.

---

### Post by SkipBlue on 2007-08-15
You think I should use the bcm43xx insterad of ndiswrapper? So should I un-blacklist the bcm43xx drivers first?

---

