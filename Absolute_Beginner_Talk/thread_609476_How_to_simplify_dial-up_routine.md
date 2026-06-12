---
title: "How to simplify dial-up routine?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by wooly on 2007-11-11
I'm really pleased after getting the built-in modem of my Thinkpad T23 laptop working, by following the set-up here:
 [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup)

Now to dial out I use this routine:
First, open a shell window and enter "sudo martian_modem --country=us"
Second, open a new shell window and enter "sudo wvdial"

I'd like to simplify this procedure by having the first part happen automatically at boot. 
How can I make that happen? Thanks in advance for your advice.

---

### Post by PointyWombat on 2007-11-11
Hi wooly,

I would put both these into a script then call the script from the application menu.

create a text file in your home directory with the following in it:
# vi dialout.sh
sudo martian_modem --country=us
sudo wvdial

then make it executable:
chmod 755 dialout.sh

then right click on the Applications -> Edit Menus -> New Item
for type, choose 'application in terminal', call it something like 'Dial Out', browse to where the dialout.sh script is, and that should be it..

Hope this helps,

PointyWombat

---

### Post by wooly on 2007-11-11
I'm reading this at work under Windows.
(Gotta get WPA working in my wireless, that's my next task) 
I'll follow your instructions later today.
Thank you for the well-explained answer!

---

### Post by wooly on 2008-02-28
After installing Ubuntu 7.10 I had another look at the Martian-modem setup.
Here's how I set it up:

Added the line "martian_modem --country=us" to /etc/rc.local .
Now it runs at start-up.

Changed permissions on wvdial so that it can run without sudo:
   sudo chmod u+s /usr/bin/wvdial 

Now the command "wvdial" will connect.

I set up an icon on the taskbar to execute "xterm -e wvdial" which opens a term window, dials my ISP, and shows the connection status.

I hope this helps someone.

---

### Post by TheDro on 2008-04-26
Wow thanks a lot. Now my mother can probably even dial-up.:P

---

