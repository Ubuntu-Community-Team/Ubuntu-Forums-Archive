---
title: "How do I load into the GUI?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by idontknow9999 on 2007-04-05
I often find myself crashed in Linux, in a Dos like screen (terminal I guess)... How do I get back 2 the GUI after I replace my broken config files with the backup (other then restarting)?

---

### Post by Nxion on 2007-04-05
Type this:


```
sudo /etc/init.d/gdm restart
```


Does that work for you ?

---

### Post by M$LOL on 2007-04-05
Never mind ^^^ got there before me.

---

### Post by idontknow9999 on 2007-04-05
> **Nxion said:**
> Type this:


```
sudo /etc/init.d/gdm restart
```


Does that work for you ?

Yes... But I am so sick and tired of gnome not working... 

I mean, getting a mouse 2 work cleanly should be easy for linux :(

---

### Post by Nxion on 2007-04-05
When you said that its always crashing, Does it only do it on a certain program ? Or a command that you do ? 

Maybe it is the video drivers that are causing the crashing ?

I had something similar happened to me along the same lines.

Maybe it is a hardware issue ?

Can you post the specs of your computer.

---

### Post by Nxion on 2007-04-05
Forgot to add,

type this in the command line to get the specs of your hardware

```
lspci
```

Also type this in the command prompt so see if something is failing with the video

```
cat /var/log/Xorg.0.log
```

---

### Post by idontknow9999 on 2007-04-05
> **Nxion said:**
> When you said that its always crashing, Does it only do it on a certain program ? Or a command that you do ? 

Maybe it is the video drivers that are causing the crashing ?

I had something similar happened to me along the same lines.

Maybe it is a hardware issue ?

Can you post the specs of your computer.

I meant all the times it crashes after I try 2 configure something...

This is getting very frustrating... I think something must be wrong with ubuntu, cause I used fedora and the mouse seemed fine.... but in ubuntu there is the nasty .2-.5 second delay on the click... 

What drives me completely crazy with Linux is the LAW that NOTHING will NEVER work on my first attempt... It is also very annoying when you go to fix one problem, but got to fix 2-3 others before you can fix the problem you want 2 fix :( 

Really makes you realize how comfortable you can be in windows :\

---

### Post by M$LOL on 2007-04-05
Trust me, once you get Ubuntu sorted, it will be heaven compared to Windows. My advice is stick with it.

What sort of mouse do you have? is it USB?

---

### Post by idontknow9999 on 2007-04-05
> **M$LOL said:**
> Trust me, once you get Ubuntu sorted, it will be heaven compared to Windows. My advice is stick with it.

What sort of mouse do you have? is it USB?

dude, look at my join date... its been a year and I still haven't gotten the most basic of devices sorted: my mouse.

It is a logitech g7 mouse.

---

### Post by Maestro23 on 2007-04-05
> **idontknow9999 said:**
> dude, look at my join date... its been a year and I still haven't gotten the most basic of devices sorted: my mouse.

It is a logitech g7 mouse.

What is wrong with you G7 under Ubuntu?  I have a G5 and it works great.

Some quick goolge links about G7/Linux(Although if you have seen them, disreguard):

G7 in Linux: [http://www.linuxlogin.com/hardware/logitech_g7.php](http://www.linuxlogin.com/hardware/logitech_g7.php)

[http://www.linuxquestions.org/questions/showthread.php?t=450126](http://www.linuxquestions.org/questions/showthread.php?t=450126)


Good luck.

---

### Post by M$LOL on 2007-04-05
> **idontknow9999 said:**
> dude, look at my join date... its been a year and I still haven't gotten the most basic of devices sorted: my mouse.

It is a logitech g7 mouse.

Have you asked the question before?

Maybe try [this thread]("http://ubuntuforums.org/showthread.php?t=219894")

---

