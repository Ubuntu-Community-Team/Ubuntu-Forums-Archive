---
title: "envy kernal update."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-10-07
Hello all you awesome people.
I have been using envy to install my nvidia driver because it is the only way I can get anything 3-d to work at all. In fact I had to reinstall 3 times tonight trying to get nvidia drivers outside of envy. So now you know why I am using it. My problem is whenever I update the kernal. I was under the understanding that when the kernal is updated, as long as run envy and have it rebuild the drivers before I restart I would be safe... wrong. And so I thought, I know I will log into the older kernal and use envy to uninstall the nvidia driver so I can then safely log into the new kernal and use envy to rebuild the driver. This didn't work.. now I have to reinstall again. 
Please... Next time this rolls around again, what can I do? And please don't say don't use envy.. pretty please.

---

### Post by Malta paul on 2007-10-07
Hi, It is my understanding, that each time you change the Kernel and you want the latest video driver you will have to install it after your new Kernel has been changed and then after you have booted into your distro which contains the default driver.  
Hope this helps :)

---

### Post by overdrank on 2007-10-07
> **osc1882 said:**
> Hello all you awesome people.
I have been using envy to install my nvidia driver because it is the only way I can get anything 3-d to work at all. In fact I had to reinstall 3 times tonight trying to get nvidia drivers outside of envy. So now you know why I am using it. My problem is whenever I update the kernal. I was under the understanding that when the kernal is updated, as long as run envy and have it rebuild the drivers before I restart I would be safe... wrong. And so I thought, I know I will log into the older kernal and use envy to uninstall the nvidia driver so I can then safely log into the new kernal and use envy to rebuild the driver. This didn't work.. now I have to reinstall again. 
Please... Next time this rolls around again, what can I do? And please don't say don't use envy.. pretty please.

HI, I have used envy on several systems and never have a problem after updates. If you install the nvidia drivers is when you will have to reinstall them after a update ( is my understanding) I did have some trouble with nvidia the other day but I tossed if off to a test system and nothing else, I may have been mistaken. What is the model of the video card?

---

### Post by osc1882 on 2007-10-07
To Malta paul, the video card is MSI 256 Meg Nvidia Geforce 8500 GT. But that really shouldn't matter. I'm 99.9% sure that when the "Kernal" updates the build of the nvidia drivers is broken and so when you try to log in useing your new Kernal X is broken and your left with only being able to go into safe mode. We'll I'm useless in safe mode, I don't know any commands by heart... anywho.  I was under the understanding that if you log into your old kernal ( that still works) you can uninstall the nvidia drivers and log into your new kernal and use envy to build the driver again.. but this did not work, now I can not boot into ether kernal.. I'm guessing that is because when you use envy to uninstall it doesn't set up any video drivers at all... and so I need to log into the old kernal, use envy to uninstall the video card drivers and then some how install the default driver that comes on the install cd and then boot into the new kernal ( that hopefully works now) and use envy to rebuild the nvidia drivers.
Does anyone know if this would work? And if so can anyone tell me how to install the default drivers that comes loaded with Ubuntu?

Some please help pretty please. I want to have this PC done being set up by later tonight.

I'm off to reinstalling Ubuntu.

---

### Post by FuturePilot on 2007-10-07
Hi there!:) After you install the kernel update, restart. Do not run Envy before rebooting or else it will end up building the kernel module against the old kernel, hence why after rebooting it didn't work for you. So install the kernel update and reboot. X will fail, that's ok. Just log in through the command line and run envy in terminal mode
```
sudo envy -t
```
Then reboot again and all should be good.

---

### Post by osc1882 on 2007-10-07
when I type that command in, what will happen? Will it bring up a gui ( unlikely ), if there is no gui, will it be easy to follow?

---

### Post by osc1882 on 2007-10-07
I love you FuturePilot, in the most non gay way (not judging gays, I'm just not one myself) possible.  The text was VERY easy to follow and it worked. Now I just have to poke around the forum and find out how to change my screen rez to 1680x1050.

---

### Post by Sonthun on 2007-10-10
Can I confirm what was said above.  If I want to compile the kernel myself (going to be my first time) I don't have to uninstall the nvidia driver and Envy?  Some of the instructions say I have to switch to vesa or the open nv driver.  This wouldn't be a problem except for some reason when I make those changes to xorg.conf it won't boot into X.  Just gives me a black screen.  So, if I don't need to uninstall the Envy drivers then I can just go straight to working on the kernel.

Is there any advantage to installing the nvidia drivers as part of the kernel?

Sorry.  I have lots of questions.  I'm really trying to learn this stuff.

---

### Post by overlord.gaurav on 2007-10-10
> **osc1882 said:**
> when I type that command in, what will happen? Will it bring up a gui ( unlikely ), if there is no gui, will it be easy to follow?
Yes, its almost the same thing that shows up when you use the command.
The reason why he pasted a command was because it is easier to explain and also most of the Linux user like the text interface more.

---

