---
title: "[SOLVED] Gutsy Livecd Problems"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-10-22
Hello, I finally ventured into completing my download of Gutsy by torrent, got it downloaded, checked the MD5 sums, which were the same, burnt it to cd and booted up.

I selected the default option at the bootscreen, it showed the new Ubuntu Bootscreen and progress bar, but after it was complete, my monitor brought up a blue box and stated:
> Sync Out of Range

That was all I could get it to do..
I can access my virtual terminals by pressing CTRL + ALT + F1 and I typed:
```
startx -- :1
```
and I got the same exact message from the monitor.

I tried to bootup in Safe Graphics mode, same thing.
I checked the cd for errors, and there are none.
I burnt the cd at 1x speed, for the record.

I am not to far in the know about video cards and what not, but I do know it is nVidia.
If you can give me some command to enter, I will gladly give you the model of my video card (onboard, for the record.)

I just want to try out Gutsy, and at least be able to see it :D
Any help would be appreciated!

Edit:
I booted up on my other hard drive that has virtualbox on it, and got the system to get past the boot splash.
So, why can not I load it as a regular live cd, instead of running it in VirtualBox ? How would I ever attempt to install it, without the alternate cd ? O.o

Dr Small

---

### Post by mikeyphi on 2007-10-22
You might want to try changing the settings

command:
sudo dpkg-reconfigure xserver-xorg

probably want to accept the defaults until you get to screen settings

---

### Post by bodhi.zazen on 2007-10-22
Change to the vesa drive and enter your monitor's vertical and horizontal ranges manually in /etx/X11/xorg.conf

Then, install the nvidia driver, either from the repos or nvidia.

---

### Post by Dr Small on 2007-10-22
Running dpkg-reconfigure did the trick.
Then I went back to vt7,restarted X, and then it worked :D

By the way, Gutsy looks great ;)

Thanks everyone!
Dr Small

---

### Post by lost_poet on 2007-10-25
Hey you guys, My friend (an absolute noob) has the exact same problem on her machine, She and I have both read this thread (and many many others), but she keeps getting stuck at the end of the xorg reconfigure when it goes 

> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xong.conf.20071025211636

The thread by her is below, someone please help her out.

[http://ubuntuforums.org/showthread.php?t=591284](http://ubuntuforums.org/showthread.php?t=591284)

thank you :)

---

