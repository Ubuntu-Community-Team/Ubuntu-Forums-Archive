---
title: "[SOLVED] nvidia fx5200 3d capabilities, creative modem blaster de5625 and other noob"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by gothdaddee on 2007-11-13
good day to everyone!

i am a noob in linux and i am very much willing to get used to it.  i have been a windows user (with extensive experience in DOS commands which i got familiar to even before windows 3.x).  i wish to migrate to ubuntu and i don't mind having to deal with command lines.  the following is my set up:

   Processor:           AMD Sempron 2800+
   Motherboard:      ECS 760GX-M
   Graphics Card:    NVIDIA GeForce FX 5200
   Memory:             256MB DDR
   Monitor:              BOKA 54H 15" CRT
   Modem:               Creative Modem Blaster DE5625 External (Serial Port)
   Printer:                Epson Stylus CX3700 (Printer/Scanner/Copier)

right now i installed edubuntu gutsy gibbon on a separate hard drive to try it out first.  i am planning to use edubuntu for my kids and eventually multi-boot with ubuntu for myself.  i have winxp installed on my other hard drive that i switch to so that i still have a workable system while i am still trying to figure things out in ubuntu.  i haven't done multi-boot with winxp yet because other members of the family are also using the pc and they might get confused with the new set-up.

my first problem was that the screen resolution was only 800x600 max.  i searched the forums and thankfully, it was solved by manually entering the horizontal and vertical frequency of my monitor. now i can use 1024x768.

my epson printer worked perfectly out-of-the-box.  even the scanner worked fine without having to do additional tweakings.

now i got into a deadlock.  i can't seem to make my modem to work.  i was able to configure it (i think) using

$ sudo pppconfig

i tried to dial it using 

$ pon

it then makes the familiar modem sound of connecting.  after the sound, i'm not sure if i got connected to the internet or not.  i tried to browse google with firefox but it seems that i still wasn't connected to the net. i got that familiar error screen that i get when i try to browse without the net connection. i also tried to configure using System>Administration>Network but somehow this method doesn't even give me the familiar modem sound.   could you help me with this please. also is there a way that i could know if i am already connected or not just like the blinking pc's in the windows tray (i'm sorry for comparing but i was just hoping that there will be some sort of indication of modem activity).  is there also a way to make connecting and disconnecting from the net with dial-up modem easier like an icon on the desktop or something so that my wife and kids could use the net the way they usually do?  i am still using dial-up because broadband isn't available yet in my location (waaah! this country is so poor!) so i should only connect to the internet whenever i need to and disconnect when i don't need to.

another problem is the 3d capabilities of my graphics card.  it seems that i need to use the nvidia-glx-new to be able to enjoy this.  i downloaded the nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb but i don't know how to install it.  i could not use the 

$ sudo nvidia-glx-new enable

nor the restricted drivers in System>Administration since i couldn't connect to the internet in edubuntu.  i tried to run the nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb file i downloaded but it gives me the message "Dependency is not satisfiable: nvidia-kernel-1.0.9755."  is there a way that i could install the drivers i downloaded without the internet connection?

can i also install multimedia codecs without the internet connection or can i install vlc and other open source media players instead?

my family will only use the usual office suite, kiddie games, internet browsing, music, movies and stuff so i think what the graphic interface of ubuntu can handle is enough.  While for me, i don't mind executing command lines to make things work.  thanks in advance for the help!

---

### Post by alienexplorers on 2007-11-13
You can try in the terminal:
> sudo apt-get install nvidia-glx-new
You can then run in the terminal
> gksudo nvidia-settings

---

### Post by gothdaddee on 2007-11-14
thanks alienexplorers! i will try that later when i get home, i am still in the office (heehee!) do i need to put the nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb file i downloaded someplace before running the commands or no need to?

---

### Post by marcelinoM on 2007-11-14
The easiest method to install the FX5200 driver is use the restricted manager included with Ubuntu.

System -> Administration -> Restricted Drivers Manager.

It will list your FX5200 card and install the correct driver.  The method your trying is fine if you know the difference between Nvidia cards.  Nvidia has 3 Linux drivers depending on the model.   I have FX5200 on two computers and that's the method I used.  Ubuntu actually launched the Restricted Driver Manager when you first installed it but you probably clicked it off without understanding what it was asking.  

Sorry, I can't help you much with the modem but I think it is software modem (also know as winmodems).  Winmodems are low cost modems which use OS to handle communication.    Ubuntu supports some winmodems with "restricted drivers".  If your lucky and they are supported, the Restricted Driver Manager" will list your modem.

---

### Post by Partyboi2 on 2007-11-14
> "Dependency is not satisfiable: nvidia-kernel-1.0.9755."The nvidia-glx package needs some other packages installed for it to work.


---

### Post by gothdaddee on 2007-11-14
marcelinoM, maybe i did overlook that restricted drivers manager during my install. i'll try it again later. in fact i will try all the possible solutions to get it working! i'll post here what worked if ever i am successful.

about the modem, i searched the forums and from what i understand, external modems (especially the ones connected via serial port) are not winmodems.  please feel free correct me if this is wrong. anyway, i hope that i get several solutions to try for this.

to Partyboi2, may i know specifically what are the other packages?

thanks again to everyone, right now i'm just collecting all the possible solutions and then later try them all out when i get home.  so everybody's suggestions are most appreciated.

---

### Post by gothdaddee on 2007-11-14
if ever i get my modem to work (hopefully someone could help!), is there a way i could place an icon like in the desktop or somewhere easily accessible so i could easily connect or disconnect to the internet without entering commands in the terminal?  This will be for my wife and kids to use.  and is there also a way that i could be informed if i am already connected to the internet or not and if there is modem activity already like the blinking icons in windows tray?

if anyone could also help me on how to make my modem work (please see the first post of this thread for full description of the problem), it will be very much appreciated.

thanks to all!

---

### Post by gothdaddee on 2007-11-14
good day! here is what happened.  I entered the commands you suggested and i got the following error:

$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

then blindly hoping that something might happen, i did this and got the response:

$ sudo nvidia-glx-new enable
sudo: nvidia-glx-new: command not found

---

### Post by gothdaddee on 2007-11-14
good day! i tried again with the restricted drivers manager but it said the nvidia-glx-new must be enabled first. so i went to the terminal and did this:

$ sudo nvidia-glx-new enable

i got the reply

sudo: nvidia-glx-new: command not found

i also tried nvidia-glx-config enable (i saw this from another post in the forum) and i got the same response.

---

### Post by alienexplorers on 2007-11-14
Do you have all your repositories enabled?  If not try enabling them and retry the sudo apt-get install nvidia-glx-new command.

---

### Post by gothdaddee on 2007-11-14
anyway, i got to searching google also and i downloaded NVIDIA-Linux-x86-100.14.19-pkg1.run from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) placed it in my home directory and ran the following commands:

$ sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

then it started executing some actions and finally displayed an error message that said my xserver is still running and i must stop it before i could proceed.

is it good to use the file i downloaded from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) or should i not use it?

if not, i already have the file nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb with me, is there a way to install it offline (because i still can't get my modem to work)?  i tried to run it but i got the dependency error i mentioned in my previous post.

how do i stop the xserver from running in case i could use the package from the nvidia site?

thanks again in advance!

---

### Post by gothdaddee on 2007-11-14
may i ask how to enable all the repositories? 
i apologize if i keep asking even simple questions, i hope you understand.
thanks again in advance!

---

### Post by alienexplorers on 2007-11-14
go to system>administration>software sources.  Check to see if everything on the first page is checked except the part about the cd-rom.

---

### Post by gothdaddee on 2007-11-15
wahoo! now everything's working just right!

i was looking in the wrong direction. i was thinking that my problem with the nvidia and my modem were not related!  last night i left my nvidia problem because i ran out of things to try.  i decided to attend to my modem problem instead and followed bartender's advice ([http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)).  I downloaded gnome-ppp for gutsy ([http://packages.ubuntu.com/gutsy/net/gnome-ppp](http://packages.ubuntu.com/gutsy/net/gnome-ppp)) and installed the package and got my modem to work.  i tried the GUI method (System>Administration>Restricted Drivers Manager) and there you go! it started downloading and enabling the nvidia drivers! the modem was the key to my problems! i was looking for a solution in the wrong way!  hah! my dad would've told me: "if that (the thing i'm looking for) were a snake, it would've bitten you already!"

thanks everyone for your suggestions! you were all pointing me to the right direction all along i probably just wasn't paying much attention.

thanks again and now it's time for me to get to workin'!

---

