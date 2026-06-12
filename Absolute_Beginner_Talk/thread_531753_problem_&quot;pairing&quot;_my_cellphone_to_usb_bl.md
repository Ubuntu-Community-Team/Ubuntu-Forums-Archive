---
title: "problem &quot;pairing&quot; my cellphone to usb bluetooth"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-08-21
i got a usb bluetooth adapter yesterday.  I am having a really hard time getting this to work.  Can anyone tell me how to set everything up so i can "pair" my cellphone to my computer via my usb bluetooth adapter? 
Here is some output of my attempts so far:

root@brad-laptop:/home/brad# hcitool scan
Scanning ...
        00:18:AF:57:89:3F       SGH-D807

root@brad-laptop:/home/brad# sdptool search DUN
Inquiring ...
Failed to connect to SDP server on 00:18:AF:57:89:3F: Connection refused


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
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "BlueZ %h (%d)";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
oh, yeah , i got this message about 15 minutes ago:
d-laptop:~$ sdptool search DUN
Inquiring ...
Failed to connect to SDP server on 00:18:AF:57:89:3F: Operation already in progress
brad@brad-laptop:~$ gnome-bluetooth-admin
bash: gnome-bluetooth-admin: command not found
brad@brad-laptop:~$ hcitool scan
Scanning ...
        00:18:AF:57:89:3F       Samsung
brad@brad-laptop:~$ -laptop:~$ sdptool search DUN
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -l
bash: -laptop:~$: command not found
brad@brad-laptop:~$ Inquiring ...
bash: Inquiring: command not found
brad@brad-laptop:~$ Failed to connect to SDP server on 00:18:AF:57:89:3F: Operation already in progress
bash: Failed: command not found
brad@brad-laptop:~$ 

can someone please tell me what im doing wrong? I've never done anything w/ bluetooth on my computer and i'm still somewhat new to linux so keep that in mind when replying.  Thanks!upd

---

### Post by bradmayne on 2007-08-22
no one can help me out? geez...

---

### Post by annda on 2007-08-22
are you trying to run error messages as commands? "-laptop....." and "Failed....." command-not-found messages are strange.

have you tried simply establishing a connection, without using the dial-up service first?

```
sudo hidd --connect 00:18:AF:57:89:3F
```

that way you can at least see if the PINs are working.

you can also read this general guide, maybe it will help you:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

unfortunately, my bluetooth phone is broken so i can't recreate the steps i used to connect :-(

---

### Post by A$h X on 2007-08-22
Looks like you have the necessary apps already installed but to be sure...

tpye linux repositories in google goto the third link, and click on feisty 7.04 (or whatever distro you are running)

Click on feisty 7.04 (or whatever distro you are running) and follw the in-screen instructions.

Once you have the security key and added the google repository, goto applications > add/remove.

There type bluetooth into the saerch box you should see 5 programs with the word bluetooth in them. d/l all of them, and install.

Once installed, goto preferences > bluetooth preferences and click "other devices can connect"

Then goto applications > internet > bluetooth OBEX client and click "search" in the bottom left corner.

You device should show up in the bottom right window, and you can send files to it.

If you want to send files from your device to the computer then goto applications > accessories >  bluetooth file sharing and then search for devices on your bluetooth phone and you should detect the computer. Send a file to it and a message pops up on ubuntu asking if you want to accept the file transfer. Check the "always allow connection from this device" box in the bottom left and your all set! :)

---

