---
title: "Ubuntu not recognizing my wireless network."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ToriArendt on 2008-02-23
First of all, I feel the need to put a disclaimer here; I am almost computer illiterate, but I am very good at following directions. So, if you are going to try to help, I appreciate it greatly, but don't assume I know much.

Alright, I dual booted my laptop ([Gateway MT6705]("http://support.gateway.com/s/Mobile/2007/Oasis/1014358R/1014358Rsp2.shtml")) with ubuntu 7.10 and windows vista. I like ubuntu a lot, but it does not seem to recognize my wireless network. My computer comes with a built in wireless card and I am using a linksys router and I think the network has a WEP passphrase (26 letter/number code).

Any help?

---

### Post by skozzy on 2008-02-23
I can't give you an answer, but I recently went through this with my laptop last week. It will help someone give you an answer if you can list the make and model of your computer. And does it have a switch or button to enable the wireless. Some have a hardware switch that turns it on, mine is a button. The button type use software to enable the wireless, in most cases you use/install the acer hotkey software. I have read in many posts its also called a softkey. If you have this software based wireless enable (softkey/hotkey) then search these forums for those terms and you will most likely find what you need.

---

### Post by gyf on 2008-02-23
Hi I just got my wireless working in ubuntu about a hour ago!

To setup wireless go to "Network" which is located in:
System -> Administration -> Network

once there click on the wireless connection then click Properties.

once in the properties check the box enable connection box. Then look for your network essid.

Once selected then choose the encryption of the password which in your case is WEP passphrase and enter the password.

Then press close and hopefully you should connect.

If ubuntu doesnt even detect any wireless networks while selecting the essid this would seem to be a driver issue which im not sure how to deal with and hopefully someone else here can help you with that ^_^

---

### Post by ToriArendt on 2008-02-23
In order to enable or disable my wireless card, I have to press the Fn + F2 buttons. So, the button is on my keyboard.

---

### Post by anewguy on 2008-02-23
Please do the following, then copy and paste the output back to a message here so we can go from there:

(1) Click "Applications", scroll down to "Accessories" and over to "Terminal" and click.  This will open up a terminal window, which you may also see referenced as access to the command line.

(2) type: 

lscpi  

and press Enter

(3) Use your mouse to highlight the output, copy it, then open a new reply here and paste the data here.

The reason for this is that we need to know what type of wireless card you have before we can proceed with any instructions.

Thanks!:)

---

### Post by ToriArendt on 2008-02-23
Sorry, I'm probably doing it wrong.

I opened up the terminal and typed in lscpi, but it didn't recognize it.

bash: lscpi: command not found

---

### Post by ToriArendt on 2008-02-23
Ah, wait I just googled it and typed in lspci and I got this:

> tori@tori-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
tori@tori-laptop:~$ 



---

### Post by anewguy on 2008-02-23
Sorry about transposing the lspci command in my post - glad you found it!


Thanks for posting that.  I didn't see your wireless listed, so I went to Gateway's site and found this link to the driver:

[http://support.gateway.com/support/drivers/getFile.asp?id=21250&dscr=Windows%20Vista%20(32-bit%20or%2064-bit)%20Wireless%20Network%20DriverVersion:%20Realtek%206.1281.130.2007&uid=187948091](http://support.gateway.com/support/drivers/getFile.asp?id=21250&dscr=Windows%20Vista%20(32-bit%20or%2064-bit)%20Wireless%20Network%20DriverVersion:%20Realtek%206.1281.130.2007&uid=187948091)

You'll need to download this to your Windows folder first, then execute it.  Since I don't run Windows I can't walk you through that or I would.  The result will probably be a folder that contains the stuff to install your driver.  You want to find the .inf and .sys files within there and copy them to CD or something you can access while in Ubuntu.

Next, in Ubuntu, follow the steps on my previous post to get to a terminal window.  In that window, type:

ndiswrapper -l  (<-- that's a lower case "L")

and press enter.

Copy and paste the results of that back here again so we can determine the next step you might need.

Thanks!
:)

---

### Post by ToriArendt on 2008-02-23
Okay, first I need some help on which files I need to save to my flash drive and what I need to do with them once I get to ubuntu.

Here is what gets downloaded to my computer from that link:

Main folder:
[IMG]http://img253.imageshack.us/img253/9788/mainbi7.png[/IMG]

VistaX64:
[IMG]http://img514.imageshack.us/img514/7594/vistax64lu3.png[/IMG]

VistaX86:
[IMG]http://img247.imageshack.us/img247/3277/vistax86xd0.png[/IMG]


Which files do I need? Thanks for all your help and I'm sorry for being so stupid about computers. I just don't want to mess anything up! =)

