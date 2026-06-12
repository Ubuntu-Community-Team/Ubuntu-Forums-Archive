---
title: "I need help with my keyboard"
date: 2005-09-23
forum: Bug Reports / Support
---

### Post by hursty on 2005-09-23
i got the ubuntu disk just to day and i tryed to run the live cd and it would let me select the laungage. i though that it could just be the live cd, so i went on to the install disk, now my key board lets me type in the command line and select the boot options but once it starts loading the os it won't let me use my key board.

I have a wirless key board but i also have a regualar keybard that i also try but neather of them worked. 

[SIZE=7]COULD SOME ONE HELP ME PLEASE[/SIZE]
if it would hlep here my hotmail (i also have msn)
[email]danhursty@hotmail.com[/email]

---

### Post by bmcage on 2005-10-26
I have the same problem. 
I can type on the boot line, I can go to the help, but when I need to select the language, my cursor doesn't move, or at least ver, very, very slowly (like minutes later). 

I did notice that my BIOS sometimes also freezes. Tried some different bios settings, no solution there. Would be great if someone had ideas


**UPDATE**
Problem is solved. I installed WinXP and noticed that mouse is not working (I have more than one, all failed, PS/2), so I attached an old serial mouse. Win detected and I could work. So I unplugged the PS/2 mouse, and rebooted from Kubuntu. 
Now installation works, keyboard can be used.  Great.

Unfortunately, Ubuntu does not detect my serial mouse. First I tried to reconfigure X with 'sudo dpkg-reconfigure xserver-xorg', but that did not let me choose my mouse. After some searching on the net, I solved it as follows: 
CTRL-ALT-F4 to go to session 4, login, make a link for the mouse: 'sudo ln -s /dev/ttyS0 /dev/input/mouse', where you change the 0 to 1, ... if your mouse is on another serial port, and then change the xorg.conf file, where the mouse inputdevice is changed to 
.....
     Option  "Device"    "/dev/input/mouse"
     Option  "Protocol"  "microsoft"
.... 
Change the protocol to the correct one for your mouse (see man xorg.conf). In session 7, restart X with CTRL-ALT-DEL, and the serial mouse should work.  

Your problem is probably different to mine, but who knows. 

Different things you can try are boot with: 'linux kbd-reset', or 'linux i8042.noaux' , see [http://www.ussg.iu.edu/hypermail/linux/kernel/0507.2/0043.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0507.2/0043.html)

**Update 2**
On reboot the symbolic link to mouse is gone, and therefore X doesn't start by lack of pointing device. There are scripts on the net on how to activate this at boot. I choose the easy way and changed xorg.conf again so that I have
     Option  "Device"    "/dev/ttyS0"
Type startx to see if it works.

---

