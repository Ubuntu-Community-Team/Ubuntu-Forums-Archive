---
title: "Video and Graphic card problems"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Carter081 on 2008-01-16
I have been working on this solo for a while now and i thought i would finally ask for some help.

System i am using is:

Dell XPS 410

CPU: 2.4-GHz Core 2 Duo E6600
Graphics Adapter: nVidia GeForce 7900GS
Monitor Model: Dell 2007WFP
Ramm: 2gb

Operating System:

Ubuntu 10.7 Gutsy Gibbin AMD64
-------------------------
The problem i am having is with screen resolution when changing the Nvidia accelerated  Graphics driver (latests cards). When i enable it, it asks for a reboot. It also deletes all the driver stuff i downloaded. Now after the reboot it sets my Screen Resolution to 800X600 and i cannot change the resolution without having to re-install the drivers. Also another thing that happens is when, when i do re-install the drivers the sound does not work, yet in 800X600 after reboot sound works perfectly.

Using Wine to run WoW:

I get alot of errors containing this situation...for example

> Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
fixme:advapi:SetSecurityInfo stub

that is all i could C&P becuase it automaticly closes the terminal, Also i get the error pertaining to "cannot open 3d acceleration"

I am sort of new to this, ive been trying my best to find this "opengl" and trying to find the right drivers to make everything work once again.

now when i try xorg.conf i get this 

> carter@Carter-Desktop:~$ xorg.conf
bash: xorg.conf: command not found

any help with this situation, im trying the best i can...it would be very appriciated ^_^

---

### Post by kpkeerthi on 2008-01-16
See my posts in this [thread]("http://ubuntuforums.org/showthread.php?t=669019") on how to install nvidia driver the suggested way and set the resolution.

Post back if you are able to solve your resolution problem and we'll deal with the sound issue after that.

---

### Post by Carter081 on 2008-01-16
Well theres one part of my problem i dont have the "nvidia settings" in my applications menu, getting that now.

---

### Post by kpkeerthi on 2008-01-16
> **Carter081 said:**
> Well theres one part of my problem i dont have the "nvidia settings" in my applications menu, getting that now.

Install the nvidia binary driver as suggested here [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Carter081 on 2008-01-16
so far ive followed the instruction to the point of Activating the driver

Once the driver is installed you need to set the system to use the driver. Open Konsole from K-Menu &#8594; System &#8594; Konsole and enter the command

sudo nvidia-xconfig

when i enter that command i get

> carter@carter-desktop:~$ suda nvidia-xconfig
bash: suda: command not found

---

### Post by Carter081 on 2008-01-16
im sorry if this is cuasing confusion...im kinda new to this but im willing to learn at all costs! omg no wonder its sudo not suda...gah im half asleep

---

### Post by kpkeerthi on 2008-01-16
It is sud**o** and not sud**a**

---

### Post by kpkeerthi on 2008-01-16
I suggest you copy/paste the instructions from ubuntu wiki. And btw, I suggest you use **gksudo** if you want to launch graphical applications in super-user mode.

---

### Post by Carter081 on 2008-01-16
Just did everything exactly as you implied and what the site information told me to do, everything is fixed. thanks for the help, really appreciate it

---

### Post by kpkeerthi on 2008-01-16
Glad you sorted it out. :)

---

### Post by Carter081 on 2008-01-16
Well i really made it easier on myself, when i first installed Ubuntu 7.10 as my OS i partioned the hard 50%. Well i just got done redoing my install and i formatted the whole harddrive, and this made a big difference. Once i logged on with the full format i got so many updates and i was able to change soo much and yet keep all my drivers. For anyone using Ubuntu and this may only be in my case, but if you want the full benefits of Ubuntu 7.10 you need to format the whole harddrive. Thats what happened in my point of view. So now im running WoW, yay. lol

---

### Post by hottls on 2008-01-16
@Carter081 - Thanks for the last post. I was having a similar problem and was trying to work through it when I read your post. Worked like a charm! :)

---

