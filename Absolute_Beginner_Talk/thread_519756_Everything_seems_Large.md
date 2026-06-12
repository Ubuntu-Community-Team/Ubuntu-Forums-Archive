---
title: "Everything seems Large"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-07
I'm new to Linux and am trying Ubuntu 7.04 on Virtual Box.

I've notice that everything in Ubuntu seems a bit Large.
The Font, Icons, along with other things.
Currently my resolution is 1024 X 768 but my Monitor will do 1280 X 1024.
I've looked at these settings in Ubuntu and the largest Resolution listed
is 1024 X 768.  

Is there a way to make things smaller like in a Windows environment.
Everything is just so large.  

Thanks.

---

### Post by Rocket2DMn on 2007-08-07
The typical command to get your resolutions available is to reconfigure the X-server
The following will take you through a hardware setup, please read, don't just ENTER your way through.
```
sudo dpkg-reconfigure xserver-xorg
```
Use TAB to move around and SPACEBAR to select/enable.  When you get to the resolutions page, enable your monitor's max resolution and everything less.  After the configuration is complete, restart the Xserver with CTRL+ALT+BACKSPACE (all unsaved data will be lost).  Re-login and you should be able to select your highest resolution.

---

### Post by Orbital75 on 2007-08-07
Thank you.....

---

### Post by Orbital75 on 2007-08-08
Just thought of something...... I'm using  Ubuntu in VirtualBox.
I'm assuming it's using a Generic driver since it's in a virtual machine.
Will changing these settings to my normal nvidia card break something?

Thanks

---

### Post by Rocket2DMn on 2007-08-08
It shouldn't, but you can always restore your old xorg.conf file if it does.
Before you upgrade, make a backup of your current xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
After you install the restricted nvidia drivers, you should be OK, but in case of breakage, you will be stuck at the CLI, just login and run:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then start gdm
```
sudo /etc/init.d/gdm start
    or just
startx
```

I don't anticipate you having to do this.

---

### Post by Orbital75 on 2007-08-08
sound good.  I did the backup as you suggested.
Now you stated that I need to install the Nvida restricted drivers.
How do I go about doing this.

When I search for drivers they have non free beside of them.
I'm new to Linux so all this command line stuff is new to me.
I'm not sure where a lot of stuff is.

What is the name of the package I am looking for
I found nvidia-glx and nvidia-glx-new.
I have a flat panel if that matters.

I should install the drivers before I do anything correct?

Thanks for your help.

---

### Post by Rocket2DMn on 2007-08-08
Have a look here, it tells you how to setup the restricted drivers for nvidia
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

