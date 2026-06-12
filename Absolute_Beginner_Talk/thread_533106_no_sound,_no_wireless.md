---
title: "no sound, no wireless"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by mcsquared on 2007-08-23
I partioned my Gateway 7330GZ notebook and installed first Ubuntu Feisty Fawn and then Mint Cassandra. On neither OS can I get my sound to function (Conexant AC-Link Audio) or my wireless connection (Broadcom 4306  802.11g wireless lan controller (Rev 03) 14e4.4320 (rev 03). I have gone thru the steps at "a howto for wifi" online and gotten to step 4 Instlal the driver.

How I got the Windows driver was to open XP and copy/paste the 2 inf files for the Broadcom to my flash driver and then pasting them into my Home folder on Mint and then using the Windows Wireless drivers ndiswrapper driver installation tool to install them. 
When I went to test to see if Mint had recognized the inf files I got this information back:
max@max-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have no clue what all this means but I still don't have wireless recognized.

I also still don't have sound.

If you could help me out, it would be MAHVELOUS!

I had previously gone to a website where someone had tried out a Gateway 7330GZ notebook using Linux and their chart going through all the hardware/drivers said everything was working.   What the heck is wrong with my install then?

Thank you VERY MUCH, 

Ms. Max

---

### Post by bmartin on 2007-08-23
> **mcsquared said:**
> max@max-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
This means your wireless device is recognized, but isn't connected to the router. If you type in **sudo iwlist scanning**, it should give you a list of recognized networks. If your network doesn't have encryption or it has WEP encryption, you can user the built-in network program to connect to wireless networks. If you use WPA, you should [read this thread]("http://ubuntuforums.org/showthread.php?t=318539").

The built-in network software doesn't work the greatest. You might want to consider installing [WICD]("http://blakecmartin.googlepages.com/wicd.html") or [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html") in order to connect. I recommend WICD because it has a tray icon program and more people tend to have success with it than any other wireless software.

---

### Post by mcsquared on 2007-08-23
I typed in sudo iwlist scanning,   and got:

O, what a tangled web we weave, When first we practice to deceive.
                -- Sir Walter Scott, "Marmion"
max@max-laptop:~$ sudo iwlist scanning
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

max@max-laptop:~$ 



Now what?

p.s. thanks for your so-quick reply, btw)

---

### Post by bmartin on 2007-08-23
It sounds like your WiFi scanning is disabled. A lot of chipsets have a keyboard combination or button/switch that enables and disables the WiFi scanning. It might be something like Fn+F2. Do you see anything like that?

---

### Post by mcsquared on 2007-08-23
I tried FN F2 which shows an icon of a circle with parenthis bars around both sides, but nothing happened.  
I also installed both wcid and the wifi-radar and then lost my network manager icon on the taskbar.  I also lost internet capabilities WITH my cable plugged in.
Then I rebooted and uninstalled wifi-radar and re-installed wicd and played around and wiggled my cable connection and rebooted again. and almost gave up, but then I tried something else in the configure connection box, or something and now I've got internet again (with cable, that is) and no icon for network manager, so I put the computer monitor icons for networking from the panel add button.  

I was worried there for a minute because when I went to install this that and the other from packaging nothing would happen because I'd lost internet connection WITH my cable plugged in. HOw does that happen. I was nearly ready to re-install the Mint cd, but....

My philosophy is like my husbands, try and try and if all else fails reinstall the whole shabang.

---

### Post by bmartin on 2007-08-23
You can probably get the icon back with **sudo apt-get install gnome-network-manager**. There might be a setting in your BIOS to enable your wireless signal transmission.

What does **dmesg | grep eth1** say? Anything that looks helpful or suggestive?

---

### Post by mcsquared on 2007-08-23
B Martin,

Here's what I got copy/pasting in both your statements into the terminal:
max@max-laptop:~$ sudo apt-get install gnome-network-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-network-manager
max@max-laptop:~$ dmesg | grep eth1
max@max-laptop:~$ 


As for the icon back, do I need to reboot to be able to see it?

---

### Post by bmartin on 2007-08-23
Sorry, the package name is network-manager-gnome.

sudo apt-get install network-manager-gnome

You might have to reinstall to get the icon back. I don't know why eth1 isn't turning up anything. Install network-manager-gnome, and if it's successful, restart and let me know how things look.

---

### Post by mcsquared on 2007-08-23
I did a google search for gnome network manager and installed it, after having to find it's dependancy which was missing. In any case it's installed now. Do I have to reboot because I don't see the icon.

---

### Post by bmartin on 2007-08-23
Yep. I can't imagine why eth1 isn't working properly though. There aren't any messages in **dmesg** at all, yet it shows eth1 in iwconfig. This is new to me.

---

### Post by mcsquared on 2007-08-23
BMartin,

In addition to your fabulous help, BMartin, I also found someone named Jon reagen (jreagan1990@gmail.com) on a website for Mint (it being Irish in origin?) and figured it couldn't hurt to get any help out there.   Jon sent me a link, and between the two of you I am actually sending you this reply wireless. Wheeeeeeee

Here's a copy of Jon's email to me

Ms. Max,

There are several ways of tackling the problem surrounding your wireless card.  I had quite a trip getting mine to work, which is a Broadcom 4318, the infamous AirForce One card.  Your wireless card is in the same "family" of cards as mine, which means that the same drivers are used in Linux.  Since I like to solve things the easy way, there is a file that I have found (and used with great success)on the forums.  It is a .deb file that gets these cards to work.

You can find the How-To here:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+wireless+card+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+wireless+card+howto)

There is a link in the first post:

To use the native bcm43xx driver:
Download [http://ubuntuforums.org/attachment.p...8&d=1177147133](http://ubuntuforums.org/attachment.p...8&d=1177147133) and double click it to install. Reboot. Enjoy wireless. (this should work, but if for some reason it fails, see the troubleshooting)

As soon as you reboot, you should then be able to start your wireless that you will have to configure through the network manager applet.  If your wireless is located on a button on your computer, make sure that it is on, and see if any wireless lights that turn on during the boot process (the lights and switch depends on your type of computer).  You should be able to see your wireless networks in the Network-Manager applet, which will allow you to connect and sign on to your network.

There are also links for using a script to install via the command line and ndiswrapper.  The script has worked fine for me as well, but I suggest trying the .deb file first, as it might save you some time.

I am not 100% sure about why the sound card is not working, but I have a feeling that it has something to do with your sound settings.  All I can recommend is that you try different settings, and check your volume.  My volume never completely shuts off when I mute it, so it might be a driver issue.

I hope this helps! (If not, feel free to email me with any questions that you have!)

Jon

And I think that did the trick along with your wicd download.


Thanking you immensely, in advance,
Ms. Max


Now there's just the sound issue to tackle and I'll be homefree?   

Thanking you

---

