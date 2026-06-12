---
title: "Dial-Up Connection..."
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by sardopsycho on 2005-10-17
I am running 5.10, and I am new to Linux and Ubuntu, but I am loving it so far.  Can you tell me how to setup a dial-up internet connection with Ubuntu?

thanx in advance...

---

### Post by davmac on 2005-10-17
Have a look at [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

This should give you the info you need.

HTH,

Dave Mac

---

### Post by Bushcamp on 2005-10-17
Hi  I've been having a problem - and posted thread earlier about connecting to the net.  Have found this useful, followed all the wiki instructions, but my machine cant seem to pick up the modem.  If I do a pon and podd it does nothing.  "audax321" command comes up with "command not found".

How can I get Ubuntu to find my modem, which is internal?

---

### Post by sardopsycho on 2005-10-17
I followed these instructions to the letter but am still not getting it to connect.  I have tried every available port - Ubuntu is detecting my modem properly....so I am not sure what to do at this point.

---

### Post by towsonu2003 on 2005-10-17
Note: Wait for confirmation from someone else before doing this. 

Message: Did you try using wvdial? 
Make sure your modem is running (if it's a winmodem or something like that, you may need to run a program to make it accessible)
then: 
sudo wvdialconf /etc/wvdial.conf
if there is no error messages, you should be fine. 
this will set up the basic things for wvdial. then
sudo cp /etc/wvdial.conf /etc/wvdial.conf.backup
backs it up if something goes wrong. Then,
sudo gedit /etc/wvdial.conf
Inside the file, look for the lines where it needs ISP's phone number, password, and username, change those for yourself.
Save and exit, then:
sudo wvdial

This will dial the ISP. It will not exit. To hang up, hit CTRL+C in the wvdial terminal. It will hang up while exiting.

If wvdial can't connect, try putting these at the end of /etc/wvdial.conf;
Stupid Mode = Yes
(if that doesn't work, add:)
Carrier Check = No

Good luck.

If wvdial can't find the modem, post the output of wvdialconf /etc/wvdial.conf here (don't post your username+password by mistake) and someone should be able to help you (hopefully).

---

