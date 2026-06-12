---
title: "after updating to restricted ati drivers, no display"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by daarkstaar on 2008-03-02
I have just installed Ubuntu 7.10 on  my machine.  After install, I was prompted to install restricted ATI drivers.  I did so and rebooted.  After reboot, my display no longer works.  I get this error message on my lcd: Input signal out of range - change settings to 1680 x 1050.  Since I cannot see what I am doing after Ubuntu boots, is there a way to reset the display resolution?  I may just reinstall isnce it's pretty quick, but I'd rather not have to.  

ATI x1300
HP w2207 display

---

### Post by Crooksey on 2008-03-02
Press ctrl+alt+F1, then login and run..

```

$ sudo aticonfig --initial
```

---

### Post by daarkstaar on 2008-03-02
After entering above code it returns this message: Found fglrx primary device section. Nothing to do, terminating.

---

### Post by daarkstaar on 2008-03-02
I then tried to change the resolution via:

sudo aticonfig --resolution=0,1680x1050

i get an error that says screen0 does not exist.  i then tried:

sudo aticonfig --initial --input=/etc/x11/xorg.conf   -which returns error: could not ifnd configuration file, please copy conf file template to /etc/x11

any thoughts on how to proceed?

---

### Post by Crooksey on 2008-03-02
```

$ sudo mv /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
$ sudo aticonfig --initial
```

---

### Post by daarkstaar on 2008-03-02
Thanks for the reply.  After entering the code you suggested, I got the Please copy config template to /etc/X11. I think I'm going to reinstall to get it back to normal - I don't need 3d anyway.  I really appreciate your help though-

---

### Post by Crooksey on 2008-03-02
Can you post your xorg.conf up here, im sure i can get it working..

---

### Post by daarkstaar on 2008-03-02
Thanks for the offer, but I just began reinstalling.  I'm in a bit of a hurry - I've got to work on a paper and I need Open Office.  Maybe today wasn't the best day to try out Ubuntu!!

---

