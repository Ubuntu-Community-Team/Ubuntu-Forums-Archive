---
title: "help With NVIDIA 8800GT"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2007-11-04
I upgraded my graphic card from nvidia 6600gt to nvidia 8800gt.
Now, i cannot log into Ubuntu 6.10. After the OS is loaded, I get a black screen.
There is nothing i can do at that black screen, mouse does not function and i have to reboot.

Furthermore, I'm trying to Upgrade to Ubuntu 7.10. I get the same black screen problem after i click on "installing Ubuntu"

Is ther a way to fix the issue. Thanks:confused:

---

### Post by Crafty Kisses on 2007-11-04
> **kiyometane said:**
> I upgraded my graphic card from nvidia 6600gt to nvidia 8800gt.
Now, i cannot log into Ubuntu 6.10. After the OS is loaded, I get a black screen.
There is nothing i can do at that black screen, mouse does not function and i have to reboot.

Furthermore, I'm trying to Upgrade to Ubuntu 7.10. I get the same black screen problem after i click on "installing Ubuntu"

Is ther a way to fix the issue. Thanks:confused:

You have to edit your xorg.conf file, basically what you want to do is enter the command to get to your xorg which is:
```
sudo gedit /etc/X11/xorg.conf
```
Then after that look in that file where it says the following:
```
Section "Device"
	Identifier	"nVidia Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
```
Change the "nvidia" to "nv" and install the drivers after you do that.
Hope this helps. :)

---

### Post by kiyometane on 2007-11-08
The problem is i don't even get to type what you suggested. nothing works even the mouse. Is there a way to access the command line?
Thanks

---

### Post by skymera on 2007-11-08
ehhh 

try access the TTY

ctrl+alt+f1 - f6

or install envy via command line and launch via command line.

sorted

---

### Post by Prefader on 2007-11-08
Try pressing "ctl-alt-F1", and see if that dumps you out to a login prompt.

If that doesn't work, when you boot your system, there's an short timeout where you can press esc to see the boot menu.  If you do this, you'll see a "recovery mode" or something very much like that.  Boot that, and you'll end up at a login prompt.

You should be able to make changes to your xorg.conf from there, using nano (sudo nano /etc/X11/xorg.conf)

From what I understand, Nvidia hasn't actually released linux drivers for the 8800GT yet, which is probably why you're having trouble.

---

### Post by kiyometane on 2007-11-08
All the command you gave me do not work, really nothing i can do.

However I did burned the ubuntu 7.10 from windows. Automatic install give the same problem too.
Is there a way to access or install ubuntu 7.10 with the cd?
can i access the command line from the cd?
Any idea would be usefull.
:confused:

---

### Post by Therion on 2007-11-08
You're booting from the hard drive, correct?

If you're booting from the hard drive hit ESCape from the GRUB menu.
Select "Recovery Mode"
This will put you at the command prompt. 
From the command prompt:
```
nano gedit /boot/grub/menu.lst
```
Scroll down past all the #'s and find the first line that begins with kernel, the long line that runs off the end of your display.
Go to the end of that line and find the **quiet** and **splash** options and remove them from that line.
Ctrl+X to save the changes, confirm the overwrite and reboot.
From there you should be prompted to install the nVidia restricted drivers and be good to go.  This is what got my 8800GTS up and running.

---

### Post by inversekinetix on 2007-11-08
> **Therion said:**
> You're booting from the hard drive, correct?

From there you should be prompted to install the nVidia restricted drivers and be good to go.  This is what got my 8800GTS up and running.

off topic but how do you feel about your 8800gts now that the 8800gt is out?

---

### Post by Therion on 2007-11-08
> **inversekinetix said:**
> off topic but how do you feel about your 8800gts now that the 8800gt is out?
Well, let's see.  The GT costs less :mad:, pumps out what, roughly 30% more performance :mad: generally speaking?  It makes Oblivion look even *better* :mad:, uses but a single-slot :mad: that wouldn't block any PCI slots in my P-180 :mad: ...

Heeeeey... how 'bout them Antec P-180's, eh?  I love mine!  How 'bout you? 
 
Yeah, how about we talk about those instead?

---

### Post by inversekinetix on 2007-11-08
> **Therion said:**
> Well, let's see.  The GT costs less :mad:, pumps out what, roughly 30% more performance :mad: generally speaking?  It makes Oblivion look even *better* :mad:, uses but a single-slot :mad: that wouldn't block any PCI slots in my P-180 :mad: ...