### Post by bradmayne on 2007-08-22
hey i tried to download the "key" on the page you spoke of.  Either I'm doing something wrong or the page is messed up.  This is what I see:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBEXwb0YRBADQva2NLpYXxgjNkbuP0LnPoEXruGmvi3XMIxjEUFuGNCP4Rj/a
kv2E5VixBP1vcQFDRJ+p1puh8NU0XERlhpyZrVMzzS/RdWdyXf7E5S8oqNXsoD1z
fvmI+i9b2EhHAA19Kgw7ifV8vMa4tkwslEmcTiwiw8lyUl28Wh4Et8SxzwCggDcA
feGqtn3PP5YAdD0km4S4XeMEAJjlrqPoPv2Gf//tfznY2UyS9PUqFCPLHgFLe80u
QhI2U5jt6jUKN4fHauvR6z3seSAsh1YyzyZCKxJFEKXCCqnrFSoh4WSJsbFNc4PN
b0V0SqiTCkWADZyLT5wll8sWuQ5ylTf3z1ENoHf+G3um3/wk/+xmEHvj9HCTBEXP
78X0A/0Tqlhc2RBnEf+AqxWvM8sk8LzJI/XGjwBvKfXe+l3rnSR2kEAvGzj5Sg0X
4XmfTg4Jl8BNjWyvm2Wmjfet41LPmYJKsux3g0b8yzQxeOA4pQKKAU3Z4+rgzGmf
HdwCG5MNT2A5XxD/eDd+L4fRx0HbFkIQoAi1J3YWQSiTk15fw7RMR29vZ2xlLCBJ
bmMuIExpbnV4IFBhY2thZ2UgU2lnbmluZyBLZXkgPGxpbnV4LXBhY2thZ2VzLWtl
eW1hc3RlckBnb29nbGUuY29tPohjBBMRAgAjAhsDBgsJCAcDAgQVAggDBBYCAwEC
HgECF4AFAkYVdn8CGQEACgkQoECDD3+sWZHKSgCfdq3HtNYJLv+XZleb6HN4zOcF
AJEAniSFbuv8V5FSHxeRimHx25671az+uQINBEXwb0sQCACuA8HT2nr+FM5y/kzI
A51ZcC46KFtIDgjQJ31Q3OrkYP8LbxOpKMRIzvOZrsjOlFmDVqitiVc7qj3lYp6U
rgNVaFv6Qu4bo2/ctjNHDDBdv6nufmusJUWq/9TwieepM/cwnXd+HMxu1XBKRVk9
XyAZ9SvfcW4EtxVgysI+XlptKFa5JCqFM3qJllVohMmr7lMwO8+sxTWTXqxsptJo
pZeKz+UBEEqPyw7CUIVYGC9ENEtIMFvAvPqnhj1GS96REMpry+5s9WKuLEaclWpd
K3krttbDlY1NaeQUCRvBYZ8iAG9YSLHUHMTuI2oea07Rh4dtIAqPwAX8xn36JAYG
2vgLAAMFB/wKqaycjWAZwIe98Yt0qHsdkpmIbarD9fGiA6kfkK/UxjL/k7tmS4Vm
CljrrDZkPSQ/19mpdRcGXtb0NI9+nyM5trweTvtPw+HPkDiJlTaiCcx+izg79Fj9
KcofuNb3lPdXZb9tzf5oDnmm/B+4vkeTuEZJ//IFty8cmvCpzvY+DAz1Vo9rA+Zn
cpWY1n6z6oSS9AsyT/IFlWWBZZ17SpMHu+h4Bxy62+AbPHKGSujEGQhWq8ZRoJAT
G0KSObnmZ7FwFWu1e9XFoUCt0bSjiJWTIyaObMrWu/LvJ3e9I87HseSJStfw6fki
5og9qFEkMrIrBCp3QGuQWBq/rTdMuwNFiEkEGBECAAkFAkXwb0sCGwwACgkQoECD
D3+sWZF/WACfeNAu1/1hwZtUo1bR+MWiCjpvHtwAnA1R3IHqFLQ2X3xJ40XPuAyY
/FJG
=Quqp
-----END PGP PUBLIC KEY BLOCK-----

How do you download this?  I have never had to download a key before so what the heck is this?  Why is there no area to click to download like with everything else in the free world?  Is the page down?  Do i cut and paste or something?

Also, this is the output I got from doing what the first person to try and help suggested:

root@brad-laptop:/home/brad# sudo hidd --connect 00:18:AF:57:89:3F
Can't get device information: Connection refused

---

### Post by bradmayne on 2007-08-22
i have an idea about what i did wrong.  I made some changes to the "/etc/bluetooth/hcid.conf" after I saw an article in the september issue of "Linux Journal".  Is there any way someone can paste your ""/etc/bluetooth/hcid.conf" so that i can see what's working for you?  I think the changes I made based on the article ending up hurting instead of helping.    The first time I used the "sdptool search DUN" I received positive results.  I didn' make any changes at the time.  Also, how the heck do I download that key from the google linux repository?

---

### Post by E_K on 2007-08-23
just right click the link and choose save as, my bluetooth isnt working either, i have a switch on the front which doesnt turn the light on, which must have something to do with it, as my wireless light did the same until i installed the drivers for it, i half feel like giving up on the bluetooth, though it feels like a shame, as its just there

---

### Post by bradmayne on 2007-08-25
okay i got the key and installed the programs as you suggested though i am still having the same problem as i had before.

---

### Post by Inxsible on 2007-08-25
Do you see the Security Manager section in the hcid file.
change ```
security user
``` to ```
security auto
``` and then use the passkey to pair once and then it will add the computer in the list of known devices

---

### Post by bradmayne on 2007-08-25
I got it! i needed the OBEX-push and some other stuff relating to my samsung from synaptic everything is cool now.  I am sending metallica's for whom the bell tolls to my cell as i write this! Now i just need to figure out how to use my cell as a modem....

---

### Post by bradmayne on 2007-08-27
i just noticed that there's a problem.  I can't send files from my phone to my computerI! I can send files from my laptop to my cell phone though.  Does anyone have any ideas agout how to solve this problem?

---

### Post by A$h X on 2007-08-28
If you installed all the programs in my first post then you should have the necessary program under Applications > Accessories > Bluetooth file sharing. Click it and then search for devices on your phone. You should see the name of your machine pop up, send a file from phone to machine and click "accept" on the pop-up dialog on ubuntu.

---

