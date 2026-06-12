---
title: "Install ATI Driver?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by cabal2000 on 2008-03-09
I have installed the newest ATI driver for my Dell 1521 Laptop but on there website it tells me to uninstall the present driver.

Uninstalling the ATI Linux Proprietary Graphics Driver

Un-installing the ATI Linux Proprietary Driver is dependent on the mode of initial installation.
Automatic or Custom Driver Installations

If the ATI Proprietary Linux Graphics Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh" 

You have now successfully uninstalled the ATI Linux Proprietary Graphics Driver. 

But i am very new at this and really don't know how to do this?

---

### Post by Rocket2DMn on 2008-03-09
Unless you enabled the Restricted Driver for your ATI card (you would know if you did), then you don't need to worry about this.
To answer the question though, you can open a terminal from Applications->Accessories->Terminal
To change a directory, you use the "cd" command
```
cd /usr/share/ati
sh ./fglrx-uninstall.sh
```

Don't be afraid of the terminal, it is a very powerful tool.  For more info, see here - [http://linuxcommand.org/](http://linuxcommand.org/)
I know it might seem overwhelming, but just take it slow, you learn as you go.

---

### Post by hhhhhx on 2008-03-09
or envy might be good if your not up to the terminal just yet, but i would advise using the terminal :)

---

### Post by cabal2000 on 2008-03-09
need help. I did what you told me and rebooted the system now I just get a black screen?

---

### Post by hhhhhx on 2008-03-09
can you boot in graphics safe mode, or is it completely trashed?

---

### Post by seijling on 2008-03-09
Whats the hardware?  radeon, mobility, ???

---

### Post by cabal2000 on 2008-03-09
how can i boot to safe mode?
When I press esc on boot up it does not give me that option

---

### Post by hhhhhx on 2008-03-09
> **cabal2000 said:**
> how can i boot to safe mode?
When I press esc on boot up it does not give me that option
ssry, i ment recovery mode, also what is your hardware?

---

### Post by Rocket2DMn on 2008-03-09
Can you please post a link to the guide you were following.  Also, what is your video card model?
The drivers you need for ATI cards are available in Ubuntu, either the open source ones or the restricted ones, you don't need them direct from ATI.
Once we have this info, we can reconfigure X (the GUI).

---

### Post by cabal2000 on 2008-03-09
I do get a recovery mode but it stops at a root@edwards-laptop:~#
I have a Dell 1521 laptop with a ATI x1200 graphics card. Ubuntu 7.10
What else you need to know.

---

### Post by cabal2000 on 2008-03-09
sorry.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by hhhhhx on 2008-03-09
> **Rocket2DMn said:**
> Can you please post a link to the guide you were following.  Also, what is your video card model?
The drivers you need for ATI cards are available in Ubuntu, either the open source ones or the restricted ones, you don't need them direct from ATI.
Once we have this info, we can reconfigure X (the GUI).
+1

---

### Post by Rocket2DMn on 2008-03-09
OK, reconfigure X from the recovery mode terminal with
```
dpkg-reconfigure xserver-xorg -phigh
```
Then reboot into the standard kernel.  You should now have access to the GUI.  If you don't I'll send you a link on reconfiguring X the more manual way.
Once back in the GUI, you can install the restricted ATI drivers (fglrx) which are needed to get good performance out of your card.  You can follow the directions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882)
-It's just those 2 lines you need to run in terminal, then enabled restricted drivers as it says, and restart X with CTRL+ALT+BACKSPACE

---

### Post by cabal2000 on 2008-03-09
i typed in the code in the root@edwards and I got a new screen come up but i don't see fglrx there. Which one do i need to use?

---

### Post by Rocket2DMn on 2008-03-09
"vesa", it is a fallback driver.

---

### Post by cabal2000 on 2008-03-09
sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

I did these 2 lines of code in termeral rebooted, and still getting black screen even with
dpkg-reconfigure xserver-xorg -phigh
with vesa driver at 800x600 resolution

---

### Post by Rocket2DMn on 2008-03-09
OK, if you need to reconfigure again to get into the GUI, do so, then let's just try Envy like xhhux suggested.  I've never used it, but people swear by it; you can get it here - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cabal2000 on 2008-03-10
YES....Envy worked perfact!!!
Much thx

---