Heeeeey... how 'bout them Antec P-180's, eh?  I love mine!  How 'bout you? 
 
Yeah, how about we talk about those instead?

I've never seen a case that comes even close to the quality of design and build in that antec.  In terms of functionality, i think they thought of everything,  even little boxes to keep screws and bits in, water cooling ready, everything has been thought of.  Sure it weighs a ton, but its quiet, the filters keep inside clean, has loads of fans.  Can't find any fault with it.

I know what you mean about the 8800GT, I'm gonna get a couple when I upgrade to an SLI mobo.

---

### Post by kiyometane on 2007-11-08
8800gt ssc edition from evga outperformed 8800gtx

Is ther a way to fix the issue or install ubuntu 7.10 from the cd?
Booting from hhd make the system crash

---

### Post by Therion on 2007-11-09
> **kiyometane said:**
> 8800gt ssc edition from evga outperformed 8800gtx

Is ther a way to fix the issue or install ubuntu 7.10 from the cd?
Booting from hhd make the system crash
Did you try Escaping out of GRUB and editing menu.lst like I suggested in one of my previous posts?

---

### Post by kiyometane on 2007-11-09
It does not work.
however i can start recovery mode when the grub show up and aksk to select a Os to boot from

---

### Post by Pumalite on 2007-11-09
If you can get into Recovery, install nvidia-glx-new

---

### Post by kiyometane on 2007-11-09
> **Pumalite said:**
> If you can get into Recovery, install nvidia-glx-new

you mean the command "nvidia-glx-new".
By the way, i tried to edit the xorg.conf. The file was empty.
I have Ubuntu 7.10 cd, is there a way to install it using the command line?

---

### Post by Tadock on 2007-11-09
I had a similar problem I upgraded my 6600 GT to a 8600GT I solved it with the alternative 7.10 install CD. I hope this helps.

---

### Post by kiyometane on 2007-11-09
I durned the iso to 4* speed. I'm making anew cd at 1*speed to see if the cd i have is not faulty. I can not make a fresh install even.

Let suppose i reformat the hardrive with windows and then reinstall 7.10, will grub be restored to give you choice of os to boot from?

---

### Post by Tadock on 2007-11-09
If the partition isn't destroyed I don't see a reason why it wouldn't be in the GRUB. But, I would call for a second opinion.

---

### Post by Pumalite on 2007-11-09
You cannot format Windows. Only partitions where Ubuntu was installed. New installation brings new Grub with options for both OS's if your Windows remains intact. (you don't format it)

---

### Post by kiyometane on 2007-11-09
I did not install 8800gt drivers before upgrading. Now i'm in a situation in witchi cannot access the hardrive and cannot even make a fresh install with cd. 
Any idea?

---

### Post by kiyometane on 2007-11-10
Can someone help me, i don't wanna get stuck with windows.

---

### Post by Pumalite on 2007-11-10
You said you could get into Recovery?:

sudo apt-get install nvidia-glx-new

Reboot.

---

### Post by Cresho on 2007-11-11
> **Pumalite said:**
> You said you could get into Recovery?:

sudo apt-get install nvidia-glx-new

Reboot.

I just built a new rig.  gigabyte mobo, athlon 6400 black edition, bfg 8800gt oc, ubuntu 64bit.  I cant seem to make the graphics card work.  i am currently in low graphics mode and typing this.  i tried NVIDIA-Linux-x86_64-100.14.19-pkg2.run from the nvidia website in terminal and compiling it and all but its a no go!.  the graphics card isn't supported.  its a shame too because this card woop my neighbours evga 8800gtx on all benchmarks under windows.  he gets around 9200 for futurmark 06 and I get 10200.  also world in conflict the scores are far better on my card.

---

### Post by nailzs on 2007-11-11
> **Pumalite said:**
> You said you could get into Recovery?:

sudo apt-get install nvidia-glx-new

Reboot.

Didn't work. I already had the newest drivers installed.

---

### Post by Pumalite on 2007-11-11
Then go with:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Once IN the system, figure out what to do.

---

### Post by nailzs on 2007-11-11
edit.

---

### Post by Cresho on 2007-11-11
> **Pumalite said:**
> Then go with:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Once IN the system, figure out what to do.

this one worked out okay.  It just allowed me to get out of my silly 640x480 resolution.  No 3d supported at the moment.