---

### Post by anewguy on 2008-02-23
Okay, I haven't worked with this wireless config before, but I think I know what you need:

in the VistaX86 folder:

Save the Netrtuw.inf file and the rtl8187.sys file, as I believe those are the 32bit drivers.  If someone else reading this thread has learned otherwise, please post back here.

Now I need you to do the ndiswrapper -l command as mentioned in the previous post (you will do this in a terminal window as with the previous post).

Please post that information back here and we'll try from there.:)

---

### Post by ToriArendt on 2008-02-23
Alright, my friend tried to help, but we didn't get too far. Here was our conversation.

> (04:41:37 PM) Alex Madjar: hello?
(04:41:41 PM) [email]Tori.Arendt@gmail.com[/email]/Home: hi
(04:41:50 PM) Alex Madjar: okay
(04:42:02 PM) Alex Madjar: so first thing is open up the command prompt
(04:42:08 PM) Alex Madjar: xD
(04:42:24 PM) [email]Tori.Arendt@gmail.com[/email]/Home: k
(04:43:06 PM) Alex Madjar: type
"mkdir wirelessdriver"
(04:43:14 PM) Alex Madjar: to make said folder
(04:43:24 PM) Alex Madjar: type cd wirelessdriver
(04:43:30 PM) Alex Madjar: to go to that folder
(04:43:47 PM) Alex Madjar: now
(04:43:57 PM) Alex Madjar: actually
(04:44:07 PM) [email]Tori.Arendt@gmail.com[/email]/Home: so it now says
(04:44:19 PM) [email]Tori.Arendt@gmail.com[/email]/Home: tori@tori-laptop:~/wirelessdriver$ 

(04:44:23 PM) Alex Madjar: just go to the "my computer" equivilent
(04:44:33 PM) Alex Madjar: and copy those driver files to that folder
(04:44:49 PM) Alex Madjar: it'll be home/wirelessdriver
(04:46:02 PM) Alex Madjar: tell me when you're done (or stuck)
(04:46:34 PM) [email]Tori.Arendt@gmail.com[/email]/Home: okay, the two files are in home/wirelessdriver
(04:46:39 PM) Alex Madjar: good
(04:46:58 PM) Alex Madjar: now go to the top
(04:47:02 PM) Alex Madjar: the settings menu
(04:47:19 PM) Alex Madjar: go to system->synaptics package manager
(04:47:25 PM) Alex Madjar: (or something like that)
(04:47:31 PM) Alex Madjar: (I;m in windows right now >_>)
(04:47:38 PM) [email]Tori.Arendt@gmail.com[/email]/Home: okay
(04:47:47 PM) [email]Tori.Arendt@gmail.com[/email]/Home: synaptic package manager, I am in.
(04:48:02 PM) Alex Madjar: search for the ndiswrapper-utils package
(04:48:29 PM) [email]Tori.Arendt@gmail.com[/email]/Home: ndiswrapper-utils-1.9?
(04:48:36 PM) Alex Madjar: yes
(04:48:54 PM) [email]Tori.Arendt@gmail.com[/email]/Home: what do I do?
(04:49:01 PM) Alex Madjar: click the check bow
(04:49:03 PM) Alex Madjar: box
(04:49:06 PM) Alex Madjar: then apply
(04:49:12 PM) Alex Madjar: or something like that
(04:49:15 PM) Alex Madjar: to install it
(04:49:30 PM) Alex Madjar: (gosh I should probably be in linux...)
(04:49:42 PM) [email]Tori.Arendt@gmail.com[/email]/Home: Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/
(04:49:50 PM) Alex Madjar: what
(04:49:55 PM) [email]Tori.Arendt@gmail.com[/email]/Home: that's what it says
(04:50:07 PM) Alex Madjar: um....
(04:50:23 PM) Alex Madjar: are you running ubutu off the disk >_>
(04:50:28 PM) [email]Tori.Arendt@gmail.com[/email]/Home: no
(04:50:35 PM) Alex Madjar: where does it say that?
(04:50:48 PM) Alex Madjar: in a pop up message box
(04:50:55 PM) Alex Madjar: where?
(04:50:59 PM) Alex Madjar: hold on
(04:51:05 PM) Alex Madjar: I'm going to restart in ubuntu
(04:51:11 PM) [email]Tori.Arendt@gmail.com[/email]/Home: Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/
(04:51:33 PM) Alex Madjar: hm
(04:51:35 PM) Alex Madjar: that's odd
(04:51:54 PM) [email]Tori.Arendt@gmail.com[/email]/Home: should I go disk?
(04:51:59 PM) Alex Madjar: I suppose
(04:52:03 PM) [email]Tori.Arendt@gmail.com[/email]/Home: one sec
(04:58:04 PM) Alex Madjar: back
(04:58:06 PM) Alex Madjar: okay
(04:58:10 PM) Alex Madjar: so what is up?
(04:58:16 PM) [email]Tori.Arendt@gmail.com[/email]/Home: i put in the disk
(04:58:19 PM) [email]Tori.Arendt@gmail.com[/email]/Home: and redid it all
(04:58:20 PM) [email]Tori.Arendt@gmail.com[/email]/Home: and it worked
(04:58:50 PM) Alex Madjar: retried to install the package you mean?
(04:59:27 PM) [email]Tori.Arendt@gmail.com[/email]/Home: yeah the ndiswrapper thing
(05:00:56 PM) Alex Madjar: the installing of the ndiswrapper-utils
(05:01:12 PM) [email]Tori.Arendt@gmail.com[/email]/Home: yes
(05:01:27 PM) Alex Madjar: okay
(05:02:05 PM) Alex Madjar: so go back to the command prompt
(05:02:30 PM) [email]Tori.Arendt@gmail.com[/email]/Home: k
(05:02:41 PM) Alex Madjar: and type in ndiswrapper -i <name of the inf file>
(05:02:56 PM) Alex Madjar: actually
(05:03:22 PM) Alex Madjar: "ndiswrapper -i *.inf"
(05:03:27 PM) Alex Madjar: should work
(05:03:46 PM) Alex Madjar: what does that output?
(05:06:06 PM) [email]Tori.Arendt@gmail.com[/email]/Home: tori@tori-laptop:~$ ndiswrapper -i Netrtuw.inf
couldn't create /etc/ndiswrapper/netrtuw: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.

