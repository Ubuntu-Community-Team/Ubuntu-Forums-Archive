---
title: "I just made the switch, now what do I do?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Karow on 2007-12-28
[CENTER]Hello all,
I just made the switch from Vista to Ubuntu because it has been recommended to me several times, however, I am slowly noticing things that are not working... and I am not sure what to do.

Perhaps someone out there could help me... 

I just installed Ubuntu on my Toshiba/Satellite A205 laptop, which has a built in web-cam, and came with Window's Vista. Vista is completely off, and Ubuntu is fully installed,

Here are the problems I am having as of now:
Firefox will not let me bookmark webpages.
I have no sound...
I cannot find my web-cam...

Now, mind you, I have never used Ubuntu or anything other than Windows, so I am completely clueless as to where I should begin... All I know is that sound and the few things that I have found to be not working are basically simple things that I would like to use as I discover this software...

Any advice?
[/CENTER]

---

### Post by Q4U on 2007-12-28
Try the fix talked about here: [http://www.linlap.com/wiki/Toshiba+Satellite+A205](http://www.linlap.com/wiki/Toshiba+Satellite+A205)

---

### Post by spiderbatdad on 2007-12-28
Hi could you post the output of ```
lspci
``` typed into the command prompt and we can see if the drivers for those devices are installed.

Nice post.@Q4U.

---

### Post by spydon on 2007-12-28
Maybe you have the "bookmark field" disabled on firefox, enable it by right click and beside the field were you write url's and choose "bookmark field" or something like that my ubuntu is in Swedish. :P

Most webcams just works when you try them in a program, you can try it in for example amsn and you can get that one by clicking the Add/Remove button.

---

### Post by markharding557 on 2007-12-28
you should make a separate thread for each problem
on my firefox you save bookmarks in the bookmarks-bookmark this page tab

---

### Post by aktiwers on 2007-12-28
Hi and welcome !

You will just have to configure those things.. 

1) First the sound problem can be fixed by following this guide:
[http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/)

2) It doesn't? What error or what happends? This sounds strange..

3) Try this for your webcam
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Btw, when asked to type a command, just copy/paste them into the Terminal (Applications =Accessories=> Terminal). You can copy/pase by using CTRL+C and then CTRL+Insert.

Good luck and again Welcom!

---

### Post by Kzin on 2007-12-28
Hey there, and welcome to the world of Linux =)
On occasion, there are little things that need to be tweaked to get up and running properly.  The good thing is, your problems have fixes as far as I know.

For the sound, you will probably need to upgrade your ALSA driver.  First, some questions.  

In order to answer these questions, we'll need to access your "console".

Click on Applications, Accessories, Terminal.

What version of Ubuntu did you install? 
(You can find out the relevant info by typing cat /etc/lsb-release )

---

### Post by Kzin on 2007-12-28
> **aktiwers said:**
> Hi and welcome !

You will just have to configure those things.. 

1) First the sound problem can be fixed by following this guide:
[http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/)

2) It doesn't? What error or what happends? This sounds strange..

3) Try this for your webcam
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Btw, when asked to type a command, just copy/paste them into the Terminal (Applications =Accessories=> Terminal). You can copy/pase by using CTRL+C and then CTRL+Insert.

Good luck and again Welcom!

LOL  When I pressed reply there were none!  By the time I hit submit there were a plethora of suggestions!

:lolflag:

---

### Post by Karow on 2007-12-28
Here is what my computer tells me:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
karow@Private-CPU:~$ 


I am browsing around the websites that you guys provided as well, thank you for the help!

---

### Post by Lostincyberspace on 2007-12-28
if you find a command on the internet then you can just select it and go to where ever you need to go, most often the terminal, and click with the middle mouse button and it will place the text their. Make sure you don't select any thing in between though, since it will put that text in instead.

---

### Post by Karow on 2007-12-28
> **Kzin said:**
> Hey there, and welcome to the world of Linux =)
On occasion, there are little things that need to be tweaked to get up and running properly.  The good thing is, your problems have fixes as far as I know.

For the sound, you will probably need to upgrade your ALSA driver.  First, some questions.  

In order to answer these questions, we'll need to access your "console".

Click on Applications, Accessories, Terminal.

What version of Ubuntu did you install? 
(You can find out the relevant info by typing cat /etc/lsb-release )

I am running the newest version of Ubuntu, 7.10, -I also have installed all of the updates available with the updater thingy...

---

### Post by spiderbatdad on 2007-12-28
for the most part that looks good..as in drivers are installed for example 00:02 where your ethernet card is, instead of all zeros, or other identifying numbers with other devices. I do not see anything that looks like a cam. I miss stuff all the time though. I can tell you there is a package in synaptic called displayconfig-gtk```
sudo apt-get install displayconfig-gtk
``` then you can navigate to it graphically...System>>Administration>>Screens and Graphics  or enter terminal command
```
gksu displayconfig-gtk
```  I'm wondering if there is some off chance it will enable some aspect of the onboard cam...this is really out in left field...I have no experience with on-board cams.

---

### Post by Karow on 2008-01-12
I have tried what was reccomended, but in the midst of the directions, I begin to get errors... I don't know if I am doing something wrong or not...

I have no idea what most of these commands mean, really...

---

### Post by Karow on 2008-01-12
This site did not help...

---

### Post by oldos2er on 2008-01-12
Post the errors, and maybe we can help.

---

### Post by Can+~ on 2008-01-12
> **Karow said:**
> I have tried what was reccomended, but in the midst of the directions, I begin to get errors... I don't know if I am doing something wrong or not...

I have no idea what most of these commands mean, really...

It's quite shocking to see some commands, but this are pretty simple:

**gksudo** or sudo: Gives you administration power and asks your user password in a graphical way (there is "sudo" which is via console/shell/terminal). Everything after gksudo or sudo will be executed with root permitions (if the password is correct of course).
**apt-get** It's the application that let's you grab files from a ubuntu server, there are graphical front ends for this, either Add/Remove programs, or the Synaptic package manager.
**install** Install is just saying to apt-get what to do.
**displayconfig-gtk** Is the application that you want to grab from the server.

So basically, the first command is saying:
Give me root power, go to the server, install <name of file>.

This is a really useful command, the manual:

**man <name of command>** Do a man apt-get, man sudo, man gksudo, whatever, it will show you the manual of the command.

And, don't be scared, you can do almost everything via the graphical interface (gnome), but it's easier to say "copy this command and paste it on a console" than doing the "open this window, then this one, then this one, etc etc"

---

