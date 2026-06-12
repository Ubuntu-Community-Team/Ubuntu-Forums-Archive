---
title: "Internet connection and printer install"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by carnelian on 2007-07-10
I am a comple novice to Linux and do not understand at all the language used. However (after always using Windows XP) I have installed Ubuntu 7.0.4 on an old machine and have surprised myself by actually enjoying exploring it.  I have found that my old floppy discs, my external hard-drive and USB sticks all open up without any effort.  However,I am defeated on two things. Firstly internet connection - I have the POP and SMTP settings (I am on ordinary dial-up), but I have tried to enter these (not knowing what some of the phrases mean).  I am told to click on a certain button that is not there!  Also I have the same problem with a printer.  I have available both Epson 760 or 925, and would like to use either.
PLEASE!  Can anyone guide me on installation, without the use of Linuxspeak, how to do these two things.  Just tell me what to click onto.  If I can get past these two points I think I might even take to Ubuntu!

---

### Post by freesitebuilder on 2007-07-10
On the printers - the 760 will work, but you'll need to install certain drivers [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson) (scroll down)

To do that, you'll need to add the Univeral repository if you haven't already - here is an explanation of the repositories, and how to add them [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then you can choose System > Admin > Synaptic, enter your password, and do a search for the driver file mentioned on the hardware page. If you haven't used the Synaptic package installer yet, here are instructions [https://help.ubuntu.com/community/Synaptic](https://help.ubuntu.com/community/Synaptic)

---

### Post by Bartender on 2007-07-10
Hi, carnelian -
Linux is pretty cool, eh?  It's come a long way in a very short time.

Unfortunately, dial-up is still a tough not to crack.  The problem is all those pesky winmodems, with proprietary drivers written only for Windows.
Can you tell what kind of modem you have?  We need the chipset, which is more important than the modem's brand name.
try ```
sudo lspci
```
I think that lists all the PCI devices that Ubuntu can identify.  If you find something about a modem, please pass that info on.

EDIT:
Dial-up problems can be divided into 3 main groups:
#1 The modem: this can be the biggest hurdle, and lots of us have given up on trying to make winmodems work.  I bought a couple of US Robotics Sportster serial external modems.  Full hardware modems are the easiest.
#2 The set-up:  Even if you have a functional modem, it can be difficult to figure out how to set up the Linux dialer software.  The difficulty lies in unfamiliarity more than anything else.
#3 The ISP:  If you are signed up with Juno, AOL, PeoplePC, or any other ISP that uses proprietary software to connect, the first thing you should do is get another ISP.

Please list your modem, the way you tried to get the modem set up (wvdial, pppconfig, gnome-ppp, KPPP, the non-functional Networking GUI), and your ISP.

---

