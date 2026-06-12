---
title: "MacBook Pro can't boot - wl_ops_config change etc."
date: 2011-11-18
forum: Apple Hardware Users
---

### Post by DanTheDane on 2011-11-18
Hi.

I have installed Ubuntu 10.10 on my Mid 2010 MacBook Pro. After booting first time after the installation it doesn't continue, but gives below messages (had to turn on nomodeset to see the output).

It gives the following output lines:

ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)

ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: true (implement)
ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 0 (implement)
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 1 (implement)

I have tried to let it boot for 45 mins. without success. I have also tried with acpi=off noacpi nolapic without success.
I have also tried to reinstall Ubuntu with no difference in behaviour.

Do any of you have any idea what could be wrong?

---

### Post by matt_symes on 2011-11-18
Hi

> **DanTheDane said:**
> Hi.

I have installed Ubuntu 10.10 on my Mid 2010 MacBook Pro. After booting first time after the installation it doesn't continue, but gives below messages (had to turn on nomodeset to see the output).

It gives the following output lines:

ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)

ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: true (implement)
ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 0 (implement)
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 1 (implement)

I have tried to let it boot for 45 mins. without success. I have also tried with acpi=off noacpi nolapic without success.
I have also tried to reinstall Ubuntu with no difference in behaviour.

Do any of you have any idea what could be wrong?

I think it maybe your wireless driver. Were you able to boot into a livecd/usb ?

Kind regards

---

### Post by DanTheDane on 2011-11-18
Hi matt.


Thanks a lot for your reply.

I have had the same suspicion but I haven't found a way to disable it on boot.

I was not able to boot the live cd itself, but when installing ubuntu (from the grub menu) I was able to connect to my wireless

---

### Post by matt_symes on 2011-11-18
Hi

> I was not able to boot the live cd itself, but when installing ubuntu (from the grub menu) I was able to connect to my wirelessI don't really understand what you mean here.

Can you boot into a root shell from the grub recovery menu ?

Have a look in your BIOS and see if there is an option to disable your wireless card. If there is then disable it and try to boot inti Ubuntu again. If it boots then we will know for sure it the wireless card.

Kind regards

---

### Post by DanTheDane on 2011-11-19
I wrote that a little too fast :-) 

What I meant was that I was unable to boot the "ubuntu live" part of the cd from the grub menu, but I was able to boot the "install ubuntu" and install ubuntu.

I can boot to the recovery mode without issues. I can also go to the root shell from there.


Since it's a mac there a no bios but efi instead, so I can'tdisable the wireless there....

---

### Post by matt_symes on 2011-11-19
Hi

> **DanTheDane said:**
> I wrote that a little too fast :-) 

What I meant was that I was unable to boot the "ubuntu live" part of the cd from the grub menu, but I was able to boot the "install ubuntu" and install ubuntu.

I can boot to the recovery mode without issues. I can also go to the root shell from there.

Let's move all the wireless drivers. We can put them back later.

Boot into the root console and type

```
mkdir /wireless_backup
``````
mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless /wireless_backup
``````
shutdown -r now
```Does this get you to a desktop ? 

You will still have wired drivers so get an Ethernet cable and plug into your router. That should give you wired Internet access on this computer (unless there is a problem there as well).

> 
Since it's a mac there a no bios but efi instead, so I can't disable the wireless there....Oh yeah :) My bad. I think i read to fast.

Kind regards

---

### Post by DanTheDane on 2011-11-19
Unfortunately not.

It was almost the same, except a new line came where it complained about an invalid MAC address.....

I have attached a picture where you can see the boot output..

And thanks a lot for helping with this. I really appreciate it!

---

### Post by matt_symes on 2011-11-19
Hi

Boot into a root console and type

```
sudo lshw -C network
```

Post back results back here. The photo's are good.

I'm convinced you have a wireless issue there.

Kind regards

---

### Post by DanTheDane on 2011-11-19
I have attached a screenshot of the output.

