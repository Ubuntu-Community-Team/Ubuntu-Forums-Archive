---
title: "Problems with WiFi"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by subhashnm on 2007-05-28
Hi,
I'm a new face to Ubuntu, though not really so to Linux. I installed Ubuntu 6.06 LTS on my Toshiba Protege Laptop today and was able to configure net thru the LAN cable for it soon after, but I'm having problems with connecting to the net thru my wireless router. The network (named Tantra by me) is getting detected in System-Administration-Networking-Wireless networks. I provided the key type (ASCII) and the key itself (which is already being used successfully in my wife's Vista system) but I'm unable to connect to the net.

Router is a Linksys wireless-G one. I don't know what further information would be helpful in identifying the issue. Please let me know if I need to provide anything more.

Hope to find a solution for this...

Thanks in advance!

Subhash.

---

### Post by ugm6hr on 2007-05-28
In Terminal - type:
lspci

Look for the output that says "Network / Ethernet Controller".  That will be the wireless chipset.  Then search for that chipset here in the forums.  Or at least copy and paste what comes out so someone can point you in the right direction.

---

### Post by ggaaron on 2007-05-28
I assume that you use some sort of program for connection? (like wlassistant?) Do you see the your router there? You know in the list of available wireless networks? And did you specify good option for the key - shared or open?

---

### Post by subhashnm on 2007-05-28
@ugm6hr: The information mentioned is given below:

 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Eth ernet Controller (rev 83)

@ggaaron: No, I'm not using any special programs to connect to the wifi network. In System-Administration-Networked-Wireless connections I can see the name of my network and the others nearby listed. Also, it doesn't ask for any shared/open option; there are two fields in there; one, type of key (ASCII or Hex) and two, the key itself. Also in Connection Settings ( in the same pane, I've selected DHCP.

Thanks,
Subhash.

---

### Post by ugm6hr on 2007-05-28
> **subhashnm said:**
> @ugm6hr: The information mentioned is given below:

 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Eth ernet Controller (rev 83)

@ggaaron: No, I'm not using any special programs to connect to the wifi network. In System-Administration-Networked-Wireless connections I can see the name of my network and the others nearby listed. Also, it doesn't ask for any shared/open option; there are two fields in there; one, type of key (ASCII or Hex) and two, the key itself. Also in Connection Settings ( in the same pane, I've selected DHCP.

Thanks,
Subhash.

Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
That's the wireless card.  I am sure that's supported "out-of-the-box" - check on the networking forum pages.

In the connection settings - try "enable roaming mode" - this should allow Network Manager (default loaded in Ubuntu) to connect without having to specify any settings apart from the password.  It appears as an icon in the top right corner - and says "Not connected" or something like that when you move the mouse cursor over it.  Right-click it and enable network and wireless, then left-click it to bring up a list of Access Points.  Clicking that should then ask for your password.

---

### Post by Atomic Dog on 2007-05-28
> **ugm6hr said:**
> Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
That's the wireless card.  I am sure that's supported "out-of-the-box" - check on the networking forum pages.

In the connection settings - try "enable roaming mode" - this should allow Network Manager (default loaded in Ubuntu) to connect without having to specify any settings apart from the password.  It appears as an icon in the top right corner - and says "Not connected" or something like that when you move the mouse cursor over it.  Right-click it and enable network and wireless, then left-click it to bring up a list of Access Points.  Clicking that should then ask for your password.

He has installed 6.06 not feisty.  This won't work the same way for him.  I think Feisty would be a better choice to install on that Toshiba.

---

### Post by subhashnm on 2007-05-28
I don't know whether I"m missing something here, but I can't see Network Manager on the right top corner. I can see Network Monitor (icon showing two computers one in front of the other) and it doesn't give me any option to enable Network and Wireless when I right click on it.

Also, in the connection settings of "eth1", I can't see an option " enable roaming mode". 

How I am connecting to the net right now is thru a cable that runs from my wireless router to the laptop. once I unplug that and try to enable eth1, I am getting signal strength as 0%.

Below is the iwconfig details that I am getting:

subhash@Subhash-Laptop:~$ iwconfig
lo        no wireless extensions.

eth1      unassociated  ESSID:"Tantra"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by ugm6hr on 2007-05-28
> **Atomic Dog said:**
> He has installed 6.06 not feisty.  This won't work the same way for him.  I think Feisty would be a better choice to install on that Toshiba.

Oops.  My mistake for not reading.

---

### Post by subhashnm on 2007-05-28
You guys think it would be better for me to upgrade to Feisty?

---

### Post by ggaaron on 2007-05-28
Feisty is better - it's newer and supports more hardware.
I don't use gnome so I can't really help you, but after trying to connect to the network open a terminal and run dmesg - the last lines could say something about the problem (you can paste them here - but only a few lines, not all dmesg=)

---

### Post by subhashnm on 2007-05-28
Last few lines:

[17181544.036000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181612.088000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17181962.092000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17181962.092000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17181972.308000] eth0: no IPv6 routers present
[17183836.092000] e100: eth0: e100_watchdog: link down


I don't feel like sleeping without solving this.... there is hardly any night left, though...

---

### Post by ggaaron on 2007-05-28
As you can see, there is some problem with your eth1 - your wifi.

---

### Post by subhashnm on 2007-05-28
But the message says the same "link not ready" for eth0 too, which is my LAN port. But I'm currently working thru that only!

---

### Post by ggaaron on 2007-05-28
> **subhashnm said:**
> Last few lines:

[17181544.036000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181612.088000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17181962.092000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[COLOR="Red"][17181962.092000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready[/COLOR]
[17181972.308000] eth0: no IPv6 routers present
[17183836.092000] e100: eth0: e100_watchdog: link down


I don't feel like sleeping without solving this.... there is hardly any night left, though...

no such line for eth1

---

### Post by ggaaron on 2007-05-28
I don't know, all that google says is to install newer drivers...

---

### Post by bvmou on 2007-05-28
Both Toshiba and the Intel chipset you have are well supported as a rule, I think they are in Ubuntu.  To try Edgy and/or feisty do sudo apt-get dist-upgrade.  These things can be quirky, good luck.

---

### Post by ugm6hr on 2007-05-28
> **bvmou said:**
> Both Toshiba and the Intel chipset you have are well supported as a rule, I think they are in Ubuntu.  To try Edgy and/or feisty do sudo apt-get dist-upgrade.  These things can be quirky, good luck.

Or download a Feisty LiveCD - it should just work booting direct from LiveCD.  That way you'll know before upgrading.

And if you're new to Ubuntu, you won't have many settings to take with you anyway.

---

### Post by subhashnm on 2007-05-28
SOLVED!!!!

Installed Network manager thru Applications-Add/Remove and it showed me the network and I just had to enter the pwd. Works like a piece of cake now!

Thanks to you all, guys! It feels amazing to know you are never left alone! Thanks a ton!

I can now go to bed peacefully, to catch whatever is left of the night....Thank god its a holiday tomorrow!

Cheers!
Subhash.

---

