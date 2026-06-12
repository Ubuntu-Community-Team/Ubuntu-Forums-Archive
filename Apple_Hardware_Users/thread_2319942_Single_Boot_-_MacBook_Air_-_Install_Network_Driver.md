---
title: "Single Boot - MacBook Air - Install Network Drivers?"
date: 2016-04-08
forum: Apple Hardware Users
---

### Post by wbbrown2 on 2016-04-08
Hi, when I installed Ubuntu Server 15.10 on my MacBook Air 6,2 it did not recognize my network hardware.

My wireless card is: [FONT=Helvetica]broadcom corp BCM4360 802.11ac Wireless Network Adapter [[/FONT][COLOR=#101010][FONT=Menlo]14e4:43a0][/FONT][/COLOR][FONT=Helvetica] rev 03[/FONT]

I have read the threads on downloading the proper driver/kernel package. The problem is that this is a single-boot machine, and the wireless card has not been recognized, so I have no connectivity to download. Of course I have other computers. Can I copy the needed components to a USB stick and install them that way? Or is there some other solution?

---

### Post by Hadaka on 2016-04-09
Hi, your wifi card [FONT=Helvetica]BCM4360 802.11ac  [[/FONT][COLOR=#101010][FONT=Menlo]14e4:43a0], works best with the "WL"
dirver - broadcom-kernel-source. The good news is, you already have this driver.
Boot to your newly installed wireless Ubuntu. Next bring up a terminal, with ctrl/alt/t
or by clicking the dash and typing in  "terminal" ..'no quotes' . Insert the media you used
to load Ubuntu, usb/dvd. Then Please Copy and paste one line at a time.
[/FONT][/COLOR][FONT=Helvetica][/FONT]```
cp /media/*/pool/main/d/dkms/*.deb dk.deb
cp /media/*/pool/restricted/b/bcmwl/*.deb wl.deb
sudo dpkg -i *.deb
sudo modprobe -v wl
```
remove the usb/dvd and boot
You should now have wireless.

---

### Post by wbbrown2 on 2016-04-09
Hi, thanks so much for the help. I feel like I don't know what I'm doing, so I will spell everything out for you as exactly as I can.

When I log into Ubuntu I see the prompt: [user]@ubuntu:~$ 
So I type "terminal" (no quotes) 
Response: "The program 'terminal' is currently not installed. You can install it by typing: sudo apt-get install rsplib-legacy-wrappers

So I connect to internet using a USB-ethernet adapter, and type exactly that. Sudo asks for my password, which I enter. Response:
"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package replib-legacy-wrappers"

Then I go ahead and connect my Ubuntu install USB disk (which I used for installation).
I type "cp /media/*/pool/main/d/dkms/*.deb dk.deb"
Response: 
"cp: cannot stat [square]/media/*/pool/main/d/dkms/*.deb[square]: No such file or directory"

I type your second line and get the same error: no such file or directory.

Any idea what I'm doing wrong? 

Thanks again for the help!

---

### Post by Hadaka on 2016-04-09
Hi, Let's try this so I know exactly what you have.
When you boot up your computer, does it boot to the new installation of Ubuntu, but just no wireless... Y/N ?
*If.. YES .. Then is this where you see a prompt,,,User@Ubuntu:~$............ Y/N ?
*If.. YES .. Then this IS the terminal. ...see attached..
You stated you have a usb/ethernet adapter... Y/N ?
*If ..YES .. Then simply boot into Ubuntu, you should also be connected to the internet ..... Y/N ?
*If.. YES .. Then do..
```
sudo apt-get update
sudo apt -get install bcmwl-kernel-source
sudo modprobe wl
``` See attached.


[ATTACH=CONFIG]268268[/ATTACH][ATTACH=CONFIG]268268[/ATTACH][ATTACH=CONFIG]268269[/ATTACH][ATTACH=CONFIG]268270[/ATTACH]

basically what you are doing without the ethernet adapter 
is taking the 2 deb files from the pool folder changing the name of them to your home directory
and installing them via the dpkg -i command.
does this help??

---

### Post by wbbrown2 on 2016-04-09
Hello, 

(1) Yes, when I boot in, it boots into Ubuntu, I get a username/password prompt, and then the terminal prompt. But I have no internet access.
(2) Yes, this is when I see the prompt [COLOR=#000000]User@Ubuntu:~$[/COLOR]
[COLOR=#000000](3)  Yes, I have a USB-Ethernet adapter, which I know works (it works when I plug it into another MacBook). [/COLOR]

[COLOR=#000000]But for some reason, when I try either of the approaches you gave me, I get error messages [see Attached].

[For the non-USB-ethernet step, I did insert the USB with my installation copy of Ubuntu into the USB drive.]

Thanks so much for your time. 

[/COLOR][ATTACH=CONFIG]268277[/ATTACH][ATTACH=CONFIG]268278[/ATTACH]

---

### Post by virgosun on 2016-04-09
Sorry to jump in, but I think that you are both confusing. Because one of you are logging in[COLOR=#000000] Ubuntu Server, while the other may be logging in Ubuntu Server/Desktop?
I am correct?[/COLOR]

---

### Post by chili555 on 2016-04-10
> (1) Yes, when I boot in, it boots into Ubuntu, I get a username/password prompt, and then the terminal prompt. But I have no internet access.
(2) Yes, this is when I see the prompt User@Ubuntu:~$
(3) Yes, I have a USB-Ethernet adapter, which I know works (it works when I plug it into another MacBook).
Can you, just for a moment, use the USB-ethernet adapter and get connected? In a server install, you should run:```
ifconfig
```You should see an ethernet interface. Depending on your exact hardware, it will probably be something like enp123whatever. 

Next, get an IP address with:```
sudo dhclient enp123whatever
```Of course, substitute the actual interface as it will not actually be enp123whatever.

Once you get connected, install the correct driver for the wireless:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Now set up your wireless to connect automatically like this: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

In 15.10. your wireless interface will not be wlan0; find it with:```
iwconfig
```As an example, on my machine, I see:```
enp0s25   no wireless extensions.

lo        no wireless extensions.

[COLOR="#FF0000"]wlp3s0[/COLOR]    IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: A4:2B:B0:DC:45:86   
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1189   Missed beacon:0

```So, in the solution I linked, you'd use wlp3s0 instead of wlan0.

Post back if you get stuck.

---

### Post by wbbrown2 on 2016-04-12
Hi, thanks so much for your help. I was able to do most of that. I also edited /etc/network/interfaces as suggested. Like yours, my wireless interface is wlp3s0.

However, I did get stuck in the end. You can see the errors in the attachments. Pinging [www.google.com](www.google.com) got an unknown host error. 

[ATTACH=CONFIG]268336[/ATTACH][ATTACH=CONFIG]268338[/ATTACH][ATTACH=CONFIG]268330[/ATTACH]

[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by Hadaka on 2016-04-12
Hi, while we are waiting on the good doctor chili555 to respond, lets post some things he
will want to see.
please post...
```
sudo dpkg -s bcmwl-kernel-source
ifconfig
iwconfig
cat /etc/network/interfaces
#wpa-psk <your_wpa_key> *Be sure to 'XXXX' your key
```
thanks.

---

### Post by chili555 on 2016-04-12
I see that you used the address 192.168.1.150, exactly as I gave in my example. However, in my example, I said: > Of course, substitute your details here.Are the other computers in your network in the 192.168.1.xx range? Is the gateway 192.168.1.1? Please check.

Here is a screenshot from my iPod. As you can see, my own network is in the 192.168.[COLOR="#FF0000"]0[/COLOR].xx network. The gateway is 192.168.0[COLOR="#FF0000"].1[/COLOR]. 192.168.1.1 will not connect.

[ATTACH=CONFIG]268351[/ATTACH]

---

### Post by wbbrown2 on 2016-04-12
Great. Here they are:
[ATTACH=CONFIG]268346[/ATTACH][ATTACH=CONFIG]268348[/ATTACH][ATTACH=CONFIG]268349[/ATTACH][ATTACH=CONFIG]268350[/ATTACH]

---

### Post by wbbrown2 on 2016-04-12
Thanks -- dumb mistake.

It is now connecting successfully.  THANKS chili555!

---

### Post by chili555 on 2016-04-12
> **wbbrown2 said:**
> Thanks -- dumb mistake.

It is now connecting successfully.  THANKS chili555!Awesome. Glad it's working.

Have fun!

---

