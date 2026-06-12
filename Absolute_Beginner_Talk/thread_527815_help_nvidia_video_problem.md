---
title: "help nvidia video problem"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by archangel1701 on 2007-08-17
Hi can anyone help me I am a Newbie with ubuntu feisty and I tried installing drivers for a nvidia 8800gts I need help I understand how to unload the x drive and I have done so. can anyone tell me what are the latest drivers. and how to install them once I get the command prompt

---

### Post by mikewhatever on 2007-08-17
The best way to install nvidia driver is to use the Restricted drivers manager, located in System>Administration.

---

### Post by archangel1701 on 2007-08-17
i already tried that then i received a screen that said something like nivida driver not found etc and it took me to a screen were it asked me for my password then there was the command prompt i looked around and found some info like typin wget [http://us.download](http://us.download) etc etc etc it found the website but it said error 404 not found the instructions i found were from may of 2007 so i must be typing in the old drivers or something

---

### Post by ZipoTe on 2007-08-17
Restricted Driver manager gives some problems so you have to use the latest drivers which are not on the repos. You should go to nvidia website and download them, follow the instructions that are there and enjoy your card! :)

---

### Post by Amazona aestiva on 2007-08-17
This usually works:
```
sudo apt-get install nvidia-glx
```

---

### Post by archangel1701 on 2007-08-17
nope i tried that earlier i get a message xserver not working or something like that. Is there a veteran in the house or someone who has had the same problem please im desperate

---

### Post by ZipoTe on 2007-08-17
Ok, let's see. 

First, explain your problem correctly :-P what's exactly the matter? You can start your X session but without nvidia drivers, or you are not able to start any X session or what...

---

### Post by RomeReactor on 2007-08-17
Hi. As far as I know, the 8800 GTS doesn't work with the **nvidia-glx-new** driver from Syanptic, as it is a little outdated; download [this driver]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run") (here's [the actual page]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") so you can get more details) and download it to your desktop. Once it finishes downloading (make sure it **did** download to your desktop), press CTRL+ALT+F1; this will get you out of X (the display) and to a command line. Now enter the following:
```
sudo /etc/init.d/gdm stop
```
to stop the X server; then:
```
cd Desktop
```
then:
```
sudo chmod +x NVIDIA-Linux-x86-100.14.11-pkg1.run
```
to make sure the file is marked as executable;
```
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```
to run the installer. If after this you're not returned to your desktop, 
enter this:
```
sudo /etc/init.d/gdm start
```
to start the X server again; or:
```
sudo reboot
```
to reboot.

Sorry about the previous formatting; had to use w3m to post.

---

### Post by archangel1701 on 2007-08-17
sorry guys barely came back on the problem is that I get a message that saids that x cannot be found because nividia driver not found then it gives me the command prompt I am not able to get to my desk top:(

---

### Post by r4ik on 2007-08-17
try,

sudo dpkg-reconfigure xserver-xorg

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Control-Alt-F7 to get back to graphical mode and then Control-Alt-Backspace to reset the X server (so your changes can take effect). 

Good luck !

link,

[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

---

### Post by Hobo Joe on 2007-08-17
Get Envy.
Install through the command line by running this command:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

```
Then run these commands:
```

cd /home/<username>

dpkg -i envy_0.9.7-0ubuntu8_all.deb

envy -t

```
The once you have it running(with the envy -t command) select uninstall nVidia driver, then once it's done install the nVidia driver. Make sure to let it configure X for you.

---

### Post by ZipoTe on 2007-08-18
If you use envy, remove any installation you have done because can get errors.

---

