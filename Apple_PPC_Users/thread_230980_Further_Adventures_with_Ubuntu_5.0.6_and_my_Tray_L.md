---
title: "Further Adventures with Ubuntu 5.0.6 and my Tray Loading Imac 333"
date: 2006-08-06
forum: Apple PPC Users
---

### Post by GREGMACKENZIE on 2006-08-06
Hi All,

I've had a week or so with Ubuntu 5.0.6 (Hoary). It occurs to me that it might be useful to pass on a few impressions to other Ubuntu Users. 

There are pros and cons.

The desktop install from the CD is fairly complete, coming with version 1.x of the Open Office suite, Gimp 1.x, and lots of other goodies. As a basic desktop its a pretty good collection of software so you can get all the basics done. 

However, I did find the Ubuntu OS itself a bit mystifying. Its not that everything isn't there I just found it an obtuse experience. I think the slogan “It just works” is an apt summary. The OS is much more direct than I expected. most Windows users are familiar with their OS pampering them somewhat with endless dialog boxes and wizards to walk them through steps. These days most users expect a GUI and can get along without a manual in most cases, but Ubuntu definitely needs the support of documentation. Without reading, help files, and other supporting information I wasn't able to always ”guess” at the purpose of some of the Ubuntu interfaces. Nevertheless, once I had digested some supporting documentation things began to make sense. I found myself digging into the discussions on the forum and contents of the help wiki, generally things went much smoother. 

Sound

Off the bat after booting to Ubuntu I noticed a lack of sound. The sound icon in the top right main menu didn't seem to do anything. Under the Gnome menu at the left I found the system preference for sound and the  panel opened to several sound sliders. I slid the far right sliders up all the way before I was able to get any sound. I turned the sound icon at the bottom of the sliders off and on. This produced a beep. Unfortunately each time I re-boot there is no sound until I do this same thing again. The system doesn't retain the settings, oddly annoying....

Internet

Connecting to the internet is a bit of a challenge. I located the network panel and created a Netscape connection, selected the modem instead of ethernet, and configured it. I used autodetect to find the modem. I entered the dialup number and my password, selected OK, and then on return to the main network panel selected activate to connect to the internet. So far so good, the Firefox browser was then able to access the internet. 

When you open the mail applicaton it asks you to configure the connection in a series of wizard like steps. That was easy enough to follow through without coaching, and I was able to retrieve mail from the net. Reading the documentation for the mail application first would be ideal. I recommend it. I closed the applications and in the network panel selected de-activate to close the connection. I shut down.

I came back later on only to find that after reboot the network panel had lost all its settings even though the “Netscape” name was still there. When I selected the connection, in my case “Netscape” it had lost all the remaining information I pre-defined. That was very frustrating.

Some things about the network panel are mystifying, like what is the connection speed? What is the modem? It seems odd those things aren't in the panel.

I was curious to see if I could find a better internet connection application which after some searching at the forum led me to Synaptic in order to find and install Gnome-PPP. In order to retrieve Gnome-PPP from the net you have to enable the extra repositories so you can find and install the application you want from the software list. Everything had to be done in the right order:

Step 1. Activate a network connection
Step 2. Open Synaptic and enable the additional repositories
Step 3. Reload the repositories
Step 4. Find the Gnome-PPP application, mark it for installation, and apply/install the program.

I really like the Synaptic repository feature! In order to get applications like Gnome-PPP you have to have an active internet connection which means going through the Network panel, setting up, and activating the connection again. After selecting the univers and multiverse repositories, and reloading the entire repository, you can search for the application you want and mark it for installation. Compared to Windows that is a real joy. I can't begin to tell you how many hours I've spent searching the net for open source software. 

During this process I found my connection painfully slow which was mentioned in my reading about the Network Control panel. So the re-loading of the repositories took a long time, too long. The Synaptic download and install of the 86k Gnome-PPP application was slow as well.

Gnome-PPP

Gnome-PPP allows you to set the modem speed and specify the connection details, connect and disconnect. It doesn't help you sort out what type of modem you have although it will autodetect the modem. I found Gnome-PPP much easier to use than the Network Control panel, and on reboot the settings were retained. In my opinion this application should be installed by default during the install of Ubuntu. However despite its convenience its performance seemed no different in terms of speed considering that you can specify what the modem is to use.

Slow Connection

I still have to sort out the modem and driver. From my readings this it appears this should have been done from the beginning. Although modem autodetect works the resulting connection is so slow as to be nearly unusable. Even trying to surf to the Ubuntu forum, the connection was so slow it was an impediment to accessing the forum. I'll update  you on my progress when I get the modem fully sorted out. I note the default is for ethernet so I suppose that the ethernet connection is likely much more satisfying. Nevertheless, we all have to live within our means, and dialup is the way I have to go. 

This also prompted me to download Gnome-PPP and try to install it locally. That I just couldn't figure out how to get installed from the debian package. That too I need to figure out.

Positive Impressions

Don't get me wrong there's lots to like about Ubuntu and be prepared to learn! I like the login from booting which will make it nice to keep the kids from messing up the system and allow all in the house to use the iMac including my Mom. All the main applications we are likely to use are easy to find. I'll update you on my impressions of using those later on.

