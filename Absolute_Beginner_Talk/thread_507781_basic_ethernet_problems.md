---
title: "basic ethernet problems"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by octocore on 2007-07-23
the main issue i'm having is getting my internet up and running.  i'm using a dell inspiron 530 with an integrated ethernet card (Intel 82562V-2 10/100 Network Connection).  When i go to the network settings in Ubuntu, only "Modem" shows up. I have the correct driver, and it's sitting on my desktop... i just have no idea how to install it! any ideas?

---

### Post by laidback on 2007-07-23
Try System > Administratiion > Network. If requested for a password it's your regular login one.

---

### Post by octocore on 2007-07-23
when i go there, all i see is "modem". there is no "ethernet" or "wired LAN" for me to choose and setup!

---

### Post by rrmoulton on 2007-07-26
I had the same problem.  Move the driver file to your home directory, then open terminal.

Type in each of the next 4 lines and hit enter after each.

tar xfvz e1000-7.6.5.tar.gz
cd e1000-7.6.5/src
sudo make install
sudo modprobe e1000

OK, your Ubuntu will try to obtain an IP address automatically now.  You'll the balls swirl up on the top taskbar.

If that doesn't happen, go back to terminal and type the line below and 'Enter' to restart the NIC:

sudo /etc/init.d/network restart

If that doesn't work, reboot.

Let us know how it works.

Cheers.

---

### Post by octocore on 2007-07-26
hey that worked first try! 

do you know how to get the rest of my drivers working? ie integrated video card (intel gma3100) or the onboard soundcard? i can't actually install ubuntu because my resolution is so low (stuck on 800x600) that i cant even get to the buttons i need to. i've been told on irc that all of my drivers should have worked immediately, but that hasn't been the case at all.

---

### Post by rrmoulton on 2007-07-27
You should be able to go into System / Administration / Restricted Drivers Manager and enable the video and sound.  Now that you are on the Net it should go out and install the restricted drivers.

Good luck.

---

