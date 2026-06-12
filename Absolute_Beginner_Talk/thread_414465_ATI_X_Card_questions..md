---
title: "ATI X*** Card questions."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by igknighted on 2007-04-19
> **Mike said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853") that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.
[LIST=1]
[*]Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
[*]Start text mode installer and install Ubuntu/Kubuntu.
[*]Finish Install and reboot.
[*]Update package list and upgrade any packages needed.
```
sudo apt-get update
sudo apt-get dist-upgrade
```
[*]Install fglrx closed source driver for ATI video cards.
```
sudo apt-get install xorg-driver-fglrx
```
[*]Update loaded modules.
```
sudo depmod -a
```
[*]Configure /etc/X11/xorg.conf
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
[*]Reboot[/LIST]
Ubuntu 7.04 should now boot into GDM/KDM.
Does this mean that x**** cards that have used the free drivers in the past are no longer able to do so in any way?  Seems like a pretty serious bug, perhaps worthy of a delay? :confused:

---

### Post by markl187ld on 2007-04-19
I did this yesterday on my 9600 and was unable to use the GL Desktop due to the composite extension being disabled by the driver.

---

### Post by fickleflame on 2007-04-19
I'm having the same problem.

I've been reading through the Bugs already logged and comments made today about the release version are all saying that ATI X**** cards wont work. Looks to be a MacBook Pro problem as well.

Back to Vista for me. :(

---

### Post by leogibson on 2007-04-19
i think a 9600 is not of the X*** variety...are you having this problem anyway?

---

### Post by neodarksaver on 2007-04-19
I am using the 64-bit version becasue i have a turion64 processor, so that means i should use the alternate CD for 64bit right?

---

### Post by Ek0nomik on 2007-04-19
sudo apt-get update

99% [Connecting to us.archive.ubuntu.com (91.189.89.6)]

I have been sitting on this for about 10 minutes.

---

### Post by electroconvulsive on 2007-04-20
I have a ATI Radoen 9200 SE in my machine and after about 2 or 3 restarts using the default desktop fx (compiz I think) my x-server broke and I was stuck at before my login screen. Thanks for the advice I will give it a go after reinstalling. The initial install was a bit of a failure all round so I'm going to start again.

---