(05:06:54 PM) [email]Tori.Arendt@gmail.com[/email]/Home: I did -l instead of -i this time
(05:06:55 PM) [email]Tori.Arendt@gmail.com[/email]/Home: tori@tori-laptop:~$ ndiswrapper -l Netrtuw.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

(05:07:15 PM) Alex Madjar: sudo ndiswrapper -i Netrtuw.inf
(05:07:23 PM) Alex Madjar: then type in your password
(05:07:31 PM) Alex Madjar: when it asks
(05:08:07 PM) [email]Tori.Arendt@gmail.com[/email]/Home: why won't it let me type in my password?
(05:08:17 PM) Alex Madjar: >_>
(05:08:22 PM) Alex Madjar: it does echo it
(05:08:27 PM) Alex Madjar: for security reasons
(05:08:30 PM) Alex Madjar: type it
(05:08:33 PM) Alex Madjar: press enter
(05:08:38 PM) Alex Madjar: it won't show it
(05:08:41 PM) Alex Madjar: but it will work
(05:08:47 PM) Alex Madjar: press ctrl+c
(05:08:54 PM) Alex Madjar: the type that in again
(05:09:01 PM) Alex Madjar: when it asks for the password
(05:09:05 PM) Alex Madjar: just type it in
(05:09:07 PM) Alex Madjar: and hit enter
(05:09:36 PM) [email]Tori.Arendt@gmail.com[/email]/Home: installing netrtuw ...
couldn't open Netrtuw.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.

(05:10:25 PM) Alex Madjar: type ndiswrapper -l
(05:10:32 PM) Alex Madjar: and tell me what that says
(05:11:03 PM) [email]Tori.Arendt@gmail.com[/email]/Home: tori@tori-laptop:~$ ndiswrapper -l
netrtuw : invalid driver!

