---
title: "Edgy Installation Problem"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by saadakhtar on 2007-01-12
i am trying to install edgy on my desktop but same as before i am getting "**Input not supported**" message since i am using a wide screen mointor with res: **1600 X 1280** and a graphics card **Nvidia FX5500**. when i installed dapper i got to this problem after the installation was complete and all i had to do was, install the nvidia drivers and edit my X11 configuration to match my monitor.
Now that i am trying to install edgy, the same problem is happening again but worst. Edgy installation is a series of steps that are designed with GUI so as boot from the installation cd the system boots into edgy live and the screen goes black with the same old message "Input not supported". i have made the same install on my laptop. booted into edgy live and installed   it without any problems since my graphics card on my laptop seems to be compatible with it.
anyone has any ideas to work around this problem.
any help would be appreciated.


** enjoying the 5 cups of ubuntu and lovin it **

---

### Post by MasterOfDisaster on 2007-01-13
Well, you could either install with the Alternate install cd and do what you did before, or:

Wait for the cd activity light to go off, then press Ctrl-Alt-F1 so the terminal appears.  Enter 'sudo nano /etc/X11/xorg.conf', and go down to the Screen section.  And note the DefaultDepth.  Go the the 'SubSection "Display"' with the Depth the same as the DefaultDepth, and change the first resolution to 1600x1280, then delete all the resolutions higher.

Press Ctrl-O to save, then Ctrl-X to exit.  Then press Alt-F7, and wait a couple seconds, then restart the X server (Ctrl-Alt-Backspace).  Hopefully that should do it.

---

### Post by msak007 on 2007-01-13
Have you tried the Safe Graphics mode? I've had problems installing in the past, but it's been due to my ATI card not being supported by the open source driver so Safe Graphics mode worked by loading vesa. I've been able to install (using a 1680x1050 monitor) using that mode, so it's worth a shot.

---

### Post by MasterOfDisaster on 2007-01-13
That didn't work for me with the same resolution monitor...  Then again, I do have an nvidia card.  Had to do it the way described above.

---

### Post by saadakhtar on 2007-01-13
just tried the above procedure and it worked smoothly.
appreciate the help.
thanks

---

