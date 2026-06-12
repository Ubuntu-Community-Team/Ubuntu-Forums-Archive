---
title: "I only get a command prompt...?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by bacon_sandwich on 2006-04-16
PLEASE HELP

After a couple of sleepless nights messing with my hardware, reflashing my bios, swearing and cussing, I finally got this ubuntu to finish installing. I think I had a bad RAM stick because removing it did the trick and stopped something called a "kernel panic".

Anyway, the thing finally installs, it asks me to take out the installation disc and then it reboots and starts installing packages (?) from the harddrive. This is where it freezes about halfway through. If I do a hard reboot, it will then start up and start ubuntu, but only to a command prompt. It lets me log in and I can do simple stuff (man, it's been a loooong time since I typed unix commands...)

What commands do I need to type to finish installing, or to start the installation process again, and/or get to the gui???

Thanks in advance!!!

---

### Post by aysiu on 2006-04-16
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by bacon_sandwich on 2006-04-16
[QUOTE=aysiu]```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```[/QUOTE]


I tried the sudo apt-get update and got the following error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

So I type 'dpkg --configure -a' and it tells me that the requested operation requires a superuser priviledge. I get the same for the second command. For the third command I get "command not found"

How do I get superuser priviledge? Or is there something else I should try?

Thanks again...

---

### Post by aysiu on 2006-04-16
You get superuser privilege by typing *sudo* in front of commands. For example, you would type ```
sudo dpkg --configure -a
``` Read more here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bacon_sandwich on 2006-04-16
[QUOTE=bacon_sandwich]I tried the sudo apt-get update and got the following error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

So I type 'dpkg --configure -a' and it tells me that the requested operation requires a superuser priviledge. I get the same for the second command. For the third command I get "command not found"

How do I get superuser priviledge? Or is there something else I should try?

Thanks again...[/QUOTE]



Ok, a little "info sudo" offers a lot of insight. Trying 
sudo dpkg --configure -a
looks like it's doing something....

---

### Post by bacon_sandwich on 2006-04-16
Ok,

It does a lot of setting up of python, libthis and libthat, but it is now stuck on setting up gstreamer0.8-audiofile (0.8.11-0ubuntu5)..


Is there a way to configure it to not try to set this one up?

---

### Post by aysiu on 2006-04-16
I don't know. What happens when you do ```
sudo apt-get -f install
```?

---

### Post by bacon_sandwich on 2006-04-16
[QUOTE=aysiu]I don't know. What happens when you do ```
sudo apt-get -f install
```?[/QUOTE]



Gives me the same message about the dpkg being interrupted, and to run dpkg --configure -a

---

### Post by bacon_sandwich on 2006-04-16
[QUOTE=bacon_sandwich]Gives me the same message about the dpkg being interrupted, and to run dpkg --configure -a[/QUOTE]


also, when i type gdm it says that "only root wants to run gdm"

---

