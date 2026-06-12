---
title: "GeForce 8800 GTS and Nvidia drivers"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by midiwriter on 2007-05-16
Please help...I am totally new to this, and have tried searching everywhere for the answer and can't find it...thank you for your help!

GeForce 8800 GTS, latest Feisty 7.04.
I am trying to get Beryl working, and Ubuntu works fine, until I add the Baryl program...then I get a jumbled desktop with no usability.  Do I need to get Nvidia's drivers first?  I have tried this so many times, I keep getting the error, cannot continue.  Here's how I am trying:
type sudo sh [Nvidia driver file name]...doesn't work.
tried ctrl-alt-F1 to stop X, still won't work.

What do I do???
Can I even get Beryl running on this system?

Thank you very much for your help!

---

### Post by echo $USER on 2007-05-16
you need to instal the driver first...

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

Should the above not enable the new driver, you can enable it manually by opening the X config file:

sudo gedit /etc/X11/xorg.conf
and replacing "nv" with "nvidia"

Then run...

sudo /etc/init.d/gdm restart

---

### Post by midiwriter on 2007-05-16
It looked like the driver was downloaded and installed, but then, when i restart, i get the usual 'cannot start the X server'... screen, and then, when i ran the command you posted, I get 'cannot open display: Run 'gedit --help' to see a list of available command line options'...

I am back to where i was, unable to even start Ubuntu again.

Can you help please???
Thank you!

p.s. upon reboot, I get the blue screen telling me 'Failed to start the X server'..............

---

### Post by Eclipse. on 2007-05-16
> **midiwriter said:**
> It looked like the driver was downloaded and installed, but then, when i restart, i get the usual 'cannot start the X server'... screen, and then, when i ran the command you posted, I get 'cannot open display: Run 'gedit --help' to see a list of available command line options'...

I am back to where i was, unable to even start Ubuntu again.

Can you help please???
Thank you!

Since your not in graphical display you cant use gedit.Use nano instead of gedit.

---

### Post by midiwriter on 2007-05-16
now i am getting 'Section :server Layout; and a bunch of options.  please remember i know nothing about this and need help.
thanks.

---

### Post by midiwriter on 2007-05-16
In edit, the filename is nvidia-xconf/etc/X11.xorg.conf

---

### Post by midiwriter on 2007-05-17
Can someone please walk me through installing nvidia drivers?  i still can't resolve this.

---

### Post by echo $USER on 2007-05-17
> **midiwriter said:**
> Can someone please walk me through installing nvidia drivers?  i still can't resolve this.

Download the driver from nvidia's site to your desktop.
CTRL-ATL-F1
Log in to the text terminal.
enter "sudo /etc/init.d/gdm stop"
cd /home/your_user_name/Desktop
sudo ./nvidia_drive_name
then let it complete the install.
enter "sudo /etc/init.d/gdm start

---

### Post by midiwriter on 2007-05-17
Hello echo, thank you for the quick reply.

After entering sudo ./nvidia_drive_name I get to the nvidia installer, but \when it runs, it gives the error:

You do not appear to have the libc header files installed on your system.  Please install your distribution's libc development package.

Can this be resolved?
thank you!

---

### Post by echo $USER on 2007-05-17
> **midiwriter said:**
> Hello echo, thank you for the quick reply.

After entering sudo ./nvidia_drive_name I get to the nvidia installer, but \when it runs, it gives the error:

You do not appear to have the libc header files installed on your system.  Please install your distribution's libc development package.

Can this be resolved?
thank you!

okay run this before you try to install the driver...

sudo apt-get install build-essential

[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3502](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3502)

---

