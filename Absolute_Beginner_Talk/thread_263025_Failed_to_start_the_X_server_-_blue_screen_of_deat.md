---
title: "Failed to start the X server - blue screen of death :("
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by sketchone on 2006-09-22
i rebooted my linux machine and am now getting a blue screen of death with this message

Failed to start the X server (your graphical
interface). It is likely that it is not set 
up correctly. Would you like to view the X
server output to diagnose the problem?

Please help, what do i do to fix this :( :confused:

---

### Post by jcrnan on 2006-09-22
did you change anything in xconf before you rebooted?

Does it give you a yes/no option or such when you get that error message?

---

### Post by sketchone on 2006-09-22
thanks for the reply- yes it does give me yes & no options

no i didnt change anything

any ideas

---

### Post by Brunellus on 2006-09-22
1) get out of the BSOD;  hit return twice.

2) You'll see a scary black and white textmode login.  log in.  Note that nothing will appear when you type your password.  This is normal--prevents guys from reading how many characters are in your password over your shoulder.  Yes, UNIX admins are that paranoid.

3) Kill GDM.

```
 sudo /etc/init.d/gdm stop 
```

4) Reconfigure!

```

sudo dpkg-reconfigure xserver-xorg
```

5) follow the prompts.  

6) reboot.

That should get you a GUI.  

Meanwhile, tell us what you were doing before this happened?

---

### Post by sketchone on 2006-09-22
thanks il try that now

dont think i did anything - i remember i auto updated my pc and it told me to reboot, thats when it went wrong

---

### Post by bulldog on 2006-09-22
No restricted modules I guess,had the same issue with the new kernel-update.

Type uname -r 
which gives you your kernel specs.

sudo aptitude install linux-restricted-modules-here your kernel

Should do it.

---

### Post by sketchone on 2006-09-22
> **Brunellus said:**
> 1) get out of the BSOD;  hit return twice.

2) You'll see a scary black and white textmode login.  log in.  Note that nothing will appear when you type your password.  This is normal--prevents guys from reading how many characters are in your password over your shoulder.  Yes, UNIX admins are that paranoid.

3) Kill GDM.

```
 sudo /etc/init.d/gdm stop 
```

4) Reconfigure!

```

sudo dpkg-reconfigure xserver-xorg
```

5) follow the prompts.  

6) reboot.

That should get you a GUI.  

Meanwhile, tell us what you were doing before this happened?

i did this and went through the setting - im now back at the terminal, what should i do now? :(

---

### Post by Brunellus on 2006-09-22
did you reboot?

```

sudo reboot
```

---

### Post by bulldog on 2006-09-22
.

---

### Post by sketchone on 2006-09-22
rebooted and it done it again

failed to start the x server

---

### Post by Brunellus on 2006-09-22
what hardware are you running?

---

### Post by sketchone on 2006-09-22
just an nvidia tnt2 32 meg graphics card
dell 17" monitor
amd 1.4 athlon
dont know the board
and 512mb sd ram

---

### Post by desjazz on 2006-10-21
Hello,

I have the same problem and i have tried a number of fixes and got nowhere. I am unable to get the GUI up and i am not expert enough to do what I want to without it. Can someone help me with this?

---

