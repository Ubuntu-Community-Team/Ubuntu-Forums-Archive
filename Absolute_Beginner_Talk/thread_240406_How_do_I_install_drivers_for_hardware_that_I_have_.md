---
title: "How do I install drivers for hardware that I have installed"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Hedge6461 on 2006-08-20
I am very new to this I have a nvidia 7900gt a creative xfi platinum sound card and a 3.0ghz pentium d 775 pin on a micro intel d101gc board with 2gigs or ram now I have downloaded and installed ubunto x86 64 or the amd64 version in the choices listed wich is the 64bit as I understand it.  My question is how do you intall drivers I went to nvidia and downloaded the appropriate drives for my video card and the linux 64bit operating system but when i click on them at my desktop I get a could not open because its not a binary file now on nvidias web page they say to type "sh nvidia-linux-x86_64-1.0-8762-pkg2.run" but nowhere does it say where to type this information i tried it in a terminal but i may not be entering it correctly.  My secound question is, is the xfi card even supported with linux according to there website its not ther is no open source driver for this card so if that is the case do I have to change speaker plugs everytime I switch between windows and linux.  Finally how do run any type of program I inserted a battlefield two disc just to see if I can run it and I cant it gives me an icon labed bf2cd1 but i cant do anything with how do install bf2.  I just dont understand at all how to use this software and any help offered would be much appreciated or any links to some basic knowlege that I can understand.  It seems to me that most of these forums and help guides assume you know something about linux I know absolutly nothing so please be very detailed with any help thank you so much again.

---

### Post by pollock.tar.gz on 2006-08-20
for the nvidia drivers try this: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

but for your battlefield 2 issues...you can try installing wine but i doubt you will be able to get it working...

tell me how installing the drivers go though.

---

### Post by %hMa@?b&lt;C on 2006-08-20
if I were you, I woudl use Automatix.  It got my nVidia card up and running really quickly!

---

### Post by Hedge6461 on 2006-08-20
thank you for your quick response I couldn't even reboot into windows before you answered me I will try these right away thanks alot

---

### Post by nalmeth on 2006-08-20
[http://appdb.winehq.org/appview.php?iAppId=2424](http://appdb.winehq.org/appview.php?iAppId=2424) 

Looks like battlefield 2 won't run in wine. If you really want to play it, you can try out Cedega, but to get the full version for good, you'll have to pay 15 bucks.

To install your Nvidia Driver, copy the following commands (one at a time) into the terminal:
sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable

EDIT: I like the kenny tux avatar! Good job!

---

