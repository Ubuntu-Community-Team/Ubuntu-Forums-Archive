---
title: "Installed NVidia Driver and now I get a blank screen"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by iampoch on 2006-08-23
I just installed my Ububntu and then installed Automatix, which I used to install the Nvidia driver. Unfortunately, whe I rebooted, the screen turns blank when I'm supposed to enter my user name.  Everything goes smoothly up to that point and then *poof* it's just a blank screen.  Should I reinstall my Ubuntu? if so, how do I do it?

I tried going to the Recovery Mode, but I'm absolutely new in Linux that I don't even know what commands to tye in the command prompt.

By the way, this also started because I wanted to change the resolution from the fixed 640x480 to 1024x768 resolution. Unfortunately, I didn't want to reconfigure the xserver becuase when I tried doing it when I was in LiveCD, it just churned out an error message.  I thought installing the Nvidia driver'll do the trick.

Please advise. Thanks.

---

### Post by b_martinez on 2006-08-23
> **iampoch said:**
> I just installed my Ububntu and then installed Automatix, which I used to install the Nvidia driver. Unfortunately, whe I rebooted, the screen turns blank when I'm supposed to enter my user name.  Everything goes smoothly up to that point and then *poof* it's just a blank screen.  Should I reinstall my Ubuntu? if so, how do I do it?

I tried going to the Recovery Mode, but I'm absolutely new in Linux that I don't even know what commands to tye in the command prompt.

By the way, this also started because I wanted to change the resolution from the fixed 640x480 to 1024x768 resolution. Unfortunately, I didn't want to reconfigure the xserver becuase when I tried doing it when I was in LiveCD, it just churned out an error message.  I thought installing the Nvidia driver'll do the trick.

Please advise. Thanks.


I'll try to help, if I can. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
Question : Did Automatix update anything? If it updated the X11 system then the following will NOT help. You need to read the 1st sticky in the Absolute Beginners Forum. There is info on how to fix your box. If not, the --->
Can you boot into recovery mode? If so, log in and type in the following commands, followed by the enter key. 1 line= 1 command. Each command you type in will be the words following the "code="
code=lsmod
this will list the modules in the kernel. Look for the nvidia one(s). If more than one, make sure that you have one that is for the video.
nano is an excellent editor. The commands to write out and to exit are simpl key combinations. When you see (up arrow)O or (up arrow)X it means to use the 'control' key (Ctrl on my keyboard) and the letter together.
This is what they look like

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

Now that that is covered,
code=sudo nano -w /etc/X11/xorg.conf
enter your user password
down arrow to navigate to the "Device" section and make sure that the "Driver" is "nvidia"
WriteOut the Exit nano.
code=startx
and you should be good to go.
hth
Bill

---

### Post by raublekick on 2006-08-23
i think i ran into this problem today as well, seems similar enough anyways. 

this is my first time with an nvidia card in linux, and i was pretty stoked about it. anyways...

i installed nvidia-glx through apt, edited xorg.conf and changed nv to nvidia, and then when i ctrl-alt-backspace'd to restart x, it was just a black screen, no console or anything. so i powered off and turned it back on the the same results.

i reinstalled Kubuntu and am holding off on installing the driver again, but i now realize i probably could have just logged into the recovery console and changed the xorg.conf from nvidia back to nv

---

### Post by Koti on 2006-08-23
On a similiar note, I have a Nvidia GeForce3 Ti 200. I've installed the latest driver from the repository, but I get no 3D rendering and I can not set the resolution to higher than 1024x768. 

I went to Nvidias site and downloaded a driver from there, but I had to install it without the xserver running. No big deal, start up in recovery mode, but then during the install I got a lot of errors that I had no idea how to resolve.

Any help in resolving the first two issues using the existing driver would be greatly appreciated.

---

### Post by iampoch on 2006-08-23
ok thanks bill : I'll try this one out today.

---

### Post by iampoch on 2006-08-23
hmm Bill I just tried what you suggested but when i opened up xorg.conf via nano, the file turned up blank. so Automatix may have oiverwritten that.  I'll go to the link you posted to fix the problem.

---

