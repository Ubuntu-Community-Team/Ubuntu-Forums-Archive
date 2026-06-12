---
title: "Asus A6KT 64 bit architecture."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by switcha on 2008-04-10
Hi all,

I'm fairly new to the linux world and I've recently installed Ubuntu 7,10 (Gutsy)
on my Asus A6kt. 

My comp specs consist of:

AMD Turion MT-34 1.8ghz 64-bit single core
ATi X1600XT Graphics with 256MB dedicated ram
1.3mb integrated cam with microphone (not sure on brand,
not sure how to tell)
14e4:4318 Broadcomm [Airforce One] wlan controller
1gig of ram & dvd burner

I have had a relatively successful install - however, I had to install the ATi x1600 xt
graphics controller - which I think was successful but Im not sure how to confirm this.

I also managed to successfully install ndiswrapper for wireless activity.

However, my dial-up modem driver isn't installed (not that it matters b/c I don't use it)
and my webcam isn't working.

I have unsuccessfully tried using easycam (easycam failed to identify the driver) and am kind of at a loss as to what to do. 

Any help or recommendations on the above points would be appreciated.

If you have any additional recommendations based on my system specs. that would be much appreciated,

cheers,
Switch.

---

### Post by red_Marvin on 2008-04-10
Enter this in a terminal:
*sudo update-usbids*
If you can find the usb id in this list:
[INDENT]05e1:0501
174f:a311
174f:a312
174f:a821
174f:5a35
174f:6a31
174f:6a33
174f:6a31
174f:6a51
174F:6a54[/INDENT]
Then you should be able to make it work by following [this]("http://doc.ubuntu-fr.org/syntek") howto to make it work. If you can't read French it's really no problem,
just install build-essential and subversion (enter this in terminal: *sudo apt-get install build-essential synergy*)
and download [this]("http://sourceforge.net/project/showfiles.php?group_id=178178&package_id=205527") file. In the installation part when it wants you to type stk11xx-x.y.z.tar.gz you must change the x'es y's and z's to the numbers in the downloaded file's name.
Other than that, just run the commands in the brown boxes in the terminal.

---

