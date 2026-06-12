---
title: "X server won't load"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by rayfossey on 2006-05-28
When I install Ubuntu I can achieve a comomand line only, the x server won't load giving an error about graphics configuration (?) .  Does anyone have any ideas what the problem is or how to correct it?

Thanks

---

### Post by Sutekh on 2006-05-28
What sort of graphics card do you have?  NVIDIA or ATI?

Unfortunately NVIDIA and ATI are not very forthcoming on how their cards work. The only way to get these cards working is to either use the manufacturers proprietry drivers or the community made free drivers. Ubuntu has a commitment to free (as in freedom) software, so they only provide free software solutions. Sadly they are often not completely up to the task, hence X server errors.


Anyway, this error should leave you at a command line where you can log in with your username and password.
  
Once logged in, you can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 

- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.


 - If you use NVIDIA and all this works out then you can consider installing the proprietry NVIDIA drivers for your card. You can read all about it here

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is by far the easiest method, and will install the Ubuntu repository NVIDIA drivers (v7667)

 - Method 2 is a little harder and can be used to install any version of the proprietry NVIDIA drivers.


 - If you use ATI and have got the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL]

---

### Post by rayfossey on 2006-05-28
Thank you - I will find out which graphics card it is.  Thank you for your prompt advice.

---

### Post by NT4usB on 2006-05-28
noob here. I'll be watching this thread as well. 
I used method 2 listed above to install the latest (8762) drivers and was able to restart gdm at the end of the process with what appeared to be a fully functional card. I could view and change the nvidia x server settings, etc.
Unfortunately, first time I restarted the box, xserver blew up. 
Editing xorg.conf to vesa allowed gdm to start.
Apparently, as long as I never restart the box, I can run the nvidia drivers.

---

### Post by NT4usB on 2006-05-28
found my solution at
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

Big thank you to Alberto Milone!

---

