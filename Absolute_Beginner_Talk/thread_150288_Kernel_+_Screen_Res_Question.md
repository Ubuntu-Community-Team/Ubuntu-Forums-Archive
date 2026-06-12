---
title: "Kernel + Screen Res Question"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-25
Hi, I have an AMD 64 process or running Ubuntu 32 bit. I currently have the 386 kernel. Should I install the intel kernel or the AMD one since I kind of have a mix ?

My second question is about the ATi Drivers. I have the drivers set to vesa now and the display doesn't look to good, I have an ATi Radeon Xpress. The drivers say that they are for the X series. Does my card count ?

My third question has to do with screen resolution. My display is currently set to 1024x768. Can I set it to 1264x1024 (I know its not the exact resolution anyone know it). I don't have the option. Can I edit my xorg file to fix it.

---

### Post by trent dillman on 2006-03-25
I would try the ati driver, and afterwards change the res. As for the kernel, if your current one works, it may be best to run with it for a while...

---

### Post by xXx 0wn3d xXx on 2006-03-25
Should I change the res by editing the xorg file ? I don't have the 1240x1024 under screen resolution. I also think the numbers are different.

---

### Post by trent dillman on 2006-03-25
Yes, that's where the changes should be made. 

Did you get the proprietary driver working?

---

### Post by xXx 0wn3d xXx on 2006-03-25
I got the driver working :) Now to edit the xorg file...

---

### Post by trent dillman on 2006-03-25
:)

---

### Post by xXx 0wn3d xXx on 2006-03-25
[QUOTE=trent dillman]:)[/QUOTE]
I can't get the screen resolution to go above 1024x768 but my lcd monitor is 1280x1024. wtf ?

I attached a picture of what it looks like. Does anyone know of a way I can change it ?

---

### Post by trent dillman on 2006-03-25
Edit the sections of your xorg.conf to include the res you want

        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

Then restart your display manager. CTRL+ALT+F2 to command line, login, then

(using gdm/Gnome/Ubuntu)
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

(using kdm/KDE/Kubuntu)
```

sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start

```

If this doesn't work, check your HorizSync and your VertRefresh under the "Monitor" section of your xorg.conf

---

### Post by xXx 0wn3d xXx on 2006-03-25
It didn't work :( sigh...what should I do ?

---

### Post by xXx 0wn3d xXx on 2006-03-25
Can anyone help ? I'm getting ready to install Fedora 5 if I can't get this fixed. I want to test other distros.

---

### Post by xXx 0wn3d xXx on 2006-03-26
Does anyone know how I can change it ? Right now I am reinstalling.

---

