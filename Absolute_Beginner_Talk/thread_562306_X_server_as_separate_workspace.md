---
title: "X server as separate workspace?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by stewartbutler on 2007-09-28
Have a relatively simple question. I have VMWare Workstation installed on my distro of Ubuntu 7.01 Feisty, and when VMware runs it outputs the window output to the Alt-F9 x server. Is there any way to access that server from a second workstation?

Alternatively, is there any way to force that to Alt-F8 instead? It is currently filled by what appears to be kernel output from the bootup process.

---

### Post by USPB on 2007-09-28
Yeah I also have the same question. Hope someone can answer

---

### Post by HermanAB on 2007-09-28
I don't get it.  I run VMware workstation myself and I don't have any idea what you are doing...

To open a VMware console, I simply run the application called 'vmware' (which is somewhere in a menu) from where I can control all the virtual machines.  Each virtual machine is set up to run bridged networking and has a unique IP address.  

If one start a machine and quit 'vmware', the machine will keep running in the background and then one can SSH (or rdesktop if Windoze) to it from any other machine on the LAN.

So, uhmm, what the heck are you doing to get output on consoles F8 and F9 and why?

Cheers,

Herman

---

### Post by funrider on 2007-09-28
are you talking about remote control from or exporting the display to other machine? to make either of these happens, first you should be sure that the other machine can access ur VM thru network.

---

### Post by stewartbutler on 2007-09-28
Alright, to see what I am talking about, open up a vm. After the machine loads, so you can actually do stuff in it, hold down Ctrl + Alt and press the F series keys, it is probably 8 or 9. You will get to a screen that shows the VMware output. I want to access that from one of the Gnome Workspaces on my primary virtual screen (Ctrl + Alt -- F7), so I can switch between my primary ubuntu desktop and my VM (windows) desktop by using control + alt + direction key, using the standard workspace switcher. 

One thought I had was to find a full-screen VNC client that runs in a dedicated Gnome workspace, but I haven't been able to find one. Then I could simply VNC into the machine locally, while it runs as a daemon. Does anybody know of such a VNC client?

---

