---
title: "Kubuntu 7.04 no longer booting properly..."
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-07-13
Hello everyone,

I rather new to the linux OS and am currently running Kubuntu 7.04(32bit version) everything has been running great up until this morning when I went to install a graphics driver update. I am currently using a Nvidia 7800GT this is the link I used to download my driver from : [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) I installed the driver properly and it said it installed ok.

Now when I let the computer boot it goes to Kubuntu loading screen but once the bar gets all the way across the screen flashes black, then shows the screen with the loading bar once more, then after that all I get is a black screen with a flashing white line in the upper left hand corner.

When the computer is turning on and I hit escape to go into the boot menu selections I have the following 5 options: 

Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

The first and 3rd options give me the same screen with black back and white flashing line(Also if it helps any I can type @ this screen but nothing else)the second and forth option allow me access to my console but I am uncertain of what command I could use to get it to boot from here. I havn't tried the 5th choice due to my lack of knowledge (I really don't wanna hit the wrong thing and kill my kubuntu installation).

Meh I was really enjoying playing around with Kubuntu until this happened. Anyone else ever had a similar problem and is willing to share a solution? Any help would be great.

Thanks Much,
~J3ff

---

### Post by twiceasworn on 2007-07-13
Could you post the contents of your /etc/X11/xorg.conf file?

---

### Post by beastrace91 on 2007-07-13
How can I pull up this file using my console? Sorry like i said still new at this and only know a few commands right now.

~J3ff

---

### Post by Damanther on 2007-07-13
Similiar thing happened to me not too long ago when I did a driver update through apt and the restricted drivers repo.

The Envy script provided here got me back on track.
[http://www.albertomilone.com]("http://www.albertomilone.com")

Damanther

---

### Post by twiceasworn on 2007-07-13
To get to the file in the terminal use something like```
 sudo nano /etc/X11/xorg.conf
``` The sudo allows you to become super user and nano is one of the terminal text editors.  I personally prefer vi, but it has a rather steep learning curve.

---

### Post by kalmah on 2007-07-13
> **beastrace91 said:**
> How can I pull up this file using my console? Sorry like i said still new at this and only know a few commands right now.

~J3ff

type

```
sudo gedit /etc/X11/xorg.conf
```

in terminal, and enter the password you used when you installed Linux.

---

### Post by DBStevens on 2007-07-13
If you can logon to your system you can use vi or nano or pico or vim to edit your /etc/x11/xorg.conf file.

You will need to use sudo to start the editor because the file you are going to edit doesn't belong to your user id.

You need to change the line that is in Device section change the Driver to read  "nv" instead of "nvidia"  save the file exit the editor and re-boot.

This should give you a system without the vendors binary driver blob.

Now a word about such binary drivers in general:

They are apt to be specific to a particular kernel release, that is they don't always play well with the kernel.       Don't be surprised if they cause you trouble.

---

### Post by beastrace91 on 2007-07-13
Ok I used this line:

sudo nano /etc/X11/xorg.conf

It brought me to a window that @ the top reads: GNU nano 2.0.2 File:/ect/X11/xorg.conf

At the bottom of the screen I have several options to choose from:

[ New File]
^G Get Help ^O WriteOut ^R Read File ^Y Prev Page ^K Cut Text ^C Cur Pos
^X Exit ^J Justify ^W Where Is ^V Next Page ^U UnCut Text ^T To Spell

What do I do from here? I would just play around with it but I don't want to mess anything else up.

Also thanks for the quick responses guys :)

~J3ff

---

