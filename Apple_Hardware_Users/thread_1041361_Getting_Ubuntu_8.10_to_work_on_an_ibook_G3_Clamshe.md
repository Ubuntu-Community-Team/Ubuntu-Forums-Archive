---
title: "Getting Ubuntu 8.10 to work on an ibook G3 Clamshell"
date: 2009-01-16
forum: Apple Hardware Users
---

### Post by waronfear on 2009-01-16
I have created a HOWTO for setting up Ubuntu 8.10 on Clamshell iBooks.  You can get to it here:

[http://www.waronfear.com/ubuntu81g3clamshell.html]("http://www.waronfear.com/ubuntu81g3clamshell.html")
I have also included here inline:

Getting Ubuntu 8.10 to work on an ibook G3 Clamshell.

Please follow the instructions carefully. A certain level of techical skill is expected.
YOU NEED INTERNET ACCESS FROM YOUR IBOOK
CONVENTIONS

You do not type the $ symbol. It is there to denote the command prompt

Press ctrl-alt-f1 to get a command prompt

Press ctrl-f7 to get back to the GUI

Please note this guide doesn't spell absolutely everything out.
Getting Ubuntu

First you need to burn the appropriate ISO to a blank cd. You can get it here. The one you want is the Mac (PowerPC) and IBM-PPC (POWER5) alternate install CD
Installing Ubuntu

    * Insert the 8.10 Alternative install cd
    * Reboot your ibook
    * hold the c key while it starts up
    * The installer will start

After the UI for the installer loads, press Alt-F2 to open a new display. Press 'Return' when it asks if you want to open the display. Type the following and press return. This will enable the CDROM for installation.
$ sudo modprobe ide-scsi

Press Alt-F1 to return to the installer.

You will have to get through the rest of the install procedure yourself. Don't worry, it isn't hard. Make sure you write down the username and password you select during the installation.

Once installation is complete (this will take a LONG time--more than an hour in my case) Reboot. When the second 'boot' prompt appears type the following:
Linux nosplash
or
Linux video=ofonly nosplash

Linux nosplash worked for me.

This will boot the machine without the splash screen which would otherwise cause the system to hang.

Now you need to edit the spash settings to ensure your machine can boot properly.
Fix the usplash configuration
Press ctrl-alt f1 to get a prompt once the system is done booting. You'll know its done because you will get a graphical error message box complaining about the video. In the error box select 'create default configuration'. You will get some feedback when its done. Click the cancel button a couple of times until you are prompted that the display is restarting. Once this is done you can press ctrl-alt f1 to get a command prompt.

From the command prompt log in and enter:
$ sudo nano /etc/usplash.conf Add the following lines: xres=800 yres=600

Press ctrl-x to save and exit nano. Follow the prompts at the bottom of the screen.
From the command prompt run:
$ sudo update-initramfs -u -k 'uname -r'

This may take a few moments to complete.
Fix the GUI settings

You need to do this so the desktop will use the correct video settings.

Edit the xorg conf file from the comman promt. Use ctrl-alt f1 to get the command prompt.You will need to log in.
$ sudo nano /etc/X11/xorg.conf

Add to Section Device

Option "NoINT10" "true"
Option "UseFBDev" "false"
Option "NoDRI"
Also add:

Section "Module"
	disable "dri"
	disable "glx"
EndSection

Press ctrl-x to save and exit nano. Follow the prompts at the bottom of the screen.
Make the Sound Work

edit the modules file
$ sudo nano /etc/modules

add the following to the end of the file
snd-powermac

Press ctrl-x to save and exit nano. Follow the prompts at the bottom of the screen.
Fix Gnome

THIS IS REQUIRED FOR THE GUI TO LOAD PROGRAMS

Press ctrl-alt-f1 to launch a terminal. Log in and enter the following commands


 $ sudo apt-get install devscripts fakeroot automake autoconf libtool pkg-config
 $ mkdir pixman
 $ cd pixman
 $ dget [http://people.ubuntu.com/~kirkland/pixman/pixman_0.12.0-1ubuntu1.dsc](http://people.ubuntu.com/~kirkland/pixman/pixman_0.12.0-1ubuntu1.dsc)
 $ dpkg-source -x pixman_0.12.0-1ubuntu1.dsc
 $ sudo apt-get build-dep pixman
 $ cd pixman-0.12.0/
 $ debuild
 $ cd ..
 $ dpkg -i libpixman-1-0_0.12.0-1ubuntu1_powerpc.deb

libpixman-1-0_0.12.0-1ubuntu1_powerpc.deb may be named slightly differently. type ls and press return to see a list of filenames in case this one doesn't work.

This process will take a short while to complete.

You can try the powerpc packages the author of this built at: [http://people.ubuntu.com/~kirkland/pixman/](http://people.ubuntu.com/~kirkland/pixman/) This method isn't advised unless you already know how to use this type of file. You will have to figure out on your own how to download and install it.

Reboot using this command
sudo reboot
Fix the Power Management

Once your system is back up and running launch Power Management. From the menus at the top:
System -> Preferences -> Power Management

Set the lid option to 'suspend' or if will shutdown/crash when you close the lid.
Congratulations! It works!

---

### Post by stream303 on 2009-01-16
NICE!!!

You put some good work into that and I'm sure that clamshell owners will be very grateful.

---

### Post by mkvnmtr on 2009-01-16
Yes indeed that is good work. There does seem to be quite a few people wanting to make that install.

---

### Post by McFrostey on 2009-01-17
Nice indeed, I assume everything will run just a little bit slower than usual compared to Xubuntu but still great for people who want to put Ubuntu on their iBook Clamshells

---

### Post by tuscho on 2009-01-29
i was trying execute "dget http://people.ubuntu.com/~kirkland/p...0-1ubuntu1.dsc"

but it display the error message "Http 404 error... not found"

The sound could work without it?

tanks!

---

### Post by tuscho on 2009-01-29
> **tuscho said:**
> i was trying execute "dget http://people.ubuntu.com/~kirkland/p...0-1ubuntu1.dsc"

but it display the error message "Http 404 error... not found"

The sound could work without it?

tanks!

My mistake, typeing url... Now it works...

Another question.... can I use some tool like "Norton Ghost" to after i finish the instalation, i make a bootable image to restore the Linux, from a DVD (per example)?

---

### Post by tuscho on 2009-01-29
After all, when the ubuntu enters in GUI (login window), the imagem is somekind wrong... Seems like a incorrect refresh rate...

I have a ibook G3 500... can somebody help me
e?

---

### Post by boblounsbury on 2009-02-06
> **tuscho said:**
> After all, when the ubuntu enters in GUI (login window), the imagem is somekind wrong... Seems like a incorrect refresh rate...

I have a ibook G3 500... can somebody help me
e?

I have an iBook G3 600 MHz. What's the problem?

---

### Post by Psicolonia on 2009-02-08
> Fix Gnome

THIS IS REQUIRED FOR THE GUI TO LOAD PROGRAMS

What exactly does this do?

I don't know all the steps in the alternative cd, but can I install fluxbox instead? will I still need to do this step? On the alternative cd I'm able to select the packages I want, correct? I can never select gnome, right? Just fluxbox?

Sorry for the basic question.

Thank you

---

