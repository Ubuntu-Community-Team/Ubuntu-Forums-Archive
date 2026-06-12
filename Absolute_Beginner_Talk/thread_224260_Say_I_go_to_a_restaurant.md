---
title: "Say I go to a restaurant"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-07-27
that has wireless internet....how am I supposed to connect to it? It's (ubuntu) not detecting the wireless connection here at my university. So when I go to Chicago next week I am not going to be able to use the internet on my laptop. Do I have to have the network name of every wireless internet I am going to connect to? I need a guide for dummies.:( :( :(

---

### Post by trivialpackets on 2006-07-27
Have you tried using network-manager-gnome?  This works great for me in network switching.  Just click on the icon and it tells you what is available.  May be worth looking into if you're running Dapper.

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> that has wireless internet....how am I supposed to connect to it? It's (ubuntu) not detecting the wireless connection here at my university. So when I go to Chicago next week I am not going to be able to use the internet on my laptop. Do I have to have the network name of every wireless internet I am going to connect to? I need a guide for dummies.:( :( :(

Wait... if everything is working with your wireless card, it should provide a  listing of available wireless networks in your network control panel (under the Properties of your Wireless Connection).

To make sure if its working, you could open a command line and type:

# iwlist scan

I do sometimes have problems with Ubuntu not connecting to new wireless access points right away.  I find sometimes I have to alter the wireless settings, deactivate the card, and shut down the network settings panel before re-entering and re-activating the card.  Only then does connecting to the new network do anything.

---

### Post by friedokra on 2006-07-27
"To make sure if its working, you could open a command line and type:

# iwlist scan"

I typed this in the terminal and nothing happened.

---

### Post by ovimunt on 2006-07-27
You need to type

```

iwlist ethX scan

```

Where ethX is eth0, eth1, or whichever eth your wireless card is.

---

### Post by friedokra on 2006-07-27
I don't know what network manager gnome is and I don't know if I have dapper. I am a linux-novice to the utmost extreme. I just installed it and here it is. I cannot get this "network manager" anyway as I cannot connect to the internet (right now I'm using the school's computer)

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> "To make sure if its working, you could open a command line and type:

# iwlist scan"

I typed this in the terminal and nothing happened.

Don't include the #

That just indicates the prompt.

```

For example, mine reads:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:3F:47:FF
                    ESSID:"blabla1"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:6C:18:48:08
                    ESSID:"blabla2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-41 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

```

If your card is finding access points, then it is probably working alright, and you just need to play around with the Network Settings manager.

---

### Post by friedokra on 2006-07-27
> **ovimunt said:**
> You need to type

```

iwlist ethX scan

```

Where ethX is eth0, eth1, or whichever eth your wireless card is.

then it says "interface doesn't support scanning":confused:

---

### Post by friedokra on 2006-07-27
okay. I typed in "iwlist scan" and then it says:

lo    interface doesn't support scanning

eth1  no scan results
eth0  doesn't support scanning

sit0  interface doesn't support scanning

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> then it says "interface doesn't support scanning":confused:

Actually, don't worry about the ethX.  If you just type iwlist scan, it will scan everything available.

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> okay. I typed in "iwlist scan" and then it says:

lo    interface doesn't support scanning

eth1  no scan results
eth0  doesn't support scanning

sit0  interface doesn't support scanning

Ok, so eth1 (your wireless connection) is at least trying to scan.

Do you have an active access point (or wireless router) in your area at present?

If so, then your PC isn't seeing it, and there is possibly something wrong.  Post the results of:

# lspci

---

### Post by friedokra on 2006-07-27
snip

---

### Post by ovimunt on 2006-07-27
Umm... you need to install the drivers for your wireless card first... similar principle as in Windows... the method is a bit different though... :-|

---

### Post by atrus123 on 2006-07-27
> **ovimunt said:**
> Umm... you need to install the drivers for your wireless card first... similar principle as in Windows... the method is a bit different though... :-|

This sounds likely.

I'll be here for a bit, and I may be able to help you with it.

---

### Post by friedokra on 2006-07-27
how do I install the drivers? and I can't manually type in all of the stuff that comes up when I type in "lspci". I'm not on the internet on my laptop. After I typed that a whole bunch of **** came up. Do you need me to manually type all of it?

---

