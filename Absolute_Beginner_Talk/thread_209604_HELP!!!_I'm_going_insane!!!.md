---
title: "HELP!!! I'm going insane!!!"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-05
I have been using Windows since the first version of 95. I know what I am doing there. I want to try Linux. I want to learn to use it. Nothing is the same, I cant find things, I cant do things. It is driving me nutz!!
I have installed several programs using Synaptic Package Manager. I look thru all the menus and sub menus and cant find a referance to them. I go back and check "installed" app's in Synaptic and it says they are there. How do I find these programs to use them?  ndiswrapper, g++ 4.0, wine. Dont they have an interface of some kind so they can be used?
I know, your thinking I have used Windows too long....you are right. I'm not ready to give up. I am cluelessly lost.

---

### Post by %hMa@?b&lt;C on 2006-07-05
if they dont show u in the menu, try restarting your Gnome-Panel. from terminal (applications>accerories>terminal)
type
```
killall gnome-panel
```
if they dont show up then, try to run the program from the terminal.
for setting up wine, type
```
winecfg
```
then to run the executables type 
```
wine /path/to/executable.exe
```
to run ndiswrapper type
```
ndiswrapper
```

---

### Post by mvaniersel on 2006-07-05
Those programs you mention are command line programs (at least g++ and wine, I'm not sure about ndiswrapper).

For example, go to Applications->Accesoires->Terminal
type g++ --help
and it prints a list of options.
Since you mention g++ I'm assuming you want to do some C/C++ programming. If you don't want to do that from the command line, I suggest looking into more user friendly Integrated development environments such as Anjuta.

If you want a very user friendly way to run windows programs, look into crossover office. It costs $40, but you can try it out for free for 30 days.

---

### Post by zhoux on 2006-07-05
[quote=mvaniersel] 
If you want a very user friendly way to run windows programs, look into crossover office. It costs $40, but you can try it out for free for 30 days.[/quote]

if you have a decent pc and a copy of windows cd w/ you, then you can try VMware Server/Player...they are free and fairly easy to setup...

---

### Post by MaximB on 2006-07-05
[QUOTE=zhoux]if you have a decent pc and a copy of windows cd w/ you, then you can try VMware Server/Player...they are free and fairly easy to setup...[/QUOTE]

BTW - I never understood/tried VMware - what is it excactly ?

---

### Post by zhoux on 2006-07-05
VMware is short for virtual machine.  This software allows you to run another OS on top or within another OS.

For example...i can run Windows XP within Ubuntu....so i can switch between OS's without reboot....

So i guess, it is similar to a dual boot...without the booting...

Of course, the downside of it is that it uses alot of resources....

EDIT: if you want to try VMware...this thread/HowTo details the steps in installing free WMware Server:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