I have found out that Ubuntu are indeed not happy with the MacBook Wireless. I found this site:
[http://www.ubuntubuzz.com/2011/10/ubuntu-1110-in-macbook-pro.html](http://www.ubuntubuzz.com/2011/10/ubuntu-1110-in-macbook-pro.html)

If I could just be able to boot and then make the patches mentioned on the website, I could probably get it working.....

---

### Post by matt_symes on 2011-11-19
Hi

You have a Broadcom wireless driver BCM43224. There are others who have had exactly the same problem with the 4xxx series.

I am going to look at the link you posted. That was a good find. Can you connect to your router via an Ethernet cable ? I.E do you have an Ethernet cable you can plug into your router ?

Kind regards

---

### Post by DanTheDane on 2011-11-19
That's nice to know. 
Yes I can hook via ethernet to download needed packages

---

### Post by matt_symes on 2011-11-19
Hi

That link shows how to compile the driver for BCM4311 card. Yours is a different model. They may or may not work.

We have a couple of options. We can try to get you connected to the net from your root console and attempt the steps in that tutorial. For this i may need the IP address of your router. This is the internal IP address so there is no security issues. It depends on how your router is set up.

Or we can try to disable wireless on your system to let you boot into a graphical environment and try the steps there. I thought moving the drivers directory might have done that but it does not look like that was the case.

**EDIT:**

Before we attempt any of these i have just noticed your Ethernet connection is disabled from lshw. This may be a show stopper.

In the root console type

```
sudo ifconfig eth0 up
```Then type 

```
sudo lshw -C network
```and check to see if the disabled word has gone.

Post back results.

Kind regards

---

### Post by DanTheDane on 2011-11-19
That seemed to get it up.

I have attached a screenshot that includes my LAN IP (and a few typos :-) )

---

### Post by matt_symes on 2011-11-19
Hi

Excellent. Let's see if we can connect you to the Internet.

Plug a cable into your laptop and a spare LAN port on your router.

Then type

```
dhclient eth0
```When it has finished chcek to see if you have an IP address, gateway and subnet mask. You can check these with

```
ifconfig
```If that looks good then try to ping Googles nameserver

```
ping -c3 8.8.8.8
```Last but not least try a lookup

```
nslookup www.google.com
```Report back on success or failure.

Kind regards

---

### Post by DanTheDane on 2011-11-19
I was able to ping both google.com and 8.8.8.8

---

### Post by matt_symes on 2011-11-19
Hi

Good !!! You have a fall back position where you can connect to the Internet. 

Let's try to get you booting into a graphical environment. To do this let's try to disable the bcm drivers. We can always re enable them later. From the root console...

```
echo blacklist b43 >> /etc/modprobe.d/blacklist
``````
echo blacklist bcma >> /etc/modprobe.d/blacklist
```Then reboot. Can you log on normally ?

Kind regards

---

### Post by DanTheDane on 2011-11-19
Unfortunately. It stalls after "disconnected from Plymouth"

I have attached the output.

Btw: I need to add nomodeset to the boot options otherwise the screen is just one garbled mess. As far as I know that shouldn't affect anything of the stuff we're trying out with the wireless though.

I need to go to bed now, but I hope we can catch on later. 
Once again thanks a lot for taking your time to help me!

---

### Post by matt_symes on 2011-11-19
Hi

It's late here as well so tomorrow ?

I am subscribed to this thread so when ever is good for you.

EDIT: After a very quick glance at the output, wireless is not the only issue here.

Kind regards

---

### Post by DanTheDane on 2011-11-26
> **matt_symes said:**
> Hi

It's late here as well so tomorrow ?

I am subscribed to this thread so when ever is good for you.

EDIT: After a very quick glance at the output, wireless is not the only issue here.

Kind regards

Hi Matt.

Sorry for not getting back earlier. I had a crazy week where I unfortunately didn't have time to experiment with this.

I have toyed around with it today and I have been able to boot to the commandline in the normal boot up (not rescue mode). I found out that it was the "vt.handoff=7" option in grub that was the reason that I couldn't continue booting.
I do though still have to set it to nomodeset, otherwise it freezes during the boot.

I have tried to run startx, but I get a "no devices detected error". I have crawled the web to find a solution to get it working without luck. I would have tried to use the Nouveau driver, but since I'm using nomodeset, that seems to be out of the question.

I have attaached the dmesg output after boot, the Xorg log, xorg conf and a picture of where it freezes when I don't set nomodeset at boot. (I had to zip the dmesg since it was to big a text file)

---

### Post by DanTheDane on 2011-11-26
BTW: I forgot to write that the wireless do actually work fine despite the error messages. I removed the blacklist, and I have no problem connecting to the web...

---

### Post by DanTheDane on 2011-11-27
I got a little further.

I was able to start X by setting the BusID in xorg.conf.
The issue now is that I just get a black screen. X seems to work though cause I can log in blindly (typing the first letter of my username, hit enter and typing my password + enter. after a few seconds I can press the power button which I know brings up the menu where I can choose to shutdown. If I hit enter it will shut down).

So it seems that it's something with the screen that it's unhappy about. I have tried to toy around with the vertical & horizontal sync with no success.

---

### Post by DanTheDane on 2011-12-11
Well I found out that the Nvidia driver just didn't like EFI.
I ended up re-installing ubuntu from a DVD which worked flawlessly (this way BIOS emulation was used).

But thanks a lot for all your help Matt. It's really appreciated

---

