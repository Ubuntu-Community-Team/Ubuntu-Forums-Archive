---
title: "Help me please"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by winzhangout on 2007-01-06
I try to install ubuntu and kubuntu with same result, if i choose testt cd it says that it ok without any errors.

And if i choose install i get up the ubuntu loading screen , and after that io get an sound i think its the starting sound of ubuntu. But my screen gets all black i have tried if several times with same result can anyone help me please?? The desktop version says wrong kernel so i stick to amd 64 desktop version of both kubuntu and ubuntu.

I have an Asus A7D laptop with Amd 64X, 1024mb memory, Ati Radeon X700

---

### Post by Sasa_Ivanovic on 2007-01-06
what version are you trying to install ?
do you get an error message ?

---

### Post by winzhangout on 2007-01-06
Its the newest 6.1 and i dont get any error message and the computer seems to not freese because when i hammer on my keys the harddrive lamp light and sounds like it work. Just the black screen.
Should i try earlier version maybe??

---

### Post by 3rdalbum on 2007-01-06
Press Control-Alt-F1 after the sound plays.

You should be brought back to a terminal. Log in with your username and password, and then type the command:

```
sudo dpkg-reconfigure xserver-xorg
```

Tell it not to autodetect the video card or monitor. When it asks you to specify a driver for the video card, choose "vesa". Anything it asks you about that you don't understand, hit OK for. When it asks you about the monitor, choose "no" autodetection and then choose to set it up the "simple" way. (this will make sense when you actually start doing it)

When that's all done, and you're back at the command line, type:

```
sudo reboot
```

and see if that works.

---

### Post by winzhangout on 2007-01-06
I have try to ctr alt f1 and i come to command field so now im sure it dont freese. I try to change it the way you describe but when i sudo reboot, it stand that i have to take out the cd and press enter and even if i do so it stand take out cd.

When i reboot with the start button it stand the useally install or start ubuntu and when i choose this i get the same problem, any suggestion??

---

### Post by winzhangout on 2007-01-06
i think the save of configure will be overwritten when i have to start with start button. Please help me sort out how to install ubuntu. Im sure it has something to do with this.

---

### Post by winzhangout on 2007-01-06
anyone??

---

