---
title: "help installing ubuntu"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-16
Hi, I have some problems installing ubuntu
When I put the Ubuntu cd to install, I configure the keyboard, language, screen... and I start installing it, but when it finishes loading, the screen shuts off and I just see a message as if my monitor weren't conneced, it says something as "sinc. out of limit". I tried with the command "live vga=771 noapic nolapic" as it says on help, but it doesn't work either. I also tried with a lot of configuration, I mean I tried with 1024x788x32, or 16, or with 800x600, or VGA but nothing worked out. I also tried with ctrl+alt+F4 when the screen is with the message, typing "sudo dpkg-reconfigure xserver xorg" and nothing happens. 
I also tried with xubuntu, and I had the same problem.
I am new in linux, so I don't know what else to do, can anyone help me please? :confused:

---

### Post by taurus on 2006-12-16
Try using the alternate CD then...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by Jorge32 on 2006-12-16
As I already said, I used Ubuntu and Xubuntu, I will download another Ubuntu version from another mirror, but I think this hardly fix the problem. 
About my video card, it is a Matrox Graphics Marvel G200 AGP, if it is a problem or if it helps you to know about my problem

---

### Post by taurus on 2006-12-16
Are you using the desktop version or the alternate version because they are NOT the same???  The desktop version will run from the CD (aka LiveCD) first before you can install it while the alternate version will let you install it, text base, right away...

---

### Post by Jorge32 on 2006-12-16
I was using the LiveCD, but now I am downloading the alternate version, I hope it works. 
thanks.

---

### Post by taurus on 2006-12-16
The LiveCD is also known as the desktop CD or vice versa...

---

### Post by houstonbofh on 2006-12-16
What is happening is that your installation is not recognizing the limitations of your monitor and trying to display a resolution you can run. In /etc/X11 is a file called xorg.conf which has all of your settings.  You need to manually go through it to limit the frequency available to your monitor.  This is quite easy if you install from the alternate install CD.  (Actually things like this are why we have it)  You also might try a newer monitor that correctly supports plug and play.

---

