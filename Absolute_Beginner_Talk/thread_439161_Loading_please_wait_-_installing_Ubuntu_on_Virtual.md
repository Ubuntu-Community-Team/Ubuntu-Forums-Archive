---
title: "Loading please wait - installing Ubuntu on VirtualBox on Windwos XP"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-10
Hi,
1. On Windows XP I have installed VirtualBox 1.3.8.
2. Inside virtual machine I have configured virtual disk and mounted CD.
3. Inserted Ubuntu 7.04 Desktop CD into CD drive.
4. Started virtual machine.
5. Ubuntu windows has started from CD
6. I selected "Start or install Ubuntu".
7. Small "Loading Linux kernel" window pops up.
8. Then in upper left angle it displays "Loading, please wait..."

I have waited for 15 minutes and nothing is happening. It looks like windows is been frozen.

I have tried to restart virtual machine for couple of times, but no success.

Any idea what should I do to install Ubuntu?

Thanks,
Abcuser

---

### Post by echo $USER on 2007-05-10
try using the alternative install disk.  the live installer always crashed for me.

---

### Post by abcuser on 2007-05-10
I have selected "Start Linux in save graphich mode" and Ubuntu started installing. It looks like that Ubuntu/VirtualBox is not recognizing my graphipc card. But it is probably not Ubuntu problem, because it starts on LiveCD without any problem at all.

---

### Post by starcraft.man on 2007-05-10
Ok, first things first... there is no compatibility issue with your graphics cards, virtual machines (like virtual box) create a virtual environment entirely _SEPERATE_ from your main hardware. They use very generic hardware to support the widest range of OS, that said virtual machines do not offer high end rendering if you want things like beryl or games to run. They do usually make a bridge to pieces of your hardware like your ethernet line to connect to the internet. If your CD fails to install in virtual box, I suggest you go to their forums. I assume there is a problem with how they create their virtual environment. 

So your options are:

1) Go to virtual box forums and ask why it isn't working.

or 2) download and use VMware server (free) which I certainly know works with almost any Linux distro (including Ubuntu).

This forum however, is the Ubuntu forum, we support the main categories of Ubuntu and mostly straight installs and dual boots. Specialized things like lesser VM programs are best handled at their support forums, we can't be expected to know every program. I doubt theres anyone here using Virtual box, so if you wait here for a solution to this do not blame the forums because you receive no response.

---

### Post by abcuser on 2007-05-10
Hi,
I managed to install Ubuntu. Installation said I need to reboot, so I rebooted.

After restarat it stopes at "Starting up... Loading, please wait..." it looks like the same problem as before when tring to start up with normal start up.

Is there any option to start Ubuntu in low graphich mode?

BTW, I have tried installing VMware server, but it just deletes all my network settings on Windows XP - very strange and noone on VMware forum knew the answer. So VirtualBox is only option to run on my computer.
Thanks,
Abcuser

---

### Post by starcraft.man on 2007-05-10
> **abcuser said:**
> Hi,
I managed to install Ubuntu. Installation said I need to reboot, so I rebooted.

After restarat it stopes at "Starting up... Loading, please wait..." it looks like the same problem as before when tring to start up with normal start up.

Is there any option to start Ubuntu in low graphich mode?

BTW, I have tried installing VMware server, but it just deletes all my network settings on Windows XP - very strange and noone on VMware forum knew the answer. So VirtualBox is only option to run on my computer.
Thanks,
Abcuser

You can select recovery mode in the GRUB menu, it should be right under the first option.

Doesn't virtual box have instructions for installing Ubuntu on its site? 

As for VMware, I can say I've never in all my years using VMware heard of that. You may wanna try Parallels, or better yet a dual boot solution is usually easiest :)

---

### Post by abcuser on 2007-05-10
I have seleted recovery mode, but it hangs up too with message "Looding please wait".

I have noticed there is an "c" option to enter commands - it shows "grub>" command prompt. How to start ubuntu from command  in low graphich mode?

BTW, I don't want to use dual boot, because I need Windows as well, so I don't have time to boot up every time I need Windows.

---

### Post by starcraft.man on 2007-05-10
> **abcuser said:**
> I have seleted recovery mode, but it hangs up too with message "Looding please wait".

I have noticed there is an "c" option to enter commands - it shows "grub>" command prompt. How to start ubuntu from command  in low graphich mode?

BTW, I don't want to use dual boot, because I need Windows as well, so I don't have time to boot up every time I need Windows.

Like I said before abc, I don't think it has anything to do with how you boot Ubuntu, I am now almost certain it has to do with how Virtual Box has been coded/implemented.

Speaking of which... I just went to the Virtual Box [forums]("http://forums.virtualbox.org/") here. Is this program brand new? All posts are may 10.... I can't really say anything else, if its brand new it needs time to improve and fix bugs (like not booting ubuntu).

So if you can't use any other program, then I guess you have a problem... and I don't think anyone here can possibly help you if this program hasn't been around for more than days >.>

---

### Post by abcuser on 2007-05-10
There is only a new forum on VirtualBox. VirtualBox program is the only open-source virtualization program and it's there for some years.

I don't quite understand if I can install Ubuntu in "in save graphich mode", why can't I boot Ubuntu in "save graphich mode". There should be some way using grub command. But I just don't know which one.

---

### Post by abcuser on 2007-05-10
I have successfully start up Ubuntu from recovery console. Ubuntu was up and running - I started Firefox and went to internet.

But I don't know which key I have pressed on recovery console. So I have rebooted, but just don't know what key I have pressed - it look like as changing fonts - it looks like changing terminal settings or something like that. Can someone help me out what key I have pressed? I know I am very very very close to solution...

---

### Post by abcuser on 2007-05-10
I have found out solution! I am so :) :) :)

I have posted it on: [http://forums.virtualbox.org/viewtopic.php?p=37#37](http://forums.virtualbox.org/viewtopic.php?p=37#37)

---

