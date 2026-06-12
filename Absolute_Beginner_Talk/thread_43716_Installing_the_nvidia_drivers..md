---
title: "Installing the nvidia drivers."
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-23
Ok, so I've downloaded the .run-file from nvidias homepage and I've sh-ed it in the terminal. What happens then is that it gives an error about shutting down X.
When I shut down X, it is rebooted again.

How do I install this .run-file?

---

### Post by Seti on 2005-06-23
Installing the nVIDIA driver can be as simple as following the howto detailed [here](http://www.ubuntuguide.org/) 
Of course if you want to install the official nVIDIA installer script from the nvidia website, you can shut down X without it resarting by changing /etc/inittab.
```
sudo gedit /etc/inittab
``` 
change runlevel to 3 and save the file.

Then kill X by [CTRL] [ALT] [Backspace]

don't forget to ```
sudo chmod 755 NVIDIA...(name of the script)
``` 

Then just ./NVIDIA........  I'm lazy so I always use tab-completion for everything. If your in the dir where the script is just NVI and hit [TAB] and bash fills in the rest. You prolly already know that. Have fun!!

---

### Post by tristan on 2005-06-23
Hi Trojan1313

Installing nvidia drivers is just about the most commonly asked question on these forums, a quick search will give you many posts which will help you out.

To really kill X you need to switch to a virtual terminal by pressing **ctrl-alt-F1** (or F2, F3 etc) and login.

Then give yourself root access with **sudo su**

**killall gdm** will kill the gnome greeter and terminate X

Just to be on the safe side switch to single user mode with **telinit 3**

OK, now you're ready to run your nvidia.run file and install the driver.

At the end of it you'll need to modify your /etc/X11/xorg.conf file to use the nvidia driver as opposed to the generic nv one. Again, see numerous posts here about that.

Once done, you can fire up X and the gnome greeter again with **gdm**.

Hope this helps you.

---

### Post by Trojan1313 on 2005-06-23
[QUOTE=tristan]Hi Trojan1313

Installing nvidia drivers is just about the most commonly asked question on these forums, a quick search will give you many posts which will help you out.

To really kill X you need to switch to a virtual terminal by pressing **ctrl-alt-F1** (or F2, F3 etc) and login.

Then give yourself root access with **sudo su**

**killall gdm** will kill the gnome greeter and terminate X

Just to be on the safe side switch to single user mode with **telinit 3**

OK, now you're ready to run your nvidia.run file and install the driver.

At the end of it you'll need to modify your /etc/X11/xorg.conf file to use the nvidia driver as opposed to the generic nv one. Again, see numerous posts here about that.

Once done, you can fire up X and the gnome greeter again with **gdm**.

Hope this helps you.[/QUOTE]
 Step 1: ctrl+alt+F1 (to shut down X)
Step 2: logon
Step 3: terminal: killall gdm
Step 4: terminal: telinit 3 (what is this?)
Step 5: terminal: sh /home/kamine/nvidia.run
Step 6: Switch to "nvidia"-driver in xorg.conf
Step 7: terminal: gdm
Done!

Did I get it right? What is this "sudo chmod 755 NVIDIA...(name of the script)" Seti mentioned?

---

### Post by Trojan1313 on 2005-06-23
[QUOTE=Trojan1313]Step 1: ctrl+alt+F1 (to shut down X)
Step 2: logon
Step 3: terminal: killall gdm
Step 4: terminal: telinit 3 (what is this?)
Step 5: terminal: sh /home/kamine/nvidia.run
Step 6: Switch to "nvidia"-driver in xorg.conf
Step 7: terminal: gdm
Done!

Did I get it right? What is this "sudo chmod 755 NVIDIA...(name of the script)" Seti mentioned?[/QUOTE]
 When I start the nvidia.run I get something about a pre-compiled kernel and then I get shuffed out of the .run-file. Why is this?

---

### Post by tristan on 2005-06-23
The point of using the nvidia.run file is that it will automatically build a kernel module for you. For this you need to get via synaptic: build-essentials (so you can build programs); and kernel headers.

Once you have these, you should be fine.

As I said earlier, there are a number of excellent nvidia install howtos sprinkled around these forums, you can save yourself a lot of headaches by using the search function :)

---

### Post by Trojan1313 on 2005-06-24
I have the build essentials installed. :s
How do I make it build my kernel then? I used "sudo sh /home/kamine/nvidia.run", then it ran the installer and came up with the "there's no prebuild kernel"-excuse.

---

### Post by codejunkie on 2005-06-24
you need to also install the kernel-headers package for your kernel then run the installer again and it will build the kernel module for you.

---

### Post by Trojan1313 on 2005-06-24
[QUOTE=codejunkie]you need to also install the kernel-headers package for your kernel then run the installer again and it will build the kernel module for you.[/QUOTE]
 The Package "linux-kernel-headers" is already installed. =/

---

### Post by codejunkie on 2005-06-24
what kernel are you using i386, i686, k7  open a terminal and type uname -a and post it here.

the reason i ask is the linux-kernel-headers package is a generic kernel header package its not the one for your kernel.

---

