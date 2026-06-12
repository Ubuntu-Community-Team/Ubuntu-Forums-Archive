---
title: "help! i can't see anything!!!"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by mental_noise on 2005-08-11
i installed Ubuntu last night to my PC. after the long installation process finished, i was delighted to have had my first Linux installation on my PC. anyways, i was really pissed because when i booted to Ubuntu, i couldn't see anything. i mean when the OS loaded, my monitor displayed an error saying **[color=red]warning! output signal is out of range[/color]**. and the screen looks like something i would describe similar to the white static you see in a TV set when there is no reception.

help!!! i want to start using Ubuntu... ](*,) 

BTW, my vid card is a **64MB GeForce MX400**.

---

### Post by heimo on 2005-08-11
You need to reconfigure Xorg. This should be helpful:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

Basicly you need to get to console, run dpkg-reconfigure (see post abowe). If that's impossible, it's possible to edit xorg.conf by hand using Live CD. If you can't get into console, try hitting ctrl+alt+backspace and ctrl+alt+F1. Don't get scared of console/terminal, it's just the way to solve these problems and all the steps and commands needed will be found on post abowe and dozens of other threads on these forums.

Hopefully you can get it fixed and get soon to use your new Ubuntu system. :)

---

### Post by poofyhairguy on 2005-08-11
[QUOTE=mental_noise]i installed Ubuntu last night to my PC. after the long installation process finished, i was delighted to have had my first Linux installation on my PC. anyways, i was really pissed because when i booted to Ubuntu, i couldn't see anything. i mean when the OS loaded, my monitor displayed an error saying **[color=red]warning! output signal is out of range[/color]**. and the screen looks like something i would describe similar to the white static you see in a TV set when there is no reception.

help!!! i want to start using Ubuntu... ](*,) 

BTW, my vid card is a **64MB GeForce MX400**.[/QUOTE]


Your card is fine. Look up specs on the your monitor and use the tool in the post above to fix it.

---

### Post by mental_noise on 2005-08-11
[FONT=Verdana]hey, i was able to change the settings for the screen resolution, thanks for the help guys. unfortunately, i could not use the 1024X768 resolution. when i change the resolution to this, the screen distorts and i can't see anything. i could only use a resolution of 800X600. it really sucks coz i can't maximize my desktop view.

could it be that the drivers i installed aren't correct? are there drivers for my **Nvidia GeForce2 MX/MX 400** vid card for the Ubuntu OS?

im just wondering because when i am on WinXP, i can get my desktop to the 1024X768 resolution but in ubuntu, it's all distorted. so i thought that it must be the drivers.

correct me if i'm wrong please...i'm still new to this cool Linux OS. :D [/FONT]

---

### Post by heimo on 2005-08-11
You should probably use nv driver or nvidias proprietary driver (nvidia). vesa driver should work too, but is probably quite slow.

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)
[http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia)

---

