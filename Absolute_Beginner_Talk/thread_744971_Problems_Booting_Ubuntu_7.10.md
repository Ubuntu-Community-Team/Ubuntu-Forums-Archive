---
title: "Problems Booting Ubuntu 7.10"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by MAD_JIHAD on 2008-04-04
Ok heres what happened first i installed Ubuntu from the live cd which i had problems doing and i had to replace some command quiet with acpi=off or something like that, so i got the live cd to work then i installed Ubuntu on the computer on a fresh drive. Now the problem is when i try to boot up my computer i see the Ubuntu logo and the progress bar gets to like around 90% or a bit higher and then it stops and nothing happens?  im kinda new to Ubuntu so detailed help would be much appreciated, TIA.

 i have run memtest and got no errors.

The specs:
amd 64 3200+
1 gig of ram
nforce 3 main board
9800 pro
WD 500 gb HD

---

### Post by TeoBigusGeekus on 2008-04-04
Are you connected to the internet during installation? I had the same problem during some installations I attempted, but when I connected the pc with a router the installation downloaded some recent updates from the net and everything went smoothly.

---

### Post by MAD_JIHAD on 2008-04-04
nope i didn't have the pc connected to the internet ill try it now.

edit: should i reinstall (with internet connection) because its  a clean version so might as well right?

---

### Post by TeoBigusGeekus on 2008-04-04
Have your router configured i.e. username, password etc. and do a complete reinstallation.

---

### Post by tangibleorange on 2008-04-04
If you could press Ctrl+Alt+F1 when your machine starts to boot, it shows what's happening behind the boot splash screen. this should enable us to see what is jamming the machine.

---

### Post by MAD_JIHAD on 2008-04-04
Ok im reinstalling while its connected  to the internet once im done that then ill try the ctrl+alt+f1 thing while it boots up.

Edit: Ok i have reinstalled it with an internet connection, and while booting up i pressed Ctrl+Alt+F1 and i saw a bunch of really fast scrolling text followed by "[OK]" and then the screen went black while the text was scrolling.

---

### Post by bumanie on 2008-04-04
Sounds as though you should try the alternate cd, which is text based and tends to have less conflicts. Go here and check the alternate cd under start download [http://www.ubuntu.com/GetUbuntu/download]("http://www.ubuntu.com/GetUbuntu/download")

---

### Post by MAD_JIHAD on 2008-04-04
Thanks i will try that after its done downloading.

Edit: Yay thx its working now and running off the HD fine, i wish i had known about the alternate CD earlier :D

Edit: bah it keeps freezing around 5-10 seconds after i log in. :(

---

### Post by MAD_JIHAD on 2008-04-04
I'm officially stumped.

---

### Post by bumanie on 2008-04-04
Have you installed ubuntu via the alternate cd? If so I assume you mean that your session stops after 10 seconds. Is that correct? 
Have you tried booting into safe mode? It is worth trying because if you are in the system, someone may be able to help you sort out your problems. An initial suspect is the ATI gpu. ATI don't seem to integrate as well as nvidia do. It could be other things though.

---

### Post by MAD_JIHAD on 2008-04-04
> **bumanie said:**
> Have you installed ubuntu via the alternate cd? If so I assume you mean that your session stops after 10 seconds. Is that correct? 
Have you tried booting into safe mode? It is worth trying because if you are in the system, someone may be able to help you sort out your problems. An initial suspect is the ATI gpu. ATI don't seem to integrate as well as nvidia do. It could be other things though.

Yes i installed it via the alternate CD, yes my session stops after 10 seconds.

How do i boot into safe mode?

Edit: do u mean recovery mode? cause i can boot into recovery mode.

---

### Post by bumanie on 2008-04-04
I guess I mean recovery mode, I'm on awindows machine at present so can't check exact terminology and my memory is not what it once was.
suggets that you boot into recovery mode. As i don't have an ATI card, I have no experience trouble shooting one. First thing to try is to install the ATI card through restricted drivers manager. 
System --> Administration -->  Restricted drivers
Assuming you have internet connection it should download a driver for you. Just supply password when asked.

---

### Post by MAD_JIHAD on 2008-04-05
theres no gui in recovery mode its just straight text so i don't know how to get to the restricted drivers module from the command line.

---

### Post by bumanie on 2008-04-05
In that case you will have to install it via command line. I have installed nvidia drivers that way, but have no experience with installing ATi drivers. I'll do a bit of searching and see what I can come up with. But hopefully there will be someone else who knows and can provide instruction, ie someone who has successfully done it.

---

### Post by dstew on 2008-04-05
> theres no gui in recovery mode its just straight text so i don't know how to get to the restricted drivers module from the command line.It sounds like you are having display driver problems. From the recovery mode command line, you can re-configure your xserver, the software that runs your display, to get a useable desktop.

Boot in recovery mode, log in, and at the command line enter this command:```
sudo dpkg-reconfigure xserver-xorg
```This runs you through a text-based reconfiguration of the desktop. Answer the questions the best you can (read the explanations). Usually the default answers are correct. When you get to the part about the display, choose the **vesa** driver. When you are done reconfiguring, enter```
startx
```and you should get a useable display. (Note: if startx gives you an error, try the key combination ctrl-alt-backspace).

Once you have a useable desktop, update your system (System --> Administration --> Update Manager). Then, check the System --> Administration --> Restricted Drivers Manager to see if you can install a restricted driver for your display.

---

### Post by bumanie on 2008-04-05
Jusr found this old forum thread, it may help.
On my A64 machine I have a Radeon X850XT-pe I have to install fglrx just to get xwindows.
I installed from the 64bit alernate CD
then rebooted - It came to a locked up X-session 
Then ctrl+alt+F1 to get a console
Then sudo nano -w /etc/apt/sources.list , then unhashed the universe & multiverse repositaries & ctrl+o to save & ctrl+x to exit.
Then sudo aptitude install xorg-driver-fglrx (it should pull the restricted modules in if they are not installed already )
Then sudo dpkg-reconfigure xserver-xorg & when it comes to the driver part put the fglrx drivers in .
then reboot -n
This will get xwindows up but most likely not 3D.
once you have x up you can follow one of the how to guides and install the fglrx drivers fully 
This is a bit quick and dirty but has worked for me from breezy to edgy on this machine - just to get it up and running .
This only works on the alternative install !
edit:- this card will not work with "vesa" or "vga" drivers (it is PCI-e)
from here [http://ubuntuforums.org/showthread.php?t=289853](http://ubuntuforums.org/showthread.php?t=289853)

---

### Post by MAD_JIHAD on 2008-04-05
Thanks guys, looks promising ill give it a try.

---

### Post by MAD_JIHAD on 2008-04-07
It seems to be working now, all i changed was the driver to "Vesa" and that seemed to do the trick.

Thanks everyone that helped me, i hope this is the last of my problems lol.

---

