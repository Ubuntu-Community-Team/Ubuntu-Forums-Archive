---
title: "wireless card driver not working"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by krakas on 2007-03-18
I installed edgy a couple of weeks ago, and it's working fine (keeping it alongside win xp to be on the safe side, i admit). I am thrilled to be moving away from windows. 

However, i cannot seem to get the wireless network card to work. Either firefox searches for my startup page for a long time, or it immediately returns the "server could not be found" page. 

The card is a 3com 3crwe154g72. 

I installed ndiswrapper (from synaptic package manager), and using that installed the driver from the installation cd from 3com. In the graphical ndiswrapper-tool, it says "hardware present: yes". So I assume that the driver should be working. 

I also installed wifi-radar, with which i am able to find the network and connect to it. 

I have tried a lot of different combinations in configuring the network connections (static ip, dhcp etc), but with no luck. 

Hope someone can help me!

cheers

---

### Post by dstew on 2007-03-18
Can you ping your router? Open the terminal, and type:

ping 192.168.2.1

---

### Post by krakas on 2007-03-18
> **dstew said:**
> Can you ping your router? Open the terminal, and type:

ping 192.168.2.1

Thanks for answering! Doing that, I get this out:

xxxx@xxxx-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.


Don't know if that means I can ping it or not?

cheers

---

### Post by dstew on 2007-03-18
That is the outgoing ping packet. Do you get the incoming packets coming back? They should look like:

64 bytes from 192.168.2.1: icmp_seq=1 ttl=255 time=3.94 ms

If you do not get returns, that means that you are not connecting with your router.

---

### Post by krakas on 2007-03-18
I tried it again, and now at least I get some more output, but it says

****@*****-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From [my static ip] icmp_seq=1 Destination Host Unreachable
From [my static ip] icmp_seq=2 Destination Host Unreachable
From [my static ip] icmp_seq=3 Destination Host Unreachable
From [my static ip] icmp_seq=6 Destination Host Unreachable

etc. 

Trying to do the same with DHCP activated, it only returns

***@***-laptop:~$ ping 192.168.2.1
connect: Network is unreachable


Any idea what this implies, or what can be done about it?

Again, your help is very appreciated!

---

### Post by dstew on 2007-03-18
We need to troubleshoot your wireless setup. Open a terminal, and enter the command

```
lspci
```

This should list your card as an Ethernet controller. Then enter:

```
iwconfig
```

Post the output on the forum.

---

### Post by krakas on 2007-03-18
Ok, this is the what i get when i use the lspci-command. I guess the relevant part is at the bottom:

***@***-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
03:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)



And this is what i get from iwconfig:

magnus@magnus-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  Mode:Managed  Frequency:2.412 GHz  
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=31 dBm   
          Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality:164  Signal level:0  Noise level:117
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions


When I did this, I disabled the LAN connection that I am using to post this.

---

### Post by dstew on 2007-03-19
OK, now we know your system has named your wireless card eth2. This means the driver is installed, and the system is talking to the card. The card just needs to be configured. Open network-admin, and we should be able to set it up properly. You may have to add eth2 to the list.

---

### Post by krakas on 2007-03-19
Hi, dstew, back from work now. 

What is the "network-admin"? Is it the thing under system>administration>networking?

That one has a list of connections (wireless, wired and modem), each of which can be configured with a "property"button on the right. Is that it?

---

### Post by DrOlaf on 2007-03-19
In case dstew is at work as well, yes, you have the right application :) . Open it and select the "wireless connection" icon. Click on properties and check the "enable this connection" button. You'll then have to fill in the connection details for your router. Are you using some kind of wireless security, like WEP, on your network? If you are, and you know what the key is, enter it here. You will also have to set the connection settings to "DHCP", or "static IP address", depending on how you have configured your router. Most routers are set to DHCP, so you could try that first.

You will also have to enter something in the "DNS" tab - usually this is the IP address of your router on a home network.

---

### Post by krakas on 2007-03-19
Hi dr! 

Now i've tried selecting the "wireless connection" (have done that a few times before) in network-admin. 

I confirmed in the router (gateway?) that it has DHCP enabled, so chose that in network-admin. 

Under WPA encryption tab on the router's menu, there was a passphrase and a lot of pairs of numbers and letters (like A3 3F 45 etc). It seemed like the passphrase was chosen as the mode of identification to the router, so I typed that into the network-admin. A lot of people will be very angry if i disable the encryption, but should i try it just to see if the fault lies there?

