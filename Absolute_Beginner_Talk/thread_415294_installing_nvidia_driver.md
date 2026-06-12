---
title: "installing nvidia driver"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by BlackBar on 2007-04-20
:confused: ok i have been trying to install my nvidia driver for  some time now but i keep hitting the same road block again and again this is how i try install it first i go to this page  [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html) then download and save the driver to my desktop and open it and get this message  Could not open the file /home/kevin/Desktop/NVID…nux-x86-1.0-9755-pkg1.run. gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again then i read on and see that i have to type this command and then i get this message  sh NVIDIA-Linux-x86-1.0-9755-pkg1.run  and hers the message  kevin@kevin-desktop:~$ sh NVIDIA-Linux-x86-1.0-9755-pkg1.run sh: Can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run kevin@kevin-desktop:~$  i cant get this to work  can some one please help i have no idea what im doing :lolflag:

---

### Post by rai4shu2 on 2007-04-20
See this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Or if you want to build a proper package:

[https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx](https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx)

---

### Post by Nik_Doof on 2007-04-20
Or you can use [Envy](http://albertomilone.com/nvidia_scripts1.html), if your not using Feisty that is.

---

### Post by tommyp on 2007-04-20
I would definitely do a search for "envy", which is an awesome script that automates the installation for the nvidia driver.

---

### Post by linuxfan3 on 2007-04-20
At first: please do ALWAYS use the searchfunction before posting problems. Your problem has been already considered. THX
Use frontend for packagemanaging like synaptic in "System"->"Administration".
search for "nvidia-glx" 
install package and reboot
Optionally use apt in terminal with command "sudo apt-get install nvidia-glx"
Please report, if it worked out.

have fun!

---

### Post by rajeev1204 on 2007-04-20
Hi

before u type the command in terminal you have to change directory to desktop cos u have saved the file to desktop .

type "cd Desktop" in terminal

then run 'sh packagename"


But i suggest you install nvidia from package manager 

go to main menu > system > administration > synaptic

Search for nvidia-glx-new if u have a  newer card 


regards

rajeev

---

### Post by bodean on 2007-04-20
> **rajeev1204 said:**
> Hi

before u type the command in terminal you have to change directory to desktop cos u have saved the file to desktop .

type "cd Desktop" in terminal

then run 'sh packagename"


But i suggest you install nvidia from package manager 

go to main menu > system > administration > synaptic

Search for nvidia-glx-new if u have a  newer card 


regards

rajeev

I downloading/installing the glx-new right now. See if that works and allows me higher resolution and refresh rates. Does anything need to be done/run after this downloads/installs? Or just reboot?

---

### Post by Seisen on 2007-04-20
This might help.

[http://ubuntuforums.org/showthread.php?p=1399268]("http://ubuntuforums.org/showthread.php?p=1399268")

---

