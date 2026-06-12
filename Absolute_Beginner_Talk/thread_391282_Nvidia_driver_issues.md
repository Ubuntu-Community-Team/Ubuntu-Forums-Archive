---
title: "Nvidia driver issues"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by rasmukri on 2007-03-23
I was having problems w/ my video card it was hanging like when the video drivers aren't installed so i came here and found the post for installing the Nvidia driver... it is quite possible that i installed the wrong one since well i am a noob. after the install it was working great i was loving it . but the screen was on like 1020x800 or something and everything was HUGE so i opened the nvidia control panel and changed the display to 1920x1200 that is the normal resolution i would use in windows (that is how i am typing this dual boot thing going yea) so well i changed it to 1920x1200 and the screen was awesome everything was so well normal, then i turned it off and came back the next day and well it hit the fan sorta speak. it will boot all the way till where normally it would have the Ubuntu splash screen for login but instead of that it comes up with this blue screen that has crazy looking symbols around it and it says "Failed to start X server (your graphical interface) it is likely not set up correctly would you like to view x server output?" so i say yes and the screen shows this error that says "API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this x module has the version 1.0-9755 please make sure that the kernel module and all NVIDIA driver components have the same version"  and that is where i get the poss wrong driver idea.  and finally after i look at that it puts me to a terminal type login screen where i can type commands and stuff. the prob is i was thinking of removing the driver but i..haha forgot how to delete stuff from terminal.
i have tried to do this and roll back the file sorta sudo dpkg-reconfigure -phigh xserver-xorg
but it didn't help at all.
i have a Nvidia GeFoce Go 7950 GTX PCI-Express 512mb card in a computer running the newest version of Ubuntu and dual boot w/ xp pro

Please help.

---

### Post by mid_night gypsy on 2007-03-23
rasmukri,
 It sounds like you have gotten a kernel update lately.Easy fix thou.Boot your computer in root(recovery mode) and reinstall the Nvidia driver. This can be done like so ....cd /home/your user name/where you have downloaded/...ENTER then sh NVIDA-Linux...plus TAB...then..ENTER...Hope this helps,gypsy

---

### Post by kratos1963 on 2007-03-23
I just installed the Ubuntu distro,  I thought everthing was great untill I tried to install a VM WinXP.  I got a SDL error. after some hard work I came up with this......

kratos@kratos-desktop:~$ glxinfo | greb rendering
bash: greb: command not found
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

nv17 Nividia gforce4 MX 420 shows up in my hardware profile.  And I feel certain I have the right drivers installed.  I have run Pokerstars through wine and it works.  I don't get sound but it works.  When I try to run Diablo II LOD or WinXP setup  I get a SDL errror.

I would be thankful for any advice!:popcorn:

---

### Post by mid_night gypsy on 2007-03-23
kratos1963,
 I don't know VM at all,But your command.....glxinfo | greb rendering. Is  type wrong try glxinfo | grep rendering...Also try and google your SDL error and see if that helps solves your problems. Sorry, I couldn't  be more help. gypsy

---

### Post by rasmukri on 2007-03-23
i tried to reinstall the driver and it still came up w/ the same problem so i thought that i would try to download and install the 1.0-7184 and it worked sorta it installed but right when it was starting it said that i was working as level 1 and should e working at level 3 but i continued anyway because i dont know what that ment. after the install i restarted and it came to the same error screen and it said the kernel has 1.0-8776 and the x module has 1.0-7184 so i went and downloaded and installed the 8776 driver and it worked sorta but this time after i typed exit from root it came to the login screen and i can work in Ubuntu at 1920x1200 resolution but of course i had to test the restart and what do ou know it came to the same stupid error screen now it says the krnel has the 7184 and i have the 8776. is there a way that i can just edit the kernel from the desktop.

---

### Post by rasmukri on 2007-03-23
i dont know what i did but it works fine now thanks

---

