---
title: "Win98 modified RTL8187B driver"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-24
Does anyone know where I can get it from?

The normal Win98 driver doesn't detect my wireless card (RTL8187B).
Its anoying me and I want to go on internet on Ubuntu. Don't like Windows. 

Thanks,
Tom

---

### Post by Tom--d on 2008-02-24
Anyone?

---

### Post by HandyAndyShortStack on 2008-02-25
the files you seek are [here]("http://www.datanorth.net/%7Ecuervo/rtl8187b/")
there are directions in the faq
good luck

oh, and don't expect signal strength indications or encryption to work.

---

### Post by Tom--d on 2008-02-25
Used that before. Too buggy and I need emcryption

I'm using ndiswrapper. Its all gonig good so far until I install a windows driver..I've tried every windows driver but they all say the hardware is not there.

It is as when I do  lsusb
My card comes up. 
I will show you when I get on the computer, at the moment im on a different laptop.. 

thanks

---

### Post by jrobertson9256 on 2008-05-05
Just wanted to say thanks for the help with the modified driver files. I got it to work without too much difficulty.  

It was only until I downloaded the modified drivers did I get the thing to work. 

The instructions I can remember were as follows:
sudo ./mkdrv
sudo ./wlan0down
sudo ./wlan0up
sudo /etc/init.d/networking/restart

It didn't mention about restarting the network in the notes although it probably assumed I would do that anyway. Also it took a few seconds for the networking settings to change in Gnome network manager, but when it did it looked no different from my own setup.

If I have the time I might also look into applying a patch if it is necessary. Also I might look at other solutions ie. 
[Wireless on Toshiba A210]("http://sarah-a-happy.livejournal.com/92492.html") [livejournal.com]
[Rtl8187b Id: 0bda:8179 - Solved!!!!!!!!!! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=708605") [ubuntuforums.org]

---

