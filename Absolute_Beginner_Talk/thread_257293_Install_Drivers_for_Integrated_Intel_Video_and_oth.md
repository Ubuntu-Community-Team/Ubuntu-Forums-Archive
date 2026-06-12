---
title: "Install Drivers for Integrated Intel Video and other Questions on installs."
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by M374llic4 on 2006-09-14
I have installed Ubuntu Desktop (obviously :P) But can not get higher then 640x480. I went to the bios and changed it to 8mb of video memory, still nothing. I downloaded the drivers for linux from intel and ran  tar -xzvf Intel-3.4.3006-20051209.i386.tar.gz

It made the folder on my desktop, not sure where to go from there though, instructions said to run  

./configure

but there is no configure, what am I supposed to do exactly? Compile and run so I have read, but not exactly sure how. 

Once I learn to do this, is that how almost all tar.gz and other files are installed and ran? 

I take it no programs have an "installer" in a sence? You must manually install them, and then to run them, you just type in

program_name  ?

then it runs? Though with drivers, I would hope its automaticly detected and ran? Other programs, like say, a game, you have a tar.gz, and you run and compile it, then does it show up in the applications menu?

Perhaps I have some more reading that needs to be done :)

---

### Post by Rumor on 2006-09-14
To install the drivers, you'll have to open a console window: Applications | Accessories | Terminal, if my memory serves.

In it, type:
```

sudo apt-get install build-essential

```

It will ask for your password, which you will not see when you type it. That will install the tools you need for compiling packages from source code. Once it installs, type:

```

cd nameoffolder (eg /home/yourusername/desktop/foldername)
./configure
make
sudo make install

```
allowing each process to run before you type in the next command.

That *should* install your drivers and you *should* be able to select a resolution greater than 640x480.

If not, you might have to edit your xorg.conf file to get the higher resolutiuons, but let's cross that bridge when we get to it.

---

### Post by reacocard on 2006-09-14
> **M374llic4 said:**
> I have installed Ubuntu Desktop (obviously :P) But can not get higher then 640x480. I went to the bios and changed it to 8mb of video memory, still nothing. I downloaded the drivers for linux from intel and ran  tar -xzvf Intel-3.4.3006-20051209.i386.tar.gz

Ubuntu comes with the intel drivers. there is no need to install them manually.

For your problem, I think there's a program called 915resolution that might help.
> **M374llic4 said:**
> It made the folder on my desktop, not sure where to go from there though, instructions said to run  

./configure

but there is no configure, what am I supposed to do exactly? Compile and run so I have read, but not exactly sure how. 

Once I learn to do this, is that how almost all tar.gz and other files are installed and ran? 

I take it no programs have an "installer" in a sence? You must manually install them, and then to run them, you just type in

program_name  ?

then it runs? Though with drivers, I would hope its automaticly detected and ran? Other programs, like say, a game, you have a tar.gz, and you run and compile it, then does it show up in the applications menu?

Perhaps I have some more reading that needs to be done :)

Generally, there is no "installer". that standard set of steps is:
Extract the tarball.
open a terminal and cd into the extracted directory
run ./configure (if available). configure will warn you if there are dependencies you need.
run make
run sudo make install

some software has an install script, in which case you run the the script instead of configure/make/install.

But this is the hard way to install software. An easier way is through the package manager. Go to System -> Administration -> Synaptic Package Manager. Search the package manager for what you need, mark it for installation, and click 'apply'. the software will be downloaded, installed and configured automatically.

---

### Post by M374llic4 on 2006-09-14
> **Rumor said:**
> To install the drivers, you'll have to open a console window: Applications | Accessories | Terminal, if my memory serves.

In it, type:
```

sudo apt-get install build-essential

```

It will ask for your password, which you will not see when you type it. That will install the tools you need for compiling packages from source code. Once it installs, type:

```

cd nameoffolder (eg /home/yourusername/desktop/foldername)
./configure
make
sudo make install

```
allowing each process to run before you type in the next command.

That *should* install your drivers and you *should* be able to select a resolution greater than 640x480.

If not, you might have to edit your xorg.conf file to get the higher resolutiuons, but let's cross that bridge when we get to it.

How big is that package? I have 56k at home for the time being, is it something I can download here at work and burn and install somehow?

---

### Post by Rumor on 2006-09-14
If you installed using the Desktop cd, reboot into your new system and insert the cd again (after you are at the desktop) A window will pop up asking if you want to add the packages on the cd to your repos. Say yes, and you shall be able to install build-essential and some other packages. Then you should be able to compile your drivers. Or, you can search for the video drivers in synaptic )System | Administration | Synaptic Package Manager) and download them that way. Driver files are usually very small, in my experience.

Good luck!

---

### Post by M374llic4 on 2006-09-14
> **Rumor said:**
> If you installed using the Desktop cd, reboot into your new system and insert the cd again (after you are at the desktop) A window will pop up asking if you want to add the packages on the cd to your repos. Say yes, and you shall be able to install build-essential and some other packages. Then you should be able to compile your drivers. Or, you can search for the video drivers in synaptic )System | Administration | Synaptic Package Manager) and download them that way. Driver files are usually very small, in my experience.

Good luck!


I will give that a try as soon as I get home, The drivers I downloaded from Intel were 22ish megs. 

Horrable on 56k. : (

I am sure it is something stupid.

---

