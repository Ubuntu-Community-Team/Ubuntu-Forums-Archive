---
title: "Installing ATI 8.30.3"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2006-11-09
Does anyone know how to install the latest ATI drivers. I got it running before and it gave me smoother video playback in comparison to the 8.29.6 drivers. However, following the guide from here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

It gives me failed messages, during the execution of: 
sudo dpkg -i xorg-driver-fglrx_8.30.3-1*.deb


I don't have the error message to hand, but it doesn't install. Any suggestions are much appreciated.

---

### Post by TusharG on 2006-11-09
I have spent quite some time in configuring Ubuntu Edgy with ATI 8.30 drivers... but no success... So now I'm waiting for someone to show the exact steps to replicate. I have HP Pavilion dv8000z with ATI Radeon XPRESS 200M

I'm getting core dump when I configure my notebook with ATI drivers.

---

### Post by ReaderRat on 2006-11-09
Did you try this guide?
ATI Video - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)**

---

### Post by Bagboy23 on 2006-11-10
I can get them to install, but having problems with XGL. XGL sometimes takes up 70-80% CPU.

Tusharg, I noticed that you have to go through the whole thing twice. First boot gives Mesa, then re-installing following the steps give ATI. However I have that CPU problem.

---

### Post by ReaderRat on 2006-11-10
Is this where you got your drivers?....
[**ATI Mobility Drivers**](http://www2.ati.com/drivers/linux/linux_8.8.25.html)

---

