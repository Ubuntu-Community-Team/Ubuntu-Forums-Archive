---
title: "successful 14.04 dual boot on a 2006 Macbook [10.6]"
date: 2014-12-22
forum: Apple Hardware Users
---

### Post by shantiq on 2014-12-22
**[COLOR=#333333][FONT=arial]had a bit of a freak-out when i tried to start the Mac partition as it would not start so i hit F2 when hovering on the Mac symbol at startup and it did give me choices i picked Safe Mode  it did some corrections and now all good    i also tried verbose     but now it starts ace on both    so all good&#65279;[/FONT][/COLOR]**



Good info here  [http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

[B]STEP 1

[/B]
was not too hard had to burn the 32-bit iso from Ubuntu,com to a DVD   since  larger then 900 MB, 64-bit no doubt ok on newer models


[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)


OK




**STEP2**


To install [COLOR=#800000]refind[/COLOR] to help with install and then to choose OS at startup


[http://sourceforge.net/projects/refind/files/latest/download](http://sourceforge.net/projects/refind/files/latest/download)


download it / unzip it / open folder/ find install.sh file/  do apple/space and enter terminal   / drag install.sh into terminal and enter     you now have refind installed.


**STEP3**


create space   open disk utility/click on hard drive and create blank space




**STEP4**


Shutdown/ start computer and immediately hold Alt/Option key  use right arrow to go to where Efi is and enter




Ubuntu now loads up   you can try it or install on "Free Space" you have created [from Format dropdown box]
It will find it automatically   Process takes about 20 mn depending on speed of internet

---

