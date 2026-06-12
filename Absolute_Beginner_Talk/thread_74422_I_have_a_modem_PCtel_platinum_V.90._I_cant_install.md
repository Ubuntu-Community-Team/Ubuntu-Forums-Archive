---
title: "I have a modem PCtel platinum V.90. I cant install"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by Geron on 2005-10-11
Hi excuse me for my english...

    I have a PCtel platinum V.90 and a cant install. im a complet Beginner. i need help please.

   Thanks

---

### Post by Zelut on 2005-10-11
Have you looked at the instrcutions on the [www.ubuntuguide.org](www.ubuntuguide.org) concerning installing and detecting a modem?  Take a look and see if that gives you any more ideas.  (I also suggest following the other suggestions there as far as updates, tweaks and codecs)

---

### Post by Kapre on 2005-10-11
[QUOTE=Geron]Hi excuse me for my english...

    I have a PCtel platinum V.90 and a cant install. im a complet Beginner. i need help please.

   Thanks[/QUOTE]

Geron - I've googled and found this [site]("http://www.modem-help.co.uk/chips/pct1789.html") which I think has all info of the drivers that you require. Since this is an old site. could you please advise what Ubuntu version did you install? I think Ubuntu 5.10 would detect your modem. Anyways, I also found (googling) that you have to set the modem to use /dev/ttyS15.

K

---

### Post by cdhinch on 2005-11-18
I have the same modem and it's a bit tricky to get it working.
First you will need to get the build-essential and linux-source packages via apt.
Next download [http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-4c.tar.gz]("http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-4c.tar.gz").

Now open a terminal window and run the following commands in the directory you just downloaded the tarball into:```
tar -zxvf pctel-0.9.7-9-rht-4c.tar.gz
cd pctel-0.9.7-9-rht-4c
sudo ./setup
```

If everything went right you will get a message saying "installation done" at the end of the output.

Now run the command:```
sudo gedit /etc/modprobe.conf
```
and enter the following into window that just opened:```
include /etc/modprobe.d
# for pctel modem
alias char-major-62 linmodem
below linmodem pctel
below pctel pctel_hw
# country code for pctel modem
options pctel country_code=1
install linmodem /bin/ln -s /dev/ttyS_PCTEL0 /dev/modem;/sbin/modprobe --ignore-install linmodem

```
Close the window and click "Save" when prompted.
Now run the command:```
sudo gedit /etc/modules
```
and enter the following at the end of the file that just opened:```
# PCTel Modem Drivers
pctel_hw
pctel
linmodem

```
Now close that window and click "Save" when prompted.
Now reboot your computer and modem should work.
The modem device will be /dev/modem.

Charles

NOTE:  This works in both Hoary and Breezy.

---

### Post by eightbit on 2006-02-20
I've got the same modem.  Question is how do I download the files necessary for the installation.  Can I grab the "build-essential and linux-source packages" on my windoz laptop?  I synaptic'ed the build-essential package via my breezy cd but the other one isn't there?

Any help would be appreciated.
Thanks,
Scott

---

### Post by towsonu2003 on 2006-02-20
[QUOTE=eightbit]I've got the same modem.  Question is how do I download the files necessary for the installation.  "build-essential and linux-source packages" 
[/QUOTE]
both should be in the installation cd (unless you really need the source, not the headers (see below). headers are usually enough for compiling stuff etc.)
make sure you have the cd in the repository options, insert cd, make sure it is mounted, and
```
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by eightbit on 2006-02-21
Couldn't get it to work.  Then I tried installing the linux-source package via apt but it wasn't found.  Could I network my laptop (with windows) to my computer(with breezy) to use the laptop's internet connection to access the files.  both computers have network connections.  Is this a possibility and how do I go about doing it?

Thanks,
Scott

---

