---
title: "Help with Picasa"
date: 2007-09-01
forum: Art &amp; Design
---

### Post by melfindlay on 2007-09-01
So, I set up Picasa on ubuntu, but when I went to run it, I got this error.

/dev/nvidia0 or /dev/nvidiact1 are not accessable.  Picasa will crash if thes files are not accessable.  To fix this, as root, please run:

chmod 666 /dev/nvidia0 /dev/nvidiact1



When I tried to do that through the terminal it told me "no such file or directory"

Can someone please help?

Thanks.:confused:

---

### Post by Dark Hornet on 2007-09-01
Try running the below from a terminal:

sudo chmod 666 /dev/nvidia0
sudo chmod 666 /dev/nvidiactl 

This seems to be a permissions issue, most likely, they are currently set at 660, or something else.

One other thing...when you run these commands, make sure you have CD'd into the correct directory, otherwise you will get the out put of "no such file or directory"....Hope this helps, and good luck

---

### Post by rfruth on 2007-09-01
No prob(s) here, didn't even need the docs :)

[http://picasa.google.com/linux/faq.html#5]("http://picasa.google.com/linux/faq.html#5")

---

### Post by melfindlay on 2007-09-01
I had tried to type "sudo chmod 666 /dev/nvidia0" and "sudo chmod 666 /dev/nvidiactl" in the terminal but that didn't work either. I am downloading from the link that was provided, so we'll see what happens. 

Thanks for your help.  :)

---

### Post by melfindlay on 2007-09-01
> **rfruth said:**
> No prob(s) here, didn't even need the docs :)

[http://picasa.google.com/linux/faq.html#5]("http://picasa.google.com/linux/faq.html#5")

Okay, so i tried that, and it won't let me open the package through the terminal, but that didn't work either. :confused:

---

### Post by rfruth on 2007-09-01
Why open the package at all, download the .DEB file & let their installer do it (no terminal)

---

### Post by Dark Hornet on 2007-09-01
I agree with rfruth, as this is what I did....simply download the link, and let your package handler "open" and install the package...you should have no issues.
Good luck.

---

### Post by rfruth on 2007-09-01
Yes have the installer open the file, don't save to disk ;)

[ATTACH]42324[/ATTACH]

---

### Post by melfindlay on 2007-09-01
> **rfruth said:**
> Why open the package at all, download the .DEB file & let their installer do it (no terminal)

Okay, so I did that and when I tried to run the program after it was installed, I got the same error as before....

/dev/nvidia0 or /dev/nvidiact1 are not accessable. Picasa will crash if thes files are not accessable. To fix this, as root, please run:

chmod 666 /dev/nvidia0 /dev/nvidiact1


So, now what? 

Grr....this is frustrating

:confused:

---

### Post by rfruth on 2007-09-02
Sounds like something is screwed up big time.  I'd start over, delete everything that has to do with Picasa (have a folder named .picasa, remove it) now reboot & reinstall the picasa DEB file (if you need the terminal for anything related to Picasa something is WRONG) if still no joy with Picasa how about GIMP or F-spot :confused:

---

### Post by zhenate on 2007-10-21
I don't think anything is messed up.  I'm getting the same error, but the strange part is that I only get it under 1 user but not another.  I thought it must be a permissions problem, but I changed them to both be in all of the same groups.  Any other ideas guys?  The user I set the installation up with can launch picasa just fine, but the user I created after installation gets this error.  I've tried everything and I cannot get it to work for the user.:confused:

---

### Post by OneST8 on 2008-01-01
I edited ```
/etc/devfs/conf.d/nvidia-kernel-nkc
``` and changed the "0660" to "0666" on both lines.

Probably not the best solution but it works for me.

---

### Post by ibizatunes on 2008-02-06
I have this problem
How do i edit the /etc/devfs/conf.d/nvidia-kernel-nkc 
do i need to be root to modify the permission, ps i dont have a nvidia card, will that command still work?

---