(05:11:26 PM) Alex Madjar: hm....
(05:11:34 PM) Alex Madjar: this is the part where I go huh?
(05:12:20 PM) [email]Tori.Arendt@gmail.com[/email]/Home: =(
(05:13:47 PM) [email]Tori.Arendt@gmail.com[/email]/Home: usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

(05:14:32 PM) Alex Madjar: uh huh
(05:14:43 PM) Alex Madjar: sorry
(05:14:52 PM) Alex Madjar: that is the extent of my knowledge
(05:15:01 PM) Alex Madjar: it shouldn't have done that x(
(05:15:07 PM) Alex Madjar: idk what is wrong
(05:15:23 PM) [email]Tori.Arendt@gmail.com[/email]/Home: any ideas of what I should type?
(05:16:04 PM) Alex Madjar: try
(05:16:21 PM) Alex Madjar: ndiswrapper -are netrtuw
(05:17:39 PM) Alex Madjar: and then "sudo ndiswrapper -i ./netrtuw.inf"
(05:18:09 PM) Alex Madjar: >_>
(05:18:10 PM) Alex Madjar: wow
(05:18:12 PM) Alex Madjar: are
(05:18:17 PM) Alex Madjar: should be r
(05:18:38 PM) [email]Tori.Arendt@gmail.com[/email]/Home: couldn't delete /etc/ndiswrapper/netrtuw: Inappropriate ioctl for device

(05:19:09 PM) Alex Madjar: try just doing the second command
(05:20:24 PM) [email]Tori.Arendt@gmail.com[/email]/Home: driver netrtuw is already installed

(05:20:34 PM) Alex Madjar: >_>
(05:20:36 PM) Alex Madjar: sorry
(05:20:55 PM) Alex Madjar: can't help

Any ideas?

---

### Post by anewguy on 2008-02-23
Please do the following:

(1) Copy the 2 driver files to your desktop

(2) open a terminal window

(3) sudo ndiswrapper -l (that's a lower case "L")

post the output back here.  I'm going to try to do this one step at a time, so please don't do anything else - just what I requested.

:)

---

### Post by ToriArendt on 2008-02-24
[IMG]http://img526.imageshack.us/img526/7176/screenshotlz4.png[/IMG]

what am I doing wrong?

---

### Post by anewguy on 2008-02-24
That's what I wanted to see for now - ndiswrapper is installed and runs, and right now it is a "clean slate" as far as drivers go.


cd ~/Desktop

sudo ndiswrapper -i Netrtuw.inf <= where:  it's a lower case "I" for "install"


Then:

sudo ndiswrapper -l 

where :  it's a lower case "L" for "list" to be sure the driver "took"

Then:

sudo modprobe ndiswrapper

sudo depmod -a

sudo ndiswrapper -m



When you have done the above your wireless should be available.
:)

---

### Post by ToriArendt on 2008-02-24
> tori@tori-laptop:~$ cd ~/Desktop
tori@tori-laptop:~/Desktop$ sudo ndiswrapper -i Netrtuw.inf
[sudo] password for tori:
installing netrtuw ...
tori@tori-laptop:~/Desktop$ sudo ndiswrapper -l
netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
tori@tori-laptop:~/Desktop$ sudo modprobe ndiswrapper
tori@tori-laptop:~/Desktop$ sudo depmod -a
sudotori@tori-laptop:~/Desktop$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...


Is that what it is supposed to say?

---

### Post by anewguy on 2008-02-24
Yes - that's exactly it!  Now if you check your network icon you should find wireless available.  If not, I'll have to seek some outside help.  :)

---

### Post by ToriArendt on 2008-02-24
It's recognizing my neighbor's wireless connection, but not mine =(. Maybe it is because mine is security enabled, but I'm not 100% sure which type because my dad set it up.

Here is the information he wrote down:

Network: jtenarendt
Passphrase:
(his handwriting is in all caps, so if anything is case sensitive, I'm screwed)

And here is what I get when I go to properties in Vista:
[IMG]http://img256.imageshack.us/img256/3149/28165365gp0.png[/IMG]

[IMG]http://img233.imageshack.us/img233/7383/99936512cz2.png[/IMG]

Any ideas on how to connect? I tried a few things, but none worked.

---

### Post by anewguy on 2008-02-24
Ok, so we at least know the wireless is working now - that one big step out of the way.  What you will need to try now is clicking on the network icon and select "Connect To Other Wireless Network".  This will pop up a screen to log into the network with.

You'll want to put the SSID you've listed in the Network Name box.  Then click on the arrow to the left of the Wireless Security box and select WEP 128-bit Passphrase, then enter the passphrase you listed where it says "Passphrase", then connect.  You may need help from your Dad on this because it's possible he's got more than 1 key (I noticed it says key 1, when I believe Linux is relative zero so it would show key 0).

By the way, while I appreciate you trying to give as much detail as possible to work with getting you onto your network, you should NEVER post the passphrase or key to any public forum.  In fact, someone should be able to tell you to enter your passphrase or key without ever seeing it.  So, you may want to let your Dad know in case he wants to change it so he can keep the network secure (although WEP can be cracked in about 2 minutes).

Let us know what happens.:)

---

### Post by ToriArendt on 2008-02-24
It isn't working =(. Under passphrase, my dad has two things written down. One is a 12-letter code that he probably picked and the other is a 26-letter/number key. Which one do I use? I tried both and neither really worked, it just keeps trying to connect.

---

### Post by anewguy on 2008-02-24
2 things you are going to need to ask your Dad:

(1) Obviously, which and what key, what case, etc.

(2) Is the SSID being broadcast by the router?  I tried hiding mine for a while and for some reason I just could never connect to it.

Post  back after you learn those things, okay?:)

---

