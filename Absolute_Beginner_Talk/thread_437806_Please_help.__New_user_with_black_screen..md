---
title: "Please help.  New user with black screen."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Staticdrifter on 2007-05-09
Hello everyone.  My specs are:
amd64 dual core
2gigs ram
2 nvidia 7900s in SLI
19'' wide screen lcd monitor

I'm not looking to install ubuntu just yet, not until I can try it first.  I had several failed attempts with the live cd where it would go through the setup and then go to a black screen.  I tried different cd with 32 and 64bit versions all with the same result. The ctrl+alt+f# keys all work and I can get to a command prompt(new new new, i've no idea what to put here)

I recently came across wubi which lets me install through windows.  Everything seemed to go well with that except I have the same black screen. the f1, F3, f7, etc all work here as well I just don't know what to do to fix the problem.

I don't know if it's a driver issue, a resolution issue, or an install issue....or all the above.  Any help would be appreciated.

---

### Post by clpc on 2007-05-09
I had a similar problem and here are the notes I made when I solved it.

I noticed this message when I did a dmesg
BUG: soft lockup detected on CPU#0!

What I found is that if I left it sitting on the black screen for 10 to 15 mins it would eventually start the gnome desktop.

# Create a file with this:sudo gedit /etc/modprobe.d/nvidia
# Add this line to it:
options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=33 NVreg_DeviceFileMode=0666 NVreg_SoftEDIDs=0 NVreg_Mobile=1

# Then add this line...
Option         "ConnectedMonitor" "DFP"
# to the devices section of xorg.conf and then reboot and all should be okay

I hope this helps
Clive

---

### Post by hartz on 2007-05-09
You have dual graphics cards....

Please post the output from these two commands:

lspci

grep BusID /etc/X11/xorg.conf

You should try plugging your monitor in to the "other" ports (I believe each of your cards have 2 ports)  (This is true despite your being able to see text-mode login-screens)


Note: SLI will not work unless you install the nVidia legacy drivers - there are many guides on this forum on how to do that, but first let's just get SOME Graphical X display working.

  _Johan

---

### Post by Staticdrifter on 2007-05-09
Thanks for the tips guys. I'll get back to you with the results.  

Concerning the "waiting ... 15 minutes" that's exactly what I did when I installed with wubi.  Although I was testing out the different function keys to see what that would do and I either hit f5 or f4 and ctrl+alt when it brought up a screen that showed all the different things being installed, etc. So it was then that I knew something was actually going on and it didn't freeze up.  

I don't know if the live CD still had things going on behind the black screen.  I guess I was just too impatient.

Again, thanks for the tips and I'll post back shortly.

---

### Post by hartz on 2007-05-10
To get from the GUI, use CTRL+ALT+F1 (or F2 F3, etc).

To switch from one TTY console to another, just use ALT-F1, ALT-F2, etc.

To switch back to the (possibly black) GUI from a TTY console, use ALT-F7.

I seem to recall that the install log ran on Console nr 6.  I could be wrong.

Sometimes System messages about errors, etc are recorded on Console nr 8 too.

---

