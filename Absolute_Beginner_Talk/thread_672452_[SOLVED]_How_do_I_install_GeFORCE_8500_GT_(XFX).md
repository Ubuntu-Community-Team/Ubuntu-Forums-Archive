---
title: "[SOLVED] How do I install GeFORCE 8500 GT (XFX)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Vinniechenzo on 2008-01-19
:confused:I don't want to destroy my system and I have never upgraded my hardware one Ubuntu before.  Please can I have a walk through or do you just plug and play.

Thanks

---

### Post by Ub1476 on 2008-01-19
This driver can be installed with [Envy]("http://albertomilone.com/nvidia_scripts1.html"), if Ubuntu doesn't already has it within Restricted Driver Manager. Make sure you remove any previously installed drivers before using Envy.

```
envy -g
```

---

### Post by Law506 on 2008-01-19
Envy shouldn't be required to install if you are running Ubuntu 7.10
7.10 comes with a restricted driver that once you boot into the system it should ask you to run it.

Careful though, you dont want to use the restricted drivers and a manufacturer 's driver at the same time, i did that with my 8600GTS and lost video and eventually reinstalled.

So bascially, plug and play should be all that there is to it and like Ub1476 said, remove the previous driver.

---

### Post by Vinniechenzo on 2008-01-19
still no luck the only way that I can get it working is to operate off the install CD.  I tried running in safe graFX mode but then I only got non-stop beeps that only ended when i hit Ctrl+Alt+Del that this was on the screen.  I attached want the screen showed.

When I just installed the card and turned it on it would go thought everything like normal but bring me to a command like screen that only showed me what it had just done and then a cursor with no other info and dose not respond to any commands like "ls" or things of that nature it will just reproduce them on the screen.

Please help me 
I think that i have to blow away the old drivers but i don't know how to do that or how do i auto detect for new ones.

---

### Post by Vinniechenzo on 2008-01-19
i tried using the restricted driver manager when I was lodged in under the boot disk and of course it told me to restart after the alleged restart and to take out the CD and I did but the changes were not saved and when the card is in it wont boot up so i cant install the driver dose any one know how i can delete the current drivers and then shout down so when i install the new card it will  auto detect.  the video card that i am using now is the integrated one on a Dell Optiplex GX280

---

### Post by A4006 on 2008-01-19
Odd... thats the exact same video card I have. Anyways, when I installed Ubuntu (7.10) it auto detected the graphics card  and worked fine.  I used Envy to get the drivers.  I suppose you could reinstall and use the live CD to back up all your stuff to a CD or jump drive, but re installation is always a pain.  I think the Ubuntu alternate installer CD has a repair function, so you could try that.  Sorry if this doesn't help much.

---

### Post by Vinniechenzo on 2008-01-19
do you know how to get the auto installer to run? to that it will reinstall the new card?  also where do I get the cd that will repair or reinstall  the ubuntu without loosing my stuff

---

### Post by marmaladejackson on 2008-01-19
I think what he means is that Ubuntu was previously installed under a different hardware configuration.  He opened the case, swapped out the vid card, and rebooted.  The OS is still trying to apply the old vid card's settings to the new configuration when launching the desktop, which obviously isn't working.  The card is obviously compatible as it works when using the live CD, but how do you get the existing installation to auto-detect and apply the appropriate settings to the new card? 

-B

---

### Post by EXCiD3 on 2008-01-19
in terminal "sudo nvidia-xconfig" will reconfigure the drivers to enable x to start :)

---

### Post by Vinniechenzo on 2008-01-19
Yes that is exactly what I mean.  I am sorry if I was not being clear but this is spinning my head.  I want to install this so i can hook my tv up as my monitor.( 46" Sharp Aquos)

---

### Post by Vinniechenzo on 2008-01-19
I just tried that and I am getting a message that is saying that command is not found.  I took a screen shot.

---

### Post by EXCiD3 on 2008-01-19
Ok so you dont have the nvidia drivers installed or something else is wrong. What was your previous graphics card?

Try 
```
sudo gedit /etc/X11/xorg.conf
```
Then change the "Driver" section to use the "vesa" driver. Then plug the card in and reboot. Then you should get the xserver to start. You will then need to install the graphics drivers for the nvidia card, using either envy or the restricted drivers manager or compile them yourself.

That hopefully should work.

---

### Post by doorknob60 on 2008-01-19
OR you could plug in the card, and turn on the computer and go in to the GRUB menu by pressing ESC when it tells you to, and go in to Recovery Mode. THen, when it gets to the command line (you should be logged on as root) type ```
 dpkg-reconfigure -phigh xserver-xorg
``` and that should fix your problem :) EDIT: After that just press CTRL-ALT-DEL to restart and then start Ubuntu normally.

---

### Post by EXCiD3 on 2008-01-19
yes doorknob60, thats a good idea. i always forget to use dpkg-reconfigure :(

---

### Post by EXCiD3 on 2008-01-19
Just the clarify, what was your previous graphics card?

---

### Post by Vinniechenzo on 2008-01-19
I had no card it was the integrated one that comes on the board. 

You two were right and it worked great.  After you boot up just go to "System - Administration - Restricted Driver Manager" and check enable then restart again. my screen looked zoomed in but all i had to do is set it to pix-to-pix  (I think pixel to pixel)

So if happen so someone else just folow the instruction given by doorknob60 in this post they were confirmed by EXCiD3 so you have to know that it is good info.


Thank you so much for all of your help 

Now on to installing a sound card.

---

### Post by Vinniechenzo on 2008-01-19
One more screen shot you will know you are having the same problem if after you plug in your video card and reboot this is what your screen looks like.

---

