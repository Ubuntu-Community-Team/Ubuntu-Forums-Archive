---
title: "Video card setup or not setup"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-09
I was wondering how to tell if my video card is setup properly. I am looking to start playing some games but not sure if my video card is installed correctly due to the fact that its very choppy. I know that it works fine on windows and have played Flight Sim X with very high graphics. so why is Lincity or other 3d games in ubuntu so choppy.:-k

---

### Post by sindrum_murdnis on 2006-11-09
Ohh i should probably add that it is geforce FX 5500.

---

### Post by Blutack on 2006-11-09
Are you using the nvidia accelerated driver?  Type glxinfo and look for this
direct rendering: Yes
If not try this
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
if it is try it anyway

---

### Post by taurus on 2006-11-09
You need to install a driver for your nVidia.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by punx45 on 2006-11-09
new nvidia drivers were also released in the past couple days:

[http://ubuntuforums.org/showthread.php?t=294992&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=294992&highlight=nvidia)

---

### Post by sindrum_murdnis on 2006-11-09
Wow thanks for the quick response. i went through the list of stuff that needed to be done and it seems to be working better now. Now im going to see about installing the new nvidia stuff. thanks:)

---

### Post by sindrum_murdnis on 2006-11-09
ok i guess i need to shutdown x server. any ideas on how this might be done. i goggled a bit and came up with ctrl-alt f4 but this isn't what im looking for ?:-k

---

### Post by taurus on 2006-11-09
No need to shutdown any X server first.  Just install nvidia-glx and then either edit /etc/X11/xorg.conf by hand, replacing nv wth nvidia, or run "sudo nvidia-xconfig" at the prompt.  Then, restart X with <Ctrl><Alt>Backspace.

---

### Post by sindrum_murdnis on 2006-11-09
ok now im kicking myself. i ended up shutting sown x server with /etc/init.d/gdm stop. then i starrted the nvidia setup found on the site above. well apparently i didnt have the right kernel for this install and completely messed up x windows](*,) . im running the live cd thankgod for that. ok any ideas on backing up the old data . i didnt see anyplace in the install that showed me the directory of where it would be stored. note the install says it backed everything up. or can do something eles maybe update the kernel? ohh well worst senerio i start fresh ;)

---

### Post by taurus on 2006-11-09
You don't have to reinstall it.  Just boot your machine to recovery mode from GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-reconfigure xserver-xorg
```

---

### Post by sindrum_murdnis on 2006-11-09
ok id first like to say if its not broke dont fix it. second thanks for showing me the reconfig file. i spent some time goin through and reconfiguring and came to the conclusion that the nvidia drivers had been changed there too. what i mean is that i select nvidia in the begining of the config file and that must have been changed cause the log file keeps giving me the same error message. soo im going to just reinstall itll go faster(just installed ilast night). this may have bothered me if it were someone else  computer but its my personal so whatever. thanks for all the help i now have a full page full of new commands.;)

---

### Post by taurus on 2006-11-09
Actually, it's best to use nv for now when you reconfigure your X.  And after everything is working again, then install nvidia for your graphic card...

---

