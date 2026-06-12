---
title: "Drivers?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Jttm69 on 2007-09-16
I'm very new to Ubuntu, and i am used to using Windows xp.  :( sad eh.  Wondering if i need to install video/audio/chipset  drivers.  Much like windows setup. If you could help me out, or send me to a link that may be helpful, that would be real great!  Thanks..


 Guy.

---

### Post by Happy_Man on 2007-09-16
Time for an explanation of how Ubuntu (and Linux in general) is different from Windows. 

With Windows, it generally comes with a core set of drivers that are generally non-usuable or crippled on most hardware, requiring you to go load up driver CD's or hunt the Internet for good ones. All this is interspersed with much rebooting and ripping of hair.

With Ubuntu, you merely burn the file you download as a .iso image (if you need help with that just ask, it's not hard, and can be done with Nero or a comparable utility). Then you stick the CD in your drive and boot from it. It will load up a full session from the RAM, never touching your hard drive. You can see what works, and what doesn't. Just remember that what you see, is what you will get when you first install. From there, it's just a bit of editing a couple text files to solve your problem in most cases. So when you boot from the LiveCD, open up the examples folder on the Desktop and play some files, see if everything is all right. If you are going to go through and install, make a note of what doesn't work (if there is anything) and in what way is it malfunctioning (eg, monitor resolution is off, sound won't play, etc.) Generally, though, everything will work. No hassle. The installer is easy to understand, and all graphical. A few quick questions, and 30 minutes later, you're ready to boot up Ubuntu!

---

### Post by RomeReactor on 2007-09-16
Hi. If your computer is connected to the internet with a LAN cable while you install Ubuntu, the installer will fetch and install the necessary drivers for your system, if they are not available in the CD itself, which most likely they will. If you connect to the internet with a wireless card, it *might* or might not work, depending on which chipset it has. Usually all your hardware will be properly configured, internet connection or not.

Try running the Live CD before installing, to see which hardware works correctly and which you have issues with (**if** you have issues; you could have all your hardware properly recognized and configured by Ubuntu).

If after running the Live CD you experience problems with a particular piece of hardware, while you're running it open a terminal (Applications->Accessories->Terminal) and enter the following commands (press enter after each one, then wait for the output **for each one** and post that here, so people can help you diagnose the problem):
```
lspci
```
```
lsusb
```
```
sudo lshw
```

---

### Post by chrome307 on 2007-09-16
Just to add in the forum you do see a large number of threads regarding ATi and Nvidia ... these are usually about how to get the 3D desktops working apart from that, Ubuntu usually works 'out the box' ..... however you might need some help with setting up wireless access if you have a USB or PCI card, but that's fairly easy.

The most common question regarding video is how to change the screen resolution once your setup - by default Ubuntu picks a safe resolution for most PC's, but we all want it to be something else :lolflag: ...... takes about 10secs to change!!

---

