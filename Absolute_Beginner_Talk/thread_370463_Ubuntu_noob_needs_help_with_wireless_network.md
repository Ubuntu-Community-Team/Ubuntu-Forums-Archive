---
title: "Ubuntu noob needs help with wireless network"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by PsychoticSheep on 2007-02-25
I have searched for topics and tried a few options but many seem too complicated.

I am using a dell laptop and running Ubuntu from a live CD. I cannot seem to get the wireless network set up

My card is: Dell Wireless 1370 WLAN Mini-PCI card Rev 4.9

can anyone help. I realise i have probably not provided enough information but i really dont know what you guys need lol.

---

### Post by jkeyes0 on 2007-02-25
Can you post the output of:

```
 lspci |grep Broadcom
```

To do this, click Applications ==> Accessories ==> Terminal, and paste the line above into the new window that opens.

Most likely, you have a Broadcom wireless card, with a model number similar to BCM43XX, which requires Ndiswrapper and a copy of the windows driver to install properly.

---

### Post by PsychoticSheep on 2007-02-25
I typed that code in exactly and just got an error message. I was reading about it and i think thats probably what i need to do. Could you maybe help me in setting it up and doing the steps you suggested?

thanks for the quick response

---

### Post by jkeyes0 on 2007-02-25
What exactly was the output of that command? On my system (I have a Marvell wired card, so mine will look slightly different), it looks like this:

```

jkeyes0@Edgydesk:~$ lspci |grep Marvell
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

I can direct you to an appropriate forum thread with instructions once we've got the result of your "lspci |grep Broadcom"

---

### Post by Workinman57 on 2007-02-25
I have the 1370 also in a Dell 

My-laptop:~$  lspci |grep Broadcom
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Is what my dell laptop reports now that I have installed ndiswrapper and used the correct drivers

I am able to connect to WPA  access points and unsecure access points 
I use info from these How To links:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3)

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

ndisgtk can be installed along with ndiswrapper. it provides a GUI interface to install windows drivers

you will need the .inf and .sys files from your windows driver save in the same folder to install .

---

### Post by Oldtimer on 2007-02-25
Try simple things first! Top menubar, SYSTEM, Administration, NETWORKING. Click on wireless.  Click properties. Enter Server name for wireless router you are connecting to and enter Hexadecimal key or password as required.  That worked for my Toshiba laptop with NETGEAR PCMICA card.

---

### Post by PsychoticSheep on 2007-02-26
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) is what i got as well

However, I am not simply connecting to a wireless router. The way i have it set up just now is  an ad-hoc connection and i tunnel in through an internet connection on my main pc.

Any suggestions?

---

### Post by Workinman57 on 2007-02-26
Your doing what!  Your first post said you need to get your card working? You have your pc set up to share a connection? Is the pc on a wireless connection? It is set up as a ad-hoc access point? Liunux PC? wow . Also the live cd errors out on system config when it sees many of the broadcom card chipsets. you may have seen a microcode error when booting from the cd.

---

### Post by oldone on 2007-02-26
pschosheep - I had the same card in a crappy laptop i just bought a few weeks ago and I could not get a squat out of it after 18 hr. days for 5 days of frustration.... I sent the new laptop back and am awaiting another new linux laptop.  I and many others never seemed to get that one working.... all i can say is good luck.

---

### Post by PsychoticSheep on 2007-02-27
PC as in windows xp. not linux. Is it possible to set up this card for adhoc connections?

---

