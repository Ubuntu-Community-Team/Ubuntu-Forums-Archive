---
title: "[SOLVED] Video Card install"
date: 2008-05-21
forum: Alabama Team - US
---

### Post by retiree on 2008-05-21
Crane
I installed my new video card and I can't start up Ubuntu normally.
It goes to a terminal look and ask for my login name and then my password. When I enter it tells me wrong login. I am barely running on Windows now. I may have to uninstall my video card and try to get it to boot from there.That is the only thing I did was install the card. Retiree

---

### Post by solitaire on 2008-05-21
You got a LiveCD handy??
if not hold doen "Esc" when you boot to get to the options and pick 
```
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
```
Then log in as "Root" you may have to run through the setup for X-Server again.

Best do:
```
apt-get install envyng
``` Then once it's installed run ```
envyng -t
``` then run through the wizard to install the correct drivers.

Then reboot as normal :D

---

### Post by retiree on 2008-05-21
I am running Gutsy, would your instructions still be the same the way you posted it? I was planning on installing Hardy after I had my card installed. I am not proficient in terminal yet, so I need to simplify as much as possible. Thanks for your post, and I will keep trying. I did have to take my video card back out and start over.  I do have a live Cd. Thanks for the help, Retiree

---

### Post by solitaire on 2008-05-21
only diffrence that the program might just be called "envy".

---

### Post by retiree on 2008-05-22
Thanks Sol for the help so far.
I did manage to install envy and from the menu to install the nvidia drivers and it recognized my new card correctly,and installed the drivers. I rebooted but it went to a terminal screen login. Can Ubuntu be run GUI from there? From the envy menu it gave me options to reconfigure X-org and I said yes.It also had option to restart xserver and I did.All of these options reboot to terminal login (clayton-clayton-desktop ~$) Thanks for any further help, Retiree

---

### Post by solitaire on 2008-05-22
One thing to try is to run Envy and remove the nvidia drivers compleatly. Reboot then run it again and install the Nvidia drivers.

For some reason this worked with my install..

I always replace the x server config when asked. you could give that a try..

---

### Post by retiree on 2008-05-22
Sol 
Boy have I messed up somewhere.
I let envy remove all drivers and then did a auto install nvidia.It didn't work. I then removed all drivers and did a manual. It gave 3 options for different cards. I did the first and got the same results.then the 2nd,same results.Then the 3rd and it installed a driver that gave me a screen res of
 800x600 and now I can't get that driver out. Everytime I run envy again it defaults to that last option driver. I can run live Cd.Any suggestions
Retiree

---

### Post by crane on 2008-05-22
I'm not very familiar with envy so I' not sure how to help. Have you tried using apt or synaptic to remove the drivers. Then use it to install then use it to install the correct driver?

---

### Post by retiree on 2008-05-22
After I used Synaptic to remove all drivers and then reinstalled the best resolution I can get is 800x600.I don't know where to go from here. Any help would be appreciated. Thanks Retiree

I'm running x64 bit Ubuntu. I don't know if this makes any difference.

---

### Post by retiree on 2008-05-23
Crane
I finally found the proper driver from the manf website and downloaded it to my desktop.If 
I put my new video card in first, it will only boot to terminal login.My question is how do I try and run it from there or do I need to boot up to desktop with my intergrated MB driver (800x600) and install it from desktop (which is a run file)? I tried this both from terminal and terminal root and could not get either to run.I copied and pasted from the manf website the command and it still would not run.The driver I downloaded was for my specific card ( exact same model as on the box it came in).I have uninsatlled drivers from synaptic and it always defaults back to a screen res of 640x480 and I can usually get it back to 800x600. Any suggestions,

Thanks for any help, Retiree
PS The driver file I downloaded is for linux 64 bit (nvida-linux-x86_64-169.12-pkg2.run)That is the command to run the file. On the website it had Quatation marks ' ' at the start and finish of the command, does this have to be in the command?

---

### Post by retiree on 2008-05-25
Hey Crane
Just wanted to let you know I finally got my resolution back to normal on Gutsy. Now I'm going to try to install Hardy again after a failed attempt.During the install it stopped and gave a write error message, of which I don't recall what it was. I did a slower burn on the original download but I guess there was still some error. I have been one frustrated man the last few days but I have learned a good bit. Probably just enough to be dangerous!!! One thing I would like to know when I try to reinstll my video card should I put the card in first and install Hardy or install Hardy first and then the card? 
I have read enough forum threads in the last 5 days to do me awhile. My wife probably thinks I'm crazy!!
I guess some how a file called nvidia glx dev got either replaced or deleted when I first put the new card in. Once I reinstalled it my resolution came back to normal.
Thanks, and I do appreciate all the help
I don't mean to be a bother, Retiree

---

