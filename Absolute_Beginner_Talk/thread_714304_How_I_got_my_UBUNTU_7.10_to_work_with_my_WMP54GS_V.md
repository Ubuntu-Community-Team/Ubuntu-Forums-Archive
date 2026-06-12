---
title: "How I got my UBUNTU 7.10 to work with my WMP54GS V1.1"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Zummy on 2008-03-03
Many people, like me, have/had trouble of getting WMP54GS v1.1 with speed booster hard to get working with ubuntu.  I have just got it to work, and I'm going to post what I did in this thread in very simple steps.

NOTE I run a i386 comp, you may need a different file setting than what I posted, be sure you get the right file for your (x32 or x64 comp [i think thats what its called XD])
just search the file name.  Most modern comps(like mine) uses i386 so just double check if your comp is slightly dated. I don't know how to check, I got it from my bro(identical comps).

First off you will need:
A few files (I will put them as attachments if I can)
A flash drive 1gig would do fine.
Ubuntu Computer (can use live CD for this, I'm still in mine in-fact =P)
Other Computer to download the files.

1) boot into Ubuntu and put your flash drive in.

2) install (in order):
a) ndiswrapper-common_1.43-lubuntu2_all.deb
b) ndiswrapper-utils-1.9_1.43-lubuntu2_i386.deb
c) ndisgtk_0.7.2-lubuntul_i386.deb
d) bcm43xx-fwcutter_20060108-6build1_i386.deb
e) wl_apsta-3.130.20.0.o (doesn't need to be installed, make sure you have it Go to: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) )

All of these are really easy to install, just double click the icon, close the popup dialog that appears, then click on install this package in the top right corner.

3) After that find the: WMP54GS_20060406.exe in your flash drive.  Right click it, and pick Extract Here. Now you will have a folder named "WMP54GS_20050406".

4) Drag that folder onto the desktop.

5) Go to the top of your screen, on the left go to System -> Administration -> Windows Wireless Drivers (Mine was at the bottom),

6) Click Add Driver.

7) Go to the directory of, Desktop -> WMP54GS_20060406 -> Drivers -> and pick a .INF file.  There is two.

8) Do the same thing in steps 6 and 7, except select the OTHER .INF file in your Drivers folder.

Check the window See if one says "Hardware Present" If so go on, if not, ask around.

9) Drag the file, "wl_apsta-3.130.20.0.o" file onto your desktop from your flash drive.

10) Go to System -> Administration -> Restricted Managers Driver

11) Check the unchecked box for your firmware.

12) When it asks for a directory, go to your desktop and pick the wl_apsta... file.

13) It should be checked and In use now.

14) go to the top right corner of your screen to the black monitors with the red icon on it.  

15) Regular click and say connect to other network.

16) Type in your ESSID (default is linksys, you should know yours)

17) Select the security (if any) and type in the pass word

18) If it goes like it did for me, you should be connected to the internet! :D congrats!

---

### Post by unknown03 on 2008-03-15
Holy Mc-*$!@K ...It actually worked! ...wow thanks alot! I'm now online from the Live CD 7.10

---

### Post by Zummy on 2008-03-17
Mhmm Just wanted to help yall in a easier way than most of the guides here ! :D

---

### Post by unknown03 on 2008-03-18
yeah thanks again..one thing ive noticed is that you dont need ndiswrapper or the wmp54gs.inf to get it working...all I need to do now is install the bcm43xx-fwcutter.deb and the firmware something*.o and it loads right up

---

### Post by SSFury on 2008-03-21
Thanks for the info - I am very new so it took me a few tries but I am now able to connect to my network. Thanks

---