An Experiment with Dapper

Some of the difficulties I had prompted me to take a run at installing Dapper, and or upgrading to it. I  had sent away for the disks, both Hoary (missed out on Breezy because its too hard to download on dialup) and Dapper,. I didn't have any trouble installing Hoary 5.0.6 on my iMac but Dapper just won't install. Here's what happens:

To boot the Dapper installation CD on an iMac you have to hold down the “c” key with the cd in the drive. On  booting there is a black screen, followed by a white screen, followed by a black screen with a boot prompt. Here's where problems set in. The system starts to boot but a white screen appears with the following message:

“Cant Allocate Initial Device Tree Chunk
Apple imac open firmware 3.0.f2 built on 04/23/99 at 14:31.03
copyright 1994-1999 Apple Computer Inc
All rights reserved
ok
0 > _”

Well I read the Dapper Ubuntu Desktop Guide and found that the G3 processor is not mentioned. G4 is the last processor specified but not G3. Hmm, well it looks like the G3 is not supported in Dapper. After reading somewhat I did find a discussion which mentions modifying the xorg file but this technique won't work on my G3 since I can't get to a command prompt by pressing alt-ctrl-F1. Even pressing it repeatedly doesn't produce results. There's no starting chime because Ubuntu Live Dapper simply does not start.

According to some the problem may be the install CD as others have pointed to success with the alternate intall CD which does not employ a GUI. I'm assuming it employs the same sort of installer as Hoary. I have no easy access to this however, and it appears unlikely that I'll get one in the immediate future. It would have been nice to have a working installer. 

Future Plans

I plan to continue with Hoary for the time being because it works and the installer caused no problems, and my next move will be to sort out the modem speed and/or drivers.

Greg
:-)

---

### Post by 3rdalbum on 2006-08-07
Unfortunately, sound on the iMacs isn't too good on ALSA. I have your exact model of iMac and under Breezy it works fine (except for Sound In, which doesn't work at all).

It's good to know that my iMac's internal modem works with Ubuntu.

Also, unless your iMac is chock-full of memory (I think that model can take 256mb), Ubuntu Dapper Live won't run. Not enough memory. However, I've actually had the Live CD start to boot on the iMac with 128 megs; it hangs up late in the startup process, and I've heard reports of the "can't allocate device-tree" thing, so I don't know what's happening.

If you can possibly get a copy of Xubuntu Alternative PPC (maybe ask a local Linux User Group?), you should try that. It doesn't have too many options for you, but at least it will run on your hardware and you can still load gnome-ppp on :-)

---

### Post by GREGMACKENZIE on 2006-08-07
Hi,

Thanks for the reply. I'm not too sure who uses Linux around here. I may get one of my friends with High speed to download the Alternate CD Dapper for me and burn a CD. However according to the Ubuntu Desktop Guide the G3 is not supported. Its a question whether or not its intended for the iMac.

I'd made another post earlier and someone suggested an upgrade path instead, hoary to breezy to dapper. I find that more appealing as a strategy to getting Dapper on the iMac. I might give that a try instead but again it means retrieving the breezy cd fron the net.

This iMac has lots of ram, 288 mb, 333mhz and comes with the rage pro video. I don't think a shortage of ram is the problem. Since the response I'm getting is an "apple" message I'm wondering if there's something on the apple side falling short of what's required to boot the live cd even partially. A lot of users seem to have at least got to the point where they can get to a prompt and edit the xorg file. It might be some sort of firmware problem. I'll have to look into it further.

While the modem works, its awfully slow. I mean to look into that as well to see if I can get an improvement.

Greg

---

### Post by GREGMACKENZIE on 2006-08-07
Okey Dokey, here's a thought. The modem may need an initialization string hence the problems I might be having with the modem. Check out this link for the strings [http://docs.info.apple.com/article.html?artnum=24708]("http://docs.info.apple.com/article.html?artnum=24708")

iMac Internal 56K:
AT&FE0Q0V1X4&C1&K3S95=1S7=75S0=0\13

iMac Internal 56K (v.34 Only):
AT&FE0Q0V1X4&C1&K3S95=1S7=75S0=0+MS=11\13

I'll have to try them and report back. In the meantime I also read that the iMac comes with a built-in modem. The telephone connector for the modem is an RJ-11 connector on the I/O panel.

The modem has the following features:

modem bit rates up to 56 Kbps (supports V.92 and K56flex modem standards)

Group 3 fax modem bit rates up to 14.4 Kbps 

The modem appears to the "MAC OS" as a USB device that responds to the typical AT commands. The modem provides an analog sound output for monitoring the progress of the modem connection.

That's about all I've learned for now.

Greg
:-)

---

### Post by GREGMACKENZIE on 2006-08-08
Here's a little update. 

I used the Gnome-PPP control panel to confirm the modem speed was in the range of 115000. Apparently this is not the connection speed but refers to the internal communication between the modem and the computer.

