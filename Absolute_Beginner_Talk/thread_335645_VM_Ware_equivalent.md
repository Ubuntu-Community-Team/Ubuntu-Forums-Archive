---
title: "VM Ware equivalent?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-01-10
I still haven't found a solution to the wireless card problem I posted about awhile ago, but I have been dealing with cable connections and it's not so bad :) I'm not that mobile anyway (I say that now, but I may regret once next semester starts).

On an unrelated note I was wondering if there is any program like VMware for Linux? What I mean is, as I understand it, VMware boots only Windows in a Linux/Mac/Windows environment, allowing you to use Windows programs in a Windows environment without emulators, WINE, etc. But for some reason ResNet (how user's authenticate to access the internet at my univ.) does not like Linux machines. At all. Especially my machine, it would appear for all the pain and going into admin files that I probably wouldn't have ordinarily discovered until much later. My point is usually when I am troubleshooting my new OS I need the internet, and usually when I am troubleshooting the OS I have no internet. I was hoping there was some equivalent that would allow me to boot Ubuntu in a Windows/Mac/Linux environment in a similar way that VMware allows users to use Windows. Then I could boot into Windows and troubleshoot the Linux OS without rebooting back and forth.

Thoughts?

---

### Post by insane_alien on 2007-01-10
vmware has a linux version. i'm writing this from feisty running in vmware server. i've also installed XP, win98, and OSX in it so it definitely works.

---

### Post by nonpareilpearl on 2007-01-10
So I misunderstood when I assumed that VMware would only boot Windows in a given environment? It will also boot Linux and etc.? Does it work with Ubuntu 6.10 do you know?

---

### Post by SoggyCornflake on 2007-01-10
> **nonpareilpearl said:**
> IOn an unrelated note I was wondering if there is any program like VMware for Linux? What I mean is, as I understand it, VMware boots only Windows in a Linux/Mac/Windows environment, allowing you to use Windows programs in a Windows environment without emulators, WINE, etc. But for some reason ResNet (how user's authenticate to access the internet at my univ.) does not like Linux machines. At all. Especially my machine, it would appear for all the pain and going into admin files that I probably wouldn't have ordinarily discovered until much later. My point is usually when I am troubleshooting my new OS I need the internet, and usually when I am troubleshooting the OS I have no internet. I was hoping there was some equivalent that would allow me to boot Ubuntu in a Windows/Mac/Linux environment in a similar way that VMware allows users to use Windows. Then I could boot into Windows and troubleshoot the Linux OS without rebooting back and forth.
Thoughts?

you might try [***bochs***]("http://bochs.sourceforge.net/").  It's sorta like a free version of VMWare.  I haven't tried it so, I can't tell you much more than that.

---

### Post by Iarwain ben-adar on 2007-01-10
AFAIK,
if you have no internet on your host, your client won't have internet access aswell :wink:

Might keep that in mind


Iarwain

---

### Post by nonpareilpearl on 2007-01-10
> **Iarwain ben-adar said:**
> if you have no internet on your host, your client won't have internet access aswell :wink:

lol yeah that's true, however all Internet functions normally with Windows. Basically it is a known problem that Linux and ResNet (the authentication system I mentioned) don't speak well. Some user's have made a few fixes that have worked on their machines, but they don't work all the time. I tried various ideas from people I work with (I work for the Computer Information Technology Dept., ironically), none of them worked-even when combined. My last resort was the router, and that seems to have fixed most problems except for the authentication. If I boot into Windows to authenticate it works fine, even if I boot into Ubuntu after.

---

### Post by jd65pl on 2007-01-10
> **SoggyCornflake said:**
> you might try [***bochs***]("http://bochs.sourceforge.net/").  It's sorta like a free version of VMWare.  I haven't tried it so, I can't tell you much more than that.

VMWare is free of charge and has the source available also so in essance is also "free" Qemu is an alternative to vmware put I found it to be a lot less comprehensive and developed as vmware.

J

---

### Post by G Morgan on 2007-01-10
Depending on your hardware you could get KVM + Qemu working when Ubuntu moves to a 2.6.20 kernel (no idea when that will be, 2.6.20 isn't even out yet). Qemu with the Qemu accelerator is also quite good. The best option by far is VMware Server though.

You won't be able to get net access for Windows running as a guest on a Linux host if that host has no net access in any case. It would likely work the other way around though if you're desperate enough to install Windows.

---

### Post by nonpareilpearl on 2007-01-10
Actually I already have Windows, I figured until I worked out the kinks it would be a good idea to dual boot. Guess that was a good idea, considering how Linux and ResNet get along! :)

---

### Post by nonpareilpearl on 2007-01-11
I have decided to go ahead and install VMware.  Currently I am working on installing it in Linux to run Windows. I have been attempting to install it using the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=183209"), but when I enter the apt-get line I receive an error stating that it couldn't find the linux-headers package. Help?

---

### Post by jvc26 on 2007-01-11
Have you enabled all the extra repositories?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
It may well be the case that you dont have the repos active - follow the instructions in that link then try your instructions again.
Il

---

### Post by nonpareilpearl on 2007-01-11
Thanks for the help, I was able to figure it all out :)

Now all I have to do is figure out how to run it :-/

---

### Post by jd65pl on 2007-01-12
The howto: you posted earlier is good follow the howto.

---

### Post by fsando on 2007-01-12
wmvare works fine for me in a normal gnome session (and under windows too)
I have one problem with wmvare:
When I log into an Xgl session (to use beryl) wmvare refuses to run in fullscreen
I have ati x1600 (fglrx driver 8.28.8 )
Have anybody had this problem?

---

### Post by LookTJ on 2007-01-12
> **fsando said:**
> wmvare works fine for me in a normal gnome session (and under windows too)
I have one problem with wmvare:
When I log into an Xgl session (to use beryl) wmvare refuses to run in fullscreen
I have ati x1600 (fglrx driver 8.28.8 )
Have anybody had this problem?
I don't think vmware is used for video drivers.

---

### Post by fsando on 2007-01-12
> **Taylor said:**
> I don't think vmware is used for video drivers.

Sorry but I'm not sure I understand your answer.

When running a gnome session I can have some tasks running in windows in wmvare full screen. The advantage of fullscreen is that it runs much faster and it looks as if windows is host.
I would like to do the same on the beryl cube - being able to scroll/turn up the windows/wmvaare session. and then run it fullscreen for performance.
Right now I have to log in normal gnome session if I want to do something serious (ie. fullscreen) with wmvare.

EDIT: the reason for my mentioning the ati driver is that from all my reading on this subject it may have something to do with the problem (I don't know though). This is, of course, the driver for the linux host. Wmvare has it own emulation of some sorts.

---

### Post by bernied on 2007-01-12
EDIT - deleted - sorry didn't read second page of thread

---

