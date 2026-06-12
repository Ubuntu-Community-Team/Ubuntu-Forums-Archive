---
title: "Installing Ubuntu 18.04 LTS on MBP 5,2 (mid 2009)"
date: 2019-04-01
forum: Apple Hardware Users
---

### Post by swarup on 2019-04-01
I use a MBP 5,2 (from mid 2009), and would like to install Ubuntu 18.04 on it. Any experience or suggestions for this. I have installed 9.04 and then 14.04 on it in the past, and the techniques I used are detailed below. As 14.04 installed in a routine manner just as on a PC, I am wondering whether that may be the case for 18.04 as well?

Here is my hardware:
MBP 5,2
Ram 8 GB 1067 DDR3
2.8 Ghz Intel Core 2 Duo
NVIDIA Ge Force 9400M/9600M GT 

History of 9.04 and 14.04 installs on this computer:

I initially installed Ubuntu 9.04 on it back in 2009, then 14.04 in 2014, and now would like to install 18.04 om it. There were some issues with the 9.04 install and I ultimately used rEFit to get it done. In 2014, the 14.04 went really smoothly: I used the regular 64-bit 14.04 iso. (NOT the MAC 64-bit), and rEFIt was not needed at all. I allocated drive space using the installation usb, just like one would do on a PC, and everything went incredibly smoothly. I did need to set the boot to [nomodeset]("https://ubuntuforums.org/showthread.php?t=1613132") for the liveusb, and I had to do it for the first boot into Ubuntu. Once I booted in and installed the NVIDIA driver, it was no longer needed. To install the NVIDIA driver, I just typed "Additional Drivers" in the dash and the tool came up right away for installing it.

---

### Post by speartip on 2019-04-01
The only thing I can suggest is download the latest isos. Burn to usb/dvd and test them out.
My personal opinion is that Ubuntu Gnome, is quite resource hungry & laggy on my system. I prefer Xubuntu for speed & stability.

---

### Post by swarup on 2019-04-01
Thanks very much. Two follow-up questions:
1) When you suggest to test out 18.04, what do you have in mind: To try running it from the install usb to see what it is like, or to install it? 

If the latter doesn't go smoothly, then I will be in difficulty. But it is this that I am most interested in: will 18.04 be a smooth install the way 14.04 was, or should I expect something different.

2) I have never run Xubuntu. As I recall, it is a lighter version of Ubuntu. My computer usage is for a very narrow spectrum of activities: email (TBird), basic web browsing (Firefox, Chrome, Opera, Midori), word processing (Libre Office), and typing in Hindi and Bengali (Input Method: M17N). If all of this will work well in Xubuntu, then I would have no need for Ubuntu. 

Again, bottom line: Whether Ubuntu or Xubuntu, does anyone have any experience that would indicate whether I can expect a smooth install. With 14.04, it worked perfectly with just the regular 64-bit 14.04 iso and no need for rEFit or anything else.

---

### Post by swarup on 2019-04-04
Writing to report the excellent news that when I went ahead and installed 18.04 on my MBP 5,2 two days ago, there were absolutely no problems or hitches whatsoever-- a very smooth installation! I did not need any special tools such as rEFIt etc. 

Here is what I did:
1. I had an existing dual boot with OSX Yosemite and Ubuntu 14.04 on my MBP 5,2. 
2. After backing up all my data, I booted up with the 18.04 install USB. (I did use [nomodeset]("https://ubuntuforums.org/showthread.php?t=1613132"); but actually I think it probably was not even needed. This idea arose because I actually booted up to the install disc a few times before moving ahead, and in subsequent boots did not use nomodeset.)
3. There I opened Gparted, made the Yosemite OSX partition as small as I dared (Just 2.5 GB larger than the smallest Gparted would allow; I never use the Mac side), 
4. I then moved the two Mac rescue partitions over to abut the Mac OSX thus creating a lot more space for the 18.04 installation
5. I deleted the existing 14.04 along with its ext 4 partition and the swap partition
6. This gave me one large, continuous unallocated space in which to install 18.04.
7. I intentionally did not create a swap partition, as I had read that for 18.04 it isn't needed
8. I created one single ext 4 partition in the entire unallocated space
9. In that partition I installed 18.04
10. Once 18.04 was installed, I rebooted and found that 18.04 booted up perfectly with full NVIDIA functionality and no need for nomodeset. All hardware worked out of the box, except for perhaps wireless internet which I haven't really checked much yet as I use an ethernet cable mostly.
11. The usual tweaks with any new installation I've been involved with, but just internal to the 18.04 OS, nothing specific to this being a Mac computer.

I encourage everyone to move ahead without concern; if your MBP is similar to mine, you won't have any problems. Just do a routine install. :-)

---