I also deleted the default modem initialization string on line 2 and replaced it. (Is there a line 1? because I couldn't find it.) The default string was "ATQ0 V1 E1 S0=0&C1&D2+FCLASS=0". I replaced it with the shorter Apple v.34 string I found on the apple page "AT&FW2S7=75+MS=11". My guess was that the string designed for the modem should work better than the default. Without reading the Apple AT Commands PDF I'm not too sure exactly what the above strings actually do (more reading ahead I'm sure). 

As a test this is not very empirical however my connection appears to have improved considerably. Normally I'd only change one thing at a time. However, the first thing I noticed was that the log on seemed to take less time to negotiate. Secondly the Ubuntu website and forum now load in the Firefox browser in a reasonable manner on my dialup service. This is a marked improvement over what was happening before.  

So, these are the only two changes I made to the connection configuration in Gnome-PPP. Between the two changes something went right. I'll have to run Synaptic later and see how an update goes. I just didn't have more time last night to confirm the actual connection and download speeds.

Greg

---

### Post by yurtboy on 2006-08-15
I have an Imace but the modem is not seen?
It is a 400mhz version of the machine?
Any suggestions?
Thanks

---

### Post by GREGMACKENZIE on 2006-08-15
Hi,

Well my default modem setting is "/dev/ttyS0". I don't have my iMac desktop in front of me so you'll have to try and follow along with my somewhat sketchy memory here. If your using the system/administration/networking panel to setup your dialup connection you need to perform the following:

Open the network panel from the menu system/administration/networking.

Set up a new connection name.

By default the dialup will say this device is not configured oPPP You need to select the dialup modem, and then configure it.

There are three tabs for configuring your connection via the modem:

Tab 1, check the box that say's something like "this device is configured" Sorry, my memory is sketchy here. However the rest of the settings are grayed out, so its pretty obvious. When you uncheck it they'll become areas you can enter information in. Username, Password, telephone number.

Tab 2, The modem setting area, which is blank, you can try autodetect! it should fill the setting with "/dev/ttyS0" if it finds your modem which I suspect it will. If it doesn't you could put the string in manually. 

Tab 3, I don't remember offhand what is in this tab...

Ok, close the tabs and return to the network panel. You need to press activate to initiate the connection. It should say this device is configured, or something to that effect under the modem. Try your browser and see if you can surf the net. Press de-activate to close the network connection.

I didn't find this that fast. Also, the network panel didn't retain my settings or if it did tried to connect to the internet on bootup. I suspect that happens if you shut down with an active network connection. 

Gnome-PPP is great. You'll need Synaptic with an active connection to the net to get it. I had to enable my extra repositories, download, and install Gnome-PPP to get something that remembered my connection details. Also, Gnome PPP has multiple settings, "/dev/ttyS1", "/dev/ttyS2", "/dev/ttyS3", and allows you to enter the modem initialization string and speed I mentioned above.

I hope this helps. It might make a good wiki for me to try writing once I get the details right. I hope this helps, let me know how it works out.

Greg
:-)

> **yurtboy said:**
> I have an Imace but the modem is not seen?
It is a 400mhz version of the machine?
Any suggestions?
Thanks

---

### Post by yurtboy on 2006-08-15
Thanks for the feed back I will try again today.
The only glitches though, and I am pretty good with this on the pc platform 
One) wvdialconf /dev/null does not find a modem
Two)lspci does not see a modem?
But the modem is on the machine, I see the port.
Maybe it is a bios thing, though a ppc bios is foriegn to me.
I will try auto detect in gnome-ppp but from what I know gnome-ppp and wvdial go hand in hand.
Yes a ppc wiki would be great, these are going to be showing up more and more as free machines but they work great over all for this.
Did you get the DVD to work, without being choppy?
It works on this machine in OS9 but not linux>?

---

### Post by GREGMACKENZIE on 2006-08-15
Hi,

My iMac just has the cdrom. Its really old, one of the first crt bondi blue machines, 333 mhz, 288 mb of ram, and the rage-pro video. No dvd in it at all.

I don't know too much about the model you've got. I'm running Hoary 5.0.6 actually, not Dapper 6.0.6 lts. Just keep mining the forum, your bound to turn up something about the dvd.

I don't know why your modem is not detected, unless its not hardware. Check the specs at apple for your hardware and see if its a softmodem.

Greg

---

### Post by GREGMACKENZIE on 2006-08-15
by the way did you try entering the dev string with a zero, everything between the quotes?

---

### Post by avtolle on 2006-08-15
@yurtboy: on the choppy DVD issue; check to see if you have DMA enabled. This is from a note I made off a thread back in June, sorry I don't have the link to post ATM. As GREGMACKENZIE posted, keep searching the forum, you will likely find the thread I recall, together with many others. Good luck; hope this helps.

---

### Post by GREGMACKENZIE on 2006-08-15
Here's a cool link I found while digging around when I was trying to get connected, not exactly my problem, but the information was useful. [http://www.ubuntuforums.org/showthread.php?t=192222&highlight=DISCONNECTING+MODEM]("http://www.ubuntuforums.org/showthread.php?t=192222&highlight=DISCONNECTING+MODEM")

---

