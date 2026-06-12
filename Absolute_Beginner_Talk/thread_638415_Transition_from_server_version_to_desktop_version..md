---
title: "Transition from server version to desktop version..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by cpuman on 2007-12-12
ok well i have searched alot through the forums and have yet to find what i need, ok well i know absolutely nothing about linux at all, windows im fine at, but not linux. ok well the reason i am getting linux is so that i can run a server, server requires linux, well after searching around, i find a site that helps me choose a distro of linux thats right for me, well it leads me to ubuntu so i decide to go with the flow on this. well i did something stupid i think, i installed the server version and i cant login with the password i made, i even tried going back and trying the repair function to basically break my way into the setup of it and i added another user that way, still cant log in. also im a GUI user, text isnt my friend, i know dos commands fine but linux is a completely new deal. also i dont know if its supposed to be like this but when i try to put in information for the password, nothing shows up, no *'s or anything. i figure it might be a safety feature, like its imputting but not showing so that people behind you have a harder time finding out your password? ok well back to the point, i need to switch to the desktop version, i downloaded the iso, burned it, booted and it works fine, BUT everytime i go into any options past the selection menu, my monitor goes black, stays that way, and then acts like the pc is off ( light when functioning normall is green, but when pc is off and monitor is on its yellow) and the light becomes yellow, im redownloading the desktop iso again, figured it might be a currupted download, either way please help me out on this. im running it as a dual OS with windows xp pro x64 edition

---

### Post by Rocket2DMn on 2007-12-12
Yes, it is a safety feature - it is taking your password.
Once you turn on the computer and you think it should be loaded, your screen is blank.  This is probably because of the video driver.  What kind of video card do you have?  At the blank screen, you can do CTRL+ALT+F1 to get to a tty (an extra command line area).  In fact, F1-F7 are possible with F7 being the GUI.
Login here, then run the command
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware, including your graphics card and monitor capabilities.  Answer everything to the best of your ability.  When necessary, press TAB to move through options and SPACEBAR to select (like when you get to screen resolution options - select your max and everything less)

Once you have this completed, you can restart the X-server which is the GUI stuff.  Run
```
sudo /etc/init.d/gdm restart
```
You might have to go to CTRL+ALT+F7, but I'm not sure.  The other option is to just reboot the computer at this point.

---

### Post by cpuman on 2007-12-12
ok when i do that it says no such package as xserver-xorg, thx for any help on this, also is there a way to just uninstall it and reinstall with the desktop version, i reburned with new download and it still has the same problem. im running an nvidia 8800 gtx video card, but now that i think about it, it wont work then because if i cant get the blank screen problem fixed then i cant even use either. ok well i reinstalled the server version, it works fine now but its still not a GUI which i need. Is there a way to make the server version have a GUI?

---

### Post by Rocket2DMn on 2007-12-12
The xserver stuff is for the GUI.  The server version does NOT come with X installed - only a terminal interface.  You CAN install a GUI on the server version, but it will just be the X-server with GNOME or KDE (or other desktop manager of your choice).  You will have the same problem.
Install the desktop version and try that command - you will need the "nv" drivers.  If that still doesn't work you will have to look up how to download and install the nvidia proprietary drivers.

---

### Post by cpuman on 2007-12-13
> **Rocket2DMn said:**
> The xserver stuff is for the GUI.  The server version does NOT come with X installed - only a terminal interface.  You CAN install a GUI on the server version, but it will just be the X-server with GNOME or KDE (or other desktop manager of your choice).  You will have the same problem.
Install the desktop version and try that command - you will need the "nv" drivers.  If that still doesn't work you will have to look up how to download and install the nvidia proprietary drivers.

where do i get these nv drivers at? because until i get able to see past the menu of the desktop installation, i cant do anything. 

Edit: ok well i went and found some drivers from the nvidia site for linux, i dont know how to use these or if these are even the right drivers. [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html)

---

### Post by Rocket2DMn on 2007-12-13
If you are running the desktop version now (or have downloaded the GUI software), when you run
```
sudo dpkg-reconfigure xserver-xorg
```
when you get to the video card part, it will prompt you for a driver to use.  "nv" is one of the choices, you don't have to download it separately.  "nvidia" is the proprietary drivers (non open-source).
If you are still in the server edition and want to get the GUI, I think the command to download ALL THE NECESSARY PACKAGES is
```
sudo apt-get install ubuntu-desktop
```
Be warned, this will probably be hundreds of megabytes of files to download.

---

### Post by cpuman on 2007-12-14
if this works i will declare you king lol

EDIT: OMG dude you are the king!!!!

Now how do i go about running windows games on here :P i already got cedega but i havent the slightest of how to use it, i followed a guide and got it installed but how do i use these .exe files i have? i tried telling it to open them with it but that didnt work. also is there a better program for running windows files? i mainly want to play a couple of games i have.

---

