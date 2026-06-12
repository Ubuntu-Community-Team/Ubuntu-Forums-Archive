---
title: "I want to boot from OS X"
date: 2007-05-31
forum: Apple Intel Users
---

### Post by alexmiller on 2007-05-31
I just installed Ubuntu to play around with it. Well, now I'm ready to go back to Mac OS X, but I can't figure out how to do this! According to this guide:

[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html](http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html)

I just need to add "defaultos=macosx" to the /etc/yaboot.conf file. And then I have to install the new bootstrap loader configuration file. 

But there is no yaboot.conf in my etc directory. Do I need to create it? Why isn't it there? And how do I use "ybin -v" to install it? As you can see I'm very unfimiliar with Linux. Thanks for the help!

---

### Post by alexmiller on 2007-05-31
update: i went to the boot menu when i started up, where it lets you select which OS you'd like to boot. no OS X there!

---

### Post by ronocdh on 2007-05-31
> **alexmiller said:**
> update: i went to the boot menu when i started up, where it lets you select which OS you'd like to boot. no OS X there!
I suspect you somehow overwrote your OS X partition and it no longer exists. To check, you can insert the installer disc for OS X and boot to that. It'll find your old OS X partition if it still exists.

---

### Post by alexmiller on 2007-06-01
by "OS X" partition, do you mean i overwrote just the OS, or like... all of my files and stuff (music, etc...)? the latter wouldn't be too good. thanks for the help.

---

### Post by Chrisj303 on 2007-06-01
^ You should never attempt to setup a Dual/Tripleboot without completley backing up anything thats needed first.

You did partition your drive before installing ubuntu, didn't you?

---

### Post by tehmacuser on 2007-06-01
You overwrote both Mac OS X and your data apparently.

[http://macmentor.org/forums/viewtopic.php?t=8758](http://macmentor.org/forums/viewtopic.php?t=8758)

that should help you :)

---

### Post by alexmiller on 2007-06-01
> **Chrisj303 said:**
> ^ You should never attempt to setup a Dual/Tripleboot without completley backing up anything thats needed first.

You did partition your drive before installing ubuntu, didn't you?

well, at least i thought i did. when i was installing ubuntu, i felt like it was partitioning for me. i think maybe there should be more warnings for non-savy computer users like myself. the only instrunctions i followed were here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and i didn't get the impression i needed to take any precautions.

---

### Post by tehmacuser on 2007-06-01
You need to partition your drive next time. It's a virtual way to split your hard drive in two pieces, one for your existing Mac OS X install (and all your data) and the other for Linux (in your case, Feisty Fawn). I recommend Boot Camp because it doesn't require you to reinstall both OSes. Check the tut and you'll see what I mean

---

### Post by alexmiller on 2007-06-01
alright, well, i guess i just made a newbie mistake. however i wish there was more instrunction on what to do... it's not the most user friendly system for people like me i guess. anyway, thanks for the info!

---

### Post by regomodo on 2007-06-01
I'm pretty sure that there are warnings when partitioning. i.e. after a warning you get "Go Back" or "Continue".

I guess you went to "use entire disk" option

You live, you learn

---

