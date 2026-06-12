---
title: "Tried to install driver, wont boot!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-09
As a first time linux user, I have begun to find myself drowning in something that seems way over my head.  With that said, I love teh challenge and as long as there are awesome communities out there such as this one, I will continue to welcome the challenge.

I was reading through the desktop.pdf  attempting to learn what I could when I came across the section covering 3D graphics cards... I followed all the instructions in this section to install my new driver:

```
 glxinfo | grep rendering
```

which returned

```
 direct rendering: NO{/CODE]

Ok, so I needed the new driver... I continued...

[CODE] sudo get-apt nvidia-glx 
```

all the beautiful code ran, except while d/ling one file, my internet  (thank you wonderful cable company) went out for a minute.... Once the internet came back up I just reran 

```
 sudo get-apt nvidia-glx 
``` 

and this time it finished installing

so I enabled it

```
 sudo nvidia-glx-config enable
```

everything seemed to be fine..... Just needs a reboot.

the directions said: 

> You can adjust the settings of the new drivers by running nvidia-settings (see the run application manual for help on how to run an application without using the menu). If you wish, add a menu entry for this program (see the menu editor manual for help on how to add menu entries).

Which was a problem being that I could not find this file. So I went on about some other stuff I was doing and didnt reboot until this morning.. Upon reboot... 

](*,) ](*,) :shock: :twisted: :twisted: :confused: :( ](*,) ERROR~!!!!!

The error: 
> Failed to start X server (your graphical interface).  It's likely it is not set up correctly.  Would you like to view the X server output to diagnose the problem.  Yes or No

I tried to look at the output, but was unable to comprehend. It eventually tells me it will shut down X server (I think it's X Server or maybe GDM).  I tell it ok, and it takes me to a command line.  I guess from this command line I should be able to t bring up the /etc/X11/xorg.conf file for editing.  But in all of my 5 days running linux, I seem to have missed the bit of knownledge on how to accomplish such a task...

Any help would be much appreciated.. If I wasnt already running late for class I would enter in all the information I get when following these screens... 

THanks for any help!! Hell, thanks for even looking!

---

### Post by Iceni on 2007-04-09
to edit xorg.conf from command line:

```
sudo nano /etc/X11/xorg.conf
```

I would try to reconfigure X first:

```
sudo dpkg-reconfigure xserver-xorg
```

run this, then try to start X

```
startx
```

---

### Post by jem7v on 2007-04-09
If you decide to edit your xorg.conf manually, go down to where it says Device, then change the Driver from "nvidia" to "nv" to go back to the default driver while you try to figure out what went wrong.  (You should be able to get back into your X server with the nv driver.)


p.s. The "X server" (aka X11 or X.Org) is the guts of the graphic environment you see when everything's working nicely. It's what your desktop manager (Gnome in Ubuntu, KDE in Kubuntu, XFCE in Xubuntu) is running in. It's when it doesn't work that you get thrown into a command line.

---

### Post by Efros on 2007-04-09
I would recommend the envy script for installing nvidia drivers.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by fobnicat on 2007-04-09
Whoo! Thanks a ton guys! It's working great now.. Maybe I woll be able to figure out the next issuie on my own!

---

### Post by GSF1200S on 2007-04-12
I wrote this in another thread, and it helped the poster of the topic. Believe me man, the setup of Linux can take time! But once its there- BLISS! I havent booted XP in a week:D 

Here it is:

To start off, download the Linux Nvidia drivers from there website and put the package in your home folder (if you use madwifi, go ahead and download the tar.gz package from their website).

You might want to write these codes down as the X window will be closed for the NVIDIA install. First, you have to shutdown the X window. Type in a terminal:

sudo /etc/init.d/gdm stop

Then, youll have a blinking cursor on a black screen. Press Alt+F1 to get back to the prompt. Then youll probably need to put in your username and password (youll have to login at the prompt). Then, type the following code:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run         (**NOTE** I dont know but Ive heard there is a new version.. just make sure you type the proper version in the command.

Follow the NVIDIA installer instructions. It doesnt matter if you try to download the kernel, just let the installer compile one for you.

After the installer finishes, youll be back at the command prompt. Type:

startx

to start the X window. DO NOT REBOOT YET!! The reason you guys are having the Xwindow fail is due to an API mismatch error between the NVIDIA drivers and the nvidia common kernel.

You need to remove the nvidia common kernel. This is where problems can enter for people needing the restricted modules (madwifi).

Open the Synaptic Package Manager and search for the nvidia common kernel. When found, completely remove it. This sucks for madwifi users, because the nvidia common kernel removal also removes the linux restricted modules (which includes the madwifi drivers), which will down your wireless. Not to worry, im going to help you fix that too...

If you dont use a wireless card, youre done. Simply try a reboot, and your X window will load fine. The API mismatch error wont happen because there is NO nvidia common kernel to have a conflict with. Open a terminal and type 'glxgears' and youll see your video card/drivers working perfectly.

Now, on to the madwifi users. Earlier in the post I told you to download the latest madwifi drivers tar.gz from the website. Make sure this package is in your home folder. Then, extract its contents (right click on the package, then click extract) to your home folder as well. Then open a terminal and change the directory to the extracted folder. For example, my madwifi drivers folder name was madwifi-0.9.3, so I would type in the terminal:

cd madwifi-0.9.3

Then, type the following command:

make

Then, type this command:

sudo make install

Then, type this command:

sudo make clean
(cleans temporary files)

And there you go- at this point you can reboot and you will be greeted by a NVIDIA splash screen, an X window that loads, and a functioning wireless card.

I hope this helps everyone out.. Let me know if you have problems and Ill try and help.

**EDIT** HAHA!! Nice.. I posted this on the wrong freaking page.. Omfg, what a good one.. glad your problems fixed... lol

---

