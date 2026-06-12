---
title: "X server issues."
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by ATOMIC2 on 2006-05-30
I've installed Ubuntu onto 2 other PC's in my home, and have just installed it onto my main. The installation was successful however when it finished installing and attempted to load the X Server, I recieve the following error message.

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I would copy the output text but it is very long and I doubt my fingers are up to it.

Brief specs of the troublesome PC...
OS: Ubuntu 5.10 i386
CPU: AMD 64 Athlon 3500+
MB: ASUS A8V-E Deluxe
HDD: Seagate 160GB SATA IDE
GFX: ATI x800 GT PCI-E
RAM: 2GB

---

### Post by Sutekh on 2006-05-30
Unfortunately ATI (and NVIDIA) are not very forthcoming on how their cards work. Sometimes only way to get these cards working is to either use the manufacturers proprietry drivers or the community made free drivers. Ubuntu has a commitment to free (as in freedom) software, so they only provide free software solutions. Sadly they are often not completely up to the task, hence X server errors.


When the error dumps you to a command line, log in with your username and password.

You can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 

- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your laptop; your keyboard, mouse/touchpad and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.


  If you get the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL]

---

### Post by ATOMIC2 on 2006-05-30
Thank you very much, Sutekh :KS It's working like a charm. Not a copy of windows in sight and loving every minute of it.

---

### Post by Sutekh on 2006-05-30
[quote=ATOMIC2]Thank you very much, Sutekh :KS It's working like a charm. Not a copy of windows in sight and loving every minute of it.[/quote]
Glad to help out.  Good to see you getting straight into it, so best of luck!

---

