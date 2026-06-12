---
title: "How do I install programs without an internet connection?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ricci on 2007-01-18
Hello guys. Im quite new with Ubuntu and really like its fast interface. But it is still in its 'stock' mode and I want to juice it up with some cool programs.

I tried to install some downloaded .tar.gz from my USB and unpack it but with no avail. I was only sucessful on 'themes package only'

I really wanted the program VLC PLayer as I watch a lot of videos. But on Synaptic Package Manager, it says that you must have a network connection, which I do not have on my Ubuntu machine. What I can i do is download it to my USB which I rent from a cafe using WinXP.

Can you help me on the step by step installation basics? also do you have any more audio players that can play MP3's or even movie editing programs that can be installed on the mentioned process? Thank you for your help :-)

---

### Post by Sasa_Ivanovic on 2007-01-18
it would be a lot easier if you had internet connection, anyway it isn't complicated :
download the *.deb package of the programs you want, and then run them on your workstation.
use Mplayer ( it's very good ) and also download GStream for playing commercial formats.

---

### Post by mikewhatever on 2007-01-18
You'll benefit from this:
[http://ubuntuforums.org/showthread.php?t=332680&highlight=tar+files](http://ubuntuforums.org/showthread.php?t=332680&highlight=tar+files)

---

### Post by kingmonkey on 2007-01-18
Do you mean you have no internet connection?

These site might be usefully for you:

[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

[http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)

---

### Post by aysiu on 2007-01-18
I've retitled your thread to more accurately address your problem.

Can you explain a bit more about your internet situation? You obviously have a connection somewhere--just not on Ubuntu. Is it a Windows computer? Is it nearby? How are you transferring files, via USB key? What kind of connection do you have--ethernet, wireless, dial-up? Can your other machine (the one that is connected) boot a Ubuntu CD?

---

### Post by ricci on 2007-01-18
thank you aysiu.i live at our company accomodation here in saudi arabia.i have a new assembled pc at my room only, it can dual boot using Ubuntu & XP. Of course in a cafe, there are no CD-ROM (USB only and quite far). My own terminal at the office i think can boot on Ubuntu. this also has an internet connection (RJ45, could be T1). On my terminal that is where i downloaded the Ubuntu CD and i can transfer files also from the USB.

So that is it. Network connection here also is very strict as you are filtered with a private and government firewall.

I have this option and i hope it would help, i have some acessories like HD-IDE to USB case wherein i put my IDE drives and can be read via USB. Is it possible I can download the appropriate files on the HD of my assemble PC installed with Ubuntu? 

Thank you again :-)

---

### Post by aysiu on 2007-01-18
> **ricci said:**
> My own terminal at the office i think can boot on Ubuntu. this also has an internet connection (RJ45, could be T1). On my terminal that is where i downloaded the Ubuntu CD and i can transfer files also from the USB. If this can boot a CD, boot the Desktop CD on it. Then, in the terminal, type ```
sudo aptitude clean
``` This will clear out a cache of already installed programs (if there even is one). Then install whatever you want ```
sudo aptitude update
sudo aptitude install vlc
``` (You need enough RAM to hold the "installed" program). Finally, copy the .deb files from /var/cache/apt/archives to a USB key. Then copy them from the key to the desktop of your Ubuntu computer at home. To install them, do ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by ricci on 2007-01-19
Ok ill try.ill give u an update soon. thank you

---

### Post by ricci on 2007-01-20
Hi again, before trying to boot up my company pc with Ubuntu, would it detect the same network configuration present in the system? I want to know from your side before i try it :-) (but still i will do it soon). In my XP machine, i have to log-in and that is the time I can connect to the network and all.

as you said, i must have enough RAM, i have 512 MB.

as mentioned on the command:

cd ~/Desktop
sudo dpkg -i *.deb
So it means I have to paste all the .deb files on the desktop right? So synaptic cannot search for these files automatically.

Thanks again for the info,

---

### Post by K.Mandla on 2007-01-20
If your company uses DHCP (in other words, if your network assigns the address to your PC), it should be able to find the Internet. Of course, every network is different, so it's almost impossible to tell if you're going to have any luck with that. You'll have to talk to your IT staff, and even then you should keep your fingers crossed.

512Mb is plenty of RAM.

Usually when you download a file it will be downloaded to your desktop -- unless you tell it to put it somewhere else. If you see it on your desktop (it will probably look like a tiny cardboard box :D ), you can just double-click on it and it should start the installation process.

---

### Post by ricci on 2007-01-20
Arigato Mandla-kun, hehe ill try and keep my fingers crossed :-)

---

### Post by ricci on 2007-01-21
waah :frown: booting was not successful. first the mouse was working and the keyboard's not. 2nd try, too much error messages are coming like hda1 was not found; VLF error, etc. I have an HP Compaq DC 7600 at the office.

Can you give me a good hack wherein I can download the package under WinXP and install it on my Ubuntu system?

Still the same VLC Player i need to be installed. hope you can help and sorry for troubling you.

---

### Post by ricci on 2007-01-22
Hi guys. maybe i will try the simple part of installation. i downloaded MPlayer and i think there is one file missing. How can i get this so that i can install the problem successfully? thank you.
still i have no internet,whatsoever, such a sad thing really.

---

