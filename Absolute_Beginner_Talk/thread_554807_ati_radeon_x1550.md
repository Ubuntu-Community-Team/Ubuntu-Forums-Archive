---
title: "ati radeon x1550"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-19
hi anyone
ive got an ati radeon x1550 but ubuntu says its a radeon x1300
also when i get the resricted driver from ati i have 2 disable it and i get no desktop effects (all i get is a white screen with my mouse arrow which lasts about 20 secondsthen normal desktop is returned. this happens whether the restricted driver is enabled or not.
if anyone out there can help me fix this itd make an old man very happy and id b content to bin xp

---

### Post by Vadi on 2007-09-19
I see you!!

Read this thread ([click]("http://ubuntuforums.org/showthread.php?t=538795&highlight=radeon+x1550")), a bunch of people posted working solutions.

---

### Post by maryjanua on 2007-09-19
i went to the ati site and downloaded this driver to my desktop
ati-driver-installer-8.40.4-x86.x86_64.run
how do i install this i tried the instructions on the ati site and:
billym@billym-desktop:~$ sudo  sh ./ati-driver-installer-8.40.4.run
Password:
sh: Can't open ./ati-driver-installer-8.40.4.run
billym@billym-desktop:~$ 
 thats what it says anyone know what to do?

---

### Post by maryjanua on 2007-09-19
thanx vadi

---

### Post by mali2297 on 2007-09-19
Have you tried the fglrx driver from the repositories? See here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Vadi on 2007-09-19
Usually for .run files, you need to right click on them, select properties, click permissions, and allow them to be executable. Then you can run them.

Edit: what mali said. The chmod is the easier way of giving it the privs, but I didn't quite learn it yet.

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> i went to the ati site and downloaded this driver to my desktop
ati-driver-installer-8.40.4-x86.x86_64.run
how do i install this i tried the instructions on the ati site and:
billym@billym-desktop:~$ sudo  sh ./ati-driver-installer-8.40.4.run
Password:
sh: Can't open ./ati-driver-installer-8.40.4.run
billym@billym-desktop:~$ 
 thats what it says anyone know what to do?

Try
```

cd /home/billym/Desktop/
chmod +x ati-driver-installer-8.40.4.run
sudo ./ati-driver-installer-8.40.4.run

```

...but check out the available driver in the repositories first.

---

### Post by maryjanua on 2007-09-19
ive tried that link
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
doesnt help has actually made matters worse now if i boot in gnome rather than x i get everything all over the place and unveiwable

---

### Post by maryjanua on 2007-09-19
also the code u sent doesnt open the file on my desktop
billym@billym-desktop:~$ cd /home/billym/Desktop/
billym@billym-desktop:~/Desktop$ chmod +x ati-driver-installer-8.40.4.run
chmod: cannot access `ati-driver-installer-8.40.4.run': No such file or directory
billym@billym-desktop:~/Desktop$

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> also the code u sent doesnt open the file on my desktop
billym@billym-desktop:~$ cd /home/billym/Desktop/
billym@billym-desktop:~/Desktop$ chmod +x ati-driver-installer-8.40.4.run
chmod: cannot access `ati-driver-installer-8.40.4.run': No such file or directory
billym@billym-desktop:~/Desktop$

Type
```

cd /home/billym/Desktop/
chmod +x ati-driver*.run
sudo ./ati-driver*.run

```

Also, where did you get the driver? Are you sure it's the right one?

---

### Post by maryjanua on 2007-09-19
i got that driver from ati 
as i said xp and the box it came in say its a radeon x1550 but ubuntu says its a radeon x1300
also ati had no radeon x1550 driver only an x1300 one or x1600 were the closest they had thats the 1300 one

---

### Post by mysticmatrix on 2007-09-19
> **maryjanua said:**
> i got that driver from ati 
as i said xp and the box it came in say its a radeon x1550 but ubuntu says its a radeon x1300
also ati had no radeon x1550 driver only an x1300 one or x1600 were the closest they had thats the 1300 one
Clearly, ATI doesn't support your card for Linux. Perhaps they don't want to let you use Linux.

Well, can you post output of this command
```
lspci
```

---

### Post by maryjanua on 2007-09-19
think that fixed it 
billym@billym-desktop:~$ cd /home/billym/Desktop/
billym@billym-desktop:~/Desktop$ chmod +x ati-driver*.run
billym@billym-desktop:~/Desktop$ sudo ./ati-driver*.run
Password:
Created directory fglrx-install.Qo6147
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.1 and later releases
Removing temporary directory: fglrx-install.Qo6147
billym@billym-desktop:~/Desktop$ 


i got a gui installshield type thing to do there
should i reboot for it to take effect?

---

### Post by maryjanua on 2007-09-19
billym@billym-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 3372
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
billym@billym-desktop:~$

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> i got that driver from ati 
as i said xp and the box it came in say its a radeon x1550 but ubuntu says its a radeon x1300
also ati had no radeon x1550 driver only an x1300 one or x1600 were the closest they had thats the 1300 one

You should probably uninstall the fglrx driver first:
```

sudo apt-get remove --purge xorg-driver-fglrx

```

EDIT: Nevermind, too late.

---

### Post by maryjanua on 2007-09-19
ok purged xorg but it was after i installed that one from ati
is that gonna b a problem?

---

### Post by mysticmatrix on 2007-09-19
> **maryjanua said:**
> think that fixed it 
billym@billym-desktop:~$ cd /home/billym/Desktop/
billym@billym-desktop:~/Desktop$ chmod +x ati-driver*.run
billym@billym-desktop:~/Desktop$ sudo ./ati-driver*.run
Password:
Created directory fglrx-install.Qo6147
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.1 and later releases
Removing temporary directory: fglrx-install.Qo6147
billym@billym-desktop:~/Desktop$ 


i got a gui installshield type thing to do there
should i reboot for it to take effect?

Yes, perform a reboot, and keep your fingers crossed that it works. Linux support for ATI is crappy indeed.

---

### Post by Maestro23 on 2007-09-19
> **mysticmatrix said:**
> Yes, perform a reboot, and keep your fingers crossed that it works. Linux support for ATI is crappy indeed.

After you're reboot, in terminal type:

> fglrxinfo

Should see something like:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6747 (8.40.4)

---

### Post by maryjanua on 2007-09-19
aaarrgghh! whats happened i purged the xorg thing and rebooted and now it wont boot into a grapihical interface at all. im having to use windows to post this!
all i get is a black screen with white txt like msdos asking me to log on to my desktop
how do i get my proper desktop back?
i guess this is the terminal

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> aaarrgghh! whats happened i purged the xorg thing and rebooted and now it wont boot into a grapihical interface at all. im having to use windows to post this!
all i get is a black screen with white txt like msdos asking me to log on to my desktop
how do i get my proper desktop back?
i guess this is the terminal

Login to the terminal and type:
```

apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
reboot

```
If it is complaining about permissions, add sudo in front of the lines.

---

### Post by maryjanua on 2007-09-19
do i have to type reboot? and is there a space after sudo?

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> do i have to type reboot?

The command *reboot* should do just that. 

> and is there a space after sudo?

Yes, but I don't think *sudo* will be necessary. (You will login as root.)

---

### Post by Dan-O on 2007-09-19
AHAHAHAHAHAHAHAHAHAHAHA
<Breathe>
LOLOLOLOLOLOLOLOLOLOLOLOLOL
<Breathe>

This is what I have been struggling with on my Dell Inspiron and Dell Dimension....both with ATI cards x1150 and X1300 respectively.

It makes me crazy.  I still have no 3D effects on either machine.  I know exactly what you are talking about with the black screen, etc.  Same thing happened to me.  Face it man.  Linux and ATI do not play nicely.  After 3 weeks of frustration, I am an expert on installing Linux but, still not any closer to getting everything working proper.  Just going to get out my Windows CD's and be happy again.

So long Linux.  Some day.....some day.....but, not today.

---

### Post by mali2297 on 2007-09-19
> **Dan-O said:**
> AHAHAHAHAHAHAHAHAHAHAHA
<Breathe>
LOLOLOLOLOLOLOLOLOLOLOLOLOL
<Breathe>

This is what I have been struggling with on my Dell Inspiron and Dell Dimension....both with ATI cards x1150 and X1300 respectively.

It makes me crazy.  I still have no 3D effects on either machine.  I know exactly what you are talking about with the black screen, etc.  Same thing happened to me.  Face it man.  Linux and ATI do not play nicely.  After 3 weeks of frustration, I am an expert on installing Linux but, still not any closer to getting everything working proper.  Just going to get out my Windows CD's and be happy again.

So long Linux.  Some day.....some day.....but, not today.

The ATI support will improve, there have been some promising news lately:
[http://ubuntuforums.org/showthread.php?t=548413&highlight=ati+open+source](http://ubuntuforums.org/showthread.php?t=548413&highlight=ati+open+source)

---

### Post by maryjanua on 2007-09-19
no i wont bcos now it says: failed to start xserver  would you like to view  y/n
when i veiw it it means nothing and theres nothing i can change anyway and i have to press esc to exit it  then it says:
xserver now disabled restart gdm when configured correctly 
i select ok and it starts loadin stuff but says WARNING DAZUKO MODULE NOT LOADED
 then loads some other stuff then:starting powernowd...
 /etc/rc2.d/s20powernowd: cannot create /sys/devices/system/cpu/cpufreq/scaling_governor : directory nonexistant
CPU frequncy not supported
then it loads some other stuff and just stops with a flashing cursor

i'm totally lost

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> no i wont bcos now it says: failed to start xserver  would you like to view  y/n
when i veiw it it means nothing and theres nothing i can change anyway and i have to press esc to exit it  then it says:
xserver now disabled restart gdm when configured correctly 
i select ok and it starts loadin stuff but says WARNING DAZUKO MODULE NOT LOADED
 then loads some other stuff then:starting powernowd...
 /etc/rc2.d/s20powernowd: cannot create /sys/devices/system/cpu/cpufreq/scaling_governor : directory nonexistant
CPU frequncy not supported
then it loads some other stuff and just stops with a flashing cursor

i'm totally lost

Strange errors. :-k

Try to boot in *recovery mode*.

---

### Post by maryjanua on 2007-09-19
is it maybe time to fire the cd in again and start from scratch if so at least i'll know how to compile my own audio drivers

---

### Post by Dan-O on 2007-09-19
I feel your pain MJ.

Your write up is like a bad recurring nightmare for me.  For 3 weeks, I have looked at the screen you are looking at and just went through the process of re-installing Ubuntu.

It's not Ubuntu's fault mind you.  Ubuntu is a really squared away OS.  It's driver support, which is a vendor problem...and that is why Linux suffers.  Many people fall off the wagon when trying Linux for the first time for this very issue.  This is my hundredth time falling off the wagon.

---

### Post by maryjanua on 2007-09-19
nice 1 mali i booted i recovery mode and got my root prompt i then typed in the apt-get install xorg-driver-fglrx       etc.
and now i have my desktop back
u really r good at this man:)
but now i get an update prompt near the clock and it iz compiz stuff but it wont go
says to do a partial upgrade and the this 

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

compiz
compiz-core
compiz-gnome
compiz-plugins
libdecoration0

---

### Post by maryjanua on 2007-09-19
also i no longer have desktop effects in applications/system/preferences
its disappeared

---

### Post by mali2297 on 2007-09-19
Are these things resolved?
> 
ive tried that link
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
doesnt help has actually made matters worse now if i boot in gnome rather than x i get everything all over the place and unveiwable


The Compiz stuff are for the desktop effects. You will probably want to get either Beryl or Compiz Fusion instead, so you could as well uninstall the packages that give the errors. (Search for them in Synaptic.)

Also, consider leaving the desktop effects off for now. As some have mentioned, it might give you a lot of headache to try to get them working. There are many other things in Linux that you can explore before going into that venture.

---

### Post by maryjanua on 2007-09-19
its still the same at the logon screen when i right clk options and choose to boot in gnome with xgl the screen is all messed up wut when i boot in xclient script its fine

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> its still the same at the logon screen when i right clk options and choose to boot in gnome with xgl the screen is all messed up wut when i boot in xclient script its fine

The problem is then XGL . You can still run Gnome, otherwise you wouldn't have much of a user interface.

I tried XGL once and experienced the same problems I think. I have an ATI radeon X700 card and I can get Compiz or Beryl working with the open source driver and AIGLX instead. But that won't work with your card.

---

### Post by maryjanua on 2007-09-19
yeah i uninstalled the compiz stuff and installed beryl i can open it but cant seem to make any of it work

---

### Post by maryjanua on 2007-09-20
stiil cant get beryl to do anything. the console opens, i choose cube or whatever, and nothing happens
the only thing i seem 2 be able to get working are the themes in system/preferences/theme
i wish i hadnt bought an ati card

---

### Post by maryjanua on 2007-09-20
just tried beryl again theres no little button or whatever to apply settings how do i do it?
pls help

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> just tried beryl again theres no little button or whatever to apply settings how do i do it?
pls help

Check this Howto:
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
You need to get XGL working first.

---

### Post by maryjanua on 2007-09-20
nope cant make xgl work desktop is all screwed up:(

---

### Post by mali2297 on 2007-09-20
If you don't want to give up just yet, you could make another try with the driver that you got from ATI. Follow Method 2 in this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by maryjanua on 2007-09-20
do i have to unistall the other 1st?
im usin the ati driver just now cos ive clicked the litl enable box

---

### Post by maryjanua on 2007-09-20
i checked to see what driver i was usin and got this
billym@billym-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


 what does the xlib line mean?
also on the applications menu i have the ati catalyst control center but when i click it nothing happens

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> do i have to unistall the other 1st?
im usin the ati driver just now cos ive clicked the litl enable box

No, follow the guide. When you have finished the instructions and rebooted, post the output of *fglrxinfo* again.

---

### Post by maryjanua on 2007-09-20
didnt get far enough to reboot getting a lot of error messages
cant post errors says im using 152 images and only allowed 8

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> didnt get far enough to reboot getting a lot of error messages
cant post errors says im using 152 images and only allowed 8

Huh? :-?

You don't post the output as images, do you? You can copy from the terminal and paste it here as text. But limit the amount, it's enough with the first error message.

---

### Post by maryjanua on 2007-09-20
not sofar as i could see heres the 1st one

billym@billym-desktop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB          
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB       
Get: 3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                    
  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Get: 5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources
Fetched 14.4kB in 0s (18.1kB/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
billym@billym-desktop:~$

---

### Post by mali2297 on 2007-09-20
> 
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems


You can ignore this for now. The next one is:
```

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

```
Note, make it just one line.

---

### Post by maryjanua on 2007-09-20
says everythings already the newest version

---

### Post by mali2297 on 2007-09-20
Alright, let's continue then. If you still got the driver on the desktop, run
```

cd /home/billym/Desktop/
sudo bash ati-driver-installer-8.41.*.run --buildpkg Ubuntu/feisty

```

EDIT:
I think you should replace the driver you had with the one suggested in the guide:
[https://www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run](https://www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run)

---

### Post by maryjanua on 2007-09-20
im downloading the driver u suggested
will i replace the numbers accordingly in the code?

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> im downloading the driver u suggested
will i replace the numbers accordingly in the code?

The line above should work after I edited it. (The terminal replaces * with the appropriate characters.)

...or you could type it as it says in the guide. It doesn't matter.

---

### Post by maryjanua on 2007-09-20
ok says everythin was successfully generated

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> ok says everythin was successfully generated

Then continue with the next steps in the guide. Post the output of fglrxinfo when finished.

---

### Post by maryjanua on 2007-09-20
here is this right before i do anything else

billym@billym-desktop:~/Desktop$ gksu gedit /etc/default/linux-restricted-modules-common
(gedit:27220): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
then loads of stuff it wont let me copyn paste it

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> here is this right before i do anything else

billym@billym-desktop:~/Desktop$ gksu gedit /etc/default/linux-restricted-modules-common
(gedit:27220): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
then loads of stuff it wont let me copyn paste it

As long as the editor opens, you can ignore that message. (I think it's a known bug.)

---

### Post by maryjanua on 2007-09-20
well ive done that and my x is gone again i only get a cmd line thingy no gui
i tried the instructions from last time and they let me get as far as 
aticonfig --initial
then i get errors and it says nothing to do

using windows again:(

---

### Post by mali2297 on 2007-09-20
So you reached all the way here?
> 
Finish the Installation

Now save any open document and reboot your system:

sudo shutdown -r now

In that case, run fglrxinfo just to see the results.

Anyhow, do what is suggested in the guide for restoring the old driver (you don't need to use sudo in recovery mode):
> 
Revert to Xorg driver

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

sudo dpkg-reconfigure xserver-xorg

and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup.

If you can't find "ati", choose "vesa".

---

### Post by maryjanua on 2007-09-20
i have no desktop again says no xserver again i cant do any of that i dont think:(
using xp to post this but iv got my post it notes handy to write any coomands down

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> i have no desktop again says no xserver again i cant do any of that i dont think:(
using xp to post this but iv got my post it notes handy to write any coomands down

You boot in recovery mode, login to a terminal and type the things there. That is:
```

dpkg-reconfigure xserver-xorg

```

---

### Post by maryjanua on 2007-09-20
nope i didnt get that far it said i had to reboot before the next step and its all gone after rebooting i get a terminal and logon scrpit

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> nope i didnt get that far it said i had to reboot before the next step and its all gone after rebooting i get a terminal and logon scrpit

Did you reboot before this?
> 
Finish the Installation

Now save any open document and reboot your system:

sudo shutdown -r now

You must have reached this far if you were following the instructions.

---

### Post by Laurence1000 on 2007-09-20
Hi
I,m a newbie, but I have an ati radeon x1550.
I visited this site:  [http://www.albertomilone.com/](http://www.albertomilone.com/)   and downloaded "Envy".
This is a program that automatically installs the latest ati driver, all dependencies and anything else required.
Now i have the ati catalyst control panel, and everything seems 100%. The only thing is, in my case, I have Ubuntu Studio installed, with only the audio options, so I can't check out all the 3D
effects etc! I now have to figure out how to get compiz downloaded and working (hint hint!!),
Laurence.

---

### Post by overdrank on 2007-09-20
> **Laurence1000 said:**
> Hi
I,m a newbie, but I have an ati radeon x1550.
I visited this site:  [http://www.albertomilone.com/](http://www.albertomilone.com/)   and downloaded "Envy".
This is a program that automatically installs the latest ati driver, all dependencies and anything else required.
Now i have the ati catalyst control panel, and everything seems 100%. The only thing is, in my case, I have Ubuntu Studio installed, with only the audio options, so I can't check out all the 3D
effects etc! I now have to figure out how to get compiz downloaded and working (hint hint!!),
Laurence.

You may look at this thread on compiz
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
And please if you have a question start your own thread. Thanks

---

### Post by maryjanua on 2007-09-20
no mali i got as far as [COLOR="Red"]configure the driver[/COLOR] it tells me to reboot there
iv got my ubuntu desktop back now but i had to manually configure my keyboard mouse and monitor before i got it working 
now my best resolution is 1024x768 whereas before it was 1260x1024

---

### Post by maryjanua on 2007-09-20
yeah that driver worked a treat but i still cant get my res. back up this looks terrible and all clunky i like stuff to look smaller can any1 tell me how to up my res.?

---

### Post by mali2297 on 2007-09-20
[LIST]
Revert this:
> 
Add "fglrx" to the line "DISABLED_MODULES"
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

That is, remove that line.
[/list]

[list]
Open Synaptic. Check "Installed (local)" under "Status". If you've got any local drivers installed (called fglrx or something), uninstall them. Then search for xorg-driver-fglrx and install that.
 [/list]

[list]
Run in terminal:
```

sudo dpkg-reconfigure xserver-xorg

```
and choose the fglrx driver. Also check if you get the option to choose the right resolution.
[/list]
[list]
Finally, run
```

sudo depmod -a
sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv

```
and reboot.
[/list]

---

### Post by maryjanua on 2007-09-20
eh? i dont get that 1st bit the  revert and the box under it?
and in synaptic all the fglrx thingys say they r for my ati card and catalyst control center

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> eh? i dont get that 1st bit the  revert and the box under it?


Open the file with
```

gksu gedit /etc/default/linux-restricted-modules-common

```
Delete the line that you added previously, save and quit.

> and in synaptic all the fglrx thingys say they r for my ati card and catalyst control center

Remove all installed packages with fglrx in their names and then install xorg-driver-fglrx.

---

### Post by maryjanua on 2007-09-20
gr8 stuff mali resolution back to normal and i can almost run in gnome with xgl(at least i can see the desktop) but i'm still gonna use xclient

---

### Post by mali2297 on 2007-09-20
> **maryjanua said:**
> gr8 stuff mali resolution back to normal and i can almost run in gnome with xgl(at least i can see the desktop) but i'm still gonna use xclient

Then we're at least back where we started. I won't help you more tonight, it's bedtime.

---

