---
title: "Hibernation Problems!!!!!!!!"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-03-04
I hibernated Kubuntu and when I came back and turned it on after the boot screen, it was blank... I shut it down manually (the "wrong" way) and when I restarted it, I saw a message flash saying something about the system (it was too fast, I didn't get much else). Then all there was was the boot splash with nothing loaded, then the virtual terminal. I pressed Ctrl-Alt-F7, but it was blank, so I logged into the virtual terminal and shutdown from there and rebooted to Windows. How do I fix this problem?!

---

### Post by chggr on 2007-03-04
try to restart your PC and boot up to linux. See if the problem persists. 

If it does, on the terminal give this command:
sudo dmesg | tail
and see if there is a problem reported there

---

### Post by i-am-me on 2007-03-04
It still doesn't work after several reboots and there is no problem reported. I've heard that Ubuntu has problems with suspend and hibernate. Is there any way to fix it other than reinstalling the OS? Anyone?

---

### Post by chggr on 2007-03-05
If you have access to the terminal, this means that only the GUI is faulty. Try reinstalling Gnome or KDE using the terminal...

---

### Post by i-am-me on 2007-03-05
> **chggr said:**
> If you have access to the terminal, this means that only the GUI is faulty. Try reinstalling Gnome or KDE using the terminal...

How do I do that? Anyway, I typed in kwin (KDE Window Manager) into the virtual terminal and it said that it couldn't connect to the X-server. Does change what you should about re-installing KDE?

---

### Post by BrowneR on 2007-03-05
thats correct, you cannot run the window manager without an X server. To restart the Xserver (and kde) try the following command:

```
sudo /etc/init.d/kdm restart
```

that should get you into a gui or at least give an explanation as to why the Xserver is failing to start.

---

### Post by i-am-me on 2007-03-07
> **BrowneR said:**
> thats correct, you cannot run the window manager without an X server. To restart the Xserver (and kde) try the following command:

```
sudo /etc/init.d/kdm restart
```

that should get you into a gui or at least give an explanation as to why the Xserver is failing to start.

That was actually the first thing I tried when I found out that the X server couldn't be connected to by kwin. As an experiment I typed in 

```
sudo /etc/init.d/kdm start
```

and it said that it was already running. I also typed in

```
X
```

and it said that no screen was found (or something similar)

---

### Post by BrowneR on 2007-03-07
sorry i didnt realise you had tried that.

there might be some clues in the Xorg log files. check out  /var/log/Xorg.0.log

```
 cat /var/log/Xorg.0.log | less 
```

if you post anything suspicious here i'll take a look.


you could also try reinstalling the Xorg packages on your system in case something has been corrupted:

(you may want to backup your /etc/X11/xorg.conf)

```
 sudo aptitude reinstall ~nx11 ~nxserver ~nlibx 
```

that should select most if not all of the xorg components and reinstall them (warning 140+ packages which amount to about 25Mb download!)

that seems very drastic to me but it shouldn't case you any problems (your not removing or adding any packages), you may wish to get a second opinion first though :S

you could also execute something similar to reinstall some kde components. maybe this would help (although i am a gnome user myself):

```
 sudo aptitude reinstall kwin kdm 
```

sorry i cant be much more help.

---

### Post by i-am-me on 2007-03-08
Xorg.0.log at the very end displays:

```
NVIDIA(0):   Failed to load the NVIDIA kernel module!
NVIDIA(0):   ***Aborting***
```

Then it says the whole no screens found stuff.

At the end of reinstalling ~nxll, ~nxserver,  and ~nlibx, it says:

```
Writing extended state information... Error!

E: I wasn't able to locate file xserver-xgl package. This might you need to manually fix this package.
E: Couldn't lock list directory... are you root?
```

Yes, I used sudo before the reinstall command, so I have no idea why it asked me if I'm root.

Reinstalling the windows manager didn't work either...

Should I just reinstall the OS? It'll only take me a week or two to get it back to where it is now... I'll never use Hibernate or Suspend until the Ubuntu community officially fixes the bug.

---

