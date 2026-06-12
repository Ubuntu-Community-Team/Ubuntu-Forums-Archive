---
title: "[SOLVED] wine"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-19
im trying to run yahoo messenger in wine so i can use my phone, but cant get anything out of wine - how do i use wine? i checked google and all the things they said to type in the terminal didnt work.

---

### Post by Captainm on 2008-03-19
What do you mean didn't work? Could you past the result of the command(s) you tried?

---

### Post by N1N31NCHN41L5 on 2008-03-19
i was doing it on my laptop at work - so i dont have the results - maybe i just dont know how to run wine

any help at all.... i'll run whatever u suggest to try it out

---

### Post by Captainm on 2008-03-19
Normally the command would be: ```
wine /path/to/program.exe
``` Are you sure wine is installed correctly?

---

### Post by N1N31NCHN41L5 on 2008-03-19
how do i find the path to ymsgr on my windows hard drive? yes its installed correctly its even in the program menu.

---

### Post by Captainm on 2008-03-19
The easiest way to install is to just download the installer from the Yahoo website and use wine to install it. So if the installer is on your Desktop you'd  type:

```
wine ~/Desktop/installer.exe
```

---

### Post by N1N31NCHN41L5 on 2008-03-19
download the regular windows version of yahoo messenger on here and run the setup through wine???

---

### Post by Captainm on 2008-03-19
Yup. That should work.

---

### Post by Faud on 2008-03-19
Just make sure that you have wine set up correctly..after you installed it(hopefully you did it from the repos) then you should have opened a terminal and typed [code]winecfg{/code} That will set up a hidden folder in your home folder called .wine (the . because it's hidden) So go to your home folder and then use the option to see hidden folders and you can follow the path that the setup puts for your messenger.
Good luck.

---

### Post by N1N31NCHN41L5 on 2008-03-19
i installed iit in add/remove and it did alll the work for me - didnt do that thing in the terminal - should i go do that now???? ag=fter i downloaded yahoo wine autograbbed it anbd stated the install but it stuck at 95%

---

### Post by undertakingyou on 2008-03-19
> **N1N31NCHN41L5 said:**
> i installed iit in add/remove and it did alll the work for me - didnt do that thing in the terminal - should i go do that now???? ag=fter i downloaded yahoo wine autograbbed it anbd stated the install but it stuck at 95%

You should run the commond ```
winecfg
```  Do that and then try and install the messenger again.  
Also, are you just installing yahoo's thing for some capability with your phone?  If you are looking for a chat client pidgin should already be installed and can do yahoo chat.

---

### Post by N1N31NCHN41L5 on 2008-03-19
GyachE doeas voice and cam and yahoo chat rooms, qnext does voice and cam and supports multi account login across multi platform BOTH a ton better than Pidgin. I just need yahoo for my voip. I have voive in and out and a cordless phone for yahoo - other than that its about qnext

---

### Post by N1N31NCHN41L5 on 2008-03-19
this is what i got:

josh@xubuntu:~$ winecfg
[code]winecfg{/code}
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
josh@xubuntu:~$ [code]winecfg{/code}
bash: [code]winecfg{/code}: No such file or directory

---

### Post by undertakingyou on 2008-03-19
There is supposed to be winecfg, and I see that here on my system.  There should also be ```
wineconfig
``` try that. :)

---

### Post by N1N31NCHN41L5 on 2008-03-19
winecfg brought up a configuration box - what do i change in it -= it had no audio drivers so i got 1 by default now - what next?

---

### Post by undertakingyou on 2008-03-19
The main thing with that box coming up is that it creates the ~/.wine directory and sets up your devices.  C: (which is the ~/.wine directory) and then Z: which is your home drive.  Using the tabs you could check to see if those are there and double check that your compatability is set to what you want, I use XP.  Then say ok or apply or whatever it is and you are good to go.  Then you can try reinstalling your app.

---

### Post by N1N31NCHN41L5 on 2008-03-19
the app is on the desktop now and i click on execute butit starts logging in then dissapears - it couldnt log in the first time so i changed settings to firewall no proxies and now it dissapears... hmmmm thanx for the help

---

