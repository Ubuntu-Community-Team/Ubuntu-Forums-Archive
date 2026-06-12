---
title: "Uninstallation of an item on Programs menu"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by cags on 2008-02-08
Hey there,

I started properly using Ubuntu last night after a few weeks of tinkering around on my girlfriend's laptop. I went to install the proprietary driver for my ATI card. The installation seemed to work, but when I was clicking on the link for the control panel which appeared on the programs menu I got an error. Not being in front of the computer now I can't recall what the exact error was, but I subsequently tried to reinstall the driver. However, it hangs when it's doing some postprocessing on the kernel. It's possible that the current installation is causing this, I figure, so I was wondering how I can go about totally removing the current installation (thus removing the ATI control panel link from the programs menu).

I took a look at the Synaptic package manager but it doesn't seem to be there. Could I just delete the director under /usr/ where it was installed to?

Any help much appreciated, and I hope I got the right forum :)

---

### Post by jan quark on 2008-02-08
better not to remove any directories in linux by hand it is not windows where everything is in one folder

linux stores the files by type.. so here are all libraries and there are all drivers... and one application can be scattered in many folders

how did you installed the ati driver?
did you used the restricted drivers manager?

---

### Post by cags on 2008-02-08
Hi, thanks for the reply.


To begin with I was using the instructions here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat81-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat81-inst.html)

After finally figuring out how to run it as a super-user (:confused:) it seemed to go through fine but then didn't work when I tried to run the control panel. Of course, it would help if I had the exact error message, but it was 2am and I had to go to work the next day so I was pretty wrecked. I'll be sure to check out the message again tonight though.

---

### Post by cags on 2008-02-08
A ha,

I just noticed this on the same page:

# Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
# With super user permissions, enter the command "sh ./fglrx-uninstall.sh" 

I'll give that a try and let you know what happens :)

---

### Post by jan quark on 2008-02-08
I would install the ati drivers via the restricted drivers manager

at the moment I don't know how to undo the installation

PS:just saw your remark concerning the sh script

I am curious too

---

