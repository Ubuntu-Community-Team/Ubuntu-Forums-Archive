---
title: "[SOLVED] My Modem"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Joshfan on 2006-11-26
[FONT="Arial Black"][SIZE="2"][COLOR="Blue"][B]Well, hi I am new to the forum and I am really liking what i see so far with my Ubuntu so far. But I have a problum. I know this was asked befor but i have a vition problum and i can not read a screen to long. So sorry, know I just installed my Ubuntu 6.06 Draper tonight and i can not find where to go to config my modem, it is a serial modem and I had someone say that a true Hardware modem would be best.

So how do i get it to work I have so much to learn.:confused:  [/B][/COLOR][/SIZE][/FONT]

---

### Post by jerrykenny on 2006-11-26
[B]Hi Joshfan, welcome to ubuntu, your serial modem might work just fine, in your Gnome Desktop, go to 

System     Admin     Networking

See if your modem is listed ?

If it is, then you're in luck . . . . if not, what is the name/type of your modem, or who is your internet provider.

If you know its an "eagle" modem for instance . . .

goto   System   Admin   Synaptic Package manager, 

and Search for "eagle"[/B]

---

### Post by jerrykenny on 2006-11-26
[B]Also Josh, if you get the thing on-line, you might want to install the 

konqueror   web browser,

It has very handy toolbar icons for quickly increasing / decreasing the text size  :)[/B]

---

### Post by Cariboo1938 on 2006-11-26
[SIZE="4"]> **Joshfan said:**
> [FONT="Arial Black"][SIZE="2"][COLOR="Blue"][B]
So how do i get it to work I have so much to learn.:confused:  [/B][/COLOR][/SIZE][/FONT]Hi and welcome to the Forum!
Maybe this helps:
1) Detect your modem. Open a terminal and type```
sudo lspci
```You have to look for a line like this> 02:07.0 Communication controller: TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice 56k modem, where TOPIC ....is my modem
2) Look for the device name, you need this for configuring purposes. Continue in the open terminal and type ```
sudo wvdialconf /etc/wvdial.conf
``` You'll find something like > Found a modem on /dev/ttyS2.
Modem configuration written to /etc/wvdial.conf.
ttyS2<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
3) before you continue be sure you know:
3a) Name of your ISP (Internet Service Provider)
3b) Phone # of your ISP
3c) The User name and Password you want to use.

4) Setting up the ppp (Peer-to-Peer Protocol). Continue in terminal and type```
sudo pppconfig
``` a dialog will open and you have to enter all the information gathered before.
Good Luck[/SIZE]

---

### Post by Bartender on 2006-11-26
Jeepers, I didn't have to do anything in terminal.  I just right-clicked on the upper panel, chose "Add to Panel", and drug Modem Monitor to the panel.  Went into System, Administration, Networking, and activated the modem.  Went into Properties, Modem, & asked Dapper to auto-detect the modem.  It found my USR serial external on /dev/tty/S0.  Under General tab, I typed in the ISP phone number.  Just the seven digits, all together.  We've got call waiting, so under "Dial Prefix" I typed *70.
Username is your entire username, including the ISP address (in other words, your [email]username@juno.com[/email] or whatever) then type in your password.
Under Options, I clicked the boxes next to "Set modem as default..." and "Use the Internet service provider nameservers".  Click OK, then backout of Networking.  Right-click on Modem Monitor, click "Activate", see if the modem responds.

---

### Post by Joshfan on 2006-11-26
Thanks, I will try you alls ideas and see what i can do. The modem i use is a 
US Robotics external Modem, from 3Com it was made in 1998 model #0701. It also has all these settings on the back called Dip Switch Settings. Should those be set different? it worked with my windows 98, but do not know if i have to have it set different with Ubuntu.

---

### Post by towsonu2003 on 2006-11-26
[SIZE="5"]Just for reference, here's how to configure a dialup connection in a number of ways: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

The main dialup howto wikipage is in my signature, in case you have difficulties with your hardware modem. However, the main page is more focused with softmodems (in contract to hardware modems)[/SIZE]

---