In wifi-radar i chose DHCP. It said that the computer was connected to the network (said so before i chose DHCP also). 

On the network monitor on the right on the top panel, I wrote eth2, and it seemed to start monitoring my wireless connection, saying that the signal was 70% strong etc.

What am i doing wrong here? Any idea? Having come this far, can I assume that the driver-card-ndiswrapper stuff went alright, or may the problem be there? 

Hope you can help!! 

(By the way, is it a good idea to disable the wired connection when testing the wireless? I have been doing that, to make sure that it is the wireless i am testing, but it takes a lot of time, since it seems like I have to reboot every time I want it connected again..)

---

### Post by DrOlaf on 2007-03-19
First off, it's very encouraging that you are getting a signal strength monitor reading - it shows that your card can see the router well, and that the problem is one of negotiating the right connection.

The text you describe (a string of hexadecimal characters like A3 3F 45 etc) sounds more like a WEP key than a WPA passphrase, although there is no reason why you couldn't use these characters as a WPA phrase. I usually make a WPA passphrase that's (a) long, (b) easy to remember, and (c) hard to guess. Something like "The quick brown fox jumped over the lazy dog" (and no, that's not my real WPA passphrase, in case you're parked outside my house..). If it really is a WPA phrase, then you will probably need a program called wpa_supplicant to administer it under ubuntu. That should be in the repositories, and there is a graphical tool called wpgui to help you run it.

If the hexadecimal characters are in fact a WEP key, you need to make sure that the settings you have in the wireless connection window match those on the router exactly - as well as typing in the key, you need to make sure that it is declared as being the right length.

At the risk of annoying people both at your place, and in these forums who will be mad that I suggested it, it may be an idea to turn the security settings off briefly, just to see if your card can connect to an open router. Just be quick about it! Most routers should let you turn off and on security, and will remember their key, but make a note of it carefully in case you have to type it in. You can always eat the note later so you don't leave the key lying around :) 

You shouldn't need to disable the wired connection to check the wireless one. I never do that when I'm setting a machine up. 

The only other thing you may want to check on the router is to see if it has MAC address filtering enabled. It's a security feature that tells the router to connect only to wireless cards whose MAC address it alreay knows. The MAC address is a string of hexadecimal characters, printed on a sticker on your card, or obtainable by looking at the output of the ifconfig command.

Anyway, it's time for **me** to head home from work now. I'll check in later to see how things went.

---

### Post by krakas on 2007-03-19
Woops, seems like it's a problem with the encryption. 

I disabled WPA/encryption in the router, enabled the wireless connection in network-admin, and connected through wifi-radar (telling it that the network was open). 

Now it worked, i'm writing this looking at a lan wire not connected to anything! However, I can't keep having the WPA disabled. Any ideas what I can do?

---

### Post by krakas on 2007-03-19
Oh, those posts crossed each other, doc.

---