### Post by twiceasworn on 2007-07-13
Well the best idea is to back up your xorg.conf before change anything.  You can do this by executing ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.old
```  Then, if you mess something up and you can only boot to the terminal you can just do a ```
sudo mv /etc/X11/xorg.old /etc/X11/xorg.conf
```  That is basically renaming the xorg.old(an exact copy of your previous xorg settings) to xorg.conf.  Then you would be able to reboot and get back into the gui.

Also, I do not use nano much so I do not know the commands by heart, but i think it is Ctrl-O to save?  All the important commands are issued with a ctrl + something.  Also I notice you said you opened /etc/X11/xorg/conf, that will create a new file.  Make sure you type exact as I had it "/etc/X11/xorg.conf"

---

### Post by beastrace91 on 2007-07-13
Sorry that was a typo in my post. I did enter it the right way thats guys I'll try to play around with it some now that I know how to back up/restore the old one if I mess it up.

Any one who could tell me what I should be looking for in this file would be a great help.

~J3ff

---

### Post by twiceasworn on 2007-07-13
Under one the device sections you should see an entry for your video card.  Under the driver option what does it say?  Or you could just post the whole thing so I could get a good look at it :).  Up to you.

---

### Post by DBStevens on 2007-07-13
You need to change the line that is in Device section change the Driver to read "nv" instead of "nvidia" save the file exit the editor and re-boot.

Then once you have a working X system you can get the proper driver for the system you are running.

---

### Post by twiceasworn on 2007-07-13
> **DBStevens said:**
> You need to change the line that is in Device section change the Driver to read "nv" instead of "nvidia" save the file exit the editor and re-boot.

Then once you have a working X system you can get the proper driver for the system you are running.

I was getting there :)

---

### Post by beastrace91 on 2007-07-13
You guys are my heros! I am now posting my my Kubuntu system instead of using my roomates windows system... thank you so much.

Could you explain exactly what changing nvidia to just nv did? Also does this mean the drivers I tryed to install where bad? Anyone willing to help me get the proper drivers if this is the case?(I really just wanna play some counter strike source right now...)

Thanks for all the help,
~J3ff

---

### Post by twiceasworn on 2007-07-13
Basically you are using the driver that only does 2d rendering (don't worry this is only temporary until you can get the good drivers up and running).  There are tons of guides on how to get 3d acceleration with Nvidia.  Be extremely grateful that you are not scarred with an ATI card like myself.  I would just do a search on the forum for Nvidia driver install or something similar.  I personally have never done the nvidia driver installation myself, otherwise I would walk you through it.

Now, if you needed to to get the propietary drivers for an ATI card I could lead you through it with my eyes closed :/  (bundle of fun, let me tell you).

---

### Post by beastrace91 on 2007-07-13
Thnx for all the help, glad that I know I can come and ask questions with out being made feel like a moron :)

~J3ff

---

### Post by DBStevens on 2007-07-13
beastrace91,

You have to be certain that the vendor provided binary drivers you attempt to use are actually for the particular version of the kernel you are running, even installing the next kernel in the sequence from your distribution provider can cause issues with binary drivers.

In short updating one without at least checking with your distribution provider about the other can lead to "issues".   It makes no difference if the distribution is a flavor of Ubuntu,  Red Hat, SuSE, Debian, Slackware,  LFS, or insert new kid on the block here.

Welcome to Linux, and as my former home distribution used to say,"Have a lot of fun."

---

### Post by beastrace91 on 2007-07-13
Let me make sure I understand this 100% before I just go try random drivers again...

I need to know what distro of linux I am running and what kernal it is running of off?(If this is the case how do I find what kernal I am using?) Also anyone have any idea where I can go Download Nvidia 7 series drivers from?

~J3ff

---

### Post by DBStevens on 2007-07-13
The kernel is the one that you system booted which was probably:

Ubuntu, kernel 2.6.20-16-generic

This can be verified by entering:

uname --all

in a terminal session

Now the kernel folks don't produce a kernel with that identification.

That kernel is provided by the Ubuntu folks and has changes that may not be in the current kernel tree.

In addition to Ubuntu providing a modified kernel they also provide access to additional drivers such as the Nvidia restricted driver.  They test the one they provide access to for compatability with their kernel.

You can not with certainity go pick any stranger's binary version of things and expect it to work, even if that stranger is the provider of the binary driver.  There may need to be some new glue that the distribution has to provide.

---

