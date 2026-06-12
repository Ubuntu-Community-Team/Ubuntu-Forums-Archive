---
title: "help with a bluetooth adapter and a mobile phone..."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-22
hello.
im trying to install and then use a bluetooth adapter (usb) to connect my sony-ericsson z530i so i can transfer pictures and such like between the phone and the pc.
ive installed eveything i need (least i think i have) but i cant get the things to pair up, neither seems to know anything is there.
ive tried using - hcitool scan , and ive also tried sdptool search HID and they both time out with out finding anything, ive checked to see if the bluetooth adapter is working (and it is) the phone is ok aswell and ive installed the bluetooth file sharing program and made sure its running, but no joy.
so any help you can give me will be appreciated.
cheers
Phone is - sony-ericsson z530i and the bluetooth adapter is a - veho class 2 adapter (ive checked on their website and theres no linux driver)

---

### Post by dan171717 on 2007-05-22
ive been thinking of getting a bluetooth dongle but wont if itisnt linux compatable

i think linux has some limited bluetooth tools built in but i willhave to check

this might help

[http://www.holtmann.org/linux/bluetooth/](http://www.holtmann.org/linux/bluetooth/)

---

### Post by Inxsible on 2007-05-22
You can transfer files between the devices even without pairing. Pairing only helps you in that you dont have to keep searching for the known device.
 
To pair the computer with your phone (Assuming that you have all the required bluetooth libraries installed --looks like you have) :
```

sudo gedit /etc/bluetooth/hcid.conf

```
 
Look for a line that says security  user;
 
Change that to :
```

security auto;

```
 
Also the default passkey is set to 1234. You can change that to anything you want, and you will have to enter this key the very first time
Save it and then reboot. Try connecting, enter the passkey. That should pair your phone to the computer

---

### Post by techno-mole on 2007-05-22
cheers i shall give it a bash and see what happens.
many thanks.

---

### Post by techno-mole on 2007-05-22
well tried that, and there has been some progress in that if i plug the adapter in a bluetooth icon appears in the top right hand corner of the screen, and it goes if i unplug the adapter but i still can get the pc and phone to talk to each other, i cant transfer files or do anything else.
i think i have all the bluetooth stuff installed (basically anything and everything from synaptic)
one thing i did notice is that after typing - sudo gedit /etc/bluetooth/hcid.conf in the file that comes up i see this 
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	_security auto;_

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";

i presume the underlined section is the part you suggested to change ?
does that fact that it says pairing disabled mean anything ?
cheers

---

### Post by Inxsible on 2007-05-22
No The line #Pairing Disabled has a # sign before it, tht means its a comment and is ignored when read by the bluetooth init
 
Your pairing is set to multi --- and that is how it should be
 
Just to make sure you have everything:
```

sudo apt-get install bluez-gnome bluez-utils

```

---

### Post by techno-mole on 2007-05-22
used the code you provided, and it didnt install anything as it said that everything was already installed.
cheers

---

### Post by Inxsible on 2007-05-22
> **techno-mole said:**
> used the code you provided, and it didnt install anything as it said that everything was already installed.
cheers
 
Thought as much....because you had told me you had the apps running. But I just thought I'd make sure.
 
Alrite, Give me a step by step of what you do
Once you change the file like I suggested, did you reboot? 
Is this an external dongle...since you say adapter ?
Make sure the dongle is connected when you reboot. Then start up the Bluetooth File Sharing App by going to Applications --> Accessories --> Bluetooth File Transfer (or similar..I am not on my Linux machine now :( )
 
Then on your phone, go to Bluetooth and then My Devices. This will do a search and hopefully list your machine. Select it and try connecting to it. It will ask you for a password and tell you that the other machine (your comp) has to put in the same password.
Type in 1234 (or whatever you have in your hcid.conf file -- if you changed it)
 
and this time it should connect and your computer should be added to the My Devices section on your phone !
 
That's how I connected my W810i

---

### Post by techno-mole on 2007-05-22
ok here goes.
Once you change the file like I suggested, did you reboot? - yes did that.
Is this an external dongle...since you say adapter ? - its a class 2 usb bluetooth adapter (i think they are also called dongles, always thought that to be a strange name for something)
Make sure the dongle is connected when you reboot. Then start up the Bluetooth File Sharing App by going to Applications --> Accessories --> Bluetooth File Transfer - adapter (dongle) was connected when i re-booted, and i started the program - applications - accessories - bluetooth file sharing.
i then did a search for bluetooth devices on my phone and the only thing it found was a v630i ? this i believe is another sony ericsson phone, but it didnt list a pc though, i did try entering the code (1234 and the default for the phone 0000) but it didnt work
i did another search on the phone and it came up with an unknown device, but i couldnt connect to that either, and now it cant find anything.
cheers

---

### Post by techno-mole on 2007-05-23
the more i mess about with it the more im thinkgin its something to do with the pc, ive tried sending a files over from the pc to the phone via bluetooth and i get an error message saying programming error......the device in the list, but i cant see the rest of the error.
so maybe ill un-install the bluetooth stuff and re-install.
cheers

tried removing and re-installing, but no joy, it doesnt really matter because we have more than one pc, ive been trying to show my other half and the kids that linux is a viable option over windows, and little things like this kind of set me back a bit, so hopefully i can get it sorted, or maybe it'll get sorted out with updates or something, so for now i shall keep trying with getting it to work under linux, but if i need it i can install it on one of the windows machines and send the files over the network, which i set up in about 2 minutes ! i couldnt get ubuntu to network with windows when i had edgy, but its so much easier with fiesty, in fact it was quicker to set my linux pc to network with an xp system than it was to network the xp systems together, the only thing i had to do was set up a user and passwords, which took no time at all, so thumbs up for that, but thumbs down for the bluetooth though, but in all fairness it maybe my phones not that good.
cheers for the help though, much appreciated.

---

### Post by laffys on 2007-05-25
ijust have to say i followed it to the "T" and got my phone paired just fine. Phone is sanyo 8400

---

### Post by Inxsible on 2007-05-25
techno,

Are you sure your bluetooth adapter is still in working condition ?

I am just shooting wildly here !

---

### Post by techno-mole on 2007-05-26
i should its in working condition, i got it a week ago, and it works fine on the windows pc's
im going to do more reading because from what i can tell the bluetooth adapter is working fine under linux, that is to say it gets detected and activated, and the phone works fine, they just dont talk to each other.
cheers

---