### Post by steve.horsley on 2006-07-27
I'm not so sure about that. I don't think eth1 would exist unless a driver found the wireless adapter. What does the command **iwconfig** say?

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> how do I install the drivers? and I can't manually type in all of the stuff that comes up when I type in "lspci". I'm not on the internet on my laptop. After I typed that a whole bunch of **** came up. Do you need me to manually type all of it?

Gnome terminal will let you copy and paste.  Just look through the menus.

If you can't find it or are using some other terminal, just look for stuff related to network.  You could try:

# lspci | grep Network

---

### Post by ovimunt on 2006-07-27
> **atrus123 said:**
> Gnome terminal will let you copy and paste.  Just look through the menus.

C'mon man! The poor guy says he's not posting on the forum from the same computer he's got Ubuntu on! How is he supposed to type all that cryptic output??? :shock:

---

### Post by friedokra on 2006-07-27
I am on the school's computer. I can't copy and paste stuff from my laptop onto my school's computer. especially if I can't connect to a network.

---

### Post by ovimunt on 2006-07-27
Right, what brand is your laptop? I'll have a look to see what wireless adapter it comes with.

EDIT: There is a slight problem... Ubuntu is not a linux distribution you want to install if you have no internet access (at least through a wired connection) on that particular computer. Ubuntu is a bit internet based as in you need to download all the packages that you don't have...

---

### Post by friedokra on 2006-07-27
the command "iwconfig" after I type it says:

lo  no wireless extensions

eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4318"
     Mode:Managed Access Point:Invalid Bit Rate=1 Mb/s
     RTS thr:off Fragmentthr:off
     Link Quality:0 Signal Level:0 Noise Level:0
     Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
     Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions

sit0 no '' ''

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> I am on the school's computer. I can't copy and paste stuff from my laptop onto my school's computer. especially if I can't connect to a network.

Sorry, missed that part.

Did you try the grep command?  I just need to know your chipset.

lspci | grep Network

---

### Post by friedokra on 2006-07-27
> **ovimunt said:**
> Right, what brand is your laptop? I'll have a look to see what wireless adapter it comes with.

EDIT: There is a slight problem... Ubuntu is not a linux distribution you want to install if you have no internet access (at least through a wired connection) on that particular computer. Ubuntu is a bit internet based as in you need to download all the packages that you don't have...

I downloaded it at home when I was connected to the internet. I can connect to the internet when I get home, but I'm trying to avoid going home at the moment. My laptop is an Acer Aspire 5004WLMi

---

### Post by ovimunt on 2006-07-27
Ubuntu comes with the drivers for that adapter! Yet, you need to install the firmware for it and I haven't got a clue how to do that without a internet connection on that computer... When I installed mine I was wired to my router.

The other option would be to install the Windows driver using ndiswrapper but that's gonna be a pain in the a** again if you have no internet access... :-(

---

### Post by friedokra on 2006-07-27
> **atrus123 said:**
> Sorry, missed that part.

Did you try the grep command?  I just need to know your chipset.

lspci | grep Network

I did that and then it be sayin': 0000:00:Ob.O Network controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN controller (rev 02)

---

### Post by friedokra on 2006-07-27
> **ovimunt said:**
> Ubuntu comes with the drivers for that adapter! Yet, you need to install the firmware for it and I haven't got a clue how to do that without a internet connection on that computer... When I installed mine I was wired to my router.

The other option would be to install the Windows driver using ndiswrapper but that's gonna be a pain in the a** again if you have no internet access... :-(

I could do it when I got home if you give a step by step intended for an eighty year old grandmother. I should be able to install the "firmware" but where do I go online to do that?

---

### Post by ovimunt on 2006-07-27
Sorry buddy but with all due respect I have to say that you're a bit stuck with that because on an Acer laptop you also need to install ***acer_acpi***... That's because on your Acer, just like on mine, the wireless button on the computer isn't working in linux, in case you haven't noticed yet...

---

### Post by friedokra on 2006-07-27
> **ovimunt said:**
> Sorry buddy but with all due respect I have to say that you're a bit stuck with that because on an Acer laptop you also need to install ***acer_acpi***... That's because on your Acer, just like on mine, the wireless button on the computer isn't working in linux, in case you haven't noticed yet...

huh? how do I install it? like I said, when I get home, I can connect to the internet on the laptop and install anything. Now your'e saying that there is no way for wireless internet to work for me?

---

