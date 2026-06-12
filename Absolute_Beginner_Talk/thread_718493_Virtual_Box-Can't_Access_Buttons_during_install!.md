---
title: "Virtual Box-Can't Access Buttons during install!"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-03-08
I have VirtualBox running on Vista.  I am trying to install Ubuntu 7.10, but virtualbox won't expand so that I can access the buttons at the bottom of the screen during the install process.  There's no "slider" that enables me to slide down.  I'm stuck on the setting time zones part.  Anyone know a fix?

---

### Post by bollix47 on 2008-03-08
Try switching to full screen.

Hold down the right CTRL key and press the letter f.

To return to 'normal' screen just repeat the process.

---

### Post by Aurora@FleetBuzz on 2008-03-08
Doesn't work; I have to do this with the cursor inside the virtual machine, right?

---

### Post by bollix47 on 2008-03-08
Inside the Virtual window you press the right CTRL key on your **keyboard** and press the letter f.

---

### Post by Aurora@FleetBuzz on 2008-03-08
Thanks again, but that didn't work.  I'm so new to Vista that I don't know how to create a screenshot to post!

I just can't get to the buttons that move me to the next screen.  I had this issue on my other computers as well (which is why I dual boot!).

Could it be the screen resolution?  I doubt that because the images are fine.

---

### Post by bollix47 on 2008-03-08
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=351226") to see if anything there helps.  It suggests that 'guest additions' might have to be installed.  Also, there's a suggestion that using the HOST key (right ctrl key) and the letter G might work.

If I get time later today I'll try going thru the install on VISTA (currently using Ubuntu) to see if I can duplicate your problem.

> Could it be the screen resolution? I doubt that because the images are fine.

What resolution are you currently running on VISTA?  Can you change it to a higher setting?

---

### Post by Aurora@FleetBuzz on 2008-03-08
Thanks, Bollix47, I'll give it a shot.

---

### Post by bollix47 on 2008-03-08
I just went through the install and on the screen that you had your problem I pressed the tab key once and then enter.  I did not have to as I could see the buttons without problem but used the keyboard anyway.

It will be a good idea to install Guest Additions under Devices once you have Ubuntu running.  (Use the HOST key (right ctrl) to allow your mouse to leave the guest o/s window.)

If you get an error saying it can't install directly you can install it manually.  The cd image for the additions should be on your desktop when doing the following:

Open a terminal.  Applications > Accessories > Terminal


```
cd /media/cdrom
sudo ./VBoxLinuxAdditions.run
```

---

### Post by Aurora@FleetBuzz on 2008-03-08
I'll give it a try on Linux Mint!   I went ahead and re-partitioned and installed Gutsy so now I'm able to dual boot, but my issue now is the wireless connection.  I started this thread for help.

[http://ubuntuforums.org/showthread.php?t=718668](http://ubuntuforums.org/showthread.php?t=718668)

---

