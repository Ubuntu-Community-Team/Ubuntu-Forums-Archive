---
title: "Slimmed down version of Ubuntu (only need enough programs/services to run Wine)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by FrozenDice on 2008-04-02
I have a program written in Delphi which is only Win32.  Now for everyone with 64bit (Windows of Linux) they can't run the program.  To overcome this I was thinking of posting a virtual machine of Ubuntu with everything extra stripped from it that isn't nessicary to run Wine and just have them get VMWare player and run the VM using wine to access the program.  Now if I can slim Ubuntu down enough and pre-install the program this shouldn't be too difficult to do.

When I go to install Ubuntu on a virtual machine I click the install icon from the cd in live mode, and it installs.  The problem is unlike other dristros I don't get a chance to remove/add stuff, in this case remove.

How can I do this?  I know Linux isn't always the answer, but it seems like it would work this time.

---

### Post by lswest on 2008-04-02
you can install a server version, or install Debian instead, it's customizable to the point of being overwhelming :P

---

### Post by doorknob60 on 2008-04-02
Maybe download the server version of Ubuntu and Install Gnome (Or a lighter WM like Fluxbox or Xfce) and Wine. I don't have much experience with thit, but it should work pretty well. Also, I recommend VirtualBox over VMware because it's open source.

---

### Post by Jerry N on 2008-04-02
Have you established that your program will even run under Wine?  This all sounds like a long shot - install Linux on a Windows machine in an emulator environment and then install Wine which is a limited Windows environment in Linux and then install your Windows program.  Sure looks like a lot of things that can go bad along the way!

Have you looked at Damn Small Linux?  It can probably be run in a virtual machine and IF it will run Wine maybe you could re-master DSL to include Wine and your Delphi program.  I haven't done any of those things so I am just tossing out possibilities.  

Jerry

---

### Post by FrozenDice on 2008-04-02
Yes, the program has been running on Wine for a few months now and no reported problems.  Although, this has been on Linux 32 bit machines.  When we have a user which has 64 bit linux they're out of luck, and 64 bit windows for that matter.

Can VirtualBox run virtual machines made in VMWare Workstation?  Or do I have to build the VM in VirtualBox?

---