### Post by atrus123 on 2006-07-27
The broadcom driver bundled with Ubuntu rarely works.  

You need to download the driver from the Acer website and extract the inf and sys file.

Then use ndiswrapper to install it.

# sudo apt-get install ndiswrapper

# sudo ndiswrapper -i bcmw1*.inf

Or something like that.

---

### Post by atrus123 on 2006-07-27
> **friedokra said:**
> huh? how do I install it? like I said, when I get home, I can connect to the internet on the laptop and install anything. Now your'e saying that there is no way for wireless internet to work for me?

No, no.. This card works fine with Ubuntu.  I'm using it myself.

I figured it was broadcom chipset when it only seemed to be sort of working.  I can help you out.

---

### Post by ovimunt on 2006-07-27
Look, the broadcom driver that comes with Ubuntu works ABSOLUTELY FINE!!! You just need to install the FIRMWARE! I am using an Acer laptop with EXACTLY the same wireless adapter and trust me, it WORKS!

---

### Post by friedokra on 2006-07-27
> **atrus123 said:**
> The broadcom driver bundled with Ubuntu rarely works.  

You need to download the driver from the Acer website and extract the inf and sys file.

Then use ndiswrapper to install it.

# sudo ndiswrapper -i bcmw1*.inf

Or something like that.

okay. so when I go to the Acer website, what exactly am I going to be looking for? and where is this firmware?

---

### Post by ovimunt on 2006-07-27
You don't get the firmware from the Acer website...