### Post by DrOlaf on 2007-03-19
OK, so it sounds like your router does have WPA (not WEP) configured on it, so now you need to get a WPA client installed on your Ubuntu machine so that you can connect to it. There is an excellent wiki page on how to do this [ here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo"). Rather than summarize the whole page, I'll just post the link. You may need to download a program called wpa_supplicant if it is not already installed on your machine, so you will need the wired connection to do that.

In case you haven't done it, you can turn WPA back on now.

Post here, or PM me if you have any problems with it. You're almost there now.

---

### Post by krakas on 2007-03-19
Thanks doc, i'll give it a go now

---

### Post by krakas on 2007-03-19
Hm... The wiki looks great, but I can't find /etc/wpa_supplicant.conf?

The newest version of the program is apparently installed. Tried to find it in the browser, and also typed the path in the terminal. Strange, no?

---

### Post by DrOlaf on 2007-03-19
Odd, indeed. Do you mean that the network-manager-gnome applet is installed, or that wpasupplicant is?

---

### Post by krakas on 2007-03-19
I misunderstood the wiki (too fast and eager, I guess) and started right on the wpa-supplicant part. So that's the one that was installed already. 

I have now installed network manager. It seems be working with connecting to the network. It doesn't seem to be very successful: Under "activity" the eth2 connection lists that it has received 72 packets (11 kb). Now the two dots are away, and i'm connected through the LAN it seems. Whenever I disable the lan or simply pulls out the cable, I can't get anywhere on the web. 

Under properties, NM says that eth2 is connected, and signal strength is 100 %.  

I have been prompted by NM for passphrase several times. I have chosen differently every time to see if that helps: is my passphrase ASCII or hexameter or something else (don't remember the third alternative, "128 passphrase" or something)? The password for logging on to the network from windows is a regular word. 

Also, i have to choose if the connection is "open" or "shared key". I guess it is shared key?

I would proceed with the wpa-supplicant thing, but still can't find the .conf file...

---

### Post by krakas on 2007-03-19
And, when I left click the connection icon top right, "wired network" is the only thing that can be checked off, not "3Com wireless" as before. Also, before I had the option of "connect to another wireless network" or something like that. Have I messed up the Network Manager already?

---

### Post by DrOlaf on 2007-03-19
> **krakas said:**
> I misunderstood the wiki (too fast and eager, I guess) and started right on the wpa-supplicant part. So that's the one that was installed already. 

Well, I've done that plenty of times myself :)


> **krakas said:**
> I have now installed network manager. It seems be working with connecting to the network. It doesn't seem to be very successful: Under "activity" the eth2 connection lists that it has received 72 packets (11 kb). Now the two dots are away, and i'm connected through the LAN it seems. Whenever I disable the lan or simply pulls out the cable, I can't get anywhere on the web. 

Under properties, NM says that eth2 is connected, and signal strength is 100 %.  

Just to check, eth2 **is** your wireless card?

> **krakas said:**
> I have been prompted by NM for passphrase several times. I have chosen differently every time to see if that helps: is my passphrase ASCII or hexameter or something else (don't remember the third alternative, "128 passphrase" or something)? The password for logging on to the network from windows is a regular word. 

Also, i have to choose if the connection is "open" or "shared key". I guess it is shared key?

I would proceed with the wpa-supplicant thing, but still can't find the .conf file...

The format of the passphrase should be whatever the router is expecting. If you log on to the router and look at the section where the passphrase is stored, it should tell you whether or not it's hex or ASCII, and how many bits long it is. But, if you are using WPA, it shouldn't be showing up in the router as ANY type of WEP key. WEP and WPA are different authentication protocols. If the router is expecting WEP, you shouldn't be giving it WPA.

Can you let me know what the make & model of the router and the card are? Some cards don't play nice with nm-applet.

---

### Post by dstew on 2007-03-19
Network manager is not necessarily the greatest tool for setting up your wireless. There are others. WiCD is highly thought of, maybe that would be better. But no matter what tool you use, you really need to know exactly what key to use.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

---

### Post by DrOlaf on 2007-03-19
Looks like our messages crossed each other. It does sound like nm-applet is only showing you the information about the wired connection.

---

### Post by krakas on 2007-03-19
Ok, here's the specs:

The card is a 3Com 3CRWE154G72

The router is a 3Com OfficeConnect Wireless 11g Cable/DSL Router


When I log on to the router, under "Wireless Settings" there is a tab called "Encryption". 

The headline is "WPA (WiFi Protected Access)". 

Here I can choose "WPA type" from a dropdown menu with the alternatives 
"Disabled"
"Manual pre-shared key"
"Pre-shared passphrase"
"Enterprise mode"

It has always been set to "pre-shared passphrase", except when I experimented with disabling the WPA and was able to use the wireless. 

When "pre-shared passphrase" is chosen, the next line on the page says "passphrase" Next to this is a box with the password i have been using to log on to the network from windows with. So i guess this is the passphrase, but do not know if this is 128 bit or ASCII or whatever. 

On the bottom of this page it says "Key: A4 3D ...[two rows with 16 pairs of letters/numbers in each]"

Should I try to reinstall the network manager and try to get the password stuff right from the beginning, or isn't that necessary? Will the WiCD-thing be any different?

---

### Post by DrOlaf on 2007-03-19
OK, this helps quite a lot, although I'm afraid the news is not good.

> **krakas said:**
> Ok, here's the specs:

The card is a 3Com 3CRWE154G72

The router is a 3Com OfficeConnect Wireless 11g Cable/DSL Router

That card has caused quite a lot of problems for folks on Edgy, although it seems OK under Dapper. If you search for "3CRWE154G72" on these forums, you will see what I mean, for example:

[http://www.ubuntuforums.org/showthread.php?t=355736](http://www.ubuntuforums.org/showthread.php?t=355736)
[http://www.ubuntuforums.org/showthread.php?t=213647](http://www.ubuntuforums.org/showthread.php?t=213647)

> **krakas said:**
> 
When I log on to the router, under "Wireless Settings" there is a tab called "Encryption". 

The headline is "WPA (WiFi Protected Access)". 

Here I can choose "WPA type" from a dropdown menu with the alternatives 
"Disabled"
"Manual pre-shared key"
"Pre-shared passphrase"
"Enterprise mode"

It has always been set to "pre-shared passphrase", except when I experimented with disabling the WPA and was able to use the wireless. 

When "pre-shared passphrase" is chosen, the next line on the page says "passphrase" Next to this is a box with the password i have been using to log on to the network from windows with. So i guess this is the passphrase, but do not know if this is 128 bit or ASCII or whatever. 

On the bottom of this page it says "Key: A4 3D ...[two rows with 16 pairs of letters/numbers in each]"

In that case, the router is expecting to get a WPA passphrase, not a WEP one. The "pre-shared passphrase" option is a standard one to choose. The bit length and the ASCII/hex options should only apply to WEP keys, not WPA ones. Altering those settings on your Ubuntu machine won't help you if the router is configured to use WPA. 


> **krakas said:**
> 
Should I try to reinstall the network manager and try to get the password stuff right from the beginning, or isn't that necessary? Will the WiCD-thing be any different?

Based on dstew's suggestion, I downloaded WiCD and tried it out on my machine. It looks nice and easy to set up, but had some problems with my DNS settings. You could try it out, but I fear that the 3Com card you have is not one of the easiest ones to set up under Ubuntu.

---

### Post by krakas on 2007-03-19
Hi, 
yeah, I have just tried WiCD myself, but with no luck. Looks neat, though. I think I got the preferences part right (WPA supplicant driver = ndiswrapper, wireless interface = eth2). 

When setting the wireless connection to DHCP it searches for a long time,  saying "Obtaining IP address", and in the end it doesn't find anything. 

When setting a static IP (the one reported for the wireless when using ipconfig in Windows) WiCD says it connects, and even how strong the signal is. But the network monitor says it's unconnected, and browsing doesnt work (Firefox says "waiting for [www.google.no](www.google.no) [my start page]).
Also, I can write anything in the "key" field under "Use encryption" (where i chose WPA1/2), not only the correct passphrase. It still says that it connects, and still doesn't work. 

So what to do? I would't like to give up Ubuntu (or just use it on the rare occations when i have LAN available). I've become quite accostumed to the speed and ease of everything (except wireless). 

Now it's WAY past bedtime in my part of the world, so I'm giving up for tonight, continuing tomorrow I guess.  

Dr and dstew, thank you both so much!

---

### Post by DrOlaf on 2007-03-20
The real sticking point here is getting your card to work with WPA under ubuntu. As you have shown, the card works fine under ubuntu when you have no security set, and it works fine with WPA under Windows. 

Your card is able to connect to the router as you have set it up, but the router will not allow it to do anything unless the WPA settings are negotiated properly. You will be able to see the signal strength, etc, but you can't do much more than that. I don't think that the problem is you entering your WPA-PSK key incorrectly, but rather that WPA access using the 3crwe154g72 is broken under edgy. Actually, I am assuming that you are running edgy (Ubuntu version 6.10) and not Dapper (version 6.06), but correct me if I am wrong on that. There are guides that show how to set this card up with Dapper, like this one:

[http://www.ubuntuforums.org/showthread.php?t=156710](http://www.ubuntuforums.org/showthread.php?t=156710)

but other threads, like this

[http://www.ubuntuforums.org/showthread.php?t=316764](http://www.ubuntuforums.org/showthread.php?t=316764)

suggest to me that there are some incompatabilities between the card and version 6.10.

I don't have the 3com card that you are using, so I can't check how to set it up properly. 

You say that you wouldn't give up Ubuntu, and neither would I. In this situation, I would be thinking seriously about getting a different card, and checking these forums to see which ones work best in Ubuntu. After all, it's fun to meet the challenge of getting the hardware to work, but it's more fun just to use Ubuntu to do the computing that you want to do. The wi-fi card that came with my notebook required ndiswrapper to work under Ubuntu: although I got it working OK, I found it easier on my blood pressure to replace it with one that worked with a native driver.

---

