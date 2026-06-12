---
title: "Need some major help."
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by python02 on 2005-06-07
Well heres goes, I just starting to use Linux again after about 5 years. I came across Unbuntu and installed it. After I installed it all, I dud updates and add'd extra repositories. And updated and upgrade'd again. after about 600 download and installs, I install Graphics Driver (NVIDIA). Then I installed and added xine-ui, J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox, install Multimedia Codecs's and DVD playback. After each install i used to command "killall gnome-panel" to refresh the OS. I restarted my computer and check everything again. Then I was happy and was read to get a p2p program. 

I installed LimeWire, and didnt like it cus it was only downloading at 1kb/s-10KB/s. Way to slow. So then I installed aMule, It wouldnt ever connect keep giving me a error when downloading the server list. So I was like i will try one more, so I installed Azureus. I did the "killall gnome-panel" command, and it really killed it this time. It never came back. After about 30 mins, I decied to reboot and use the recovery mode in Linux on the boot option. It did help after load it came to black DOS like screen and said "login:" no GUI or gnome. I was like what? So I rebooted my computer again and login into normal mode, and got the same thing. How can I get the GUI and gnome-panel to load up?

sorry about the lenght, but wanted to let you know EVERYTHING. I mean it was all working fine, graphics card, and everything till i "killall gnome-panel" that last time. 

Thanks you,
-Python

---

### Post by mtron on 2005-06-07
hi! 

let's start with the first problem: the Xserver
when you boot up ubuntu in the normal mode what is the displayed error? 
and: paste the file /etc/X11/xorg.conf here. 

(if you can ony boot in windows, install [this](http://ubuntuguide.org/index.html#readlinuxpartitionsinwindows)  to read linux partitions in windows)

---

### Post by python02 on 2005-06-07
1) when I boot up ubuntu, there is no error. It just loads like basic hard code linux. 
Its just boots up in like MS-Dos. and stays there and asks me to login to Ubuntu. I can log in that way. But theres no OS.



2) file /etc/X11/xorg.conf
 I do not have a xorg.conf file in the /etc/X11/
I can only boot in windows, and I use the program you listed to search my linux partition. *thanks for this*

---

### Post by N'Jal on 2005-06-07
Have you tryed logging in and typed GDM? Whenever Gnome crashes for me if i get thrown into the bash shell i just type gdm and it mostly loads gnome back. Some times it does not but mostly it does

---

### Post by python02 on 2005-06-07
Nope N'Jal GDM didnt work. But thanks  ;-)

---

### Post by mtron on 2005-06-07
ok, so gdm and the xserver are insalled? 

(just run "sudo apt-get install gdm xserver-xorg ubuntu-desktop" to see if you have all the needed stuff)

what is the output of "sudo dpkg-reconfigure xserver-xorg" and can you run "xorgconfig" ?

if it is ok, type "startx"

this will display a error, then post here the error and this 2 files:
- xorg.conf (see post above)
- /var/log/Xorg.0.log (or just Xorg.log)

---

