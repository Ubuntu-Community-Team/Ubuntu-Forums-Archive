---
title: "Runs good except for NVidia TNT M64- how to?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by BudaTx on 2007-07-20
Got F-fawn installed in a Dell Opt P3-866mhz w/384 memy, 20gb hdd. Very impressed, runs well. looks super.  Now, I go to install my 16mb NVidia TNT M64 video card, change bios to 'Auto' (so it uses the Nv-card for main vid. board) and Ubuntu shows me the splash screen, then dumps to 'tty--blah blah' and says X-server failed to start.  No problem, search these threads and run some sudo, apt-get glx-legacy, run some nano -w and reconfigure display files, Ooops, still no-go.  Now I can't even boot to the regular on-board video, dumped to the X-server prompt.   
Question:  Is there and easy way to install hardware in Ubuntu?  
We're one setp away from making this work before I put in my AverMedia TV Tuner and start running MythTV.  
Any help is appreciated.
Thx
TomC

---

### Post by hamburglar6 on 2007-07-20
First make sure your computer is recognizing the video card by using the command
```
lspci
```
and look through the list to see if your card is there.

Then, you should probably generate a fresh xorg.conf by typing in:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
which will ask you a few questions like screen resolution, drivers, etc.

Finally, to install the binary drivers from nvidia, the easiest way is to use tseliot's Envy, which can be found here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by BudaTx on 2007-07-20
Thanks.  Now I really screwed it up. It would start in onboard video mode but now it just dumps me to the xserver failed to start' screens.  I did some reconfiguring using dpkg-reconfigure xserver-xorg but have absolutely no idea what I'm doing with these commands.  Yes, I picked VGA driver.  Anyway, is there a way to get 'back' or should I reinstall?  Of course, I'll be in the same boat since Ubuntu doesn't support my Nvidia card and I'll start all over again.  Thx

---

### Post by hamburglar6 on 2007-07-20
try running the command again but this time pick 'vesa' as the driver and see what happens.  if that doesn't work you can give this a shot:
```
sudo X -configure
```

but before you do anything i would make sure in your bios you're using whichever card you want.  if you're still going for the nvidia one you should still give that Envy script a try afterwards too.

---

### Post by BudaTx on 2007-07-21
Hamburglar- I think I hosed the xorg file (sounds like I know what I'm talking about -heh?)  The deal is when I use the onboard video (intel 810 chipset) I can boot fine.  I even downloaded the Envy app and ran it, installed and it told me to reboot.  Then upon reboot I stopped at bios and chose the Nvidia card, booted into Ubuntu (which gives the splash screen) then it dumps me to Xserver 'Failed to start' with 'failed to load module 'nvidia' (module does not exist)  No drivers available"  Fatal server error: No screens found"
So, I reconfigure and pick the onboard (intel 810) while leaving the monitor plugged to the Nvidia (bios set to Nvidia) and I get the Ubuntu splash and then black screen.  Reboot, choose onboard and now I don't know where to go.  
Thanks for anymore advice.
Tom

---

### Post by hamburglar6 on 2007-07-21
if you want to try the nvidia one, you should have it selected in the bios before you run envy.  to do that, when you start up your computer and the x server crashes, you should be at a command line (if youre not try alt + ctrl + F1) and type 
```
envy -t
```
and pay attention for any error messages or anything like that- it seems weird to me that if envy installed the drivers that you would get the 'nvidia driver not found' message when you start X.

if you want to use the onboard one, select that in the bios and run envy -t like above, and choose the option to remove the nvidia driver.  after that do 
```
sudo X -configure
```

in either case, reboot, see what happens, and let me know how it goes.

---

### Post by BudaTx on 2007-07-24
That didn't work so good. But only because I have tried to install/reinstall the legacy drivers so many times I had a real mess [booting the onboard to work in the xserver cli, reconfiguring xorg, rebooting & installing nvidia to find out they crash xserver, going back to onboard to remove and try something else...etc]  I finally found 2 more threads about blacklisting and something else I already forgot but my nvidia TNT64 is diplaying Ubuntu gui - Yay!   
One more question:  I only get up to 1024x768 and I know I only have 16mb but I should be able to get higher res's, right?   I installed the envy Nvidia controls but it doesn't show any controls, just a box with check-boxes.  It seems there should be 'sliders' but they're not there?  
Anyway, it's displaying thru the Nvidia and now I'm going to try to get sound out of my SoundBlaster Live! pci card and not my onboard AC97.  This issue also has as many 'fixes' as the nvidia.   
Thx

---

### Post by hamburglar6 on 2007-07-25
glad to hear you managed to get it working.

You can adjust your screen resolution with nvidia-settings in the section titled 'X Server Display Configuration'.  If there are resolutions not listed there that you would like to use (and your card/monitor can handle) you can add them to your xorg.conf file under the 'Screen' section.

---

