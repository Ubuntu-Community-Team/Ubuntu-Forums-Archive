---
title: "Nvidia GeForce4 MX 420 driver issues"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by kouya77 on 2007-12-08
Hi,
I am using Nvidia GeForce4 MX 420 graphics card on gutsy. Do I have to install drivers for the card? If so, how? (I cannot enable desktop visual effects and my screen tend to lag when playing videos) 
Also, the graphics card is listed on the "Restricted Drivers" window. I tried enabling it but it claims that "The software source for the package nvidia-glx is not enabled". What does that mean?
Help will be greatly appreciated!

---

### Post by Partyboi2 on 2007-12-08
Easiest way to install restricted drivers for nividia is using envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by bumanie on 2007-12-08
If you don't decide to use envy (which is not supported by ubuntu), you will have to go to the nvidia site and download a linux driver suitable for your graphics card. This should be under the legacy tab. Agree to the nvidia terms, download then run file. In your case it should be NVIDIA-Linux-x86-96.43.01-pkg1.run
Ensure you have build-essential installed. Go to terminal and type in sudo apt-get install build-essential --> enter
If you download to your desktop, type cd ~/Desktop --> enter
Next you will have to type
sudo /etc/init.d/gdm stop --> enter
Next install the driver (if on your desktop), in terminal type
sh NVIDIA-Linux-x86-96.43.01-pkg1.run --> enter
answer all the questions and nvidia should build the driver via their ftp site - so answer yes when it asks whether you want to go to nvidia's ftp site. Once installed, type
sudo /etc/init.d/gdm start
Your graphics card driver should be installed.

---

### Post by kouya77 on 2007-12-08
Thanks for the replies!

I have installed the driver, however whenever I attempt to change my Screens and Graphics settings and restart the computer I am always notified that the system could not detect my screen and graphics card. The system will then boot into "low graphics configuration" mode. How do I remedy this?

I have tried correcting the configurations in System > Admin > Screens and Graphics, but when I apply these changes, the configurations somehow revert back to the previous ones.

---

### Post by rdavidso on 2008-01-20
I am having the same error - "The system will start in low graphics mode". Does anyone know how to solve this?

---

### Post by later on 2008-02-26
if some one know the solution don't hesitate 'cause i hav the same problem plz help

---

