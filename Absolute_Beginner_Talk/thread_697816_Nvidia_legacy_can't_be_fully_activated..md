---
title: "Nvidia legacy can't be fully activated."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by gkiteguy on 2008-02-15
OK, I have been struggling with 7.1 for 3 days now.  I determined my Nvidia GeForce2 MX Integrated video card needed the Legacy Driver so I downloaded it and have been reading the forums and trying stuff and re-installing Gutsy as needed. 
I currently have the legacy driver running, I Think, but the desktop effects still won't activate including the screen savers. 

Most recently I have downloaded the driver performed the following commands. 

[SIZE="3"]sudo apt-get install nvidia-glx-legacy[/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-legacy is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 [SIZE="3"]sudo apt-get install nvidia-xconfig[/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-xconfig is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[SIZE="3"]sudo apt-get install nvidia-set[/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-set
 so when I appy the command

[SIZE="3"]sudo nvidia-xconfig[/SIZE]
nothing much happens.  I then had to configure xorg.conf to read 
ection "Device"
	Identifier	"nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
	Driver		"[SIZE="2"]nvidia[/SIZE]"
	BusID		"PCI:1:0:0"
EndSection

Can anyone point me in the next direction?

GKitguy

---

### Post by beege on 2008-02-15
I have the same card. What I ended up doing was going to the Nvidia site, downloading their .run package and followed the instruction there.

You have to run the install from outside of X. That means as you boot, you go into rescue mode, and "init 3".
Then maneuver to the directory that you downloaded the file into and run the script there.

Let me know if you find success!

---

### Post by gkiteguy on 2008-02-16
I got it to start but it said it didn't have the kernal compiled it would have to generate it locally. Then it said I had to download a Libc development package. I don't know what that is or where to get it, it wasn't listed in the synoptic manager.  Any Ideas?

---

### Post by gkiteguy on 2008-02-17
OK.  Now I flailed around and added some headers and got the installer to install, but now it just freezes at the NVIDIA Splash Screen.  I ran dpkg-reconfigure -phigh xserver-xorg and  sudo nvidia-xconfig

 got the error sudo: nvidia-xconfig: command not found. It still freezes when I try to use the driver. 

I can reuse my old xorg.conf with NV selected, but cannot enable any screensavers, etal.   It's been two weeks, and I haven't had the opportunity to enjoy UBUNTU yet. <SIGH>

---

### Post by bumanie on 2008-02-17
The only way I could get the nvidia card installed in gutsy was to do it through console mode. The closest driver I can find on the nvidia site is NVIDIA-Linux-x86-96.43.05-pkg1.run Get it from here [http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)
If you want to try that, download it to your desktop and then follow these instructions. I will warn you that the video card settings won't be updated when a new kernel is released. You will have to install again via the same method (that's if this works, re I have got the right driver).
Once downloaded to your desktop, depress ctrl-alt-f1 together
put in user name and password, then type cd ~/Desktop
then type > sudo /etc/init.d/gdm stop
Then > sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run 
Answer the nvidia questions. When that has finished, type
> sudo /etc/init.d/gdm start and your card should work. If it doesn't you may have to find an earlier driver with the .run file type.

---

### Post by gkiteguy on 2008-02-18
Yes, that's the one I used that freezes at the NVIDIA splash screen.  I'll have to uninstall it and try an earlier version like you suggested.  Stay tuned. :popcorn:

---

### Post by crjackson on 2008-02-18
I have a GForce 2 card in one of my machines also.  I just installed the restricted driver and it works fine.  However I don't have the ability to use desktop effects.  It's 16MB card I think.  Are desktop effects even possible with this card?

Please keep us updated...

BTW, you do know that Envy has a package to install the legacy driver don't you?  You might want to check it out and she what driver version is included with that package.

---

