---
title: "ATI Drivers installation :("
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by WardLoockx on 2006-12-19
Im trying to install my Asus Ati EAX1600PRO card on ubuntu using this tutorial

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

now I used method 1 but when I reboot I get a black screen and can' t login :( because can't see a thing

Anybody an idea?

---

### Post by deethree on 2006-12-19
No clue dude. I too had ATi issues. Let me dig up the threads (yes there is an S there) 

that I went through before I finally got it.

1) [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
(same as you. tried both ways)

2) [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79)

3) had a user post what he tried as well: [http://www.ubuntuforums.org/showthread.php?t=315753](http://www.ubuntuforums.org/showthread.php?t=315753)

4)[http://www.ubuntuforums.org/showthread.php?t=273934](http://www.ubuntuforums.org/showthread.php?t=273934)

5) [http://www.ubuntuforums.org/showthread.php?t=305665](http://www.ubuntuforums.org/showthread.php?t=305665)

#5 worked for me. I'm sooo new to ubuntu I can't help you more with your black screen. maybe one of the 4 other ways will help you in your quest.

d3.

---

### Post by raul_ on 2006-12-19
>     * f the screen is coming up blank on startup, start in recovery mode then try editing your /etc/X11/xorg.conf file to remove this line 

    Load "extmod"

    and optionally replace it with this 

SubSection "extmod" 
     Option "omit XVideo" 
     Option "omit XVideo-MotionCompensation" 
     Option "omit XFree86-VidModeExtension" 
EndSubSection

from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1")

---

