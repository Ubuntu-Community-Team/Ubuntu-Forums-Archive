---
title: "XORG and mouse ERROR!"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Tampee on 2008-03-08
Hi there! Im a beginner and ive got a problem.
When i try to use ubuntu, it everything fine until appear desktop. After that my mouse stops working. I tryied Gentoo and it gaves me a XORG error so i read about that error and i think its from my Graphic Card. Its a ATI x800GT 256mb, i read about it and ubuntu auto choose a X800SE  driver that doesnt work with mine.

[FONT="Arial Black"][SIZE="5"]look i think its the same problem[/SIZE][/FONT]

> I have a Powercolor ATI X800GT 256Mo.
It's detected by Ubuntu Hoary (final) installer and Ubuntu Dapper (Flight 1)
installer as a X800SE.
The installer auto-choose the "ati" driver for xorg, bu this driver doesn't
work, so that when xserver
starts for the first time after installing Ubuntu (Hoary Final or Dapper Flight
1), xserver crashes.
It Oops, saying that it can't launch.
To bypass this problem, I just edit /etc/X11/xorg.conf and change the "ati"
driver by "vesa"n then
I restart xserver (with /etc/init.d/gdm restart) and it works perfectly !
If I apt-get and install fglrx-driver-xorg, I can also use "fglrx" driver, it
works perfectly too
(with 3D accel of course).
I can reproduce this bug, I have produced it many times.
I can't say what make the crash exactly : X800SE detection or non functionnal
"ati" driver
for X800 series (or even installer driver choosing problem ?).
This problem is relatively annoying for new users because with an X800GT,
xserver crashes just after
the installation ... so I suggest to make xorg detecting X800Gt as X800GT and
applying it the "vesa" driver, or
"fglrx" if it's integrated. 


I hope u would be able to help me with this problem. thankz!:popcorn:

---

### Post by Tampee on 2008-03-08
I really dont know what to do about it... xS 
thankz

---

### Post by ssj3strife on 2008-03-08
Just so we're clear, does your mouse work at the login window? If not, can you use your keyboard to login?

Try running this:

sudo dpkg-reconfigure xserver-xorg

You could try that a couple times, selecting different options until you find a configuration that works for your system.

---

