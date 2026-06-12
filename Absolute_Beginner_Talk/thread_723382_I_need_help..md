---
title: "I need help."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by X3zh on 2008-03-13
Hello. 

I just started using ubuntu, and I know very little about it, so let's cut to the chase.
I am trying to install my graphic card driver (GFX card: GeForce 7600GS) and it won't work. There's an error message who looks like this:

-Could not open the file /home/xlv/Skrivbord/NVID&#8230;Linux-x86-169.12-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
Character Coding: Current Locale (UTF-8 ).

I would appreciate if someone could tell me how to install the driver since I completely suck at linux.


Thank you.

---

### Post by OffAxis on 2008-03-13
are you trying to open or install a downloaded driver?

There's no need.
Just go to the System Settings and use the 'Restricted Driver' Manager to install the driver. It's a checkbox.
Easier, yes?
The actual path is:
System > Administration > Restricted Drivers Manager

And here's a nice graphical walkthrough:

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Charcoal1981 on 2008-03-13
You seem to be opening the package in gedit, which is a text editor - clearly this won't be very successfull! - If you are new to linux/ubuntu, I would highly recommend not trying to install packages from files downloaded to your desktop, instead use synaptic to install from the repositories.

Go to "System > Administration > Synaptic Package Manager". Search for 'nvidia', and a list of all the packages related to nvidia will be displayed. Mark the one you want for installation (probably linux-restricted-modules-2.6.22-14-generic) and click apply.

---

### Post by forrestcupp on 2008-03-13
The Restricted Drivers Manager way is much easier than doing it in Synaptic, though.  It is automated for you.

---

### Post by X3zh on 2008-03-13
@offAxis.

I already tried that, and when I did, it came ANOTHER error message. It says like this.

-The software source for the package

   nvidia-glx-new

 is not enabled.


But I will check through the walkthrough, thanks.


@Charcoal1981.

All I find is "nvidia-kernel-common" who says that it already is installed.

---

### Post by Charcoal1981 on 2008-03-13
@forrestcupp: Very true, but it won't help when trying to install other software. Synaptic is more generic, and the OP seems to have some issues in a more general sense...

---

### Post by diablo75 on 2008-03-13
You probably need to enable the restricted software source (thank god this is now enabled by default on newer installs...[or so I've been told]("http://brainstorm.ubuntu.com/idea/4143/")).

System>Administration>Software Source

Check everything off, then try to use the Restricted Drivers manager again.

---

### Post by Therion on 2008-03-13
Save yourself a lot time and frustration and just download/run [Envy](http://www.albertomilone.com/nvidia_scripts1.html).  

It will download and install the correct nVidia Restricted Driver and then configure your xorg.conf file for you... Automatically.

No muss, no fuss, no bother.  No rubbing, no buffing.

---

### Post by OffAxis on 2008-03-13
> -The software source for the package

nvidia-glx-new

is not enabled.

ah. You need to enable some repositories in your repository listing. You can enable them in one of two ways.
1. Use the GUI. It's under System somewhere (I can't remember).

2. Edit the files directly.
```
sudo nano /etc/apt/sources.list
```

Delete the hash (**#**) mark in front of lines that say **deb **or **deb-src**
then run
```
sudo apt-get update
```

Then try to Enable in the Restricted Driver Manager.

---

### Post by Charcoal1981 on 2008-03-13
> **X3zh said:**
> 

@Charcoal1981.

All I find is "nvidia-kernel-common" who says that it already is installed.

You probably need to enable the optional repositories. Go to "System>Administration>Software Sources" and make sure that the restricted drivers repo is selected (you probably want the multiverse repo whilst your at it).

---

