---
title: "Getting Internet connection working"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Ioannes on 2006-08-31
I'm new to Linux and Ubuntu and urgently need some help. I need to get an internet connection working under Linux and I seem to be having problems. Can somebody give me a walkthough of the steps needed to get a connection to my ISP established. I'm still on dial up via a modem as I have not got broadband yet. 

Many thanks in advance...

John

---

### Post by monktbd on 2006-08-31
I have not used Dial-up for years but from what I get from messages on this board
> 
sudo wvdial

is an easy way to setup a dial-up connection.

---

### Post by Ioannes on 2006-09-01
Many thanks I'll try it.

John:)

---

### Post by driggars on 2006-09-04
> **monktbd said:**
> I have not used Dial-up for years but from what I get from messages on this board


is an easy way to setup a dial-up connection.
How do I find this "sudo wvdial"  I cant for the life of me figure out how to to a dial up connection either. I sure wish someone would post s detail step by step direction,, ,Please.
Clint

---

### Post by JNowka on 2006-09-04
*edit* This is for Gnome btw :)

Assuming your modem is installed with drivers, goto System->Admin->Networking.

Once there select the modem, and then click properties.

Goto the modem tab and click Autodetect beside Modem port.

Select your Dial type

Select Volume.

Click on the general tab

make sure the Enable this connectiong box is clicked.

enter the ISP's phone number, user name, and password.

click ok

Click the Activate button.

You are connecting to the net.

---