Go here and it will tell you all you need to know about setting up your adapter:
[B]
*EDIT:*[/B] [https://help.ubuntu.com/community/wifidocs/driver/bcm43xx/dapper]("https://help.ubuntu.com/community/wifidocs/driver/bcm43xx/dapper")

Then for the **acer_acpi** module I'm writing a how to right now.

---

### Post by atrus123 on 2006-07-27
> **ovimunt said:**
> Look, the broadcom driver that comes with Ubuntu works ABSOLUTELY FINE!!! You just need to install the FIRMWARE! I am using an Acer laptop with EXACTLY the same wireless adapter and trust me, it WORKS!

Not always.  You can deal with firmware or ndiswrapper.  I'm more comfortable with ndiswrapper.

Go ahead and walk him through the firmware method then; i don't want to confuse him.

---

### Post by friedokra on 2006-07-27
thanks for the help guys. I am about to leave the library. I will check back later so any bit of info would be helpful.

---

### Post by atrus123 on 2006-07-27
You may also want to have a look at this wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

It helped me out in the past getting this card working.

---

### Post by ovimunt on 2006-07-27
The ***help.ubuntu.com*** site seems to be down... Can someone else check and let me know if it works for them?

---

### Post by ovimunt on 2006-07-27
**ATTENTION: This HOW TO covers ONLY the installation of the *acer_acpi* module and NOT of the wireless adapter drivers.**

Before you can go ahead and install the ***acer_acpi*** module you need to make sure you have some other tools installed.
```

sudo aptitude update
sudo aptitude install build-essential

```

You'll also need the linux headers so check the version of kernel you are running:
```

uname -r

```

You should get some output like this
```

2.6.15-26-386

```

Now you need to type:
```

sudo aptitude install linux-headers-X.X.XX-XX-XXX

```

Where X.X.XX-XX-XXX is the kernel version i.e. 2.6.15-26-386

Once this is done you can go ahead and install the ***acer_acpi***.
First you should create a folder to keep all your downloads in one place.
```

mkdir /home/USER_NAME/download

```
Where USER_NAME is your actual user name.

Now go to the new folder
```

cd /home/USER_NAME/download

```

and download and install the package:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
cd ../..

```

Load the acer_acpi into memory and activate the wireless:
```

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit

```

And check if it worked:
```

dmesg | grep acer_acpi

```

You should get some output like this:
```

[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

```

Right, this might have worked for now but you need to load and activate ***acer_acpi*** every time your computer starts. 
For this you can write a little start up script so you don't have to do it manually each and every time.

[b]ATTENTION!
For Gnome type:[/b]
```

sudo gedit /etc/init.d/acer_acpi_wireless_enable

```
**Or if you're running KDE type:**
```

sudo kate /etc/init.d/acer_acpi_wireless_enable

```

Paste the following code and save:
```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Make the file executable and add it to the appropiate linux run levels.
**ATTENTION! Don't miss ANY of the characters in the following lines, especialy the dots in the third line!**
```

su
chmod 755 /etc/init.d/acer_acpi_wireless_enable
update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
exit

```

Now check if it worked:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

If you get any ***No such file or directory*** messages then something must have gone wrong during the last couple of steps but your ***acer_acpi*** is still installed and can be started manually if needed.

If you didn't get any error messages everything should be up and running. You can now restart the computer and, if you have already installed the wireless drivers, your wireless adapter should work fine and be ready to configure.

---

### Post by moshuptrail on 2006-07-27
you'll need to type:
sudo iwlist scan

it will ask for your password

---

### Post by Rich3077 on 2006-07-27
Good topic because I also have an Acer laptop that I am thinking of switching to Ubuntu. I also have a hardware button on my laptop to activate the network card. If I went the firmware route would the button work? Any beta stuff out to enable the button?

---

### Post by ovimunt on 2006-07-27
The ***acer_acpi*** is needed no matter what method you use to install the wireless drivers. It is not part of the wireless drivers and it does more then just enable the wireless adapter. 

Check this out:

[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

---

### Post by Perogies on 2006-07-27
I was having a lot of trouble with getting my wireless to work on my laptop (not the same brand as your's, though), but I came across a post suggesting WifiRadar.  After installing it I was able to open it up, see all the networks around my house (including mine ;) ) and it sort of walked me through on how to connect to it.  

[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

One thing I never had the chance to try with it is connecting to the wireless at somewhere besides my house.

Does anyone else like using this or is there something better to use?

---

### Post by friedokra on 2006-07-27
> **ovimunt said:**
> **ATTENTION: This HOW TO covers ONLY the installation of the *acer_acpi* module and NOT of the wireless adapter drivers.**

Before you can go ahead and install the ***acer_acpi*** module you need to make sure you have some other tools installed.
```

sudo aptitude update
sudo aptitude install build-essential

```

You'll also need the linux headers so check the version of kernel you are running:
```

uname -r

```

You should get some output like this
```

2.6.15-26-386

```

Now you need to type:
```

sudo aptitude install linux-headers-X.X.XX-XX-XXX

```

Where X.X.XX-XX-XXX is the kernel version i.e. 2.6.15-26-386

Once this is done you can go ahead and install the ***acer_acpi***.
First you should create a folder to keep all your downloads in one place.
```

mkdir /home/USER_NAME/download

```
Where USER_NAME is your actual user name.

Now go to the new folder
```

cd /home/USER_NAME/download

```

and download and install the package:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
cd ../..

```

Load the acer_acpi into memory and activate the wireless:
```

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit

```

And check if it worked:
```

dmesg | grep acer_acpi

```

You should get some output like this:
```

[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

```

Right, this might have worked for now but you need to load and activate ***acer_acpi*** every time your computer starts. 
For this you can write a little start up script so you don't have to do it manually each and every time.

[b]ATTENTION!
For Gnome type:[/b]
```

sudo gedit /etc/init.d/acer_acpi_wireless_enable

```
**Or if you're running KDE type:**
```

sudo kate /etc/init.d/acer_acpi_wireless_enable

```

Paste the following code and save:
```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Make the file executable and add it to the appropiate linux run levels.
**ATTENTION! Don't miss ANY of the characters in the following lines, especialy the dots in the third line!**
```

su
chmod 755 /etc/init.d/acer_acpi_wireless_enable
update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
exit

```

Now check if it worked:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

If you get any ***No such file or directory*** messages then something must have gone wrong during the last couple of steps but your ***acer_acpi*** is still installed and can be started manually if needed.

If you didn't get any error messages everything should be up and running. You can now restart the computer and, if you have already installed the wireless drivers, your wireless adapter should work fine and be ready to configure.

All I am getting is error messages saying "no such file or directory. How come the linux magic isn't working:

clay@clay-laptop:~$ sudo aptitude update
Password:
clay@clay-laptop:~$ 417
bash: 417: command not found
clay@clay-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [42.7kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4101B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [10.6kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [25.4kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Fetched 146kB in 3s (47.1kB/s)
Reading package lists... Done
clay@clay-laptop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libmudflap0 libmudflap0-dev libstdc++6-4.0-dev linux-kernel-headers make
The following packages have been kept back:
  firefox firefox-gnome-support kdelibs-bin kdelibs-data kdelibs4c2a
  libfreetype6 libnspr4 libnss3 linux-image-2.6.15-26-amd64-generic
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libmudflap0 libmudflap0-dev libstdc++6-4.0-dev
  linux-kernel-headers make
0 packages upgraded, 15 newly installed, 0 to remove and 9 not upgraded.
Need to get 12.6MB of archives. After unpacking 49.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1 [1564kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libc6-dev 2.3.6-0ubuntu20 [2329kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main cpp-4.0 4.0.3-1ubuntu5 [2261kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc-4.0 4.0.3-1ubuntu5 [526kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc 4:4.0.3-1 [5040B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1480kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2585kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1388B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [299kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main build-essential 11.1 [6672B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe libmudflap0 4.0.3-1ubuntu5 [175kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe libmudflap0-dev 4.0.3-1ubuntu5 [111kB]
Fetched 12.6MB in 2m47s (74.9kB/s)
Selecting previously deselected package binutils.
(Reading database ... 83664 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_amd64.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_amd64.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_amd64.deb) ...
Selecting previously deselected package libmudflap0.
Unpacking libmudflap0 (from .../libmudflap0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package libmudflap0-dev.
Unpacking libmudflap0-dev (from .../libmudflap0-dev_4.0.3-1ubuntu5_amd64.deb) ...
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up libmudflap0 (4.0.3-1ubuntu5) ...

Setting up libmudflap0-dev (4.0.3-1ubuntu5) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
Errors were encountered while processing:
 python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
clay@clay-laptop:~$ uname -r
2.6.15-26-amd64-generic
clay@clay-laptop:~$ sudo aptitude install linux-headers-2.6.15-26-amd64-generic
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  linux-headers-2.6.15-26
The following packages have been kept back:
  firefox firefox-gnome-support kdelibs-bin kdelibs-data kdelibs4c2a
  libfreetype6 libnspr4 libnss3 linux-image-2.6.15-26-amd64-generic
The following NEW packages will be installed:
  linux-headers-2.6.15-26 linux-headers-2.6.15-26-amd64-generic
0 packages upgraded, 2 newly installed, 0 to remove and 9 not upgraded.
Need to get 7772kB of archives. After unpacking 76.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26 2.6.15-26.45 [6908kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26-amd64-generic 2.6.15-26.45 [864kB]
Fetched 7772kB in 50s (153kB/s)
Selecting previously deselected package linux-headers-2.6.15-26.
(Reading database ... 85782 files and directories currently installed.)
Unpacking linux-headers-2.6.15-26 (from .../linux-headers-2.6.15-26_2.6.15-26.45_amd64.deb) ...
Selecting previously deselected package linux-headers-2.6.15-26-amd64-generic.
Unpacking linux-headers-2.6.15-26-amd64-generic (from .../linux-headers-2.6.15-26-amd64-generic_2.6.15-26.45_amd64.deb) ...
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.15-26 (2.6.15-26.45) ...

Setting up linux-headers-2.6.15-26-amd64-generic (2.6.15-26.45) ...
Errors were encountered while processing:
 python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
clay@clay-laptop:~$ mkdir /home/USER_NAME/download
mkdir: cannot create directory `/home/USER_NAME/download': No such file or directory
clay@clay-laptop:~$ mkdir /home/clay/download
clay@clay-laptop:~$ mkdir/home/clay/download
bash: mkdir/home/clay/download: No such file or directory
clay@clay-laptop:~$ mkdir /home/USER_NAME/downloaclay
mkdir: cannot create directory `/home/USER_NAME/downloaclay': No such file or directory
clay@clay-laptop:~$ mkdir /home/clay/download
mkdir: cannot create directory `/home/clay/download': File exists
clay@clay-laptop:~$ cd /home/clay/download
clay@clay-laptop:~/download$ wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
--22:10:27--  [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
           => `acer_acpi-0.3.tar.gz'
Resolving [www.archernar.co.uk](www.archernar.co.uk)... 212.159.9.131
Connecting to www.archernar.co.uk|212.159.9.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,083 (16K) [application/x-tar]

100%[====================================>] 16,083        57.30K/s

22:10:28 (57.18 KB/s) - `acer_acpi-0.3.tar.gz' saved [16083/16083]

clay@clay-laptop:~/download$ tar zxvf acer_acpi-0.3.tar.gz
acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
clay@clay-laptop:~/download$ cd acer_acpi-0.3
clay@clay-laptop:~/download/acer_acpi-0.3$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/clay/download/acer_acpi-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
  CC [M]  /home/clay/download/acer_acpi-0.3/acer_acpi.o
  Building modules, stage 2.
  MODPOST
  CC      /home/clay/download/acer_acpi-0.3/acer_acpi.mod.o
  LD [M]  /home/clay/download/acer_acpi-0.3/acer_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
clay@clay-laptop:~/download/acer_acpi-0.3$ sudo make install
mkdir -p /lib/modules/2.6.15-26-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.15-26-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko'
depmod -a
clay@clay-laptop:~/download/acer_acpi-0.3$ cd ../..su
bash: cd: ../..su: No such file or directory
clay@clay-laptop:~/download/acer_acpi-0.3$ modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko): Operation not permitted
clay@clay-laptop:~/download/acer_acpi-0.3$ chmod 777 /proc/acpi/acer/wireless
chmod: cannot access `/proc/acpi/acer/wireless': No such file or directory
clay@clay-laptop:~/download/acer_acpi-0.3$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: No such file or directory
clay@clay-laptop:~/download/acer_acpi-0.3$ exitsu
bash: exitsu: command not found
clay@clay-laptop:~/download/acer_acpi-0.3$ modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko): Operation not permitted
clay@clay-laptop:~/download/acer_acpi-0.3$ chmod 777 /proc/acpi/acer/wireless
chmod: cannot access `/proc/acpi/acer/wireless': No such file or directory
clay@clay-laptop:~/download/acer_acpi-0.3$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: No such file or directory
clay@clay-laptop:~/download/acer_acpi-0.3$ exitdmesg | grep acer_acpi
bash: exitdmesg: command not found
clay@clay-laptop:~/download/acer_acpi-0.3$ dmesg | grep acer_acpi
clay@clay-laptop:~/download/acer_acpi-0.3$ su
Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~/download/acer_acpi-0.3$ dmesg | grep acer_acpi
clay@clay-laptop:~/download/acer_acpi-0.3$ dmesg | grep acer_acpi
clay@clay-laptop:~/download/acer_acpi-0.3$ su
Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~/download/acer_acpi-0.3$ wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
--22:13:14--  [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
           => `acer_acpi-0.3.tar.gz'
Resolving [www.archernar.co.uk](www.archernar.co.uk)... 212.159.9.131
Connecting to www.archernar.co.uk|212.159.9.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,083 (16K) [application/x-tar]

100%[====================================>] 16,083        57.03K/s

22:13:14 (56.97 KB/s) - `acer_acpi-0.3.tar.gz' saved [16083/16083]

clay@clay-laptop:~/download/acer_acpi-0.3$ tar zxvf acer_acpi-0.3.tar.gz
acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
clay@clay-laptop:~/download/acer_acpi-0.3$ cd acer_acpi-0.3
clay@clay-laptop:~/download/acer_acpi-0.3/acer_acpi-0.3$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/clay/download/acer_acpi-0.3/acer_acpi-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
  CC [M]  /home/clay/download/acer_acpi-0.3/acer_acpi-0.3/acer_acpi.o
  Building modules, stage 2.
  MODPOST
  CC      /home/clay/download/acer_acpi-0.3/acer_acpi-0.3/acer_acpi.mod.o
  LD [M]  /home/clay/download/acer_acpi-0.3/acer_acpi-0.3/acer_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
clay@clay-laptop:~/download/acer_acpi-0.3/acer_acpi-0.3$ sudo make install
mkdir -p /lib/modules/2.6.15-26-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.15-26-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko'
depmod -a
clay@clay-laptop:~/download/acer_acpi-0.3/acer_acpi-0.3$ cd ../..
clay@clay-laptop:~/download$ wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
--22:13:24--  [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
           => `acer_acpi-0.3.tar.gz.1'
Resolving [www.archernar.co.uk](www.archernar.co.uk)... 212.159.9.131
Connecting to www.archernar.co.uk|212.159.9.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,083 (16K) [application/x-tar]

100%[====================================>] 16,083        62.78K/s

22:13:25 (62.55 KB/s) - `acer_acpi-0.3.tar.gz.1' saved [16083/16083]

clay@clay-laptop:~/download$ tar zxvf acer_acpi-0.3.tar.gz
acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
clay@clay-laptop:~/download$ cd acer_acpi-0.3
clay@clay-laptop:~/download/acer_acpi-0.3$ make
make: Nothing to be done for `all'.
clay@clay-laptop:~/download/acer_acpi-0.3$ sudo make install
mkdir -p /lib/modules/2.6.15-26-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.15-26-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko'
depmod -a
clay@clay-laptop:~/download/acer_acpi-0.3$ cd ../..
clay@clay-laptop:~$ su
Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~$ sudo gedit /etc/init.d/acer_acpi_wireless_enable
clay@clay-laptop:~$ su
Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~$ ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls: /etc/rcS.d/S39acer-acpi-wireless-enable: No such file or directory
clay@clay-laptop:~$ ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls: /etc/rc0.d/S34acer-acpi-wireless-enable: No such file or directory
clay@clay-laptop:~$ ls /etc/rc6.d/S34acer-acpi-wireless-enable
ls: /etc/rc6.d/S34acer-acpi-wireless-enable: No such file or directory
clay@clay-laptop:~$ wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
--22:15:34--  [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
           => `acer_acpi-0.3.tar.gz'
Resolving [www.archernar.co.uk](www.archernar.co.uk)...
212.159.9.131
Connecting to www.archernar.co.uk|212.159.9.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,083 (16K) [application/x-tar]

100%[====================================>] 16,083        56.81K/s

22:15:35 (56.71 KB/s) - `acer_acpi-0.3.tar.gz' saved [16083/16083]

clay@clay-laptop:~$ tar zxvf acer_acpi-0.3.tar.gz
acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
clay@clay-laptop:~$ cd acer_acpi-0.3
clay@clay-laptop:~/acer_acpi-0.3$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/clay/acer_acpi-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
  CC [M]  /home/clay/acer_acpi-0.3/acer_acpi.o
  Building modules, stage 2.
  MODPOST
  CC      /home/clay/acer_acpi-0.3/acer_acpi.mod.o
  LD [M]  /home/clay/acer_acpi-0.3/acer_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
clay@clay-laptop:~/acer_acpi-0.3$ sudo make install
mkdir -p /lib/modules/2.6.15-26-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.15-26-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko'
depmod -a
clay@clay-laptop:~/acer_acpi-0.3$ cd ../..
clay@clay-laptop:/home$ su
Password:
su: Authentication failure
Sorry.
clay@clay-laptop:/home$

---

### Post by friedokra on 2006-07-27
man....I don't know what to do. I downloaded a driver on the acer website in zip format, but all the files are for windows. I don't know how to use any of what I just downloaded.:confused: :sad: :confused: and on top of all of this, the tutorial I just went through didn't work. All I get are error messages.

---

### Post by friedokra on 2006-07-27
this is the main thing holding me back. I was so close.

"Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~/download/acer_acpi-0.3$"

---

### Post by friedokra on 2006-07-27
and I spotted another problem here: Selecting previously deselected package linux-headers-2.6.15-26.
(Reading database ... 85782 files and directories currently installed.)
Unpacking linux-headers-2.6.15-26 (from .../linux-headers-2.6.15-26_2.6.15-26.45_amd64.deb) ...
Selecting previously deselected package linux-headers-2.6.15-26-amd64-generic.
Unpacking linux-headers-2.6.15-26-amd64-generic (from .../linux-headers-2.6.15-26-amd64-generic_2.6.15-26.45_amd64.deb) ...
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.15-26 (2.6.15-26.45) ...

Setting up linux-headers-2.6.15-26-amd64-generic (2.6.15-26.45) ...
Errors were encountered while processing:
python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
python2.3-4suite

---

### Post by ovimunt on 2006-07-28
Man, I could spot an awful lot of typing errors in the output you provided so it's no wonder it doesn't work. Don't copy and paste entire paragraphs of command lines, try doing it line by line, it's a lot easier to avoid typing mistakes.

Also, you're running the ***amd64-generic*** kernel which I've never seen before. When I installed the 64bit linux it didn't have the ***generic*** part in the version name so I'm not sure about your kernel. Besides I think you may need some additional packages for the AMD64 kernel, I'll have to look into that. 

Bottom line is that unless you're running a server you really don't need the AMD64 version and should use i386 instead. The main reason for this is that quite a few applications are not avaialable for 64bit, most notably Flash and Windows Media Codecs. Right now these are for 32bit ONLY.

The problem is that unlike WinXP64 in linux you cannot really run 32bit applications under an AMD64 environemt. Actually you can't do that in Windows either. Microsoft provides a 32bit emulator that comes with the 64 bit Windows and that't how 32bit applications are run.

---

### Post by richardward101 on 2006-07-28
> **friedokra said:**
> this is the main thing holding me back. I was so close.

"Password:
su: Authentication failure
Sorry.
clay@clay-laptop:~/download/acer_acpi-0.3$"

su is a request to change to the super user by suppling the super users passwod. the super user doesn't have a password by default (which is why we use sudo which just asks for your password), so thats why its saying authentication failure. instead of su, try
```
sudo su
```
and put your password in.

instead of the prompt you see being:
```
clay@clay-laptop
```
it should be:
```
root@clay-laptop
```
now go on with the things from that section.

I've read through the thread but just have one question (I may have missed the answer). When you try:
```
sudo iwlist eth1 scanning
```
and it says nothing was found, are you definately near the wireless network?

---

### Post by friedokra on 2006-07-28
now go on with the things from that section.

I've read through the thread but just have one question (I may have missed the answer). When you try:
Code:

sudo iwlist eth1 scanning

and it says nothing was found, are you definately near the wireless network?"

right now, I'm near my home wireless network and when I type "
sudo iwlist eth1 scanning" it says "eth1 interface doesn't support scanning"

---

### Post by friedokra on 2006-07-28
I just did it again and it comes back saying "no scan results"

---

### Post by friedokra on 2006-07-28
I have to go to work. I'm going to try to do all this again when I get home. I don't want to install i386 unless I absolutely have to. In that case, it'd be easier for me just to reinstall windows. There has to be some way to get this wireless crap working. I also installed "wifi-radar" (and network manager)  but no networks are showing up even though I am near one. I looked on the acer website for the drivers but have no idea what to do after I have downloaded the zip file.

---

### Post by rob7622 on 2006-07-28
Don't give up now.  Check back earlier in the thread and use ndi swapper.  I think you said you downloaded a zip file from acer?  Wherever you downloaded it, go to that folder, right-click (i think, i'm from the kde world) and then extract the files.  There should be an inf file that ndi swapper will want

---

### Post by friedokra on 2006-07-28
well. Where do I download ndi swapper? how will I know what file ndi wrapper will want?

---

### Post by Raistlin355 on 2006-07-30
I believe I have found a new problem with this solution.  After I type "modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless" 

I get this error "FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-25-386/extra/acer_acpi.ko): No such device"

and if I paste it in all at once I get
root@Tanis:/home/kyle# chmod 777 /proc/acpi/acer/wireless
chmod: cannot access `/proc/acpi/acer/wireless': No such file or directory
root@Tanis:/home/kyle# echo "enabled: 1">/proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: No such file or directory

Any ideas?  I have not had any errors up 2 this point

A little update:  After I do 'make install'  everything seems to go fine but then I type 'sudo modprobe acer_acpi' and it tells me that 
"FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-25-386/extra/acer_acpi.ko): No such device"  
Any ideas why this could be I have gone to the directory /lib/modules/2.6.15-25-386/extra/ and guess what acer_acpi.ko is there!!  I can't figure out why its telling me its not there!!  I believe that this is the only problem and I need to get this figured out so please help!!

---

### Post by friedokra on 2006-07-31
bump. anyone have anymore ideas?

---

### Post by Raistlin355 on 2006-08-05
I still haven't had any luck, I've tried the howto about 5 times and no dice.  Has anyone else had this work?

---

### Post by friedokra on 2006-08-05
this thread is now being moved to:
[http://www.ubuntuforums.org/showthread.php?p=1344207#post1344207](http://www.ubuntuforums.org/showthread.php?p=1344207#post1344207)

I still need help if anyone can provide it.:-({|=

---

### Post by friedokra on 2006-08-06
> **rob7622 said:**
> Don't give up now.  Check back earlier in the thread and use ndi swapper.  I think you said you downloaded a zip file from acer?  Wherever you downloaded it, go to that folder, right-click (i think, i'm from the kde world) and then extract the files.  There should be an inf file that ndi swapper will want

did this. I gave ndi swapper the inf file (for my acer aspire 5004). Still can't get on wireless network,

---

