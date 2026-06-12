---
title: "VB - Seamless mode for one single Program not working"
date: 2012-03-23
forum: Any Other OS
---

### Post by membersound on 2012-03-23
HI,

I'm running a linux mint 12 system, and have one of these windows programs that I have to work with and cannot replace.
As it requires .NET 4 among serveral other things, Wine failed.
So I have to set up a VM System and run it every time I have to use the program.

My aim is to set the VM up in a way that ONLY the program window is show, and the entiry VM is hidden to the user, as if it would not exist. So: no taskbar, no vm-windows, no need to execute anything manual apart from launching a script.

I use VirtualBox and XPsp3.
The actual state is: when launching by console, I cannot get it to work in any case.
When starting manual by gui and switching manual to seamless mode, I can have a taskbar. I can launch programs from taskbar to have them single windowed.
confs: 1. Taskbar of windows, 2. task entry in linux taskbar, 3. a lot manual clicking to do


But maybe I'm missing something. There are so many tuts out there that say it should work.
Maybe someone can check my results and help me?



**startup manual** either:
VBoxManage startvm "XP" --type headless
VBoxHeadless --startvm "XP" --vrde=config --seamless

Host+L hotkey cannot be executed in both modes

*result when logged in:*
rdesktop -A -s notepad 192.168.178.113:3389 -u linux -p linux
rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe notepad" 192.168.178.113:3389 -u linux -p linux
>both show the full desktop, but do NOT launch the program

VBoxManage guestcontrol "XP" execute "c:\windows\notepad.exe" --username linux --password linux
>launches the program inside the vm, but does not show anything in linux (neither desktop nor program). But when I execute the command to show the full desktop, I can see the program was launched here.


*result when logged out:*
>both rdesktop show user quicklogin screen
>guestcontrol does not do anything!

--------

**Start VM by VM Manager:**
VM launches full desktop of course, so Host+L MUST be manual executed (so only taskbar is visible)
seamless mode only possible when logged in.

*result:*
Same as above with manual modes!!

How on earth can I get just a single program to linux?
Hope you could help  :cry:

---

### Post by Perfect Storm on 2012-03-23
Moved to Other OS/Distro Talk.

---

### Post by PhantomTurtle on 2012-03-23
I'm not sure if you can make it comepletly seamless, but you can still hide the Windows Taskbark. Just right click on the taskbar, click properties, and under the taskbar tab check autohide the taskbar. This will autohde the Windows Taskbar. Ofcourse when you move your mouse to the bottom of the screen it will appear again. If you get VMWare Player though, it has seamless mode like feature called unity which works much better. It does not show a big taskbar across your screen, instead it shows you a button from which you can launch programs from and additionally it looks much better than the vbox seamless mode. The only downside is that you have provide vmware with a lot of personal information to make an account and download it.

---

### Post by sup on 2012-12-14
> **membersound said:**
> HI,

I'm running a linux mint 12 system, and have one of these windows programs that I have to work with and cannot replace.
As it requires .NET 4 among serveral other things, Wine failed.
So I have to set up a VM System and run it every time I have to use the program.

My aim is to set the VM up in a way that ONLY the program window is show, and the entiry VM is hidden to the user, as if it would not exist. So: no taskbar, no vm-windows, no need to execute anything manual apart from launching a script.

I use VirtualBox and XPsp3.
The actual state is: when launching by console, I cannot get it to work in any case.
When starting manual by gui and switching manual to seamless mode, I can have a taskbar. I can launch programs from taskbar to have them single windowed.
confs: 1. Taskbar of windows, 2. task entry in linux taskbar, 3. a lot manual clicking to do


But maybe I'm missing something. There are so many tuts out there that say it should work.
Maybe someone can check my results and help me?



**startup manual** either:
VBoxManage startvm "XP" --type headless
VBoxHeadless --startvm "XP" --vrde=config --seamless

Host+L hotkey cannot be executed in both modes

*result when logged in:*
rdesktop -A -s notepad 192.168.178.113:3389 -u linux -p linux
rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe notepad" 192.168.178.113:3389 -u linux -p linux
>both show the full desktop, but do NOT launch the program

VBoxManage guestcontrol "XP" execute "c:\windows\notepad.exe" --username linux --password linux
>launches the program inside the vm, but does not show anything in linux (neither desktop nor program). But when I execute the command to show the full desktop, I can see the program was launched here.


*result when logged out:*
>both rdesktop show user quicklogin screen
>guestcontrol does not do anything!

--------

**Start VM by VM Manager:**
VM launches full desktop of course, so Host+L MUST be manual executed (so only taskbar is visible)
seamless mode only possible when logged in.

*result:*
Same as above with manual modes!!

How on earth can I get just a single program to linux?
Hope you could help  :cry:

The same problem here on Ubuntu 12.10. No matter what I do, I cannot get single window.

---

### Post by sup on 2012-12-15
> **sup said:**
> The same problem here on Ubuntu 12.10. No matter what I do, I cannot get single window.


Try to look at this, it works even though it is cumbersome: [http://superuser.com/questions/519545/what-is-the-difference-between-startup-programs-in-windows-and-the-same-programs](http://superuser.com/questions/519545/what-is-the-difference-between-startup-programs-in-windows-and-the-same-programs)

---