---

### Post by Prefader on 2007-11-12
[http://www.phoronix.com/scan.php?page=news_item&px=NjE3MA](http://www.phoronix.com/scan.php?page=news_item&px=NjE3MA)

There is no linux driver for the 8800GT cards as of yet.

---

### Post by aoanla on 2007-11-17
As of yesterday, there is a beta driver which claims to support the 8800GT:

[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

Try it out and see if it works?

---

### Post by regomodo on 2007-11-17
> **aoanla said:**
> As of yesterday, there is a beta driver which claims to support the 8800GT:

[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

Try it out and see if it works?

yea just saw that at [phoronix]("http://www.phoronix.com/scan.php?page=article&item=918&num=1"). It's been a day so i wonder if anyone has tried out the new [drivers]("http://www.nvidia.com/object/linux_display_ia32_169.04.html").

Wait, just looked at the URL. It's 32bit. That was an anti-climax

[edit] just found the 64 bit beta [driver]("http://www.nvidia.com/object/linux_display_amd64_169.04.html")

---

### Post by mellowd on 2007-11-17
I'm keen to see if it works. My 8800GT is currently holding me off installing ubuntu desktop on my main machine

---

### Post by Cresho on 2007-11-17
tried installing it and does not work.  still in vesa after the whole mess.

---

### Post by regomodo on 2007-11-17
> **mellowd said:**
> I'm keen to see if it works. My 8800GT is currently holding me off installing ubuntu desktop on my main machine

Just tried it. Seems to work fine so far. My videos are now playedback at there proper resolutions. Also, everything seems a lot more snappier (redrawing)

Make sure to install libc-dev before you try to run the installer and when you go to install ubuntu do so in safe-graphics mode. Additionally (AFAIK) you won't get a boot up screen unless you edit your grub's menu.lst to remove "splash" or add "vga=normal" ( i think on that 2nd one)

---

### Post by Cresho on 2007-11-17
> **regomodo said:**
> Just tried it. Seems to work fine so far. My videos are now playedback at there proper resolutions. Also, everything seems a lot more snappier (redrawing)

Make sure to install libc-dev before you try to run the installer and when you go to install ubuntu do so in safe-graphics mode. Additionally (AFAIK) you won't get a boot up screen unless you edit your grub's menu.lst to remove "splash" or add "vga=normal" ( i think on that 2nd one)

hmmm...ill try your advice.  ill do a fresh install since i just updated my system to a 64 athlon 6400 black edition.

---

### Post by regomodo on 2007-11-17
> **Cresho said:**
> tried installing it and does not work.  still in vesa after the whole mess.

i thought it was rather pain free. you are trying to install it with the xserver stopped?

$ sudo /etc/init.d/gdm stop

or for kde users

$ sudo /etc/init.d/kdm stop

 also, ignore the issue about downloading a kernel when the installer asks

---

### Post by Cresho on 2007-11-17
hmm.  still no go.

here are the steps I gathered so far.

downloaded NVIDIA-Linux-x86_64-169.04-pkg2.run

log out

ctrl+alt+f1

log in @ terminal with my username

cd /home/yousername/Desktop





ohh yah, dev tools installed like this.

sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

ls

sudo /etc/init.d/gdm stop

install new drivers like with "sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run"

after that, configure xorg with sudo dpkg-reconfigure xserver-xorg

reboot and my pc is messed up.

---

### Post by Cresho on 2007-11-17
> **Cresho said:**
> hmm.  still no go.

here are the steps I gathered so far.

downloaded NVIDIA-Linux-x86_64-169.04-pkg2.run

log out

ctrl+alt+f1

log in @ terminal with my username

cd /home/yousername/Desktop





ohh yah, dev tools installed like this.

sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

ls

sudo /etc/init.d/gdm stop

install new drivers like with "sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run"

after that, configure xorg with sudo dpkg-reconfigure xserver-xorg

reboot and my pc is messed up.


UPDATE:  It works fine.  I did the above but before that, i uninstalled everything that was nvidia from the synaptic manager.  even the restricted driver manager.  I am not sure exactly what i did but after the driver install, x.org configuration, a simple reboot, it all works fine.

I still have issues with my cd.  I cannot install ubuntu unless i remove the pciexpress graphics card, use the built in graphics card and install it from there.  I'm still tripping out!

---

### Post by regomodo on 2007-11-18
> **Cresho said:**
> hmm.  still no go.

here are the steps I gathered so far.

downloaded NVIDIA-Linux-x86_64-169.04-pkg2.run

log out

ctrl+alt+f1

log in @ terminal with my username

cd /home/yousername/Desktop





ohh yah, dev tools installed like this.

sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

ls

sudo /etc/init.d/gdm stop

install new drivers like with "sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run"

after that, configure xorg with sudo dpkg-reconfigure xserver-xorg

reboot and my pc is messed up.

You shouldn't of had to dpkg-reconfigure xserver-xorg. If the installer didn't ask to do your xorg.conf then nvidia-xconfig would have done it anyway. Also, no idea why you needed all those dev-tools. libc-dev was enough for me and i haven't installed much yet. It's only a 1 day old install.

> **Cresho said:**
> 
I still have issues with my cd.  I cannot install ubuntu unless i remove the pciexpress graphics card, use the built in graphics card and install it from there.  I'm still tripping out!

I couldn't get ubuntu to install even in safe-graphics mode so i tried Kubuntu , which would only work in safe graphics mode. I got no cli which i probably should have entered at the start with some boot options but the desktop loaded up reasonably quickly.

---

### Post by Cresho on 2007-11-18
okay, i posted a tutorial here so you guys can play with it.  I just had to because i keep loosing my notes.

setup bios
(monitor vga cable on vga pci-e card)
advanced bios features->boot from cd rom
advanced bios features->init display first->onboard vga
advanced bios features->onboard gpu->always enabled
save and exit

power off
(monitor vga cable on onboard vga)
--------------------------------------------------------------------------------
load ubunu cd and bootup (during install, gpu fan is spinning at its max which is normal).
--------------------------------------------------------------------------------
install ubuntu
reboot
eject cd when prompted
--------------------------------------------------------------------------------
reboot into the operations system, log into it and you should be fine after this point (this is just to verify that your onboard is alright).


open terminal up and type this without the quotes.  you also should have the ubuntu cd in the drive as well.

"sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev"

dont forget to answer the termianl questions like yes and enter.....8(
--------------------------------------------------------------------------------
download the driver from nvidia

[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

log out of ubuntu after download is finished
hit ctrl+alt+F1
log into your username at the prompt in terminal

then in terminal
cd /home/yourusername/Desktop
ls (just to see if your in the right directory where you downloaded the file in firefox)
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
(ignore the question or say no to kernel download during instal, allow 32bit compatibility, and have nvidia xconfig update the x)

"sudo reboot" in the terminal

--------------------------------------------------------------------------------
shut down and reboot into bios

eject cd since its not needed

setup bios

advanced bios features->boot from hardisk
advanced bios features->init display first->peg
advanced bios features->onboard gpu->enabled if no ext peg

save and shut pc down
(monitor vga cable on  onboard vga)
turn on pc and it should boot into ubuntu (gpu fan slows down) at this point, everything is black and should be left alone until something pops up.  be patient.  there is a fix for this problemby editing grub's menu.lst to remove "splash" or add "vga=normal"


troubleshooting!!!!!!
after some updates, I had blackscreens and couldnt get back into the system.  something got overwritten during the update so i fixed my problem by re-doing the steps from the very start.  It has only happened to me once after some updates.  i was able to get back into everything easily .  I keep the nvidia driver easily accessible so i can cd into the directory.
--------------------------------------------------------------------------------



--------------------------------------------------------------------------------

---

### Post by regomodo on 2007-11-18
@ Cresho

you must have a very arsey motherboard. i only had to install libc-dev and that was it. at least you are able to use the driver now.

---

### Post by Cresho on 2007-11-18
> **regomodo said:**
> @ Cresho

you must have a very arsey motherboard. i only had to install libc-dev and that was it. at least you are able to use the driver now.

HE HE!  thanks for your persuasion.  I decided to give up the 64bit since after i had everything tweaked and died just too often.  I tried booting into the 32bit version of ubuntu and it went just fine under safe graphics mode.  It was like starting an engine.  3 times and on the fourth, it took me to the window where i could install.  I didnt need to use the motherboard gpu.  installed it, went to nvidia site and downloaded the 32bit version.  loged off, shut down gdm, installed (ohh yeah i installed the dev packages as well as libc6-dev) and it just booted up fine.  glxgeared test at terminal and it was running.

No problems!!!!  I guess my hardware just hates the 64bit version.....for now!

---

