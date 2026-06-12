---
title: "Flash Movies Bug..."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by cannabis on 2008-03-23
HELLO ALL!

My dream is came true! I finally have installed and working version of Ubuntu! Congrats to me :D 

I have configured music players and etc. all seems working just fine, but I have one problem with flash content on sites. Movies are lagging and thouse bugs are found (videos from youtube). Its not about computer .. under Windows they work fine.

[IMG]http://img01.picoodle.com/img/img01/4/3/23/f_Screenshotm_651c6ba.png[/IMG]
[[IMG]http://img01.picoodle.com/img/img01/4/3/23/t_Screenshot1m_33c56a6.png[/IMG]](http://www.picoodle.com/view.php?img=/4/3/23/f_Screenshot1m_33c56a6.png&srv=img01)

I have installed Gnash and When I was installind flash plugin for firefox i canselled its operation.. then it continues. Can it be the reason? 


**Thank you!**

P.S. Also Im able to boot after rebooting becouse at the first boot bar moves a bit forward and then black screen coming up (From other topic: "I see the swerving orange rectangle, and then the load bar, and then, a black screen, with my lowly flashing underscore in the top left.").. after restarting by pressing CTRL + ALT + DELETE system boots properly. Why so? (Crushed 1 time already)
P.P.S. Sorry for my english.

---

### Post by Bubba64 on 2008-03-23
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Take a look at this thread and see if your missing any codecs or secondary programs your probably not dealing with a bug due to tons of us have no problems, but that doesn't fix your problems. It is about your computer in the sense that it probably doesn't have the dual boot set up correctly, I wish I could help you there but I have never used Microsoft stuff.

---

### Post by cannabis on 2008-03-24
Hello Ill check this manual out, but what about:
> Also Im able to boot after rebooting becouse at the first boot bar moves a bit forward and then black screen coming up (From other topic: "I see the swerving orange rectangle, and then the load bar, and then, a black screen, with my lowly flashing underscore in the top left.").. after restarting by pressing CTRL + ALT + DELETE system boots properly. Why so? (Crushed 1 time already)

I tried to press CTRL + ALT + F1 when I got this black screen today, so here is the screenshot of **error log**. I dont have Windows on the same HDD, only Ubuntu.

[[IMG]http://img26.picoodle.com/img/img26/4/3/24/t_DSC00784m_39222f2.jpg[/IMG]](http://www.picoodle.com/view.php?img=/4/3/24/f_DSC00784m_39222f2.jpg&srv=img26)

**THANK YOU!**

---

### Post by cannabis on 2008-03-24
> **cannabis said:**
> Hello Ill check this manual out, but what about:


I tried to press CTRL + ALT + F1 when I got this black screen today, so here is the screenshot of **error log**. I dont have Windows on the same HDD, only Ubuntu.

[[IMG]http://img26.picoodle.com/img/img26/4/3/24/t_DSC00784m_39222f2.jpg[/IMG]](http://www.picoodle.com/view.php?img=/4/3/24/f_DSC00784m_39222f2.jpg&srv=img26)

**THANK YOU!**


Ok... i have solved my problem with:

```
# sudo "password"
# sudo apt-get install ubuntu-desktop
# reboot
```

but .. still have problems with flash movies :( I have tried to reinstall flash plugin via TERMINAL by command sudo not helped ... Any suggestions?

---

### Post by halln on 2008-03-24
are you using 32 bits or 64 bits ubuntu

---

### Post by cannabis on 2008-03-24
> **halln said:**
> are you using 32 bits or 64 bits ubuntu

heh actually i have asked myself about it :) I think that it is 32 bit system, but where I can get real info about my system? Then I will be able to say 100% correct answer to this question ^ 

Thank you!

---

### Post by halln on 2008-03-24
i think you need to install flash non free. If youre using 32 bits ubuntu, the easiest way to install is just go to nvidia website and if you dont have flash installed it will tell you to download it from their site by just clicking it and it will install it for you. Tell me if it works.

---

### Post by cannabis on 2008-03-24
> **halln said:**
> i think you need to install flash non free. If youre using 32 bits ubuntu, the easiest way to install is just go to nvidia website and if you dont have flash installed it will tell you to download it from their site by just clicking it and it will install it for you. Tell me if it works.

Yeah, but look at screenshot...Flash is installed but its buggy as topics title says:

[[IMG]http://img29.picoodle.com/img/img29/4/3/24/t_Screenshotm_832b1b2.png[/IMG]](http://www.picoodle.com/view.php?img=/4/3/24/f_Screenshotm_832b1b2.png&srv=img29)

 can see flash moves but they are kinda ugly .. :( as this one...

---

### Post by halln on 2008-03-24
have you uninstall gnash and previous flash non free installation? I think you should do this things first. remove it tru synaptic

---

### Post by cannabis on 2008-03-24
> **halln said:**
> have you uninstall gnash and previous flash non free installation? I think you should do this things first. remove it tru synaptic

so can u please post commands what i should use for installing plugins? I have uninstalled them both using synaptic.

---

### Post by cannabis on 2008-03-24
> **cannabis said:**
> so can u please post commands what i should use for installing plugins? I have uninstalled them both using synaptic.

Hello! 
Thank you man, i have working flash player ;) I think my problem was that i cancelled downloading operation .. but reinstall helped ;)

Thanx again ;)

---

### Post by halln on 2008-03-24
If you already installed the one from nvidia site and uninstalled gnash and previously installed flash it shoul work fine now but if not try this thread:      [http://ubuntuforums.org/showthread.php?t=719605&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=719605&highlight=flash+player)

---

### Post by cannabis on 2008-03-24
> **halln said:**
> If you already installed the one from nvidia site and uninstalled gnash and previously installed flash it shoul work fine now but if not try this thread:      [http://ubuntuforums.org/showthread.php?t=719605&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=719605&highlight=flash+player)


soz, it was old post ;) All worx fine now after reinstall ;) Thank you!

---

